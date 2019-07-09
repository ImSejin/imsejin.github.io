---
layout: post
title: 누구나 따라하는 Jekyll 블로그 만들기
thumbnail: /public/imgs/jekyll.png
category: Jekyll
tags: jekyll howToStart
comments: true
published: true
---

개발 공부하면서 깨달은 것을 기록하기 위해 블로그를 선택하려 했는데, 제품이 너무 많았다. 네이버 블로그, 티스토리, 브런치, 워드프레스 등등 아예 나만의 홈페이지를 백지에서부터 만들어서 호스팅할까도 생각했다.

그와중에 Github Pages를 이용하면 무료호스팅을 받을 수 있다는 걸 알게 됐고, 여기에 정적 블로그를 생성해주는 Jekyll를 만났다.

실행환경은 <u>Windows 10 Pro</u>이다.

## Goals

- 자신만의 블로그를 만들 수 있다
- 무료 호스팅 서비스를 받을 수 있다
- 개발 블로그가 없던 개발자에서 개발 블로그가 있는 개발자로 거듭날 수 있다 :-)

## Let's do this

### Ruby 설치

Jekyll은 Ruby 스크립트로 이루어져 있다. 먼저 [여기](<https://rubyinstaller.org/downloads/>)에서 Ruby 설치파일을 다운받는다.

> 자신의 OS 비트에 해당하는 RubyInstaller를 받는다.
>
> 64bit 운영체제인데 32bit Installer로 설치하면 MSYS2 설치할 때 오류 난다.

![001](.\_img\rubyInstaller\001.png)

`Add Ruby executables to your PATH`에 체크를  한다.

> 환경변수 PATH에 루비 설치경로가 추가된다.
>
> 체크하지 않으면 나중에 따로 환경변수에 GEM_HOME을 추가해야 한다.

![002](.\_img\rubyInstaller\002.png)

`MSYS2 development toolchain`에 체크되어 있는지 확인하고 다음을 누른다.

> MSYS2는 Windows의 Command Prompt에서 루비 명령어를 사용할 수 있게 해준다.
>
> 이 역시 설치하지 않으면 나중에 설치할 bundle의 원활히 동작하지 않게 된다.
>
> 그럼 [여기](<http://www.msys2.org>)에서 다운받아 따로 설치해야 하는데 정말 귀찮아 진다. Installer가 떠먹여 줄 때 먹자.

![003](.\_img\rubyInstaller\003.png)

`Run 'ridk install' to setup MSYS2 and development toolchain. MSYS2 is required to install gems with C extensions.`에 체크하고 finish한다.

> 체크하지 않은 채 Installer를 종료했다면, cmd를 실행시키고 `ridk install` 명령어를 실행하자.

![004](.\_img\rubyInstaller\004.png)

MSYS2를 사용하기 위해 1, 2, 3 옵션을 순차적으로 설치한다.

![](.\_img\rubyInstaller\005.png)

1번 옵션 `MSYS2 base installation`을 성공적으로 완료했다면 경고창이 뜬다.

MSYS2를 처음 실행했기에 필수 사항을 적용하기 위해서 쉘을 다시 시작하라고 하니,

enter 눌러 종료하고 커맨드에서 `ridk install` 명령어를 실행한다.

그러면 아까 봤던 RubyInstaller2 for Windows가 우리를 환영해준다. 2번 옵션부터 마저 설치한다.

3번 옵션까지 설치했다면 `ruby -v`와 `gem -v` 명령어를 실행시켜

버전이 제대로 출력되는지 확인한다.

### Jekyll과 Bundler 설치

Jekyll과 Bundler는 Gem(Ruby 라이브러리)이기에 gem 명령어로 설치한다.

`gem install jekyll`

`gem install bundler`

> *이것 때문에 Ruby와 repository를 스무 번 이상 설치/삭제한 것 같다, 껄껄껄.*
>
> *`ruby dk.rb init` 명령어를 실행하라고 하는데 dk.rb 파일은 어디에도 없고.*
>
> *Develpoment Kit를 설치하니까 되긴 됐는데 여러 번 삽질해보니까 저 명령어가 필요없었다.*

### 블로그 생성

#### 직접 생성하기

이제 Jekyll로 정적 블로그를 생성해본다. 나의 경우 Github에서 pull한 저장소를 관리하는 폴더(D:\repositories)가

있기 때문에 여기에서 블로그를 생성하겠다. `jekyll new [저장소 이름]` 명령어를 실행해준다.

#### Github에서 fork하기

구동해 보면 블로그가 많이 심심하고 허전하다.

기본 블로그의 디자인에 아쉬워 하는 우리를 위해 [여기](<http://jekyllthemes.org/>)에서 Jekyll 블로그 테마를 배포하고 있다.

원하는 테마를 찾아 github 저장소를 fork하고 clone받자.

> fork와 clone에 대해서 모른다면 [이 글](을 참고하자.

### 블로그 구동

명령어로 직접 생성했다면 `jekyll serve` 명령어를 실행하여 로컬에서 블로그를 구동한다.

URL은 *<u>localhost:4000</u>*이다.

#### Github에서 fork했다면

위의 명령어로는 아래와 같은 에러가 발생해 구동할 수가 없을 것이다.

```log
Traceback (most recent call last):
        5: from C:/Ruby25-x64/bin/jekyll:23:in `<main>'
        4: from C:/Ruby25-x64/bin/jekyll:23:in `load'
        3: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/jekyll-3.8.5/exe/jekyll:11:in `<top (required)>'
        2: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/jekyll-3.8.5/lib/jekyll/plugin_manager.rb:48:in `require_from_bundler'
        1: from C:/Ruby25-x64/lib/ruby/2.5.0/rubygems/core_ext/kernel_require.rb:59:in `require'
C:/Ruby25-x64/lib/ruby/2.5.0/rubygems/core_ext/kernel_require.rb:59:in `require': cannot load such file -- bundler (LoadError)
```

이제 설치한 Bundler를 써야할 때가 왔다. Bundler는 꼭 필요한 버전의 루비 젬을 찾고 설치하는 도구다.

`bundle exec jekyll serve` 명령어를 실행한다.

```log
Traceback (most recent call last):
        2: from C:/Ruby25-x64/bin/bundle:23:in `<main>'
        1: from C:/Ruby25-x64/lib/ruby/2.5.0/rubygems.rb:303:in `activate_bin_path'
C:/Ruby25-x64/lib/ruby/2.5.0/rubygems.rb:284:in `find_spec_for_exe': Could not find 'bundler' (1.16.4) required by your E:/repositories/imsejin.github.io/Gemfile.lock. (Gem::GemNotFoundException)
To update to the latest version installed on your system, run `bundle update --bundler`.
To install the missing version, run `gem install bundler:1.16.4`
```

친절하게도 Bundle을 최신버전으로 업데이트하라고 한다.

`bundle update --bundler` 명령어를 실행한 뒤 다시 구동시킨다.

하지만 열에 아홉은 오류가 난다 ^___^

### Trouble Shooting

#### TimeZone Dependency Error

```log
 Dependency Error: Yikes! It looks like you don't have tzinfo or one of its dependencies installed. In order to use Jekyll as currently configured, you'll need to install this gem. The full error message from Ruby is: 'cannot load such file -- tzinfo' If you run into trouble, you can find helpful resources at https://jekyllrb.com/help/!
jekyll 3.8.4 | Error:  tzinfo
```

TimeZone 설정값이 에러가 나는 문제다.

`_config.yml`에서 timeZone 속성의 값을 비운 채로 남긴다.

#### No Repository Name Error

```log
   GitHub Metadata: No GitHub API authentication could be found. Some fields may be missing or have incorrect data.
   GitHub Metadata: Error processing value 'description':
  Liquid Exception: No repo name found. Specify using PAGES_REPO_NWO environment variables, 'repository' in your configuration, or set up an 'origin' git remote pointing to your github.com repository. in /_layouts/post.html
             ERROR: YOUR SITE COULD NOT BE BUILT:
                    ------------------------------------
                    No repo name found. Specify using PAGES_REPO_NWO environment variables, 'repository' in your configuration, or set up an 'origin' git remote pointing to your github.com repository.
```

원격 저장소를 불러오지 못하는 문제다.

`_config.yml`에서 `repository: [GitHub 유저명]/[저장소 이름]`을 추가한다.

> ex). repository: ImSejin/imsejin.github.io

#### Conversion Error

```log
  Conversion error: Jekyll::Converters::Scss encountered an error while converting 'assets/css/style.scss':
                    Invalid CP949 character "\xE2" on line 5
jekyll 3.7.4 | Error:  Invalid CP949 character "\xE2" on line 5
```

CharacterSet 종류로 인해 해당 캐릭터를 인코딩하지 못하는 문제다.

`chcp 65001` 명령어를 실행한 뒤 다시 구동한다.

> 437: 영문
>
> 949: 한글(KSC5601-92, 조합형 한글)
>
> 65001: UTF-8

#### EventMachine Error

```log
Unable to load the EventMachine C extension; To use the pure-ruby reactor, require 'em/pure_ruby'
Traceback (most recent call last):
        22: from C:/Ruby25-x64/bin/jekyll:23:in `<main>'
        21: from C:/Ruby25-x64/bin/jekyll:23:in `load'
        20: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/jekyll-3.8.4/exe/jekyll:15:in `<top (required)>'
        19: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/mercenary-0.3.6/lib/mercenary.rb:19:in `program'
        18: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/mercenary-0.3.6/lib/mercenary/program.rb:42:in `go'
        17: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/mercenary-0.3.6/lib/mercenary/command.rb:220:in `execute'
        16: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/mercenary-0.3.6/lib/mercenary/command.rb:220:in `each'
        15: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/mercenary-0.3.6/lib/mercenary/command.rb:220:in `block in execute'
        14: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/jekyll-3.8.4/lib/jekyll/commands/serve.rb:75:in `block (2 levels) in init_with_program'
        13: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/jekyll-3.8.4/lib/jekyll/commands/serve.rb:93:in `start'
        12: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/jekyll-3.8.4/lib/jekyll/commands/serve.rb:93:in `each'
        11: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/jekyll-3.8.4/lib/jekyll/commands/serve.rb:93:in `block in start'
        10: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/jekyll-3.8.4/lib/jekyll/commands/serve.rb:101:in `process'
         9: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/jekyll-3.8.4/lib/jekyll/commands/serve.rb:147:in `register_reload_hooks'
         8: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/jekyll-3.8.4/lib/jekyll/commands/serve.rb:147:in `require_relative'
         7: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/jekyll-3.8.4/lib/jekyll/commands/serve/live_reload_reactor.rb:3:in `<top (required)>'
         6: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/jekyll-3.8.4/lib/jekyll/commands/serve/live_reload_reactor.rb:3:in `require'
         5: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/em-websocket-0.5.1/lib/em-websocket.rb:3:in `<top (required)>'
         4: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/em-websocket-0.5.1/lib/em-websocket.rb:3:in `require'
         3: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/eventmachine-1.2.7-x64-mingw32/lib/eventmachine.rb:8:in `<top (required)>'
         2: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/eventmachine-1.2.7-x64-mingw32/lib/eventmachine.rb:8:in `require'
         1: from C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/eventmachine-1.2.7-x64-mingw32/lib/rubyeventmachine.rb:2:in `<top (required)>'
C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/eventmachine-1.2.7-x64-mingw32/lib/rubyeventmachine.rb:2:in `require': cannot load such file -- 2.5/rubyeventmachine (LoadError)
```

`jekyll serve --watch --livereload`

LiveReLoad 옵션은 파일에 변경사항이 발생했을 때 자동으로 브라우저를 새로고침하는 기능을 갖고 있다.

이 옵션을 사용하려면 EventMachine이 필요한데 이를 로드할 수가 없는 문제다.

`gem uninstall eventmachine` 명령어를 실행한다.

`gem list --local` 명령어를 실행하여 루비 젬이 제대로 삭제되었는지를 확인한다.

`gem uninstall eventmachine` 명령어를 다시 실행하여 루비 젬이 제대로 삭제되었는지를 확인한다.

삭제해도 남아 있다면 `gem uninstall -i C:/Ruby25-x64 eventmachine` 명령어를 실행한다.

정상적으로 삭제되었다면 `gem install eventmachine --platform=ruby` 명령어를 실행하고 다시 구동한다.

```log
Select gem to uninstall:
 1. eventmachine-1.2.7
 2. eventmachine-1.2.7-x64-mingw32
 3. All versions
```

eventmachine을 삭제하려고 할 때, 여러 버전이 설치되어 있어서 위와 같이 출력되면 `2번` 항목을 삭제한다.

#### Posting 404 Error

모든 원인을 검토해봤는데도 자기가 올린 글에 접근 시 에러가 난다면,

해당 파일의 경로에 한글이 들어가지 않았나 확인한다.

#### Permanent Links Error

```log
Since v3.0, permalinks for pages in subfolders must be relative to the site source directory, not the parent directory. Check https://jekyllrb.com/docs/upgrading/ for more info.
```

고유링크가 사이트 소스 디렉토리와 관련되지 않아서 발생한 문제다.

`_config.yml`에서 `relative_permalinks: true` 속성 항목을 삭제한다.

#### Highlighter Dependency Error

```log
Dependency Error: Yikes! It looks like you don't have pygments or one of its dependencies installed. In order to use Jekyll as currently configured, you'll need to install this gem. The full error message from Ruby is: 'cannot load such file -- pygments' If you run into trouble, you can find helpful resources at https://jekyllrb.com/help/!
  Liquid Exception: pygments in C:/Users/SEJIN/git/my-jekyll-blog/_posts/2014-01-01-example-content.md
             ERROR: YOUR SITE COULD NOT BE BUILT:
                    ------------------------------------
                    pygments
```

하이라이터 'pygments'를 빌드되지 않아 발생한 문제다.

`gem install pygments.rb` 명령어를 실행하고

블로그 디렉토리에 있는 `Gemfile`이란 파일에 `gem 'pygments.rb'`를 추가한다.

그런데 위의 방법보다 더 편한 방법이 있다. `_config.yml`에서 highlighter 속성 값을 `rouge`로 바꾼다.

## References

- [박군~ 즐겨라!!: Ruby Gem, Failed to build gem native extension 에러 해결하기](<http://creator-textcube.blogspot.com/2009/03/ruby-gem-failed-to-build-gem-native.html>)
- [[Jekyll] 윈도우에서 지킬 설치 및 블로그 생성하기 - Shryu8902’s Blog](<https://shryu8902.github.io/_posts/2018-06-22-jekyll-on-windows/>)
- [Jekyll 윈도우에 설치해서 사용하기 - WhaTap Tech Blog](<https://tech.whatap.io/2015/09/11/install-jekyll-on-windows/>)
- [지킬(jekyll) 로 포스팅하기 · Jungtae Kim Blog](<https://jungtaejtkim.github.io/dev/2017/05/02/posting/>)
- [Jekyll 블로그 github를 통해 퍼블리싱하는 방법 · Yoon's devlog](<http://blog.hyeyoonjung.com/2017/05/22/how-to-write-posts/>)
- [Fixing the "No GitHub API authentication could be found" when jekyll serve · Issue #140 · DIYbiosphere/sphere](<https://github.com/DIYbiosphere/sphere/issues/140>)
- [Jekyll - Github page 오류 해결](<https://aisiunme.github.io/jekyll/2018/07/25/troubleshooting-in-jekyll-serve/>)
- [Unable to load the EventMachine C extension; To use the pure-ruby reactor, require 'em/pure_ruby' · Issue #96 · oneclick/rubyinstaller2](<https://github.com/oneclick/rubyinstaller2/issues/96>)
- [Unable to load the EventMachine C extension; To use the pure-ruby reactor - Stack Overflow](https://stackoverflow.com/questions/30682575/unable-to-load-the-eventmachine-c-extension-to-use-the-pure-ruby-reactor)
- [Making Jekyll + LiveReload work on Windows](<https://httpain.com/blog/jekyll-live-reload-windows/>)
- [LoadError on RubyInstaller for Windows 2.1.3 · Issue #536 · eventmachine/eventmachine](<https://github.com/eventmachine/eventmachine/issues/536>)
- [chcp (윈도우 cmd 창 언어셋 설정)](http://mins01.nayana.kr/mh/tech/read/916?type=read&b_id=tech&sh=titleOrText&sw=오라클&cat=&page=5&b_idx=810&tq=&q=&ct=)
- [문자 집합(Character Set)과 인코딩(Encoding)](<https://nuli.navercorp.com/sharing/blog/post/1079940>)
- [Compability with Jekyll 3? · Issue #99 · poole/poole](<https://github.com/poole/poole/issues/99>)
- [Jekyll - rouge로 코드 highlighting](<http://dalzony.github.io/2016/01/highlighting>)
