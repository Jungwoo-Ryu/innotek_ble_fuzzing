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

### 도커 도입 이유
1. 기존에는 Python 라이브러리는 물론, bluez와 같은 시스템 패키지까지 오프라인 PC의 환경에 맞춰 수동으로 설치하고 버전을 관리해야 하는 '의존성 지옥(dependency hell)'의 문제가 있었습니다. 하지만 Docker 도입 후, 온라인 환경에서 모든 의존성이 포함된 실행 환경 전체를 tar 파일 하나로 패키징하여, 오프라인 PC에서는 docker load 명령어 한 번으로 어떤 PC에서든 100% 동일한 환경을 완벽하게 복제할 수 있게 되어 배포 과정이 매우 간단하고 신뢰성이 높아졌습니다.


### 
