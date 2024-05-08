# lpu237 history
2023.08.04 부터 기존 history.pdf 문서 firmware 부분 업데이트는 중단 되고. 이 문서로 대체.

## 2024.05.08 - himalia version 2.0
- 암호화 기능 추가.
- 암호화 기능이 활성화 되면, firmwatr 를 download 해야만, 암호화 기능이 비 활성화됨.
- 암호화 기능이 활성화 되면
    * usb hid, usb keyboard, uart interface 에 모두 영향이 미침.
    * msr은 항상 iso 1,2,3 순서로 암호화해서 전송.
    * msr은 항상 combiantion 0 만 적용해서 암호화해서 전송.
    * usb hid interface 에서는 다수의 220 bytes 크기의 report 가 전송되는데, 각 report 앞에 있는 0xE6,0xE6,0xE6 3 bytes 를 제거 후, 전송된 모든 report 를 하나의 바이트 스트림으로 연결 한 후, 이 바이트 스트림의 각 바이트를 2자리 16진수 ASCII 코드로 변경한 문자열은 usbkeyboard, uart interface 에서 전송되는 문자열에서 global pre/postfix를 제거한 문자열과 동일하다.
    * usbkeyboard, uart interface에서 데이타 전송시, global pre/postfix는 항상 전송되고, private pre/postfix 는 무시된다.
    * transaction 마다 변겨되는 인자를 저장하기 위한 flash rom 은 총 1600개가 있음.

## 2024.04.18 - himalia version 1.1
- 부저꺼도 소리나는 문제 수정. off 시 PWM 부저 주파수 수정.

## 2024.04.17 - himalia version 1.0
- ganymede version 5.22 기능을 MH1902T 마이컴에 전부 포팅하고 이름을 himalia 로 붙임.

## 2024.02.26 - ganymede version 5.22.0.1
- ganymede version 5.22.0.1 는 mmd1100_iso_mode 브랜치에서만 얻을 수 있음.
- ganymede version 5.22에서 combination 기능을 모두 삭제해서, flash 메모리 확보.
- ganymede version 5.22에서 mmd1100 송신 버퍼 크기를 줄여서, ram 메모리 확보.
- mmd1100 mode 관련 system parameter 추가.
- 데이터 길이가 짧은 카드에서, mmd1100 을 binary mode 로 동작 시키면, 데이터를 잡음으로 처리해서 무시하는 경우, iso mode 로 변경 하기 위한 업데이트. 그러나 mmd1100를 iso mode 변경하면, 다시 binary mode 로 변경 불가능함. - 엄청 주의
- WIZNOVA 의 report 에 따르면, MMD1100 은 마그네틱 헤드에서 전송되는 첫 8개의 zero 비트를 검출한 후, 1track 은 24 byte(24x8 bits), 2track 은 14byte(14x8 bits), 3track 은 24 byte(24x8 bits) 만큼의 데이터를 카운트 해서, 데이터 개수가 그 미만이면, 잡음으로 간주해서, 무시 한다고 합니다. 즉, ISO1,3 track 최소 8 bits(zero bits) + 192 bits(stx, data, etx ,lrc) + 8 bits(zero bits ) ISO2 track 최소 8 bits(zero bits) + 112 bits(stx, data, etx ,lrc) + 8 bits(zero bits ) 만큼의 데이터 비트가 있어야 마그네틱 카드 데이터를 무시하지 않고, 읽는 다고 합니다. 

## 2023.10.11 - ganymede version 5.22 , callisto version 3.23.
- i-button None Mode 에서, USB keyboard interface 면, i-button 전송범위 선택 가능 추가.
- i-button None Mode 에서, Virtual COM interface 면, i-button 전송범위 선택 가능 추가.
- i-button None Mode 에서, Real COM interface 면, i-button 전송범위 선택 가능 추가.
- 선택 가능한 범위는 0~15(최소 한 개는 선택되야함).

## 2022.11.03 - ganymede version 5.21 , callisto version 3.22.
-	system structure v4.0 을 변경.
-	i-button 제거시, 전송되는 키정의 기능 추가.
-	i-button 데이타에 대한 pre/postfix와 i-button 제거에 대한 pre/postfix 구분 기능 추가.

## 2022.05.09 - [ganymede version 5.20](../lpu237/old_raw/lpu237_5.20.zip)
- M001, M003 type 에서 MMD1100을 Magtek이라고 mapper 에게 알리 주는 버그 수정.

## 2022.03.18 - [ganymede version 5.19](../lpu237/old_raw/lpu237_5.19.zip)
-  MMD1100 reset interval 를 disable(240)으로 하면, 계속 MMD1100을 reset 하는 버그 수정.

## 2022.03.07 - ~~ganymede version 5.18 배포된적 없음.~~
- firmware 크기를 줄이기 위해 IDE 를 LPCXpress v4.1에서 MCPXpresso v11.5로 변경.
- 삭제 되었던 Magtek decoder 지원 코드 추가.
- enter config commnad 에, 현재 연결된 decoder 를 detect 하는 기능 추가.( 기본값은 magtek de-coder, 연결 없으면, magtek decoder 로 인식).

## 2022.02.23 – [ganymede version 5.17](../lpu237/old_raw/lpu237_5.17.zip)
- card reading direction 설정 불가 버그 수정.

## 2022.02.18 – ~~ganymede version 5.16~~
- 다시 적용되는 MMD1100 decoder 지원 추가.
- Magtek decoder 지원 중단.(flash memory 부족)
- MMD1100 decoder 먹통 해결을 위한 HW reset 기능 추가.
- buzzer side effect 회피를 위해 buzzer on 동안 MMD1100 을 reset 시킴.

## 2020.7.21 – [callisto version 3.21](../lpu237/old_raw/lpu237_3.21.zip)
- lpu208 사용자가 통장 포맷 읽기 요청에 따라, combination 관련 부분 활성화.( callisto 는 lpu208 firmware 는 아니지만, ganymede 와 - 동일한 기능을 해야 한다는 규칙에 따라 추가 됨. )
- 모든 트랙 중 정상적인 트랙이 존재하면, 정상 처리 표시(부저 및 LED) 선택 기능 추가.
- ISO1,2 에 같은 데이터가 있으면, ISO2 만 보내는 옵션 추가.
- ISO3,2 에 같은 데이터가 있으면, ISO2 만 보내는 옵션 추가.
- ETXL pattern 이 0xe0 이고, 첫 데이터가 ASCII code 로 변경 했을 때 , ':'(colon) 인 경우, 이 colon 을 전송하지 않을 옵션 추가.(우리증권 테스트 통장 관련 요청으로 )
- CONF_USE_LANGUAGE_SPANISH 제거
- CONF_USE_EQUINSA_DEFAULT 제거
- CONF_USE_WEBANDVISION_DEFAULT 제거
- CONF_USE_GENERAL_DEFAULT 제거
- Util_Msr_Reset() 에 g_MsrObj[i].BaseObj.cLastError = 0 추가(  parity, error correct method 변경 가능하도록, 2 combination 에서 에러 난 후, 정상 읽기 전 까지 계속 에러 나는 것 수정.)

## 2020.7.2 – [ganymede version 5.15](../lpu237/old_raw/lpu237_5.15.zip)
- 버그 수정
- CONF_USE_LANGUAGE_SPANISH 제거
- CONF_USE_EQUINSA_DEFAULT 제거
- CONF_USE_WEBANDVISION_DEFAULT 제거
- CONF_USE_GENERAL_DEFAULT 제거
- CONF_REMOVE_MSR_COMBINATION 제거
- CONF_MSROBJ_ALWAYS_USE_PARITY 제거
- CONF_MSROBJ_ALWAYS_USE_ERROR_CORRECT 제거
- CONF_MSROBJ_ALWAYS_USE_LRC_TYPE 제거
- Util_Msr_Reset() 에 g_MsrObj[i].BaseObj.cLastError = 0 추가
- parity, error correct method 변경 가능하도록, 2 combination 에서 에러 난 후, 정상 읽기 전 까지 계속 에러 나는 것 수정.

## 2020.7.16 – [ganymede version 5.14](../lpu237/old_raw/lpu237_5.14.zip)
-  lpu208 사용자를 위해.
- ISO1,2 에 같은 데이터가 있으면, ISO2 만 보내는 옵션 추가.
- ISO3,2 에 같은 데이터가 있으면, ISO2 만 보내는 옵션 추가.
- ETXL pattern 이 0xe0 이고, 첫 데이터가 ASCII code 로 변경 했을 때 , ':'(colon) 인 경우, 이 colon 을 전송하지 않을 옵션 추가.(우리증권 테스트 통장 관련 요청으로 )

## 2020.7.15 – [ganymede version 5.13](../lpu237/old_raw/lpu237_5.13.zip)
- lpu208 사용자가 통장 포맷 읽기 요청에 따라, combination 관련 부분 활성화.
- 내부 flash 크기가 부족해서 MMD1000 디코더 지원 코드 모두 제거.
- 모든 트랙 중 정상적인 트랙이 존재하면, 정상 처리 표시(부저 및 LED) 선택 기능 추가.

## 2018.7.27 - 버전 관리
* v3.18, v3.19, v3.20, v5.10, v5.11, v5.12 는 아직 필드에 배포되지 않았고, 요청 사항이 기존 v3.17, v5.9 에서 해결 할 수 있는 것으로 판명되서 폐기함. 그러나 버전 관리를 위해서 다음 버전은 v3.21, v5.13 으로 할 예정.

## 2018.7.19 - [ganymede version 5.12](../lpu237/old_raw/lpu237_5.12.zip)
-  re.postfix 값이 04h,59h,04h,62h 이면, 현재 number lock 키가 off 이면 on 하고  04h ,00h, 04h, 59h, 04h, 00h, 04h, 62h, 04h, 00h, 00h, 00h  로 보낸 후 number lock 키 다시 off 하도록 수정.

## 2018.7.19 - [callisto version 3.20](../lpu237/old_raw/lpu237_3.20.zip)
-  re.postfix 값이 04h,59h,04h,62h 이면, 현재 number lock 키가 off 이면 on 하고  04h ,00h, 04h, 59h, 04h, 00h, 04h, 62h, 04h, 00h, 00h, 00h 로 보낸 후 number lock 키 다시 off 하도록 수정.

## 2018.7.11 - callisto version 3.19 : 내부에서 테스트용으로 만 사용. 미배포.
-  re.postfix 값이 04h,59h,04h,62h 이면, 현재 number lock 키가 on 이면 off 하고  04h,59h,04h, 00h, 04h,62h, 00h, 00h 로 보낸 후 number lock 키 다시 on 하도록 수정.

## 2018.7.11 - ganymede version 5.11 : 내부에서 테스트용으로 만 사용. 미배포.
-  re.postfix 값이 04h,59h,04h,62h 이면, 현재 number lock 키가 on 이면 off 하고  04h,59h,04h, 00h, 04h,62h, 00h, 00h 로 보낸 후 number lock 키 다시 on 하도록 수정.

## 2018.7.11 - [callisto version 3.18](../lpu237/old_raw/lpu237_3.18.zip)
- pre.postfix 값이 04h,59h,04h,62h 이면 usb 키보드 인터페이스에서 04h,59h,00h, 00h, 04h,62h, 00h, 00h 로 보내 던 것을 04h,59h,04h, 00h, 04h,62h, 00h, 00h 로 보내도록 수정( 즉 ALT 키를 계속 누른고 있는 상태에서 키패그 1, 0 키를 눌렀다 띰 )uart 인터페이스에서는 0ah 로 대체헤서 보냄.

## 2018.7.11 - [ganymede version 5.10](../lpu237/old_raw/lpu237_5.10.zip)
- pre.postfix 값이 04h,59h,04h,62h 이면 usb 키보드 인터페이스에서 04h,59h,00h, 00h, 04h,62h, 00h, 00h 로 보내 던 것을 04h,59h,04h, 00h, 04h,62h, 00h, 00h 로 보내도록 수정( 즉 ALT 키를 계속 누른고 있는 상태에서 키패그 1, 0 키를 눌렀다 띰 )uart 인터페이스에서는 0ah 로 대체헤서 보냄.

## 2018.3.16 – [callisto version 3.17](../lpu237/old_raw/lpu237_3.17.zip)
- i-button 접촉시, 씨리얼 번호 보내고, “out” 문자열 보내고, 제거시 “Out” 문자열 보내는 기능 추가.
- Addmit's codestick 의 uart 프로토롤지원.

## 2018.3.16 – [ganymede version 5.9](../lpu237/old_raw/lpu237_5.9.zip)
- i-button 접촉시, 씨리얼 번호 보내고, “out” 문자열 보내고, 제거시 “Out” 문자열 보내는 기능 추가.
- Addmit's codestick 의 uart 프로토롤지원.

## 2017.3.6 - [callisto version 3.16](../lpu237/old_raw/lpu237_3.16.zip)
- i-button 제거 시, keyboard interface 일 때, 선택적으로 “0000000” 전송 가능하도록 기능 추가.

## 2017.3.6 - [ganymede version 5.8](../lpu237/old_raw/lpu237_5.8.zip)
- i-button 제거 시, keyboard interface 일 때, 선택적으로 “0000000” 전송 가능하도록 기능 추가.

## 2016.11.17 – [callisto version 3.15](../lpu237/old_raw/lpu237_3.15.zip)
- 부저 기본값을 2.8KHz( 카운터 값 25000 ) 에서 3.0KHz( 카운터 값 26000 ) 으로 변경.
- 부저 카운터 값을 25000 으로 변경하려하면, 자동으로 26000 으로 세팅 되게 함.

## 2016.11.17 – [ganymede version 5.7](../lpu237/old_raw/lpu237_5.7.zip)
- 부저 기본값을 2.8KHz( 카운터 값 25000 ) 에서 3.0KHz( 카운터 값 26000 ) 으로 변경.
- 부저 카운터 값을 25000 으로 변경하려하면, 자동으로 26000 으로 세팅 되게 함.

## 2015.5.19 – [callisto version 3.14](../lpu237/old_raw/lpu237_3.14.zip)
- i-button 제거 시, keyboard interface 일 때, “0000000000000000”  전송이 선택 사항으로 변경됨.

## 2015.5.19 - [ganymede version 5.6](../lpu237/old_raw/lpu237_5.6.zip)
- i-button 제거 시, keyboard interface 일 때, “0000000000000000”  전송이 선택 사항으로 변경됨.

## 2014.12.8 – [callisto version 3.13](../lpu237/old_raw/lpu237_3.13.zip)
- i-button 제거 시, keyboard interface 일 때, 선택 적으로 F12 만 전송 할 수 있는 기능 추가.

## 2014.12.8 – [ganymede version 5.5](../lpu237/old_raw/lpu237_5.5.zip)
- i-button 제거 시, keyboard interface 일 때, 선택 적으로 F12 만 전송 할 수 있는 기능 추가.

## 2014.11.25 – [callisto version 3.12](../lpu237/old_raw/lpu237_3.12.zip)
- i-button USB HID Vendor interface 추가.

## 2014.11.25 – [ganymede version 5.4](../lpu237/old_raw/lpu237_5.4.zip)
- i-button USB HID Vendor interface 추가.

## 2014.9.18 - [callisto version 3.11](../lpu237/old_raw/lpu237_3.11.zip)
- Global pre/postfix 기능 추가.

## 2014.9.18 - [ganymede version 5.3](../lpu237/old_raw/lpu237_5.3.zip)
- Global pre/postfix 기능 추가.

## 2014.6.12 - [ganymede version 5.2.0.0](../lpu237/old_raw/lpu237_5.2.zip)
- 현재 inteface 가 usb keyboard mode 일 때, ISO2 트랙 최대 길이를 38자(STX, ETX, LRC 포함 하면 41자) 까지 허용하도록 수정.
- PS2 interface 를 제거.
- mmd1100 chip 컨트롤을 HW SPI 엔진을 사용 하던 것을 GPIO를 사용하도록 변경.
- LPU230 REV F.x PCB( ganymede board )에서 Magtek DeltaAsic 및 mmd1100 동시 지원.

## 2014.6.12 - [callisto version 3.10](../lpu237/old_raw/lpu237_3.10.zip)
- 현재 inteface 가 usb keyboard mode 일 때, ISO2 트랙 최대 길이를 38자(STX, ETX, LRC 포함 하면 41자) 까지 허용하도록 수정.
- PS2 interface 를 제거.

## 2013.10.28 - ganymede version 4.8.0.0
- wiznova chip 을 지원하는 첫 C, D, E, F type 통합 펨웨어.

## 2013.09.30 - ganymede version 4.6.0.0
- buzzer 결정 기본 값을 2000에서 1600 으로 변경함.

## 2013.09.05 - ganymede version 4.5.0.0
- MMD1100 magnetic decoder SPI 지원 FW. 이 FW 는 MagTek chip에 사용 할 수 없고, LPU230 PCB Revision F.B or later.  CSS TMSR PCB Revision B or later 에 사용 할 수 있고, PCB 거버를 변경하여 부저에 의한 MMD1100 side effect 를 회피함.
- 프로그램 메모리 부족으로 PS2 interface 삭제.
- vender-defined HID interface 지원.

## 2013.06.17 – callisto version 3.9
- vender-defined HID interface 를 외부에서 사용 할 수 있게 수정.

## 2013.06.14 – callisto version 3.8.3.4
- usb 가 suspend 상태 일때, Uart TX 라인을 강제로 Low 로함.

## 2013.04.15 – ganymede version 4.2.1.4
- MMD1100 magnetic decoder SPI 지원 FW. 
- 이 FW 는 MagTek chip에 사용 할 수 없고, LPU230 PCB Revision F or later. LPU230-1 PCB Revision E or later. LPU230-2 PCB Revision C or later. CSS TMSR PCB Revision B or later 에 사용 할 수 있고, delay 로 부저에 의한 MMD1100 side effect 를 회피함. System 이름이 callisto 에서 ganymede 로 변경됨.

## 2012.10.24 – version 3.8.0.4
- USB 리셋 완료시 부저 4 번 울리던 것을, 1번으로 변경함.

## 2012.09.25 – version 3.7.0.4
- iButton Reader board 지원 기능 추가.
- Device Unique ID 읽기 기능 추가.

## 2012.04.04 – version 3.6.0.4
- PC와의 Interface 가 PS2 일 때, PS2 키보드 연결 및 제거 자동 감지 기능 추가.
- 이 펨웨어는 C002 회로 버전 D 이상에서 만 동작함.

## 2012.02.29 – version 3.5.2.4
- UART OPOS mode 에서 leave 할 때 code missing 수정.

## 2012.02.27 – version 3.5.1.4
- PS 에서 HOST request 에 대하 응답할때 지연시간 추가함.
- USB OPOS mode 에서 leave 할 때 code missing 수정.

## 2012.02.10 – version 3.5.0.1
- 키 사상표 다운하는 부분의 코드 실수 수정.
- PS2 interface 의 timing 수정.
- 정상 모드에서 Hid boot 모드로 변경 할 때, 지연 시간 추가.

## 2012.01.20 – version 3.4.0.1
- lpu237-c002 모델의 i-Button Interface에서, i-Button 제거시 “0000000000000000” 전송함.
- USB OPOS 모드에서 i-Button 읽기 기능 중지.
- 펨웨어 크기 축소를 위해 나라별 키 사상표를 펨웨어에서 삭제하고, PC 로 부터 한 개의  키 사상표 다운받도록 변경.

## 2012.01.18 – version 3.3.0.2
- lpu237-c002 모델를 위한 i-Button Interface 추가.
- lpu237-c002 모델을 위한 TTL RS232 Interface 추가.
- lpu237-c002 모델을 위한 TTL RS232 Interface 를 통한 OPOS Service Object 지원 추가.
- lpu237-c001 과 c002 하드웨어를 자동 구분하는 기능. 추가.

## 2011.12.23 – version 2.2.0.4
* 기존 bootloader 를 HID bootloader 로 변경하면서, 프로그램 시작위치, IVT 위치 수정함, 펨웨어 read lock 해제. HID bootloader 1.0.0.0 추가.

## 2011.11.2 – version 2.1.1.1
* bootloader 실행 시간 변경가능하게 수정. bootloader 실행 시간의 기본값을 15초에서 30초로 변경.

## 2011.11.1 – version 2.1.0.1
* 각 트랙의 prefix / postfix default 값을 변경함.

## 2011.9.14 – version 2.0.1.1
* Usb bus reset 명령시, D+ 1.5K pull-up 저항 그대로 유지.

## 2011.9.9  – version 2.0.0.1
* 기능은 1.8.1.0 과 동일 버전 관리를 위해 버전만 변경.

## 2011.8.17 – version 1.8.1.0
* OPOS 모드 입출시, 부저음.

## 2011.8.17 – version 1.8.0.0
* OPOS 모드 기능 추가.

## 2011.8.16 – version 1.7.0.0
* 카드데이타 전송 함수를 callback 형식으로 변경.

## 2011.7.4 – version 1.6.3.0
* Usb bus reset 명령시, 장비 인식 과정이 끝났으면, D+ 1.5K pull-up 저항 리셋.

## 2011.6.22 – version 1.6.2.0
* 1개 또는 2개의 트랙만 사용 할 때, 미사용 트랙에서의 에러가 에러로 표시되는 코드실수 수정.

## 2011.5.11 – version 1.6.1.4
* MagTek 칩을 이용한 첫 버전.

