# 📦 Gnuboard5 Docker Setup

도커 기반으로 구성한 **Gnuboard5 초기 개발 환경**입니다.  
WSL + Docker 환경에서 빠르게 그누보드5를 실행할 수 있도록 구성되어 있습니다.

---

## 🚀 특징

- Docker 기반 환경 구성
- WSL(Windows Subsystem for Linux) 지원
- 포트 변경(8000) 대응
- Git Submodule 문제 해결 가이드 포함
- Gnuboard5 초기 설치 자동화 환경

---

## ⚠️ 주의 사항 (Git Submodule 문제)

GitHub에서 폴더가 화살표(→)로 보이는 경우는  
해당 폴더 내부에 `.git`이 존재하기 때문입니다.

👉 즉, **하위 저장소(Submodule)** 상태

### 🔧 해결 방법

```bash
git rm --cached . -rf
```
또는 해당 서브 폴더의 .git 삭제

## 🐳 프로젝트 실행 방법
### 1️⃣ 저장소 클론
```
cd app
git clone https://github.com/pdy1207/gnuboard5.git public
```
### 2️⃣ Docker 실행
```
docker-compose up -d
```
### 3️⃣ 접속
```
http://localhost:8000
``` 
## 🛠️ 초기 설정

그누보드 최초 실행 시<br/>
설치 페이지가 자동으로 나타납니다.


## 📁 데이터 폴더 생성 (WSL 기준)
```
mkdir data
chmod 707 data
```
👉 권한 문제 방지를 위해 707 권한 부여

## ⚙️ 포트 설정

Docker 환경에서 포트를 **8000으로 설정**하였기 때문에

👉 반드시 설정 파일에 반영해야 합니다

## 📄 config.php 수정
```
define('G5_DOMAIN', 'http://localhost:8000');
```
## 🧩 환경 구성 개요
- Docker
- Nginx / Apache (환경에 따라 다름)
- PHP
- MySQL
- Gnuboard5
## 🧠 개발 메모
- `G5_DOMAIN`이 핵심 설정값
- URL 설정이 잘못되면 CSS / JS 경로가 깨짐
- `dbconfig.php`는 DB 설정 전용
- `config.php`에서 전체 URL 관리
## 💡 트러블슈팅
### ❌ CSS 깨짐

→ `G5_DOMAIN` 포트 미설정

### ❌ headers already sent

→ config.php 출력 / 중복 define 문제

### ❌ G5_URL already defined

→ `G5_DOMAIN` 또는 `G5_URL` 중복 선언

## 📌 정리


👉 도커 기반 그누보드5 실행 환경 </br>
👉 WSL 개발 환경 대응 </br>
👉 포트 8000 커스텀 세팅 완료 </br>
