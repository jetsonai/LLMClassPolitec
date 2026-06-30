
# 📸 영상 상황 분석 에이전트 프로젝트 ( Agent v1.0)



## 🛠️ 개발 환경 및 필수 패키지 설치

본 프로젝트는 Anaconda 가상환경(`ai_agent`) 환경에서 테스트 및 최적화되었습니다.

### 1. 가상환경 활성화 및 필수 라이브러리 설치
터미널 또는 Anaconda Prompt를 열고 프로젝트 폴더로 이동한 뒤 아래 명령어를 순서대로 실행하세요.

```bash
# 가상환경 활성화 (본인의 환경 이름으로 변경 가능)
conda activate ai_agent

### 2. PyTorch 설치 (노트북 환경별 선택)
허깅페이스 관련 라이브러리 의존성 해결을 위해 PyTorch 설치가 필수적입니다. 본인의 하드웨어 사양에 맞춰 한 가지만 선택하여 설치하세요.

NVIDIA GPU(예: RTX 5070 등) 가속 환경 노트북:

```python
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu132
```
일반 강의장 및 사무용 노트북 (CPU 전용 환경):

```python
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu

```


# LangGraph, Streamlit 등 핵심 패키지 설치
```
pip install langgraph langchain-core langchain-openai langchain-community langchain-text_splitters chroma4py
pip install streamlit pillow python-dotenv fastapi 
pip install langchain-ollama python-multipart
pip install ultralytics opencv-python faiss-cpu langchain-huggingface sentence-transformers
```

## 필드 설명
class SituationAgentState(TypedDict):
    messages: Annotated[list, add_messages]
    id: str         
    user_id: str          
    team_id: str                
    image_path: str          
    reg_date: str            
    items: List[Dict[str, Any]] 
    detected_item_count: int  
    memo: str                
    result_status: str       
    vision_raw_text: str     
    annotated_image_base64: str  # [추가] 박스/텍스트가 그려진 이미지
    final_report: str 
    

### BackEnd 실행 방법

```powershell
# 가상환경 상에서 실행
cd ..\backend
python -m uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```
#### Swagger 확인 (웹)

```python
http://localhost:8000/docs
```

### FrontEnd 실행 방법

```python
# 가상환경 상에서 실행
streamlit run app.py
```

### 관리자 페이지 실행 방법

```bash
# DB에 저장된 영수증/지출 내역 조회
streamlit run admin_app.py
```

### Streamlit GUI 사용 가이드

```python
# 가상환경 상에서 실행
cd ExpenseGraph
streamlit run app.py
```

### FrontEnd GUI 

#### user GUI 

<img width="473" height="427" alt="image" src="https://github.com/user-attachments/assets/3e7d80a1-65c3-4f77-97b5-80dff2152d7d" />


### 🌐 브라우저에서 FrontEnd 확인 및 권한 테스트 방법

Streamlit이 실행되면 브라우저 창(http://localhost:8501)이 자동으로 열립니다.

pdf 문서를 올리고 FAISS DB 를 생성

이미지를 올리거나 카메라로 이미지 캡처

분석 요청 버튼 클릭

영상 분석 결과 이미지 / 분석 결과 보고서 보기

문의 채팅



