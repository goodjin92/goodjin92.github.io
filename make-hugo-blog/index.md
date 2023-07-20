# Hugo Blog 만들기




# 목적

개발자가 된다면 나만의 블로그를 개설해봐야지. 라는 막연한 생각으로 시작하게 되었습니다.

본격적인 개발 공부를 시작하기도 전에 블로그부터 만들게 되었지만...

흥미가 있는 것부터 시작하는게 더 좋겠다는 생각으로 블로그를 먼저 만들어봅니다.

</br>

많은 개인 사이트 및 블로그를 생성하는 방법들이 있습니다.

대표적으로 Static Site 와 Dynamic Site 일텐데, 저는 Static Site 방식을 선택했습니다.

상대적으로 접근하기 쉽고, 심플한 것이 더 마음에 들어서 선택했습니다.

Static Site Generators에는 Next.js, Hugo, Gatsby, Jekyll 등 많지만, 저는 Hugo를 선택했습니다.

정적 사이트 생성기는 [JAMSTACK](https://jamstack.org/generators/)에서 비교해보실 수 있습니다.

많은 개발 언어나 환경은 잘 모르겠지만, 고랭(Golang)이 뭔가 더 흥미롭고 재밌어 보여서 선택했습니다.

</br>

앞으로 블로그를 생성하고 커스터마이징하는 등 좌충우돌 운영기를 작성해보고자 합니다.

제 기준으로 순서대로 진행해보겠습니다.

숙련되신 분들이 보기에 답답해보일 수 있으니 주의해주세요...



---

## 프로그램 설치 및 준비

1. [Git 설치](https://git-scm.com/)
2. [Hugo 설치](https://gohugo.io/)
3. [Windows Terminal 설치](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=ko-kr&gl=kr&rtc=1)

- 자세한 설치 과정은 생략하겠습니다. 대부분 확인을 누르면서 그냥 진행하면 됩니다.

</br>

## Hugo Blog 생성하기

1. Windows Terminal을 연 뒤 아래 명령어를 입력하여 static site 생성 후 해당 폴더로 이동한다.

- 폴더 이름은 "blog"로 설정한다. (원하는 이름으로 설정 가능)

```powershell
hugo new site blog
cd blog
```

</br>


2. [Hugo Themes](https://themes.gohugo.io/) 사이트에서 원하는 테마 선택 후 아래 명령어를 Windows Terminal에 작성하여 submodule로 테마를 가져온다.

- 참고로 저는 [DoIt](https://themes.gohugo.io/themes/doit/) 테마를 선택해서 사용중입니다.

```powershell
git init
git submodule add https://github.com/HEIGE-PCloud/DoIt.git themes/DoIt
```

</br>

3. Blog 폴더에 있는 hugo.toml 파일을 아래와 같이 수정한다. toml 파일은 [VSCode](https://code.visualstudio.com/), [Typora](https://typora.io/) 등 에디터를 활용하여 수정한다.

- 기존
```toml
baseURL = 'http://example.org/'
languageCode = 'en-us'
title = 'My New Hugo Site'
```
- 수정 후
```toml
baseURL = 'http://goodjin92.github.io/'
languageCode = 'en-us'
title = 'GOODJIN.note'
theme = 'DoIt'
```

</br>

4. [DoIt 테마 가이드](https://hugodoit.pages.dev/theme-documentation-basics/)에 따라 원하는대로 블로그를 커스터마이징한다.

- Hugo는 overriding을 지원하기 때문에 굳이 themes 폴더 안의 파일들을 건드릴 필요는 없습니다.
- 선택한 테마에 따라 개발자가 테마 활용 가이드를 함께 업로드해둡니다. 가이드만 잘 따라해봅니다.
- 제 기준으로, blog\themes\DoIt\exampleSite 폴더를 참고하여 블로그를 꾸몄습니다.
- 위 exampleSite 폴더를 참고하여 blog\config\\_default 폴더에 params.toml를 만들어 작성했습니다.
```toml
# website title
[params]
title = "GOODJIN.note"
description = "This is GOODJIN's Blog like a note."
keywords = ["GOODJIN", "Coding", "Programming", "IT", "Tip"]

# DoIt theme version
version = "0.3.X"

# site default theme ("light", "dark", "black", "auto")
defaultTheme = "auto"

# 아래에 코드들이 아주 많이 있습니다. 위에 설명대로 테마 가이드 혹은 exampleSite 샘플을 참고해서 작성합니다.
```

</br>

5. Windows Terminal에서 아래 명렁어 입력 후 새 포스트를 만든다.

- content 폴더 안에 posts 폴더가 생기고, 그 폴더 안에 hello-world.md 라는 파일이 생성된다.
```powershell
hugo new posts/hello-world.md
```

</br>

6. 테마 가이드에 따라 config.toml 수정, 포스트 작성 등 일부 작업 수행 후 Windows Terminal에서 아래 명령어를 작성하여 실행한다.

```powershell
hugo serve
```

</br>

7. 웹 브라우저 주소창에 localhost:1313 입력 후 열리는지 확인한다.

   </br>

8. 잘 실행되는 것을 확인했다면 테마 가이드를 참고하여 더 다양하게 응용해본다.

</br>

현재는 로컬 환경에서 블로그가 잘 실행되는 것을 확인했습니다.

조만간 깃허브(GitHub)를 활용하여 외부에서 다른 사용자들도 접속할 수 있는 진짜 블로그 운영법을 소개하겠습니다.
