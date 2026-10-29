# 기본 이미지 설정
# alpine : Alpine Linux 기반
FROM python:3.8-alpine
# Alpine 패키지 인덱스 갱신
RUN apk update && apk add --no-cache bash
# C/C++ 빌드도구, Python 개발헤더, pip 관련 패키지 설치
RUN apk add --update build-base python3-dev py-pip
# 컴파일 과정에서 라이브러리를 검색할 경로 지정
ENV LIBRARY_PATH=/lib:/usr/lib
# Flask CLI가 사용할 애플리케이션 모듈 지정
ENV FLASK_APP=py_app
# Flask의 개발환경 설정
ENV FLASK_ENV=development

# 컨테이너 내부 작업 디렉토리 설정
WORKDIR /py_app

# 호스트의 app 디렉토리 내용을  컨테이너 작업 디렉토리로 복사
COPY ./app .
# python 의존성 패키지 설치
RUN pip install -r requirements.txt
# 컨테이너 실행 시 기본 실행 프로그램 지정
ENTRYPOINT ["python"]
# ENTRYPOINT에 전달할 기본 인수 지정
CMD ["py_app.py"]

# FROM -> RUN -> ENV -> WORKDIR/COPY -> RUN pip install -> 이미지 완성