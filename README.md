# 게시판모아(BoardMoa) 앱 연동 — XE3 플러그인

스마트폰 게시판 앱 **게시판모아**가 XE3 사이트의 게시판을 읽고 쓸 수 있게 하는 플러그인입니다.

- 앱 받기: [iPhone·iPad (App Store)](https://apps.apple.com/app/id6826114071) · [Android (Google Play)](https://play.google.com/store/apps/details?id=com.easyapplabs.boardmoa)
- 최신 버전: **1.0.32 (시험판)** · 내려받기: [releases/appapi-xe3-1.0.32.zip](releases/appapi-xe3-1.0.32.zip) · [latest.json](latest.json)
- 설치한 뒤에는 관리 화면(설정 → 플러그인 → 게시판모아 앱 연동 → 설정)의 [업데이트 확인]으로 새 버전을 받습니다.
- XE 1.11·Rhymix 사이트용 모듈은 [boardmoa-appapi](https://github.com/easyapplabs/boardmoa-appapi) 에 있습니다.


> **시험판입니다.** XE3 연동은 아직 시험 중이라 일부 기능만 됩니다.
> 되는 것: 로그인, 메뉴, 게시판 목록·검색, 새 글 모아 보기, 글·댓글 보기, 첨부 내려받기, 페이지,
> 글쓰기(사진 포함)·고치기·지우기, 댓글·답글 쓰기·지우기, 추천·비추천, 스크랩(=즐겨찾기), 신고(claim 플러그인),
> 내가 쓴 글·댓글·스크랩, 닉네임·비밀번호 바꾸기.
> 웹에서 하는 것: 회원가입(앱에서 웹 가입 화면이 열립니다), 이메일 변경, 프로필 사진.
> XE3 에 없는 쪽지·친구·알림은 앱에서 보이지 않습니다.

XE 1.11·Rhymix 사이트는 이 플러그인이 아니라 [boardmoa-appapi](https://github.com/easyapplabs/boardmoa-appapi) 모듈을 설치합니다.

## 필요한 것
- XE3 3.1 이상 (3.1.3 에서 시험), PHP 7.4
- 댓글 알림 메일: 댓글이 달리면 XE3 가 글쓴이에게 메일을 보낸다. 사이트 메일 설정이 잘못돼 있으면 웹·앱 모두 댓글 쓰기가 실패한다

## 설치
1. `appapi-xe3-<버전>.zip` 을 받아 압축을 풉니다. `appapi` 폴더가 나옵니다.
2. 사이트의 `plugins/` 폴더 안에 `appapi` 폴더째 올립니다. → `plugins/appapi/plugin.php`
   웹 서버가 읽을 수 있게 소유자·권한을 다른 플러그인과 같게 맞춥니다.
3. 플러그인을 켭니다. 둘 중 하나:
   - 관리자 페이지 → 플러그인 → 설치된 플러그인 → **게시판모아 앱 연동** → 켜기
   - 서버에서: `php artisan plugin:activate appapi`
4. 확인: 브라우저에서 `https://<사이트>/modules/appapi/api.php?r=site` 를 열어 `"ok":true` 와 `"engine":"xe3"` 가 보이면 됩니다.
   그 뒤 앱에서 사이트 주소를 추가하면 됩니다.

## 권한
게시판을 볼 수 있는 사람은 XE3의 게시판 권한(목록·읽기)과 메뉴 공개 설정으로 정해집니다.
목록 권한이 없는 게시판은 앱의 메뉴·새 글·검색 어디에도 나오지 않습니다.

## 업데이트·지우기
- 업데이트(0.3.0부터): 관리 화면(설정 → 플러그인 → 게시판모아 앱 연동 → 설정)의 **[업데이트 확인]** → **[업데이트]**.
  공개 저장소에서 받아 전자서명을 확인하고, 지금 파일을 `storage/app/appapi_backup/` 에 백업한 뒤 바꿉니다. 웹 서버가 `plugins/appapi` 에 쓸 수 있어야 합니다.
  0.2.x 이하는 `plugins/appapi` 를 새 버전으로 직접 바꿔 올립니다.
- 지우기: 관리자 페이지에서 끈 뒤 `plugins/appapi` 폴더를 지웁니다. 설치할 때 만들어진 표 `xe_appapi_ids`·`xe_appapi_tokens`(앱 로그인 정보)는 남아 있으므로 필요하면 직접 지워 주세요.

## 문의
easyapplabs@gmail.com
