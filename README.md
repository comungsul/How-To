# 여기 좀 봐주세요 교수님!!!!

해당 저장소들의 동작 방법입니다.

## 간단한 방법

저희가 EC2 인스턴스 환경에서 구현해 놓았기 때문에 가장 간단한 확인 방법은 아래와 같습니다.

1. `vim main-service.pem` 파일을 생성해 줍니다.
2. 이메일로 보내드릴 main-service.pem 파일을 원하시는 곳에 저장해 주세요.
3. `ssh -i "main-service.pem" ubuntu@ec2-3-34-48-86.ap-northeast-2.compute.amazonaws.com` 로 접속해 주세요.
4. `docker node ls` 로 연결된 노드를 확인해주세요.
5. `docker service ps` 로 서비스를 확인해주세요.
6. [operations](https://github.com/comungsul/operations) 스크립트를 실행을 위해 `cd ~/healthcheck` 로 이동해 주세요.
7. `docker ps` 로 확인할 컨테이너 이름을 확인해 주세요.
8. `python3 healthcheck.py --container-name <컨테이너 이름>` 으로 healthchecker 를 실행해 주세요.
9. 해당 컨테이너가 정상적으로 "Running" 상태이면 유지, 그 외 상태이면 "Restart" 플래그로 재구동 시킵니다.


## 사용자 서비스 확인 절차

도커 실행에 필요한 이미지들은 홍성민(seanhong2000) 도커 허브에 올려놓았습니다.
따라서 필요한 이미지는 pull 될 것입니다. 

로컬에서 해당 서비스 앱을 확인하기 위해서는 아래와 같은 절차를 거쳐야 합니다.

1. [microservice-main](https://github.com/comungsul/microservice-main.git) 저장소를 클론합니다.
2. `git clone https://github.com/comungsul/microservice-main.git`
3. `cd microservice-main` 로 이동합니다.
4. `docker-compose up -d` 로 로컬 환경에 실행해 줍니다.
5. 서브 웹 서비스들은 확인을 쉽게 하기 위해서 ec2 public ip 로 연동 되어있습니다.
6. 따라서 해당 서비스가 작동하는 것은 쉽게 확인하실 수 있습니다.
7. 오늘의 기술 스택에서는 `Prometheus` 등 문자열을 input 태그에 입력해서 출력되는 것을 확인할 수 있습니다. [LiC](https://github.com/comungsul/LiC) 컨테이너 스택은 현재 EC2 인스턴스로 돌고 있어서 Graphql 쿼리를 날려 해당 값을 확인할 수 있습니다.
8. 기타 웹 서비스들은 각 버튼을 클릭해서 서비스를 사용할 수 있습니다. 

## 참고 사항

- Commit User 가 Ubuntu 로 나와있는 사용자는 홍성민 입니다.
- 각 개인이 제작한 서비스에 해당하는 저장소는 별도로 참고 부탁드립니다.
- [기술스택 확인 서비스](https://github.com/comungsul/LiC) - 홍성민
- [healthchecker](https://github.com/comungsul/operations) - 홍성민
- [메일 포털 서비스](https://github.com/comungsul/microservice-main) - 홍성민
- [마켓 서비스](https://github.com/comungsul/shoppingmall) - 배준일
- [스포츠 서비스](https://github.com/comungsul/football) - 한상우
- [일정 관리 서비스](https://github.com/comungsul/dateScheduling) - 임혜진
- [모니터링 서비스](https://github.com/comungsul/swarmprom) - 참고 및 적용 홍성민
- [참고 노션 링크](https://github.com/comungsul/Notion)