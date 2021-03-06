## TCP와 UDP 방식의 비교

- 단편화와 버퍼링 유무에 따라 구분함
- UDP 방식은 일반적으로 512바이트 미만의 페이로드를 대상으로 오직 전송에만 초점을 맞췄기 때문에 단편화롸 버처리 처리과정이 업고 그만큼 지연 발생이 없다.

## TCP

- 데이터 수신의 신뢰성을 보장하기위한 전송 프로토콜
- 3/4 -way handshake를 통해서 본격적인 통신 이전 또는 이후에 연결/ 종료를 확인하는 절차를 수행
- 헤더에 존재하는 플래그를 통해 계솏적으로 동신의 상태를 주고 받음
- 버퍼의 존재로 인해 송신자은 수신자의 수신 확인 응답을 받기전까지 페이로드를 버퍼에 저장후 순차적으로 송신이 가능
- 일련번호와 확인응답 번호를 통해 데이터의 연속성을 보장

- 윈도우를 통해서 전송중에 발생할 오류에 대비

## UDP

- 헤더가 출발지포트,. 목적지포트, 길이, 오류검사 정도로 간단함
- 데이터의 신속성을 위해서 사용
- DNS request에 UDP를 사용
- 신뢰성을 보장하지 않으나 응용계층에서 어느정도 매꿀수 있음
