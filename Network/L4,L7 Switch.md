#### 스위치란?
- 여러 개의 네트워크 장치(컴퓨터, 서버, 프린터 등)를 연결하고 이들 간에 데이터 패킷을 전송과 흐름을 제어한다.

#### 라우터란?
- 라우터란 목적지로 가는 적합한 경로를 찾아주는 라우팅 기능을 제공하는 장치이다.
- 라우터는 L3(네트워크 계층)에 속하는 장치이다. 즉 IP주소를 기반으로 디바이스 위치를 파악하고 통신한다.

#### L4 스위치란?
- L4 스위치는 L4(Transport Layer)에서 동작하는 기능을 제공하며, 로드 밸런싱 역할을 하는 스위치이다.
- L4 스위치는 전송 계층의 헤더 정보를 분석하여 데이터 패킷을 처리하고 전송 방향을 결정한다.

#### L7 스위치란?
- L7 스위치는 L7(Application Layer)에서 동작하는 기능을 제공한다.
- IP, Port 뿐 아니라 Http의 URL, 쿠키 정보 및 바이러스 패턴을 분석하여 보안에 더 유리하고 정교한 로드 밸런싱이 가능하다.
- 다만 데이터 페이로드 분석에 많은 자원 소모를 보여 병목 현상을 일으킬 수 있다.

#### L7이 더좋은 스위치 같은데, L4대신 L7 스위치만 사용하면 되는거 아닌가?
- L7은 데이터 분석을 통해 보안 기능 제공 및 Http 분석을 통해 세밀한 로드밸런싱을 제공하지만, L4에 비해 무겁다는 단점이 있다.
- 굳이 페이로드 분석이 필요없는 로드밸런싱 기능에 중점을 두고자 한다면 L4를 사용하는것이 더욱 효율적이다.

