# Python 3.10 버전을 기반으로 이미지 생성
FROM python:3.10-slim

# 작업 디렉토리 설정
WORKDIR /app

# 현재 폴더의 모든 파일을 컨테이너의 /app 폴더로 복사
COPY . .

RUN apt-get update && apt-get install -y gcc make linux-headers-generic bluez

# requirements.txt에 명시된 파이썬 라이브러리 설치
RUN pip install -r requirements.txt

# 컨테이너가 시작될 때 기본으로 실행될 명령어 (bash 셸 실행)
CMD ["bash"]
