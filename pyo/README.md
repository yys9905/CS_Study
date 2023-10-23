## 2023-10-20 금요일
<details>
  <summary> TCP와 UDP 차이점 </summary>
    <div markdown="1">

TCP는 **Transmission Control Protocol**으로, 전송 제어 프로토콜입니다.<br>
TCP는 신뢰성 있는 데이터 전송을 위해 사용되는 **연결지향 프로토콜**입니다.

UDP는 **User Datagram Protocol**으로 사용자 데이터그램 프로토콜입니다.<br>
UDP는 **빠른 데이터 전송을 중요시**하는 **비연결 프로토콜**입니다.<br>
두 단어 모두에게 존재하는 프로토콜(Protocol)이 디지털 장치간의 서로 통신하고 상호작용하기 위한 규칙의 집합입니다.

**TCP와 UDP의 차이점**은 다음과 같습니다:

**신뢰성**:
- TCP는 데이터 손실이나 순서의 뒤섞임이 발생하지 않습니다.
- UDP는 정확성을 확인하거나 재전송을 요청할 수 없기에 데이터가 손실 되거나 순서가 뒤섞일 수 있습니다.

**연결**:
- TCP는 데이터를 전송하기 전에 연결을 설정하고, 전송 후 연결을 해제합니다. 연결 및 해제과정에서 추가적인 오버헤드는 초래할 수 있으나, 신뢰성 있는 통신을 보장합니다. (오버헤드: 데이터전송 및 처리 과정에서 추가 부담이나 리소스 낭비를 뜻함)
- UDP는 연결 및 해제 단계가 없기에 빠른 전송이 가능하지만 데이터의 무결성을 보장하지 않습니다.

**사용사례**:
- TCP는 주로 이메일, 파일 전송과 같이 신뢰성이 중요한 경우 사용됩니다.
- UDP는 실시간 스트리밍, 온라인 게임, 음성통화 같이 데이터 전송 속도가 중요한 경우 사용됩니다.

![TCP의 3way&4way](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbHoWOZ%2FbtsyQSUDDPR%2FzSvULeIM1LJunmoUVinc4k%2Fimg.png)

"SYN"은 "Synchronize"의 약자로 동기입니다.
"ACK"는 "Acknowledgment"의 약자로 승인입니다.
"FIN"은 "Finish"의 약자로 종료입니다. 그 과정을 리눅스를 통해 3way, 4way인 것이 보입니다.
중간의 P의 경우, 패킷의 약자로 데이터 패킷을 전송하는 과정입니다.

**TCP 패킷의 재전송 과정**:
1. 패킷 송신: 송신자는 여러 개의 패킷으로 나눠 수신자에게 보냄. 각 패킷은 고유한 일련번호를 가지고 있습니다.
2. 패킷 수신: 수신자는 패킷을 받고, 패킷의 일련번호를 확인하여 순서대로 재조립합니다.
3. 패킷 손실 확인: 만약 패킷이 손실되었다고 감지하면, 송신자에게 패킷 손실을 알리기 위한 메시지를 보냅니다.
4. 재전송 요청: 송신자는 손실된 패킷을 재전송하고, 이 패킷의 일련번호를 통해 수신자는 어떤 패킷이 재전송된 것인지 판단할 수 있습니다.
5. 패킷 재전송: 재전송된 패킷은 수신자에게 도착하고 재조립합니다.

**TCP 세션 관리 (연결의 설정과 종료 과정) - Easy Version**:
- 연결 설정 (Handshake): 두 컴퓨터 간의 통신을 먼저 연결 설정해야 합니다. 이 단계를 연결 설정 또는 핸드쉐이크라고 부릅니다.
- 데이터 전송: 연결 설정 후, 데이터를 주고 받을 수 있습니다. A는 작은 조각으로 나눠 B에게 보내면 재조립하여 사용합니다.
- 연결 해제 (Termination): 데이터 통신이 끝난 후, 연결을 해제합니다. A는 B에게 끝내고자 하는 의사를 전달합니다. B는 요청을 수락하고 연결이 종료됩니다.

![TCP의 통신방식](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbaYyaw%2FbtsyPwLxTLK%2FOUwLGVUiHYa0ij2pZNQI8K%2Fimg.png)
- 연결 지향 방식, 패킷 교환방식
- 3way handshaking 으로 연결 4way handshaking으로 해제
- 흐름제어 - 송.수신측의 데이터 처리속도 차이 줄이기 위함, receiver가 현재 상태를 sender에게 피드백해 패킷 수를 조절
- 혼잡 제어 - 송신측의 데이터 전달과 네트워크 데이터 처리 속도 차이를 해결 하기 위함
- 높은 신뢰성- 낮은 성능
- 전이중(각각의 독립된 회선 사용), 점대점(1대1통신) 방식
- 각각의 패킷들은 연결되어있으며 번호가 매겨짐
- 신뢰성있는 전송이 필요할때 사용
- 가변길이 헤더
  
![UDP의 통신방식](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F6tEyH%2FbtsyOFvfD9d%2FvQXKydWBR3KTHCKTRvwZc0%2Fimg.png)
- 비연결형 방식, 데이터그램 방식
- 정보를 주고받을떄 신호절차를 가지고 있지 않음
- UDP헤더의 CheckSum 필드로 최소한의 오류 검출
- 낮은 신뢰성 -높은 성
- 각각의 패킷들은 독립되어있다
- 빠른 전송이 필요할때 사용
- 고정 길이 헤더
- 일반적으로는 저런 내용이지만 UDP는 커스터마이징이 가능하며 개발자의 역량에 따라서 UDP를 이용해 TCP와 비슷한 신뢰성 가지게 할 수 있음 ex) QUIC
  </div>
</details>


## 2023-10-23 월요일
<details>
<summary> 비대칭키 암호화, 대칭키 암호화에 대해 간단히 설명해주세요. </summary>
<div markdown="1">
대칭키 암호화는 암호화와 복호화에 같은 키를 사용하는 암호화 방식입니다.

비대칭키 암호화는 암호화와 복호화에 다른 키를 사용하는 암호화 방식입니다.

### 1. 대칭키(비밀키) 암호화

**장점**: 데이터를 암호화하기 위한 연산이 빨라 대용량 데이터 암호화에 적합, 구현이 용이, 기밀성을 제공
**단점**: 키를 교환해야하는 문제, 탈취 관리 걱정, 사람이 증가할 수록 키 관리가 어려움, 확장성 떨어짐

- 하나의 비밀키를 서버와 클라이언트 모두 함께 사용
- 암호화와 복호화에 같은 키를 사용하는 방식
- 비밀키 하나만 알아내면 암호화된 내용 해킹 가능
- 속도가 빠르다는 장점이 있지만, 키를 교환해야 한다는 문제가 있어서 중간에 탈취 당해 해킹당할 수 있다.
- (위험한 이유: 처음 상대방에게 대칭키를 전송하는 과정에서 탈취당하면 통신 내용 모두 해킹 가능)
- 서로 키를 보관해야 하기 때문에 관리해야 할 키가 방대해질 수 있다.

![대칭키(비밀키)](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FGTeWO%2Fbtsy2oZWZpu%2FTuxdc1d3GLkKjLF0shMa3K%2Fimg.png)

**대칭키(비밀키) 암호화의 종류**

- DES(Data Encryption Standard): 64-비트 블록 암호, 56-비트 비밀키 사용
- AES(Advanced Encryption Standard): 128-비트 블록 암호, 안전성 문제로 인해 DES 대체
- 아리아(ARIA): 한국에서 개발된 128-비트 블록 암호
- 시드(SEED): 한국에서 개발된 128-비트 블록 암호

### 2. 비대칭키(공개키) 암호화

**장점**: 키 분배 및 키 관리 용이, 기밀성/인증/부인 방지 기능 제공
**단점**: 속도가 느림, 상대적으로 키의 길이가 길다

- 공개키와 개인키(비밀키) 두 개를 가지고 있음
- 공개키는 모든 사람이 접근 가능한 키
- 개인키는 각 사용자만이 가지고 있는 키
- 공개키는 누구나 알 수 있지만, 그에 대응하는 개인키(비밀키)는 키의 소유자만이 알 수 있다. 특정 비밀키를 가진 사람만이 내용을 열어볼 수 있도록 하는 방식.
- (안전한 이유: 공개 키로 누구든지 암호화해서 보낼 수 있지만, 복호화가 가능한 것은 개인키를 가진 사람뿐 - 반대 상황도 가능)

![비대칭키(공개키)](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fd8dYeE%2Fbtsy2or8Ca4%2FubcsvZYNPX9ek7WqNrj920%2Fimg.png)

**비대칭키 암호화 종류**

1. RSA: 가장 대표적인 공개키 암호화 알고리즘, 소인수분해 문제의 해결이 어려운 점을 이용
2. DSA (Digital Signature Algorithm): 전자 서명을 위해 사용되는 암호화 방식
3. ECC (Elliptic Curve Cryptography): 타원 곡선 이산대수 문제를 기반으로 하는 공개키 암호 알고리즘, 무선 인터넷, 스마트 카드 등의 제한된 환경에 적합

![비밀키/ 공개키 요약표](https://file.notion.so/f/f/ca443b80-1159-4dfd-b76f-00521933db07/aa2e76fc-9f93-4f08-b806-977ad86580cc/Untitled.png?id=7af9ad0f-79d5-473e-9a47-59031ce9d3f8&table=block&spaceId=ca443b80-1159-4dfd-b76f-00521933db07&expirationTimestamp=1698192000000&signature=9TsxVUWaxV4nljm9bKXwNg4Tgy3uZNRU2dRUi7ri5BE&downloadName=Untitled.png)
</div>
</details>
