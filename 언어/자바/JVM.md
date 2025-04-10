# JVM
- JVM은 Java 바이트 코드를 실행하는 가상 머신
- 클래스 로더, 실행 엔진, 런타임 데이터 영역, 네이티브 인터페이스로 구성
- 런타임 데이터 영역은 Heap, Stack, Method Area 등을 포함
- 실행 엔진은 인터프리터와 JIT 컴파일러로 성능을 최적화
- GC를 통해 메모리를 자동으로 관리하고, JNI를 통해 네이티브 코드와 연동

## JVM 구성 요소
### 클래스 로더 시스템 (Class Loader Subsystem)
- .class 파일(바이트코드)을 JVM으로 로딩하는 역할
- 단계
  - 로딩 (Loading) : 클래스 파일을 읽음
  - 링크 (Linking) : 검증/준비/해결 수행
  - 초기화 (Initialization) : static 초기화 블록 실행

### 런타임 데이터 영역 (Runtime Data Area)
- Heap : 객체, 배열 등 동적으로 생성된 데이터 저장 (GC 대상)
- Stack : 각 쓰레드마다 존재, 메서드 호출 시 지역 변수와 함수 호출 정보를 저장
- Method Area : 클래스 정보, static 변수, 메서드 코드 저장
- PC Register : 각 쓰레드가 실행 중인 명령의 주소 저장
- Native Method Stack : 자바 외 JNI 등의 네이티브 코드 실행용 스택

### 실행 엔진 (Execution Engine)
- 바이트코드를 기계어로 변환하고 실행
- 구성
  - 인터프리터 : 바이트코드를 한 줄씩 실행
  - JIT 컴파일러 : 자주 실행되는 코드를 네이티브 코드로 변환해 성능 향상
  - GC (Garbage Collector) : Heap 영역의 객체 자동 정리

### 네이티브 인터페이스 (JNI, Java Native Interface)
- C/C++ 같은 플랫폼 종속 코드를 Java에서 사용할 수 있도록 해주는 연결 통로
