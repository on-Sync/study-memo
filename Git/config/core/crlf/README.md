# Git CRLF 설정

## CRLF 란 ?

> [EOL](../../../../interview/reserved-word/eol/README.md) 참조바란다.

### 설정방법

#### 1. core.autocrlf (default=false)

- `checkout` , `commit` 을 기점으로 `eol` 방식을 __변환한다.__
- 교차플랫폼으로 협업할 경우 사용된다.

```shell
# 설정 종류
git config --global core.autocrlf true
git config --global core.autocrlf input
git config --global core.autocrlf false
```

|설정|동작|교차플랫폼 협업|사용자|
|-|-|-|-|
|true|`checkout` 은 CRLF , `commit` 은 LF|O|Windows 계열|
|input|`commit` 만 LF|O|Unix 계열|
|false|X|X|Windows 또는 Unix 계열|

#### 2. core.eol (default=native)

- `checkout` , `commit` 을 기점으로 `eol` 방식을 __지정한다.__
- 단일플랫폼으로 협업할 경우 `강제` 를 목적으로 사용된다.

```shell
# 설정 종류
git config --global core.eol native
git config --global core.eol crlf
git config --global core.eol lf
```

|설정|동작|
|-|-|
|native|사용자 시스템의 `eol` 방식을 사용|
|crlf|`crlf` 방식을 사용|
|lf|`lf` 방식을 사용|

#### 3. core.safecrlf (default=native)

- `checkout` , `commit` 을 기점으로 `eol` 방식을 __제어한다.__
- `crlf -> lf -> crlf` 변환 후의 데이터 차이로 `eol` 교차사용을 판단한다.
- 교차사용 확인시 중단 유무를 설정한다.
- _* false 일 경우, `autocrlf` 의 설정을 수행한다._

```shell
# 설정 종류
git config --global core.safecrlf true
git config --global core.safecrlf warn
git config --global core.safecrlf false
```

|설정|동작|
|-|-|
|true|중단|
|warn|경고 후 진행|
|false|X|

#### .gitattributes ([설정 상세참고](https://git-scm.com/docs/gitattributes))

- `.gitignore` 와 같이 프로젝트 내부에 git 설정을 저장한다.
- 별도로 사용할 경우, `'.git/info/attributes'` 에 지정한다.
- `pattern attr1 attr2 ...` 으로 파일 유형별로 설정할 수 있다.
  
```shell
# 설정 방법 예시
# 1. core.autocrlf=true
*.java text=auto
# 2. core.eol crlf
*.java eol=crlf 
# 3. core.eol lf
*.md eol=lf
# 4. 파일타입 지정
*.java text
*.java binary 
```
