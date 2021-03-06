# socket-chatting-with-AES

## 개요
본 프로그램의 목적은 대칭키 암호화를 적용하여 1:1 양방향 통신을 구현하는 것이다. 
통신 참여자를 서버와 클라이언트로 나눠서 소켓 프로그래밍을 통해 통신을 구현했으며, 상호간에 오가는 모든 메시지는 AES-256암호화를 이용하여 암호화된 상태로 전해진다. 
대칭키 분배 과정에는 RSA가 사용된다. 
서버 또는 클라이언트는 통신을 시작하여 상대를 기다리고 연결이 완료되면, 서버측은 RSA 키 페어를 생성하여 public key를 클라이언트에게 전달한다. 
클라이언트는 연결 후에 AES Key를 생성한 뒤 전달받은 RSA public key를 이용하여 자신의 AES key와 암호화에 사용될 IV를 암호화하여 서버 측에 전달한다.  

## 구동방식
프로그램은 서버 클라이언트 양방향 채팅 프로그램이므로, 양측 모두 원할 때 채팅을 입력할 수 있으며, 모든 메시지는 AES로 암호화되어 넘겨진다. 
암호화된 메시지를 넘겨받으면 가지고 있는 AES key를 이용해 메세지를 복호화하여 출력한다. 입력되는 메시지가 exit라면 양측 프로그램은 종료된다. 

