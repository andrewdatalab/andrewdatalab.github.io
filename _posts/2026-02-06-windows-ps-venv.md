그럼 Windows PowerShell에서 Python venv 설정하는 걸 “완전 처음부터” 차근차근 갈게.
(에러 잘 나는 포인트도 같이 표시할게)

목표

PowerShell에서 venv 생성

venv 활성화

MCP 개발에 필요한 패키지 설치

Claude Desktop에서 쓸 python 경로 확보

STEP 0️⃣ Python 설치 확인 (가장 중요)

PowerShell 열고:

python --version

결과 케이스

✅ Python 3.10.x 이상 → OK

❌ python : The term 'python' is not recognized → Python 미설치 또는 PATH 문제

❌ Python 없을 때

https://www.python.org/downloads/windows/

설치 시 반드시 체크

☑ Add Python to PATH

설치 후 PowerShell 다시 열기

STEP 1️⃣ 프로젝트 폴더 생성
cd $HOME
mkdir nc2-mcp
cd nc2-mcp

STEP 2️⃣ venv 생성

⚠️ 여기서 제일 많이 틀림

python -m venv venv

❌ 자주 나는 에러

python-m ❌
python - m ❌

👉 붙여서 python -m

정상 결과

아무 출력 없음 = 성공

확인:

dir


→ venv 폴더 생성됨

STEP 3️⃣ venv 활성화 (Windows 전용)
.\venv\Scripts\Activate.ps1

성공 시 프롬프트
(venv) PS C:\Users\Andrew\nc2-mcp>
