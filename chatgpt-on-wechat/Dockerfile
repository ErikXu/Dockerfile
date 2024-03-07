FROM python:3.10-slim-bullseye

RUN apt-get update
RUN apt-get install git -y
RUN git clone --depth 1 --branch 1.5.7.1 https://github.com/zhayujie/chatgpt-on-wechat.git

WORKDIR /chatgpt-on-wechat

RUN apt-get install --no-install-recommends bash ffmpeg espeak libavcodec-extra -y

RUN pip install --no-cache --upgrade pip
RUN pip install --no-cache -r requirements.txt
RUN pip install --no-cache -r requirements-optional.txt
RUN pip install azure-cognitiveservices-speech

CMD ["python", "app.py"]
