# Beacon_RAON
2022 공과대학 학술제 RAON 발표를 위한 비콘 위치추적

# BOT-CLE310
## 회로 배선
비콘들은 3V정도의 전압만 주고 나머지에는 아무것도 꽂지 않는다. <br>
클라이언트는 3V정도의 전압 + GPI도 같은 전압을 준다. 그리고 TX, RX는 코드에 적힌대로 꽂는다. <br>
AT커맨드 할 때는 뭐든지 GPI도 같은 전압을 줘야한다.

## AT커맨드 에러
AT커맨드가 계속 에러나올 때는 <br>
void loop(){ <br>
**while**(mySerial.available()) <br>
  Serial.write(mySerial.read()); <br>
**while** (Serial.available())  <br>
  mySerial.write(Serial.read());<br>
} <br>
에서 if를 while로 바꿔보라

## AT커맨드 짤림
가끔 +K 등 응답이 짤릴 때가 있는데 루프문에 딜레이 10정도 주면 해결 됨, 너무 길면 좀 프레임이 끊긴거 처럼 

## RSSI
새로운 실험 결과 50cm가 넘으면 -69가 꽤 빈번하게 나옴, 그 안에선 -63밑으로 노는 듯, 50cm에선 -63이 적당한듯

# 아두이노 관련 
## 파싱 제대로 안됨
스캔 결과에 USER_DATA하면서 뒤에 이상한 문자가 나와서 그 뒤를 못 읽어서 그런다. <br>
나는 이를 tailOR-headOR가 특정 크기일 때까지 스캔해서 해결하려 한다. 파싱이 제대로 안되면 이는 0이다. <br>

## 루프문 종료
break 말고 exit(0); 
