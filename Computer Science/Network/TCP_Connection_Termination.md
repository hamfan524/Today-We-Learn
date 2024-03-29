# TCP
>TCP(전송 제어 프로토콜) :  인터넷을 통해 데이터를 전송하기 위해 널리 사용되는 프로토콜입니다.  
이는 신뢰할 수 있는 연결 지향 프로토콜로, 데이터를 전송하기 전에 두 장치 간에 연결이 설정되어야 합니다.  
연결 설정 프로세스에는 `HandShake`라고 하는 일련의 단계가 포함됩니다.

## TCP 3-way handshake
> 두 장치 간에 연결을 설정하는 3단계 프로세스 입니다. 

![image](https://user-images.githubusercontent.com/37105602/226270675-09269903-4313-431b-a935-1c29283289e8.png)


1. SYN : 첫 번째 단계는 `SYN(동기화) 패킷`입니다. 클라이언트는 서버에 SYN 패킷을 보내 연결을 시작하려고 함을 나타냅니다. 패킷에는 연결을 식별하는 데 사용되는 임의의 시퀀스 번호가 포함되어 있습니다.

2. SYN-ACK : 두 번째 단계는 `SYN-ACK(synchronize-acknowledge) 패킷`입니다. 서버가 SYN 패킷을 수신하면 SYN-ACK 패킷을 다시 클라이언트로 보냅니다. 패킷에는 클라이언트가 보낸 것과 동일한 시퀀스 번호와 자체 임의 시퀀스 번호가 포함됩니다.

3. ACK : 세 번째 단계는 `ACK(승인) 패킷`입니다. 클라이언트가 SYN-ACK 패킷을 수신하면 ACK 패킷을 다시 서버로 보냅니다. 이 패킷에는 SYN-ACK 패킷의 시퀀스 번호에 1을 더한 값이 포함되어 있습니다.

### 요약  
```
3 way handshake는 두 대의 컴퓨터가 일련의 메시지를 교환하여 서로 연결을 설정하는 프로세스입니다.

마치 두 사람이 전화로 

C - "여보세요? 내 말 들려요?"

S - "네, 들려요."

C - "좋아요. 이야기를 시작해 볼까요?"

라고 말하는 것과 같습니다.
```


## TCP 4-way handshake
> 연결을 종료하는데 사용되는 4단계 프로세스입니다.

![image](https://user-images.githubusercontent.com/37105602/226270830-237f1905-3b50-4b65-8887-02646c13dba4.png)

1. FIN : 첫 번째 단계는 `FIN(종료) 패킷`입니다. 연결을 종료하려고 할 때 클라이언트에서 FIN 패킷을 서버로 보냅니다.

2. ACK : 두 번째 단계는 `ACK 패킷`입니다. 서버가 FIN 패킷을 수신하면 ACK 패킷을 다시 클라이언트로 보냅니다. (이때 모든 데이터를 보내기 위해 CLOSE_WAIT 상태가 됩니다.)

3. FIN : 그런 다음 서버는 자신의 `FIN 패킷`을 클라이언트로 보내 연결을 종료할 것임을 나타냅니다.

4. ACK : 마지막으로 클라이언트는 FIN 패킷을 수신하고 확인했다는 `ACK 패킷`을 서버로 다시 전송합니다. (아직 서버로부터 받지 못한 데이터가 있을 수 있으므로 TIME_WAIT을 통해 기다립니다.)
    - 서버는 ACK를 받은 이후 소켓을 닫습니다 (Closed)
    - IME_WAIT 시간이 끝나면 클라이언트도 닫습니다 (Closed)

이렇게 4번의 통신이 완료되면 연결이 해제됩니다.


### 요약  
```
4 way handshake는 두 대의 컴퓨터가 일련의 메시지를 교환하여 서로 연결을 종료하는 과정입니다.

마치 두 사람이 전화로 

C - "좋아, 얘기 다 했어."

S - "알았어, 들었어"

S - "사실 나도 끝났어"

C - "알았어, 안녕!"

라고 말하는 것과 같습니다.
```

### Reference

https://sjlim5092.tistory.com/35