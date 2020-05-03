# [구공팩토리 3기] SNS 미러(90Insta) - django

## 개요
`Instagram Clone(PV ver.)`을 통해서 SNS 웹 사이트의 구조와 프로세스를 분석하고 구현

## 아키텍처
![90Insta_아키텍처](https://user-images.githubusercontent.com/58096698/80915179-8e901800-8d8b-11ea-96f7-dbd73670ccfe.PNG)

## 데이터베이스 ERD
![90Insta_데이터베이스|center](https://user-images.githubusercontent.com/58096698/80915229-f47c9f80-8d8b-11ea-8b64-467eb90f8eb7.png)

## django Sever 설치 및 실행
1. Python 가상 환경 및 프로젝트 폴더 구축
2. 프로젝트 root에서 `pip install django`로 프레임워크 설치
3. requirements.txt의 패키지들을 설치하기 위해 `pip install -r requirements.txt` 입력
4. 프로젝트 root에서 `python manage.py runserver <ip address>:8000`을 입력하여 서버를 실행

## django Sever 구조
### Model
- 총 3개의 application 폴더를 생성 (users / posts / comments)
- 각 폴더마다 `models.py`에 해당 DB 테이블을 정의.
- users/models.py    ==> `class User`, `class UserProfile`
- posts/models.py    ==> `class Post`, `class Photo`
- comments/models.py ==> `class Comment`
### Controller
- django Server는 회원 관리 기능을 담당하므로 Controller는 users/views.py에 정의
- 회원가입     : `class SignUpView`
- 이메일 인증  : `class UserActiveView`
- 로그인       : `class SignInView`
- 비밀번호 변경: `class PasswordChangeView`
- 비밀번호 찾기: `class PasswordSearchView`
- 프로필 편집  : `class ProfileEditView`
### 로그인 상태 관리
- 사용자의 로그인 상태를 확인하기 위하여 데코레이터를 구현
- Client로부터 받은 Request Header의 JWT(access token)를 확인. 
- config/authentication.py ==> `func login_validate`

## 추가
- Front-end: https://github.com/90factory/3rd_90Insta_Frontend
- nodeJS: https://github.com/90factory/3rd_90Insta_nodeJS
