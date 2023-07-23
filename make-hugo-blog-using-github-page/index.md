# GitHub Blog Page를 활용한 Hugo Blog 만들기




# 목적

블로그를 운영하는 것은 내 경험을 정리하기 위한 것이기도 하지만,

내 경험과 지식을 다른 분들과 나누고 싶기 때문입니다.

그러려면 당연히 다른 분들이 볼 수 있게 해야겠죠.

다양한 방식들이 있지만, 저는 깃허브 페이지(GitHub Page)를 활용해보겠습니다.

참고로, 제가 진행하는 과정에서 문제가 발생했는데 이에 대한 해결과정까지 순서로 넣었습니다.



---

## 사전준비

- [깃허브(GitHub)](https://github.com/)를 활용할 예정이기 때문에 당연히 깃허브 계정 및 레포지토리가 있어야 합니다.

  계정만 미리 생성해주시고 따라해주세요.

</br>

## GitHub에 Hugo Blog 업로드하기

1. GitHub에 2개의 레포지토리(Repository) 미리 생성하기

- 저의 경우, 2개의 레포지토리를 생성했습니다.

  - Blog (Hugo Blog 관련 모든 파일을 저장, 이건 private으로 해도 상관없음)

  - [Github Username].github.io (렌더링한 파일들을 업로드, 실제 사용자가 접근, 공개로 설정)

</br>

2. Windows Terminal에서 아래 순서대로 입력하며 GitHub에 업로드하기

- 아래 코드를 입력하기 전에 blog 폴더에 public 폴더가 있다면, 반드시 삭제하고 진행해주세요.

```powershell
git init

git remote add origin https://github.com/goodjin92/blog.git

git submodule add -b main https://github.com/goodjin92/goodjin92.github.io.git public

hugo -D

cd public

git add .

git commit -m "First Commit"

git push origin main

cd ..

git add .
```

</br>

3. 2번의 마지막 줄 명령어를 작성해보니 아래와 같은 warning, hint 문구가 나타났습니다.

- 이번 문제(adding embedded git repository: public)가 발생하지 않는다면 5번으로 넘어가주세요.
- in the working copy of 문제는 다른 방법으로 해결해야 하니, 우선은 넘어가겠습니다.

```powershell
PS C:\Project\blog> git add .
warning: in the working copy of '.gitmodules', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'archetypes/default.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'content/posts/hello-world.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'content/posts/last-year-2022.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'hugo.toml', LF will be replaced by CRLF the next time Git touches it
warning: adding embedded git repository: public
hint: You've added another git repository inside your current repository.
hint: Clones of the outer repository will not contain the contents of
hint: the embedded repository and will not know how to obtain it.
hint: If you meant to add a submodule, use:
hint:
hint:   git submodule add <url> public
hint:
hint: If you added this path by mistake, you can remove it from the
hint: index with:
hint:
hint:   git rm --cached public
hint:
hint: See "git help submodule" for more information.
```

</br>

4. 3번 문제는 아래 명령어를 입력하여 해결하겠습니다.

- 아래 명령어 입력 후 fatal log가 뜨더라도 무시하고 5번으로 넘어가겠습니다.

```powershell
git submodule add -b main https://github.com/goodjin92/goodjin92.github.io.git public
```

</br>

5. 아래 명령어를 마지막으로 입력한 뒤 GitHub에 접속하여 잘 저장되었는지 확인합니다.

```powershell
git commit -m "First Commit"
git push origin main
```

</br>

6. 조금의 시간이 흐른 뒤 인터넷 주소창에 "[Github Username].github.io"를 입력하여 접속해본다.

</br>

---

## 이후 진행 순서

이후부터는 개인 스타일에 맞게 글을 작성하거나 메뉴 구성, 블로그 커스터마이징 등을 수행하시면 됩니다.

블로그 업데이트 쉽게 하기, 블로그 꾸미기, 댓글 추가, 커스텀 도메인 등록 등에 대해서도 공유하겠습니다.
