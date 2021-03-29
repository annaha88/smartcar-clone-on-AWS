# **Smart car pilot clone on AWS**

### 본 프로젝트의 목적
:  빅데이터 하둡 에코시스템을 이용한 스마트카 파일럿 프로젝트를 AWS 위에 올려 구현하는 것
1. AWS 클라우드 시스템의 이해와 구현
2. Hadoop eco system의 이해와 구현

### 소스 코드로서 스마트카 파일럿 프로젝트 선정 배경
   (출처 : https://github.com/wikibook/bigdata2nd)
- 본 프로젝트의 목적은 위에 서술한 것처럼, AWS 클라우드와 빅데이터 하둡 에코시스템의 프로세스를 이해하고 구현해보는 것이 주된 것이다.
- 스마트카 파일럿 프로젝트는 잘 짜여진 설계구조와 검증된 데이터를 가지고 있기에, 정제되지 않은 데이터 문제 등으로 인한 불필요한 사이드 이펙트를 줄이고, 단기간에 본연의 목적인 시스템 이해와 구현에 초점을 맞출수 있다고 판단하였다.


- 프로젝트를 진행하면서, 기존의 운영체제(Window) 위 버추얼박스 CentOS 6 서버 환경을 Reference로 하여, AWS 의 EC2(Amazon Linux 2 AMI) 위주의 서버 환경의 장단점 또한 비교해보려고 한다. 


#### 1. 개발환경 비교 참고
CentOS 8 vs. Amazon Linux 2 - Feature Comparison
참고 출처: https://computingforgeeks.com/centos-vs-amazon-linux-feature-comparison/
