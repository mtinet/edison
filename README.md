--
맥에서 Edison 세팅하는 방법
--

1. USB 케이블을 에디슨 보드의 FTDI 포트에 연결한다.  FTDI포트는 에디슨 보드의 Micro USB 소켓 앞부분에 새끼 손톱만 한 칩이 붙어 있는 포트이다. 
2. 맥북의 터미널을 연다.
3. Bloop을 설치한다.   
- # sudo npm install -g bloop
4. Bloop의 기본적인 사용 명령어는 다음과 같다. 우리는 SSH를 사용할 것이므로 그냥 bloop ssh 라고 명령하면 자동으로 에디슨 보드에 SSH로 접속해준다. 
- bloop c - 시리얼포트로 콘솔에 연결해준다. 'screen /dev/cu.usbserial.XXXXX 115200 -L'과 동일한 기능을 함
- bloop list - USB serial을 통해 연결되어 있는 에디슨 보드 목록을 출력한다.
- bloop scan - 로컬 네트웍에 연결되어 있는 에디슨 보드 목록을 출력한다. 로컬 네트웍에 여러대의 에디슨이 있으면 첫번째 발견된 보드만 출력해 준다. 만일 전체 목록을 다 보고 싶으면 '-r' 옵션을 붙이면 된다.
- bloop ssh - 로컬 네트웍에 연결되어 있는 에디슨 보드에 ssh로 연결해 준다. 로컬 네트웍에 여려대의 에디슨이 연결되어 있는 경우 '-e' 옵션으로 보드를 지정할 수 있다. ssh연결에 디폴트로는 root 계정으로 연결하도록 되어 있는데 만일 다른 계정으로 접속하려고 하면 '-u' 옵션을 사용하면 된다.
- bloop push - 현재 디렉토리의 내용을 에디슨의 ~/node_app_slot/ 디렉토리에 복사한다. 여기도 bloop ssh와 동일하게 '-e', '-u' 옵션을 사용할 수 있다.
- bloop clean - bloop c를 사용하는 경우 screen 프로세스가 떨어져 재접속 하려고 할 때 "Could not find a PTY"나 "Resource Busy" 에러가 나는 경우가 있다. 이럴때 bloop clean 명령을 내리면 떨어져 나간 세션을 전부 삭제해 bloop c로 다시 접속할 수 있게 해 준다. 또는  'bloop c -f' 명령을 내리면 bloop clean + bloop c 와 같은 효과를 낸다.
