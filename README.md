# C++ 버전의 remuxing

ffmpeg은 C로 작성되었다. 예제들도 마찬가지다. 
성능적인 장점은 있겠지만, C++의 장점을 잘 살려 메모리 관리나 기능을 확장하는 등의 작업을 진행해보고자 한다.

## 빌드 환경 구성

cmake 기반으로 작성한다. ffmpeg의 remuxing.c 예제로부터 시작할 것이기 때문에 ffmpeg에서 제공하는 라이브러리가 필요하다. 
우선은 윈도우에서 작업을 할 것이기 때문에 [zeranoe](https://ffmpeg.zeranoe.com/builds/, "zeranoe") 사이트에서 
제공하는 개발 및 런타임 리소스를 이용한다. 버전은 4.2.2를 이용한다.

