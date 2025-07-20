# innotek_ble_fuzzing


## 리눅스 환경에서의 실행 계획

### 온라인 PC에서 준비

- docker compose build로 두 이미지를 빌드합니다.

```
docker save -o ble_images.tar innotek_intern-sweyntooth:latest innotek_intern-fuzzer:latest 명령으로 이미지 파일을 생성합니다.
```

### 오프라인 리눅스 PC로 이동

- ble_images.tar 파일과 innotek_intern 프로젝트 폴더 전체를 복사합니다.

### 오프라인 리눅스 PC에서 실행

1. (필수) Docker와 Docker Compose를 먼저 설치합니다.

2. `docker load -i ble_images.tar` 명령으로 이미지를 로드합니다.

3. `innotek_intern` 폴더로 이동한 뒤, `docker compose run ...` 명령어로 컨테이너를 실행하고 테스트를 진행합니다.
