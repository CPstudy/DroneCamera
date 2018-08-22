# 라즈베리파이 스트리밍

## 라즈비안 설치

https://www.raspberrypi.org/downloads/raspbian/에 들어가서`RASPBIAN STRETCH WITH DESKTOP` 다운로드



https://etcher.io/에서 프로그램 설치 후 SD카드에 이미지 넣기



## 라즈비안 한글 설정

```
sudo apt-get install fonts-unfonts-core
```



## 와이파이 설정

1. `기본 설정` - `Raspberry Pi Configuration`
2. `Localisation` - `WiFi Country`를 `US`로 바꿔줌



## 파이 카메라 연결

1. 최신 버전으로 업그레이드

```
sudo apt-get update
sudo apt-get upgrade
```
2. 라즈베리파이 설정에 들어감

```
sudo raspi-config
```

3. 카메라를 enable 시켜줌

```
Interfacing Options -> Camera -> 예
```

4. 재부팅



## VLC

### vlc 설치

```
sudo apt-get install vlc
```

### 카메라 실행

```
raspivid -o - -n -t 0 -w 640 -h 360 -fps 25|cvlc -vvv stream:///dev/stdin --sout '#standard{access=http,mux=ts,dst=:8090}' :demux=h264
```



## GStreamer

