# WSL2

> WSL2 는 Windows Subsystem Linux 2 이며, 2020.05 에 발표되었다.
> Docker Desktop 은 Docker 사용을 위해 Linux Kernel 을 요구한다.
> Windows 는 WSL 를 통해 Linux Kernel 를 지원한다.
> Docker Desktop 에서 WSL 은 1 또는 2 를 선택할 수 있다.
> 해당 문서는 WSL2 선택할 경우를 고려하여, PowerShell 을 CLI 로 이용한 설치순서를 기록한다.

## List of Distribution

```sh
## Installable list
wsl --list --online
wsl -l -o
## Local list
wsl --list --verbose
wsl -l -v
```

## Install Distribution

```sh
wsl --install -d {Distribution}
## my setting
wsl --install -d Ubuntu
```

## Set WSL version

```sh
wsl wsl --set-default-version {Verison}
## my setting
wsl --set-default-version 2
```

## Set WSL Distribution

```sh
wsl --setdefault {Distribution}
wsl -s {Distribution}
## my setting
wsl -s Ubuntu
```

## Get Administration

- WSL update 를 위해서는 관리자 권한이 필요

```sh
## 관리자 권한 : 터미널 재실행
start-process powershell -verb runAs
```

## Update WSL for version 2

```sh
## wsl 업데이트
wsl --update
```

## Restart WSL

```sh
## wsl 재실행 (Distribution 전체종료 후)
wsl --shutdown
## Distribution 실행
wsl --distribution {Distribution}
wsl -d {Distribution}
## my setting
wsl -d Ubuntu
```

> 배포판 설치 및 WSL2 설정이 끝났다.
> 이후에는 Docker Desktop 을 재실행해 주면된다.