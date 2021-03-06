---
title: ubuntu permission
date: 2018-11-27 17:44:04
tags:
- Ubuntu
categories:
- Ubuntu
---

파일 정보 보기

![](/images/1543396256153.png)
`ls -al`: 현재 위치에 있는 파일들을 자세히 보여주는 명령

| 파일 Type | 퍼미션정보 | 링크수 | 소유자  | 소유그룹 | 용량 | 생성날짜      | 파일이름 |
| --------- | ---------- | ------ | ------- | -------- | ---- | ------------- | -------- |
| d         | rwxr-xr-x  | 28     | p829911 | p829911  | 4096 | 11월 27 20:30 | .ipython |

- 파일 Type: `d` (디렉토리), `ㅣ` (링크파일), `-` (일반파일)
- 퍼미션정보: 해당 파일에 어떠한 퍼미션이 부여되어 있는지
- 링크수: 해당 파일이 링크된 수, 윈도우의 바로가기와 같다. `in [대상파일][링크파일]`명령으로 만든다.
- 소유자: 해당 파일의 소유자 이름
- 소유그룹: 해당 파일을 소유한 그룹이름
- 용량: 파일의 용량
- 생성날짜: 파일이 생성된 날짜
- 파일이름: 파일의 이름


**퍼미션 정보**

- 앞에서 두번째부터 아홉번째까지 퍼미션 정보이다.
- ` rwxr-xr-x`


**퍼미션 종류**

- r : 파일의 읽기 권한
- w : 파일의 쓰기 권한
- x : 파일의 실행 권한


**퍼미션의 사용자지정**

- 소유자: 소유자에 대한 퍼미션 지정 `rwx`
- 그룹: 소유그룹에 대한 퍼미션 지정 `r-x`
- 공개: 모든 사용자들에 대한 퍼미션 지정 `r-x`
- `-`:  그 퍼미션은 없다

**소유자는 읽기, 쓰기, 실행을 허용하고 파일의 소유그룹에 속하고 있는 사용자들은 읽기 실행만 허용하고 이외에 나머지 모든 사용자들도 읽기, 실행만 허용한다.**



## 퍼미션 변경하기

`chmod  [변경될 퍼미션값][변경할 파일]`

- 각 퍼미션 기호를 숫자로 변환한다. ( r = 4, w = 2, x = 1)
  ex) r - x = 4 0 1
- 변환한 숫자를 합산한다.
  ex) 4 0 1 = 5
- `rwxr-xr-x`  = 755

- `chmod 775 [변경할 파일]` : 변경할 파일이 755에 해당되는 퍼미션으로 변경된다.
- 디렉토리의 경우 `-R` 옵션을 사용하면 하위 디렉토리의 모든 디렉토리 및 파일의 퍼미션이 변경된다.
  ex) `chmod -R 777 [변경할 디렉토리]`



## 소유자 변경하기

`chown [변경할 소유자][변경할 파일]`

이 명령으로 소유자뿐만 아니라 소유그룹도 변경할 수 있다.

`[변경할 소유자]`에 `.그룹이름` 형식으로 입력하면 된다.

ex) p829911.text 파일의 소유자를 p829911 소유그룹을 p829911로 동시에 변경할 경우
`chown p829911.p829911 p829911.text`