# v0.21 웹 펌웨어 준비

Arduino IDE 빌드 폴더에서 다음 파일을 복사합니다.

```text
build/TamaPoke.ino.merged.bin
```

이 폴더에 다음 이름으로 저장합니다.

```text
tamapoke-ko.bin
```

`TamaPoke.ino.bin`만 사용하지 마세요. 애플리케이션 영역만 포함된 파일이라 웹에서 `0x0`으로 설치하면 부팅에 실패할 수 있습니다.
