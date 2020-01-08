# Anti-debug

### 1. IsDebuggerPresent 함수

​	가장 기본적인 Anti-debugger

​	windows.h 헤더 파일에 있다.

### 2. NtGlobalFlag

​	PEB에서 0x68 위치에 존재하는 값

​	디버깅 중일 경우 이 값이 0x70으로 설정

​	![NtGlobalFlag](https://github.com/aht7525/aht7525.github.io/blob/master/img/ntglobalflag.PNG?raw=true)

### 3. CheckRemoteDebuggerPresent

​	![CheckRemoteDebuggerPresent](https://mblogthumb-phinf.pstatic.net/MjAxNzA4MTBfMTYg/MDAxNTAyMzYyMjk2MTE2.AubJAAXo-q6VgN82SqWFxdA-OaeSu7MrwC5nYdppjScg.rMYi1hT2fqRW-l4iEkxB9WtK-xEgFsR99ySPqWLjegIg.PNG.interr0bang/K-001.png?type=w800)

	### 4. FindWindow

​	![FindWindow](https://mblogthumb-phinf.pstatic.net/MjAxNzA4MTFfNSAg/MDAxNTAyNDE3MTM5MzE5.qhKs4meYG4bMPDcQerIlst56KrJZN5URB9c2Up4vgYAg.xEurVmxryRNxwu9wET21ah5SJ8b_tiohgJsrazObCswg.PNG.interr0bang/K-001.png?type=w800)

​	ex) FindWindow(NULL,L"OLLYDBG");

### 5. NtQueryObject

​	디버깅 중이면 DebugObject라는 객체를 생성

​	이 객체를 탐지하여 방어

​	https://m.blog.naver.com/interr0bang/221079731023

### 6. NtQuerySystemInformation

​	https://m.blog.naver.com/interr0bang/221081447439

### 7. NtSetInformationThread

​	pNtSetInformationThread(GetCurrentThread(), ThreadHideFromDebugger, NULL, NULL);

### 8. OutputDebugString

​	SetLastError와 GetLastError값을 비교

​	디버거가 작동 중이라면 두 값은 같다

### 9. Trap Flag

​	TF를 1로 설정

​	Cpu는 Single Step 모드로 변경

​	SINGLE_STEP 예외를 발생

​	예외가 발생한 경우 TF가 1로 초기화

​	JMP 명령이 실행이 되지 않음, Call 명령 시 step over로 진행

​	https://ruinick.tistory.com/65

### 10. GetTickCount

​	OS 부팅할 때 부터 지나간 시간을 msec 단위로 돌려준다

​	디버깅 할 경우 이때의 시간 차이를 이용하여 보호



### 11. Process32first, process32next

​	![process32](https://github.com/aht7525/aht7525.github.io/blob/master/img/process32.png?raw=true)



추가예정