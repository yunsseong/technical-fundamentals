# GC
JVM이 더 이상 사용되지 않는 객체를 자동으로 제거하는 메모리 관리 방식입니다. 기본적으로 Mark, Sweep, Compact 단계를 따르며, 메모리는 Young, Old 영역으로 구분되어 세대별로 관리됩니다.
GC는 Serial, Parallel, CMS, G1, ZGC 등 다양한 종류가 있으며, 각각 지연 시간이나 처리량을 기준으로 선택됩니다.

## 대상
- 더 이상 참조되지 않는 객체
- Heap 영역만 해당
```
Person p = new Person();
p = null;
```
- new Person() 객체는 더 이상 참조 되지 않으므로 GC 대상이 됨

## 작동 과정
### 1. Mark
루트(스택, static 변수 등)에서 도달 가능한 객체들을 표시
### 2. Sweep
마킹되지 않은, 즉 도달 불가능한 객체 제거
### 3. Compact
메모리 단편화 방지를 위해 남은 객체들을 한쪽으로 모음

## 세대 구분
JVM은 객체의 생명 주기에 따라 메모리를 구분해서 관리함 
### Young Generation
새로 생성된 객체가 위치

### Old Generation
오랫동안 살아남은 객체가 이동됨

### Permanent / Metaspace
클래스 메타정보 저장 (JDK 8부터 Metaspace로 변경)

## 주요 GC
### Serial
- 단순, 단일 스레드
- 적은 메모리 사용
- Stop-the-world 시간 큼

### Parallel
- 멀티 스레드
- Throughput 좋음
- 짧은 지연시간 요구에 불리

### CMS
- 동시 GC 가능
- 지연시간 짧음
- 메모리 단편화 문제

### G1
- Region 기반
- 균형 잡힌 성능
- 설정이 복잡할 수 있음

### ZGC
- 초저지연
- 실시간 시스템에 적합
- 상대적으로 새로움

## 현대 JDK의 기본 GC
현대 Java JDK에서는 기본적으로 G1 GC를 사용합니다.
G1 GC는 Heap을 Region 단위로 나누어 관리하며, Stop-the-world 시간을 최소화하도록 설계된 GC 입니다.
또한 JDK 15 이상에서는 ZGC, Shenandoah 같은 초저지연 GC도 선택적으로 사용할 수 있습니다.