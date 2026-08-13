# TamaPoke 한국어판 v0.12

| 항목 | 내용 |
|---|---|
| 릴리즈 | v0.12 |
| 배포자 | jjoding |
| 목적 | 영역별 한글 크기·혼합 문자열 실기 검증 |
| 대상 보드 | Waveshare ESP32-S3-Touch-AMOLED-1.75 |

## v0.12 변경 사항

- 한글·영문·숫자 혼합 문자열용 크기별 렌더러 추가
- 작은 라벨·상태 메뉴 목표: 18px
- 일반 문장·버튼 목표: 20px
- 포켓몬·도감 이름 목표: 22px
- 큰 제목 목표: 24px
- 스타팅 포켓몬 이름에 22px 적용
- 메인 포켓몬 이름에 22px 적용
- 메인 상태 메시지에 20px 적용
- SND ON/OFF 및 주요 한글 출력 경로 유지

## Arduino IDE에서 열 파일

압축 해제 후 다음 파일을 엽니다.

```text
TamaPoke/TamaPoke.ino
```

`TamaPoke.ino`와 `pin_config.h`는 반드시 같은 폴더에 있어야 합니다.

## 폰트 파일

```text
TamaPoke/font/ko_fonts.h
```

이 파일에는 18·20·22·24px 글리프 테이블이 포함되어 있습니다. `ko_renderer.h`가 이 파일을 포함하는지 확인합니다.

## 권장 보드 설정

```text
Board: ESP32S3 Dev Module
USB CDC On Boot: Enabled
Flash Size: 16MB
PSRAM: OPI PSRAM
Partition Scheme: Huge APP
```

## 필요한 Arduino 라이브러리

Arduino IDE Library Manager에서 다음 세 라이브러리를 설치합니다.

- GFX Library for Arduino — `Arduino_GFX`
- SensorLib — 터치·RTC
- XPowersLib — 보드 전원관리 칩(PMU)

## 실기 검증 항목

1. 시리얼 로그에 `TamaPoke fw v1.4-ko3-16px`가 표시되는지 확인
2. 설정에서 `KO` 선택
3. 스타팅 포켓몬 이름이 이전보다 크게 보이는지 확인
4. 메인 포켓몬 이름과 상태 메시지의 크기 차이 확인
5. `먹이·행복·에너지·위생` 라벨 확인
6. `소리 켬·소리 끔` 버튼 확인
7. `Lv.`, 숫자, 한글이 섞인 문자열의 기준선과 폭 확인
8. 도감 이름·상세 헤더 확인
9. 진화·작별·도망 버튼 확인
10. 영어 모드로 돌아가 기존 UI가 유지되는지 확인

## 문제 기록 방법

문제가 생기면 다음을 기록합니다.

- 화면 이름
- 표시 문자열
- 한글·영문·숫자 중 어떤 부분이 어긋났는지
- 글자 크기·줄 간격·잘림 여부
- 시리얼 로그
- Arduino IDE와 ESP32 코어 버전

## 주의

- 컴파일된 `.bin`은 포함하지 않은 소스 테스트 릴리즈입니다.
- 업로드 전 시리얼 모니터를 닫습니다.
- 기존 저장 데이터를 보존하려면 전체 Flash Erase를 하지 않습니다.
- 업로드 중 `Connecting...`에서만 BOOT 버튼을 사용하고, 업로드 후에는 누르지 않습니다.
