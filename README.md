# 1주차 미션: Django 튜토리얼

## 스터디 자료

[1주차 : Django와 개발 환경 설정](https://yourzinc.notion.site/1-Django-95b587b18097471c9a07e7cb8b2c598b)

## 미션

- [Writing your first Django app](https://docs.djangoproject.com/ko/3.0/intro/tutorial01/)의 Part 1~4 따라합니다.
- 코딩의 단위를 기능별로 나누어 Commit 메세지를 작성합니다.
- 새롭게 알게 된 것을 정리합니다.

## 목표

- Django 의 MTV 패턴을 이해합니다.

## 기한

- 2022년 9월 24일 토요일 </br></br>

---

## 내용 정리

### | Make Project

```bash
django-admin startproject <프로젝트 이름>
```

### | Run Develop Server
- basic
```bash
python manage.py runserver
```
- change port
```bash
python manage.py runserver <포트 번호>
```
- change ip 
```bash
python manage.py runserver <ip>:<port>
```

### | Create App
```bash
python manage.py startapp <앱 이름>
```

### | Project vs App
- 프로젝트 = 웹사이트
- 앱 = 기능의 묶음 (API라고 생각하면 될듯!?)

### | Setting.py
- 프로젝트의 환경설정에 대한 내용을 담고 있음
- 시간대에 맞춰 `TIME_ZONE` 설정 가능
- `INSTALLED_APPS` : 활성화된 모든 어플리케이션
##### ❗ SECRET_KEY는 보안적 이슈를 고려해 env 파일에 등록해서 사용하자

### | model & migration

- model : 데이터베이스의 테이블과 같은 역할
- migrations : django에서 데이터베이스 model의 변화를 적용시킬 때 사용하는 방법
- migrate : 자동으로 데이터베이스 스키마를 관리해주는 명령어
    ```bash
    python manage.py migrate
    ```
  
### | Create Model
- 데이터베이스 애트리뷰트(필드)는 클래스의 인스턴스로서 표현
- 예시
    ```python
  choice_text = models.CharField(max_length=200) # 문자(character) 필드
  pub_date = models.DateTimeField('date published') # 날짜와 시간(datetime) 필드
    ```
  
- 모델 활성화
    ```bash
  python manage.py makemigrations <앱 이름>
    ```
  
- SQL 문 확인
    ```bash
  python manage.py sqlmigrate <앱 이름> 0001
    ```
  
### | Create Admin
```bash
python manage.py createsuperuser
```

### | View
- `HttpResponse` 로 응답
- `HttpResponseRedirect` 를 통해 다른 앱에 바로 요청 보낼 수 있음 

### | Generic View
- View Class
- 코드를 깔끔하게 작성할 수 있음
- 템플릿 느낌