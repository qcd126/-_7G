# 창의공학 7조_스마트폰으로 서버를 거쳐, LED를 켜고 끄는 IoT 프로그램

## 앱인벤터
![스크린샷 2023-09-14 185441](https://github.com/qcd126/-_7G/assets/128008018/14c568f6-6b27-4578-8ac0-e8c43f158ed6)
![스크린샷 2023-09-14 185451](https://github.com/qcd126/-_7G/assets/128008018/4c38c59e-2aad-42ce-956e-b85e982835e8)

## **Arduino_code**
```
void setup() {
  pinMode(13, OUTPUT);
  Serial.begin(9600);
}
void loop() {
  if(Serial.available()>0){
    char v = Serial.read();
    if(v=='1') digitalWrite(13, HIGH);
    if(v=='0') digitalWrite(13,LOW);
  }
}
```
### 시리얼 모니터 시현
![스크린샷 2023-09-14 185715](https://github.com/qcd126/-_7G/assets/128008018/ddc381d3-030c-4c09-9176-2703709d71c5)
![스크린샷 2023-09-14 185741](https://github.com/qcd126/-_7G/assets/128008018/a3b5afb2-cb99-4bc1-b347-bb5ac4d83043)

=> 아두이노 보드에 led가 켜졌다(1) 꺼짐(0)

## **Processing_code**
```
import processing.serial.*;
import processing.net.*;
Server s;
Client c;
Serial p;
void setup(){
  p = new Serial(this,"COM3",9600);
  s = new Server(this, 12345);
}
void draw(){
  c =s.available();
  if(c!=null){
    String m=c.readString();
    m = m.substring(m.length()-1);  // 마지막 1문자만 추출하기
    p.write(m);
    if(m.indexOf("1")==0) background(255,0,0);
    if(m.indexOf("0")==0) background(0,0,255);
  }
}
void keyPressed(){
  background(0);
  textSize(64);
  text(key, 30, 70);
  p.write(key);
}
```
## 원격 시현 
![KakaoTalk_20230914_193929479_02](https://github.com/qcd126/-_7G/assets/128008018/83d314df-8f9a-4814-bee0-0b2a1584837c)
### ON
![스크린샷 2023-09-14 190045](https://github.com/qcd126/-_7G/assets/128008018/63b9b78e-1236-40f6-809f-5436369f1c80) <br>
![KakaoTalk_20230914_193929479](https://github.com/qcd126/-_7G/assets/128008018/07b5ea4c-395a-441e-b1c7-662633081a0e)

### OFF
![스크린샷 2023-09-14 190103](https://github.com/qcd126/-_7G/assets/128008018/c9ad9397-53b8-4c14-9e32-af971847005d) <br>
![KakaoTalk_20230914_193929479_01](https://github.com/qcd126/-_7G/assets/128008018/d63087c0-1509-4ca3-97ad-79a90b68f96e)

# <소감>

### 박채연
:프로세싱과 아두이노 코드를 작성하고 서버 통신과 앱인벤터 연결로 스마트폰을 통해 실시간 원격으로 led가 켜지고 꺼지는 것을 볼 수 있었고, 프로세싱 시현 창으로 색깔이 바뀌는 것도 확인 할 수 있어서 재밌고 유익한 프로젝트였습니다. 해보지 못한 것들을 실현해내고 난 후 다른 프로젝트를 통해 IOT를 더 알아가고 싶었고, 더욱 흥미가 커졌습니다.
<br>
### 백지은
:아두이노를 접해보지 못한 저를 팀장이 많이 도와주어 해결해낼 수 있었던 과제였으며, 내가 작성한 소스들이 아두이노와 모니터를 통해 바로바로 작동되는 것을 보니 신기했고 더 재미있던 과제였습니다.
