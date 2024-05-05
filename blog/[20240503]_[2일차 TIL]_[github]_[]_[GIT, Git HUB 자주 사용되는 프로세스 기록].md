## ☑️ GitHub 기본 4가지 동작

- `git pull`: 원격 저장소(repository)에서 코드를 받아옴
- `git add .`: 수정 사항 전체를 커밋하기 위해 스테이징 함
- `git commit`: 수정 사항을 반영하여 새로운 버전을 생성함
- `git push`: 생성한 새로운 버전의 코드를 원격 저장소에 반영함

## ☑️ 로컬 파일을 GitHub 원격 저장소와 연동하기

1. GitHub에서 새 레포지토리 생성(README.md는 가급적 우선 생성 하지 않기)
2. `git init`
3. `git remote -v` 로 현재 remote origin 상태 확인
4. origin이 있다면 우선 삭제, 없다면 연동하고자 하는 레포지토리로 연동

`git remote add origin 레포지토리 주소`

1. `git remote -v` 로 추가된 origin 확인
2. initial commit 진행

❗️`git pull 또는 git push` 할 시에 가끔 발생하는 아래의 에러 해결방법
`remote: Invalid username or password.`

1. GitHub 프로필 메인에서 오른쪽 사이드바에 `Settings` 들어가기

![Screenshot 2024-05-03 at 15.33.37.png](https://velog.velcdn.com/images/elma98/post/90132b9c-378f-464d-87d0-033daf8762b2/image.png)

1. 왼쪽 사이드바에서 `Developer Settings` 메뉴의 `Personal access tokens -> Tokens(classic)` 들어가기

   ![Screenshot 2024-05-03 at 15.43.17.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8f11927-b70c-4524-9227-a3efac08e7aa/63eb03c6-6434-4dd3-9828-b531f419572a/Screenshot_2024-05-03_at_15.43.17.png)

2. `Generate new token` 클릭

   ![Screenshot 2024-05-03 at 15.49.07.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8f11927-b70c-4524-9227-a3efac08e7aa/34dd06b9-f241-41d1-96bc-f6d8b482b3b6/Screenshot_2024-05-03_at_15.49.07.png)

3. 토큰 생성 완료, 토큰 복사 후 반드시 따로 저장해두기

   ![Screenshot 2024-05-03 at 16.10.36.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8f11927-b70c-4524-9227-a3efac08e7aa/8ebcbee0-59a9-4e75-b15b-eaa2a69721dc/Screenshot_2024-05-03_at_16.10.36.png)

4. `git origin` 삭제 후 다시 설정

```bash
$ git remote remove origin # 기존 origin 삭제
$ git remote add origin https://닉네임:토큰@github.com/레포지토리 경로 # 토큰 추가한 origin 재설정
```

## ☑️ GitHub blog 만들고 페이지 라우팅하기

### 1. 기본적인 페이지 라우팅

1. 레포지토리 이름이 `닉네임.github.io` 인 새 레포지토리 생성
2. 원하는 로컬 디렉토리에 해당 레포지토리 clone 받기
3. 프로젝트에 index.html 파일 추가하기

```bash
$ cd username.github.io
$ echo "Hello World" > index.html
```

1. 커밋 후 푸시 완료하기

```bash
$ git add --all
$ git commit -m "Initial commit"
$ git push -u origin main
```

1.  https://username.github.io 페이지로 이동하여 페이지가 활성화 되었는지 확인(계정마다 라우팅에 소요되는 시간이 다를 수 있음)

### 2. 오픈 소스 fork로 페이지 라우팅

1. (주의!) GitHub pages는 한 계정 당 한 페이지만 라우팅 해주기 때문에 기존에 라우팅 되어있는 레포지토리가 존재한다면 해당 레포지토리를 삭제하고 시작해야 함.
2. 사용하고자 하는 오픈 소스 레포지토리를 fork 해온다.

![Screenshot 2024-05-03 at 17.00.24.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8f11927-b70c-4524-9227-a3efac08e7aa/7fcca493-5948-4f90-9b8f-a1f118b7e0dd/Screenshot_2024-05-03_at_17.00.24.png)

1. fork 해온 레포지토리 상단 바의 `Settings` 클릭
2. 왼쪽 메뉴바의 Pages 클릭
3. Source를 `None` 에서 `main(또는 master)` 브랜치로 변경 → 선택한 브랜치의 버전으로 페이지 라우팅이 진행됨
4. 위의 작업이 완료되면 라우팅된 주소로 이동하여 페이지가 잘 뜨는지 확인(라우팅에 어느정도 시간이 소요될 수 있음)

   ![Screenshot 2024-05-03 at 17.11.02.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8f11927-b70c-4524-9227-a3efac08e7aa/076eb444-8c72-462c-b82d-7f69af74d195/Screenshot_2024-05-03_at_17.11.02.png)

## ✅ (추가!) 파이참에서 깃헙 사용하기

<aside>
🎯 파이참에서 진행한 로컬 프로젝트를 깃헙 레포지토리에 올리려고 한다. 이때 IDE 상에서 할 수 있는 연동 작업은 무엇이 있을까

</aside>

1. 파이참 상단 메뉴(VCS >> Share Project on GitHub) 클릭

![Screenshot 2024-05-03 at 16.52.05.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8f11927-b70c-4524-9227-a3efac08e7aa/5842a790-cde7-4b96-b51b-f1a4ae6ed549/Screenshot_2024-05-03_at_16.52.05.png)

1. GitHub에 새롭게 생성될 레포지토리 이름 설정(계정에 같은 이름의 레포지토리가 이미 있다면 중복으로 생성되지 않음) → Share 클릭

![Screenshot 2024-05-03 at 16.53.08.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/e8f11927-b70c-4524-9227-a3efac08e7aa/fee0bfe5-0b7b-42c1-829e-0fe0ae11a22c/Screenshot_2024-05-03_at_16.53.08.png)

1. initial commit을 진행할 파일을 체크박스로 선택하고 커밋 메시지를 남긴 후 Add 클릭
2. GitHub에 새롭게 생성된 레포지토리와 initial commit이 제대로 업로드 되었는지 확인, 확인 되었다면 파이참 프로젝트와 GitHub 연동 완료!
