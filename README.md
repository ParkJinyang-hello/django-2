# 1단계 Django 프로젝트 생성
    - django-admin.exe startproject myproject .
# 2단계 어플리케이션 생성
    - django-admin startapp myapp
# 3단계 어플리케이션 등록
    - settings.py
# 4단계 모델 정의
    - myapp/model.py
# 5단계 데이터베이스 마이그레이션   
    - python manage.py makemigrations 
    - python manage.py migrate
# 6단계 관리자 패널에 모델 등록
    - myapp/admin.app
# 7단계 슈퍼유저 생성   
    - python.exe .\manage.py createsuperuser
# 8단계 서버 실행   
    - python.exe .\manage.py runserver
    - localhost:8000/admin
# 9단계 관리자 화면에서 데이터 입력
    - 임의의 데이터 2개 입력
# 10단계 데이터 조회
    - myapp/views.py
# 11단계 URL 설정
    - myproject/urls.py
    - myapp/urls.py
# 12단계 템플릿 생성
    - myproject/templates/myapp/post_list.html
# 13단계 템플릿 경로 생성
    - myproject/templates 생성
    - myproject/settings.py
        TEMPLATES = [
            ....
            'DIRS' : [BASE_DIR / 'templates'], # 템플릿 디렉토리 설정 ]
# 14단계 데이터 베이스 설치
    - PostgreSQL 설치
    - 환경변수에 C:\Program Files\PostgreSQL\17\bin\ 등록 후 vscode 재시작
    - 데이터베이스 생성
        - psql -U postgres
        - create database mydatabases;
# 15단계 psycopg2 설치
    - pip install psycopg2-binary
# 16단계 DB 설정 변경
    - myproject/settings.py
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'mydatabases', # 데이터 베이스 이름
        'USER' : 'postgres', # 데이터 베이스 사용자
        'PASSWORD' : 'admin1234' # 데이터 베이스 비밀번호
        'HOST' : 'localhost', # 데이터 베이스 호스트
        'PORT' : '5432' # 데이터 베이스 포트
    }
}
```

# 17단계 마이그레이션
    - python manage.py makemigrations
    - python manage.py migrate
    ```
    postgreSQL은 별도 DB서버에서 동작 Django에는 sqlite3처럼 db파일이 없음
    데이터 베이스 연결 확인
        python manage.py shell

        from myapp.models import Post
        Post.objects.all()

    생성한 데이터베이스로 접속
    psql -U postgres -d mydatabases
    \dt
    ```
# 18단계 db.sqlite3 삭제
# 19단계 superuser 생성
    - migrate 실행
# 20단계 사용별로 권한 부여
    - 그룹생성
    - 사용자에게 그룹을 할당
    - 뷰에서 권한을 확인
    - 템플릿에서 권한에 따른 메뉴 표시