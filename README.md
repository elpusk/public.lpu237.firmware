# public.lpu23x.firmware

## lpu237 - [history](./doc/history_lpu237.md)
### 2022.11.14
* 버전
  * callisto v3.22 과  ganymede v5.21
* 배포 파일
  * [lpu237_00026.zip](./lpu237/lpu237_00026.zip)
* 배포 파일 내용
  * lpu237_00026.rom - callisto 용 v3.22 와 ganymede 용 v5.21 가 포함된 ROM file.
  * Update 가능 조건 - target device 의 버전이 ROM 파일에 포함된 firmware 버전 보다 높거나 같음.
  * tylenol_3.22.bin - lpu237_00026.rom 에 포함된 callisto 용 v3.22 firmware.
  * tylenol_5.21.bin - lpu237_00026.rom 에 포함된 ganymede 용 v5.21 firmware.
  * 일반적인 상황에서 firmware 를 업데이트 할 때, lpu237_00026.rom 를 사용.
  * A/S 등 기타 상황에서 강제로 firmware 를 업데이트 할 때, tylenol_3.22.bin 또는 tylenol_5.21.bin 를 사용.
* Update program
  * lpu230.exe(Mapper v1.45.0.4 이상 사용). [Installer](https://github.com/elpusk/public.lpu237.software)
  * 업데이트 방법은 Mapper 설치 후, 포함된 Mapper 사용설명서 참고. 
* 변경 내역
  * 내부 system structure v4.0 을 변경.
  * i-button 제거시, 전송되는 키정의 기능 추가.
  * i-button 데이타에 대한 pre/postfix와 i-button 제거에 대한 pre/postfix 구분 기능 추가.

## lpu238 - [history](./doc/history_lpu238.md)
### 2023.08.03
* 변경 내역
  * test case 결과 추가.
  * [lpu238_00001.zip](./lpu238/lpu238_rom00001.zip) 는 수정없이 europa v1.0 으로 release 확정.
### 2023.07.27
* 버전
  * europa v1.0
* 배포 파일
  * [lpu238_00001.zip](./lpu238/lpu238_rom00001.zip)
* 배포 파일 내용
  * lpu238_00001.rom - europa 용 v1.22
  * Update 가능 조건 - target device 의 버전이 ROM 파일에 포함된 firmware 버전 보다 높거나 같음.
  * lpu238_1.0.bin - lpu238_00001.rom 에 포함된 europa 용 v1.0 firmware.
  * 일반적인 상황에서 firmware 를 업데이트 할 때, lpu238_00001.rom 를 사용.
  * A/S 등 기타 상황에서 강제로 firmware 를 업데이트 할 때, lpu238_1.0.bin 를 사용.
* Update program
  * <span style="color:red;">~~lpu230.exe(Mapper v1.46.0.4 이상 사용).~~ - 개발 중.</span>
  * ~~업데이트 방법은 Mapper 설치 후, 포함된 Mapper 사용설명서 참고.~~
* 변경 내역
  * ganymede 용 v5.21 기반
  * flash 용량 부족으로 usb key board interface 삭제.
  * Virtual COM(usb CDC) interface 추가.
  * 장비 인식을 결정하는 USB descriptor 변경으로 USB PID(product ID) 를 0x0214로 설정하고, lpu238 이라는 새로운 model name 생성(참고 - lpu237의 PID 는 0x0206)


## lpu230_update
이 프로그램은 lpu237, lpu238 firmware 를 mapper(lpu230.exe) 설치 없이 변경 할 수 있다.

단, 일반적인 경우, mapper(lpu230.exe)를 통한 firmware update가 권장됩니다.

* 버전
  * lpu230_update.exe v1.2
* 배포 파일
  * [lpu230_update_v1.2.zip](./lpu230_update/lpu230_update_v1.2.zip)
* 배포 파일 내용
  * lpu230_update.exe v1.2 - 실행파일
  * ng_DDL_hid.dll v1.3 - lpu230_update.exe 가 사용하는 dll.
  * tg_rom.dll v1.2 - lpu230_update.exe 가 사용하는 dll.
  * lpu230_update_UM_EN_003.pdf - 영문판 일반 사용 설명서.
  * lpu230_update_UM_KOR_003.pdf - 한글판 일반 사용 설명서.
* 사용방법
  1. [lpu230_update_v1.2.zip](./lpu230_update/lpu230_update_v1.2.zip) 를 다운받아 원하는 폴더에 압축을 해제.
  2. lpu230_update.exe, ng_DDL_hid.dll 과 tg_rom.dll 가 동일한 폴더에 있는지 확인.
  3. 일반 사용 설명서의 내용에 따라 원하는 rom 파일 다운받아 사용.
* 특수 기능 - 아주 예외적인 경우를 제외하고, 아래에 설명하는 기능은 사용자제.
  * lpu237-mw003 model를 lpu238-mw003 model 로 변경하고, interface를 virtual COM으로 설정.
    1. 콘솔에서 -m2 option 으로 lpu230_update.exe 를 실행.( 여기서 virtual COM interface 번호가 2, 1 은 usb vendor defined HID, 0 은 usb keyboard, 10은 read uart)
    ``` 
    lpu230_update -m2 
    ```
    2. "Update" 버튼 실행.
    ![00_start.jpg](./img/00_start.jpg)
    3. "Select rom file" dialog box 에서 "Yes".
    ![01_select_rom.jpg](./img/01_select_rom.jpg)
    4. lpu238_x.rom 파일 선택.
    ![02_select_lpu238.jpg](./img/02_select_lpu238.jpg)
    5. "Selects firmware" dialog box 에서 "europa" 선택.
    ![03_select_europa.jpg](./img/03_select_europa.jpg)
    6. "Notice" message boxdialog box 에서 "Yes".
    ![04_warning.jpg](./img/04_warning.jpg)
    7. upate 진행 중. 기다림.
    ![05_ing_lpu238.jpg](./img/05_ing_lpu238.jpg)
    8. upate 완료.
    ![06_complete_lpu238.jpg](./img/06_complete_lpu238.jpg)
    8. devce manager 에서 Virtual COM 확인.
    ![07_devmgmt_lpu238.jpg](./img/07_devmgmt_lpu238.jpg)


  * lpu238-mw003 model를 lpu237-mw003 model 로 변경하고, interface를 usb keyboard로 설정.
    1. 콘솔에서 -m0 option 으로 lpu230_update.exe 를 실행.( 여기서 usb keyboard interface 번호가 0)
    ``` 
    lpu230_update -m0 
    ```
    2. "Update" 버튼 실행.
    ![00_start.jpg](./img/00_start.jpg)
    3. "Select rom file" dialog box 에서 "Yes".
    ![01_select_rom.jpg](./img/01_select_rom.jpg)
    4. lpu237_x.rom 파일 선택.
    ![12_select_lpu237.jpg](./img/12_select_lpu237.jpg)
    5. "Selects firmware" dialog box 에서 "ganymede" 선택.
    ![13_select_ganymede.jpg](./img/13_select_ganymede.jpg)
    6. "Notice" message boxdialog box 에서 "Yes".
    ![04_warning.jpg](./img/04_warning.jpg)
    7. upate 진행 중. 기다림.
    ![15_ing_lpu237.jpg](./img/15_ing_lpu237.jpg)
    8. upate 완료.
    ![16_complete_lpu237.jpg](./img/16_complete_lpu237.jpg)
    8. devce manager 에서 usb HID 장치 확인.
    ![17_devmgmt_lpu237.jpg](./img/17_devmgmt_lpu237.jpg)

    