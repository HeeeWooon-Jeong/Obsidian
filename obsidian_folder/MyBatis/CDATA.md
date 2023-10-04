
> [!NOTE] <![CDATA[ ... ]]>
> XML 문서 내에서 CDATA 섹션을 정의하는 방법입니다. CDATA는 문자 데이터를 나타내는데 사용되며, 이 데이터는 일반적인 XML 요소와 달리 특수 문자 및 태그를 해석하지 않고 그대로 처리됩니다.

CDATA 섹션은 일반적으로 특수 문자나 마크업을 포함하는 XML 요소 내에서 사용됩니다. 

```xml
<![CDATA[내용]]>
```

- `<![CDATA[ ... ]]>`: CDATA 섹션을 시작하고 종료하는 태그입니다.
- `내용`: CDATA 섹션에 포함된 문자 데이터입니다.

CDATA 섹션은 특히 다음과 같은 상황에서 유용합니다:

1. **특수 문자 포함**: XML 요소 내에 특수 문자(&, <, > 등)가 포함된 경우, CDATA 섹션을 사용하여 이러한 문자를 이스케이프 처리하지 않고 그대로 표시할 수 있습니다.

```xml
<description><![CDATA[This is a <b>bold</b> statement & more.]]></description>
```

2. **대량의 텍스트 데이터**: 대량의 텍스트 데이터를 XML에 포함해야 할 때 CDATA 섹션을 사용하면 이 데이터가 마크업 요소와 상호작용하지 않고 그대로 유지됩니다.

```xml
<text><![CDATA[Lorem ipsum dolor sit amet, consectetur adipiscing elit. ...]]></text>
```

CDATA 섹션은 텍스트 데이터의 원시 형식을 그대로 보존하고자 할 때 유용하며, 특수 문자와 마크업에 대한 이스케이프 처리를 피할 수 있습니다.