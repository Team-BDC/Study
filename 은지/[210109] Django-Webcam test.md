# 1. Django에서 Webcam 이용하기

## 1-1. streaminghttpresponse

> https://docs.djangoproject.com/en/3.1/ref/request-response/ 참고
> 브라우저에서 스트리밍 서비스를 구현할 때 사용하는 클래스.

- 장고는 short-lived 리퀘스트를 처리하도록 설계되었다.
  장고에서의 스트리밍 서비스는 response 전체 기간동안 프로세스를 차지하므로, 성능을 매우 안좋게 만든다.
  따라서, 스트리밍 응답을 기다리기보다는, request-response 싸이클 밖에서 스트리밍 동작을 처리하는게 좋다.
- HttpResponse와 다른 API를 사용하지만, 거의 유사하다.
  - byte 문자열을 만드는 iterator를 제공한다.
  - response가 client에게 반환될 때만 컨텐츠에 액세스할 수 있다.
  - content 속성 대신 streaming_content 속성을 갖는다.
    > 데이터를 클라이언트에게 전송해야하므로, 전체 콘텐츠가 반복되지않는 상황에서만 사용해야한다.

## 1-2. cv2

> OpenCV : Open Source Computer Vision Library

    얼굴 인식, 물체 식별, 이미지 결합 등의 작업 가능.

- pip install opencv-python으로 설치ㄴ
- import cv2로 모듈 불러오기

### VideoCapture

> opencv에서 동영상 입력 부분을 관리하는 함수.

- VideoCapture(filename) : 동영상 파일 명 또는 이미지 파일명
  => 저장된 비디오를 불러온다.
- VideoCapture(device) : 연결된 영상 장치 index. 하나만 있는 경우 0
  => 입력 디바이스 순서에 따라 촬영 frame을 받아온다.

### Imencode / Imdecode

> 이미지를 읽을 때, openCV 또는 PIL을 사용할 수 있다.
> openCV의 imencode를 이용, 이미지 파일을 binary 형태로 읽은 후 jpeg로 디코딩할 수 있다.
