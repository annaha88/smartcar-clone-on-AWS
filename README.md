# **Smart car pilot clone on AWS**

### 본 프로젝트의 목적
:  빅데이터 하둡 에코시스템을 이용한 스마트카 파일럿 프로젝트를 AWS 위에 올려 구현하는 것
1. AWS 클라우드 시스템의 이해와 구현
2. Hadoop eco system의 이해와 구현

### 소스 코드로서 스마트카 파일럿 프로젝트 선정 배경
   (출처 : https://github.com/wikibook/bigdata2nd)
- 본 프로젝트의 목적은 위에 서술한 것처럼, AWS 클라우드와 빅데이터 하둡 에코시스템의 프로세스를 이해하고 구현해보는 것이 주된 것이다.
- 스마트카 파일럿 프로젝트는 잘 짜여진 설계구조와 검증된 데이터를 가지고 있기에, 정제되지 않은 데이터 문제 등으로 인한 불필요한 사이드 이펙트를 줄이고, 단기간에 본연의 목적인 시스템 이해와 구현에 초점을 맞출수 있다고 판단하였다.


- 프로젝트를 진행하면서, 기존의 운영체제(Window) 위 버추얼박스 CentOS 7 서버 환경을 Reference로 하여, AWS 의 EC2(CentOS 7) 위주의 서버 환경의 장단점을 비교해보려고 한다. 


#### 1. 개발환경 비교
CentOS 8 vs. Amazon Linux 2 - Feature Comparison
: 기본적으로 같은 origin(Redhat) base 라 진행에 무리가 없다고 판단하고, Amazon Linux 2 로 운영체제를 선택하겠다.
참고 출처: https://computingforgeeks.com/centos-vs-amazon-linux-feature-comparison/
-> AWS에서도 CentOS 7을 지원하니 CentOS로 선정하는 것으로 변경하겠다.

#### 2. Cost Estimation
- Amazon CentOS 7 (m4.large cpu:2, 메모리: 8gb), 3대 : 3 instances x 0.123 USD x 730 hours in month = 269.37 USD (monthly onDemand cost) * 한달 내내 돌릴경우
- 아래 주소에서 AWS 서버 운용에 대한 cost 를 추산해볼수 있다.
https://calculator.aws/#/addService

#### 4. Putty를 이용하여 생성된 ec2 인스턴스 접근
- AWS 콘솔에서 키페어 생성후, 다운받은 pem 키를 putty gen 을 이용하여 ppk 로 변환 후, putty 를 이용해 ec2 인스턴스에 접속할수 있다
- CentOs 인스턴스의 경우에 username은 centos 이다.(다른 경우, 보통 ec2-user나 ubuntu)
- cloudera 설치를 위해서 root 접근 권한을 추가해서 root 로 접속할수 있다. 

#### 3.Installing Cloudera Manager on EC2
https://docs.cloudera.com/documentation/manager/5-1-x/Cloudera-Manager-Installation-Guide/cm5ig_install_on_ec2.html
https://aws.amazon.com/ko/quickstart/architecture/cloudera/

- 결론적으로 cloudera installing 부터 실패하였다.**(21.3월 기준)**
- 이유는, 클라우데라 정책 변경으로 인해, 21년 1월 기준으로 모든 소프트웨어 접근에 subscription이 필요하게 되었다. 
- subscription은 클라우데라에 따로 컨택이 필요하다.
- AWS 가 아닌 로컬환경에서 예전에 진행했던 내용을 정리해서 Update 해두어야 겠다.

## AWS 클라우드 방식의 장단점(기본적인 환경 구성에 대해서만)
1.장점
- 로컬 리소스가 충분치 않은 경우, 초기 비용 없이 프로젝트를 시작할수 있다.
- 원하는 운영체제로 쉽게 바꿔가며 구성해볼수 있다.(CentOs, Ubuntu, Amazon Linux etc 거의 모든 운영체제 지원), EBS 스토리지를 추가로 붙이기도 쉽다.
- CloudFormation 등의 서비스를 이용하면, 비교적 쉽게 스택 구성을 할수 있다.
 
2.단점
- 항상 원치 않은 과금을 고려해야 한다.\
     : 기본적으로 클라우데라를 돌리기 위해서는 16gb 정도의 메모리를 구성하는 것이 좋은데, AWS의 프리티어의 메모리는 1gb정도라, 서버 구성시 최대한 연습을 해봐서 서비스 시간에 따라 과금을 최소화할 plan 이 필요하다. \
     : 이 파일럿 프로젝트의 경우에는 3대의 서버로 클러스터링이 필요한데, 역시 인스턴스 수가 증가하면 그에 따라 과금된다. \
     : 고정 IP를 쓰기 위한 Elastic IP도 과금된다.(하지만, 실사용시 과금율은 상대적으로 크지 않고, 미사용하면서 잡아두는 경우 과금이 더 나가니 주의가 필요)\
- root 설정과 같은 권한 설정을 추가로 작업해줘야한다.\
     : AWS 자체에서 config edit 을 보호하려고 하는 경우가 있기 때문에, 이런 경우 추가적으로 손이 가게 된다.
   





