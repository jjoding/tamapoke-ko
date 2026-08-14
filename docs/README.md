# 다마포케 한국어판 웹 배포

이 폴더는 소스 코드가 아닌 웹 펌웨어 설치 파일을 배포하기 위한 구성입니다.

## 배포 파일

```text
index.html
manifest.json
firmware/tamapoke-ko.bin
```

`tamapoke-ko.bin`은 Arduino IDE 빌드 폴더의 `TamaPoke.ino.merged.bin`을 복사해 이름을 바꾼 전체 플래시 이미지입니다. 부트로더, 파티션, boot_app0, 애플리케이션이 포함되어 있으므로 manifest의 주소는 `0x0`입니다.

## 설치 순서

처음 설치하는 사용자는 반드시 [원작자 TamaPoke 웹 설치 페이지](https://socquique.github.io/TamaPoke/web/)에서 먼저 원본 펌웨어를 설치하고, 원본 페이지의 스프라이트 설치까지 완료해야 합니다. 원본이 정상 작동하는 것을 확인한 뒤 이 페이지로 돌아와 한글 펌웨어를 설치합니다.

한글 펌웨어 설치 시에는 저장 데이터와 microSD 스프라이트를 보존하기 위해 전체 `Erase`를 선택하지 않습니다. 이 페이지는 스프라이트 설치를 지원하지 않습니다.

## GitHub Pages 배포

저장소의 `docs` 폴더에 `index.html`, `manifest.json`, `firmware/tamapoke-ko.bin`을 올리고 `Settings → Pages`에서 `main` 브랜치의 `/docs`를 배포 원본으로 선택합니다.

Chrome 또는 Edge에서 HTTPS 주소를 열어 설치합니다. `manifest.json`의 파일명과 실제 firmware 파일명은 항상 같아야 합니다.

## 원작자 존중

이 한국어판은 socquique의 TamaPoke 프로젝트를 기반으로 한 비공식·비상업적 한국어판입니다. 원본 펌웨어와 스프라이트는 원작자 페이지에서 먼저 설치하며, 원작자 프로젝트와 라이선스의 권리를 존중합니다.
