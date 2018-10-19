+++
date = "2018-10-19T12:30:20+00:00"
title = "[네트워크] TCP의 3HandShake, 4HandShake"

+++
#### 연결 

1\.처음에 SYN을 보낸다 (Seq = 10) 전송. 

2\.받는쪽에서 SYN + ACK (ACK = 11 —> 처음에 보낸 seq + 1 , Seq = 50 )를 전송 

3\.다시 돌아와서 ACK를 보낸다 (Seq = 11, ACK = 51) 

#### 종료 

1 FIN -> 전송 

2  ACK <- 전송 

3 FIN <- 전송a 

4 ACK-> 전송 