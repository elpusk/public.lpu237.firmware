# public.lpu237.firmware

## 2022.11.14
* 버전
  * callisto v3.22 과  ganymede v5.21
* 배포 파일
  * [lpu237_00026.zip](./lpu237_00026.zip)
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

