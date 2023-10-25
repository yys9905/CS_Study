# CS_Study
2023-10-20 시작
#Contents
1. [네트워크](#네트워크) 1) [TCP와 UDP의 차이점](#tcp와-udp의-차이점에-대해서-설명해보세요-231020)
# 네트워크
## TCP와 UDP의 차이점에 대해서 설명해보세요. (231020)
- 네트워크 통신이 일어나는 과정을 나눈 표준모델인 OSI 7계층 중 4계층 및 TCP/IP 4계층 중 3계층인 전송계층에 있는 전송방식으로 송신자와 수신자를 연결하는 통신 서비스를 제공하는서 사용되는 방법 두가지
### - TCP(Transmission Control Protocol)
- 연결 지향 방식, 패킷 교환방식
- 3way handshaking 으로 연결 4way handshaking으로 해제
- 흐름제어 - 송.수신측의 데이터 처리속도 차이 줄이기 위함, receiver가 현재 상태를 sender에게 피드백해 패킷 수를 조절
- 위 두가지 기능 가능
- 높은 신뢰성- 낮은 성능
- 전이중(각각의 독립된 회선 사용), 점대점(1대1통신) 방식
- 각각의 패킷들은 연결되어있으며 번호가 매겨짐
- 신뢰성있는 전송이 필요할때 사용
- 가변길이 헤더
- 예시 (S:SYN, .:ACK, P:PSH, F:FIN)
![tcpex](https://raw.githubusercontent.com/yys9905/CS_Study/main/yang/image/tcpex.png)
### - UDP(***User Datagram Protocol)***
- 비연결형 방식, 데이터그램 방식
- 정보를 주고받을떄 신호절차를 가지고 있지 않음
- UDP헤더의 CheckSum 필드로 최소한의 오류 검출
- 낮은 신뢰성 -높은 성
- 각각의 패킷들은 독립되어있다
- 빠른 전송이 필요할때 사용
- 고정 길이 헤더
- 예시
![udpex](https://raw.githubusercontent.com/yys9905/CS_Study/main/yang/image/udpex.png)
- 일반적으로는 저런 내용이지만 UDP는 커스터마이징이 가능하며 개발자의 역량에 따라서 UDP를 이용해 TCP와 비슷한 신뢰성 가지게 할 수 있음
ex) QUIC
