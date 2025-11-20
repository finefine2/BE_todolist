# TodoList Backend API

FastAPI 기반의 TodoList 백엔드 서버입니다.

## 기술 스택
- **Framework**: FastAPI
- **Database**: SQLite (SQLAlchemy ORM)
- **Python Version**: 3.8+

## 주요 기능
- Todo CRUD 작업 (생성, 조회, 수정, 삭제)
- Category 관리
- Priority 레벨 지원 (High, Medium, Low)
- Due date 설정
- CORS 지원 (프론트엔드 연동)

## 프로젝트 구조
```
BE_todolist/
├── main.py          # FastAPI 앱 및 라우터
├── models.py        # SQLAlchemy 데이터베이스 모델
├── schemas.py       # Pydantic 스키마
├── database.py      # 데이터베이스 연결 설정
├── requirements.txt # 의존성 패키지
└── todolist.db      # SQLite 데이터베이스 파일 (자동 생성)
```

## 설치 및 실행

### 1. 가상환경 생성 및 활성화
```bash
python -m venv venv
source venv/bin/activate  # macOS/Linux
# venv\Scripts\activate   # Windows
```

### 2. 의존성 설치
```bash
pip install -r requirements.txt
```

### 3. 서버 실행
```bash
uvicorn main:app --reload
```

서버는 http://localhost:8000 에서 실행됩니다.

## API 엔드포인트

### Todo 관련
- `GET /todos/` - 모든 Todo 조회
- `POST /todos/` - 새 Todo 생성
- `GET /todos/{id}` - 특정 Todo 조회
- `PUT /todos/{id}` - Todo 수정
- `DELETE /todos/{id}` - Todo 삭제

### Category 관련
- `GET /categories/` - 모든 Category 조회
- `POST /categories/` - 새 Category 생성
- `DELETE /categories/{id}` - Category 삭제

### API 문서
- Swagger UI: http://localhost:8000/docs
- ReDoc: http://localhost:8000/redoc

## 데이터 모델

### Todo
```python
{
  "id": int,
  "title": str,
  "description": str (optional),
  "completed": bool,
  "priority": "high" | "medium" | "low",
  "due_date": datetime (optional),
  "category_id": int (optional),
  "created_at": datetime,
  "updated_at": datetime
}
```

### Category
```python
{
  "id": int,
  "name": str,
  "color": str (hex color code)
}
```

## 개발 정보
- 프론트엔드 Repository: https://github.com/finefine2/FE_todolist
- CORS 설정: localhost:3000, localhost:5173 허용

## 생성 정보
Generated with Claude Code
