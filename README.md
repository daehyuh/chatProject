
일반 웹소켓

![sadfsdaf](https://github.com/user-attachments/assets/90862527-77b3-437f-99a3-ee3411fec8cf)



STOMP

![sadfsdaf4567](https://github.com/user-attachments/assets/a1f9f312-8c10-4c7b-891e-479afaa27fd0)

- Stomp는 websocket과 다르게, 목적지기반 메시지 라우팅 지원
    - 클라이언트와 서버가 특정 주제(topic) 또는 경로를 기준으로 메시지를 교환하는 구조
- 메시지 교환 절차
    - 클라이언트에서 지정된 특정 roomId에 메시지를 발행하면 broker에 의해서 해당 roomId 채널에 메시지가 전달
    - 동시에 roomId를 구독하고 있는 클라이언트에게 실시간으로 메시지가 전달


redis pub/sub을 통해 멀티서버 환경 고려


![asdfsdfsdf](https://github.com/user-attachments/assets/0595c482-2612-44e0-bc30-aeb89b1c5e3c)

- 웹소켓 통신에서 특정 사용자는 특정 서버의 메모리에 의존적이어서, 클라이언트A가 발행한 메시지를 클라이언트B는 다른 서버에 연결되어 받지 못할수 있음
- 이러한 멀티 서버 환경에서 원활한 채팅을 위해서 메시지를 서버에 모두 전파해주는 redis pub/sub기능 사용
- 메시지 발행, 구독 절차
    - 클라이언트는 송신할 메시지를 websocket server에 송신
    - websocket server는 해당 메시지를 곧바로 특정 topic에 메시지를 발행하지 않고, redis의 pub/sub 기능을 활용하여 메시지를 모든 서버에 publish
    - 모든 서버는 redis를 subscribe하고 있기에 redis로부터 발행된 message를 받아서, 본인 서버의 topic에 메시지를 발행
    - 각 서버를 subscribe하고 있는 클라이언트들은 특정 room에 전파된 message를 수신




회원가입, 로그인 (jwt토큰 기반)


![1234](https://github.com/user-attachments/assets/206d4ff7-8d12-4e50-a771-11694bdc4508)

stomp를 활용한 실시간 채팅


![2134weraf](https://github.com/user-attachments/assets/edf06d5b-ee73-418c-978f-cb9baccf9e97)

채팅서비스
-실시간 채팅


![2134weraf](https://github.com/user-attachments/assets/37f06ab8-a65d-414e-b084-dc6c86ea69d6)

1:1 채팅

![sadfsadf678](https://github.com/user-attachments/assets/bdd8dd80-45a3-419e-83f3-dff8db02b34a)

단체 채팅


![asdjfbhjsdaf](https://github.com/user-attachments/assets/7e4fc0d4-39af-4ba5-b8b3-d5ec06d94fae)
