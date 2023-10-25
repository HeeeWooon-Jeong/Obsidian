
>bert-base-uncased 모델 제한 512 토큰 데이터 셋 가장긴 url800토큰 으로 학습 제한



```python
# 데이터 전처리

X = df['url']

y = df['type']
# 레이블 인코딩

label_encoder = LabelEncoder()

y = label_encoder.fit_transform(y)

df['url'].describe()
df["type"].describe()
np.unique(y)
df.info()


```

```python
from transformers import BertModel, BertTokenizer

import torch

  

# Load the pre-trained BERT model and tokenizer

model = BertModel.from_pretrained('bert-base-uncased', output_hidden_states=True)

tokenizer = BertTokenizer.from_pretrained('bert-base-uncased')
device = "cuda:0" if torch.cuda.is_available() else "cpu"

sentence  = 'Hello World!'

  

inputs    = tokenizer(sentence, return_tensors="pt",add_special_tokens=True).to(device)

model     = model.to(device)

outputs   = model(**inputs)

# Define a function to extract features for each transaction

def extract_features(text):

    # Tokenize the text

    input_ids = tokenizer(text, return_tensors="pt", add_special_tokens=True).to(device)['input_ids']

    # Get the hidden states for each token

    with torch.no_grad():

        outputs = model(input_ids)

        hidden_states = outputs[2]

    # Concatenate the last 4 hidden states

    token_vecs = []

    for layer in range(-4, 0):

        token_vecs.append(hidden_states[layer][0])

    # Calculate the mean of the last 4 hidden states

    features = []

    for token in token_vecs:

        features.append(torch.mean(token, dim=0))

    # Return the features as a tensor

    return torch.stack(features)
dftest = url_data.drop(['Unnamed: 0',  'type'], axis=1)

from sklearn.model_selection import train_test_split, cross_val_score, cross_val_predict

  

x = dftest.drop(columns=['url_type','bw'])

y = dftest['url_type']

_,x_data,__,y_data = train_test_split(x,y,test_size=0.15, random_state=52)

x_data.size

tokenizer(x_data.iloc[0]["url"], return_tensors="pt", add_special_tokens=True).to(device)['input_ids'].shape

tokenizer(x_data.iloc[0]["url"], return_tensors="pt", add_special_tokens=True)['input_ids'].shape

# Extract features for each transaction

features = []

for i in range(len(x_data)):

    if len(x_data.iloc[i]["url"]) < 512:

      features.append(extract_features(x_data.iloc[i]["url"]))

    else:

      features.append(extract_features(x_data.iloc[i]["pri_domain"][:511]))

    if i%10000==0:

      print(i)

# Concatenate the features and convert to a numpy array

features = torch.cat(features).cpu().numpy()

```