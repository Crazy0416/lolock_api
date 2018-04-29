# LoLock_API

## LoLock이란

기존 도어락을 스마트하게 만들어 주는 IoT 기기입니다.

등록된 사용자의 출입 기록, 원격으로 도어락 오픈, SMS로 일회용 키를 url로 발급해 원격으로 오픈, 불법 침입 감지 등 다양한 기능을 제공합니다.



## 시연영상 

[유튜브 영상](https://drive.google.com/file/d/15rSLboE11s0tOM-GOkWjteBQhcGrLojL/view?usp=sharing)



## 통신 구조

![통신 구조](https://raw.githubusercontent.com/Crazy0416/lolock_api/master/lolock_api/resource/CommunicationStructure.jpg)

Applicatoin Server가 현재 프로젝트의 서버

Lolock API 서버는 ThingPlug와 안드로이드 어플 사이의 중계서버로 

클라이언트가 다양한 기능을 다룰 수 있게 도와주는 역할을 수행합니다. 



## 서버 아키텍처

![서버 구조](https://raw.githubusercontent.com/Crazy0416/lolock_api/master/lolock_api/resource/serverArchitecture.png)

서버 아키텍처 구조

HTTP 프로토콜로 통신하며 firebase를 통해 푸시 메세지를 보내거나 기상청 API를 이용할 땐 클라이언트 역할을 하여 데이터를 받거나 전송하고 그 외에 기능들은 클라이언트(안드로이드 앱)와 직접적으로 http 프로토콜 통신한다.

ThingPlug와 통신할 때도 ThingPlug가 제공하는 규격대로 http 요청을 보낼 수 있다. ThingPlug 서버가 LoLock API 서버의 주소를 구독하고 있으므로 ThingPlug의 요청을 받을 수 있다.

## Dependency

- 리눅스 환경 (개발환경은 ubuntu 16.04)
- weather_location.c의 out 파일(리눅스 환경 실행파일)
- node.js (개발 환경은 node.js v8.9.4 LTS)
- npm
- [기상청 API](https://www.data.go.kr/dataset/15000099/openapi.do)
- mysql
- config/db_config.json 파일 (mysql 설정 파일)
- firebase 클라우딩 메세지 서버 (푸시 메세지 기능 제공)



## 전제 조건

1. 로락 디바이스를 판매자(우리)가 먼저 DB의 lolock_devices에 등록을 해둔다
2. lolock_devices 등록과 동시에 subscribe를 해둔다. subscribe 이름 : AlldataNoti;
3. 사용자가 로락 디바이스를 구매한 뒤 앱으로 등록을 하게 되면 앱에서 POST 방식으로 /register로 데이터전송 그리고 DB table에 등록한다.

## API 문서

다음을 참고

[API 문서](https://github.com/Crazy0416/lolock_api/tree/master/lolock_api/routes/README.md)

