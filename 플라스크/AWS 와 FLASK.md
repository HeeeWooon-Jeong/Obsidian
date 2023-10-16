Flask는 Python으로 작성된 경량 웹 프레임워크이며, AWS(Amazon Web Services)와 함께 사용할 수 있습니다.
AWS를 사용하여 Flask 웹 애플리케이션을 배포하려면 다음과 같은 단계를 따를 수 있습니다:

1. **EC2 인스턴스 생성:** AWS EC2 (Elastic Compute Cloud) 서비스를 사용하여 가상 서버를 생성합니다. EC2 인스턴스에는 Flask 애플리케이션을 호스팅할 수 있는 환경을 설정해야 합니다.

2. **인스턴스 설정:** EC2 인스턴스를 생성한 후, 필요한 소프트웨어를 설치하고 인스턴스의 보안 그룹 및 네트워크 구성을 구성합니다. 이 단계에서는 웹 서버 (예: Nginx 또는 Apache)를 설치하여 Flask 애플리케이션을 프록시로 사용하도록 설정할 수도 있습니다.

3. **Flask 애플리케이션 배포:** Flask 애플리케이션 코드를 EC2 인스턴스로 업로드하거나 Git 또는 SCP를 사용하여 코드를 배포합니다.

4. **웹 서버 구성:** Flask 애플리케이션을 외부 웹 트래픽에 노출시키기 위해 웹 서버 (Nginx 또는 Apache)를 설정하고 Flask 애플리케이션을 연동합니다. 이 단계에서 웹 서버는 HTTP 요청을 받고 Flask 애플리케이션에 전달합니다.

5. **도메인 구성:** 도메인 네임을 AWS Route 53 또는 다른 도메인 등록 서비스를 사용하여 EC2 인스턴스의 퍼블릭 IP 주소와 연결합니다.

6. **SSL/TLS 설정 (선택 사항):** 보안을 강화하기 위해 SSL/TLS 인증서를 생성하고 설치하여 HTTPS를 사용하도록 설정할 수 있습니다.

7. **로드 밸런서 추가 (선택 사항):** 웹 애플리케이션의 확장성을 향상시키기 위해 AWS Elastic Load Balancer (ELB) 또는 Application Load Balancer (ALB)를 사용할 수 있습니다.

8. **보안 그룹 및 IAM 역할 설정:** 보안 그룹 및 IAM 역할을 구성하여 EC2 인스턴스와 다른 AWS 서비스 간의 보안을 관리합니다.

9. **애플리케이션 모니터링 및 로깅:** AWS CloudWatch와 같은 모니터링 및 로깅 도구를 사용하여 애플리케이션의 성능과 상태를 관찰하고 추적합니다.

10. **백업 및 복구 계획:** 데이터베이스 백업 및 EC2 인스턴스의 AMI(Amazon Machine Image) 백업을 설정하여 데이터 손실을 방지하고 시스템 장애 시 빠른 복구를 수행합니다.

이러한 단계를 따라 Flask 웹 애플리케이션을 AWS에서 배포할 수 있습니다. AWS는 다양한 서비스 및 기능을 제공하므로 웹 애플리케이션을 보다 안전하고 확장 가능하게 배포할 수 있습니다.


---

pyTorch at AWS

(https://pytorch.kr/get-started/cloud-partners/)


---
# AWS로 FLASK

https://tes-b.github.io/aws/flask/AWS_Flask/