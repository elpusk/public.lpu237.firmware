# lpu238 history

## 2024.06.17 - release v1.2
- 안드로이드에서 usb vendor hid interface 사용시, driver 에서 polling 이 없어서, i-button, reset 되는 문제 수정. 최소화를 위해 ibutton start/stop command 추가.

## 2023.10.11 - release v1.1
* i-button None Mode 에서, USB keyboard interface 면, i-button 전송범위 선택 가능 추가.
* i-button None Mode 에서, Virtual COM interface 면, i-button 전송범위 선택 가능 추가.
* i-button None Mode 에서, Real COM interface 면, i-button 전송범위 선택 가능 추가.
* 선택 가능한 범위는 0~15(최소 한 개는 선택되야함).
* Virtual COM interface에서 Real COM를 같이 연결한 상태에서, i-button 이 Addmit Polling 모드이면, 응답이 Real COM 쪽으로 가는 문제 수정. 


## 2023.08.03 - release v1.0
* lpu237 ganymede 용 v5.21 기반으로 제작
* flash 용량 부족으로 usb key board interface 삭제.
* Virtual COM(usb CDC) interface 추가.
* 장비 인식을 결정하는 USB descriptor 변경으로 USB PID(product ID) 를 0x0214로 설정하고, lpu238 이라는 새로운 model name 생성(참고 - lpu237의 PID 는 0x0206)
* lpu237-mw003 H/W 에 만 사용 예정.

