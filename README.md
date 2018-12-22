﻿# OfflineJudgment2

## 문서 개요
1. [프로그램 개요](https://github.com/Uanid/OfflineJudgment2#%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%A8-%EA%B0%9C%EC%9A%94)
2. [사용 방법](https://github.com/Uanid/OfflineJudgment2#%EC%82%AC%EC%9A%A9-%EB%B0%A9%EB%B2%95)
- [1. 과제 파일 정규화](https://github.com/Uanid/OfflineJudgment2#1-%EA%B3%BC%EC%A0%9C-%ED%8C%8C%EC%9D%BC-%EC%A0%95%EA%B7%9C%ED%99%94)
- [2. 정규화된 파일 확인](https://github.com/Uanid/OfflineJudgment2#2-%EC%A0%95%EA%B7%9C%ED%99%94%EB%90%9C-%ED%8C%8C%EC%9D%BC-%ED%99%95%EC%9D%B8)
- [3. 자동 채점 하기](https://github.com/Uanid/OfflineJudgment2#3-%EC%B1%84%EC%A0%90-%ED%95%98%EA%B8%B0)
- [4. 유사도 구하기](https://github.com/Uanid/OfflineJudgment2#4-%EC%9C%A0%EC%82%AC%EB%8F%84-%EA%B5%AC%ED%95%98%EA%B8%B0)
- [5. 파일 삭제](https://github.com/Uanid/OfflineJudgment2#5-%ED%8C%8C%EC%9D%BC-%EC%82%AD%EC%A0%9C)
- [6. 업로드 자동화](https://github.com/Uanid/OfflineJudgment2#6-%EC%97%85%EB%A1%9C%EB%93%9C-%EC%9E%90%EB%8F%99%ED%99%94)
3. [프로젝트 개요](https://github.com/Uanid/OfflineJudgment2#%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EA%B0%9C%EC%9A%94)
4. [업데이트 로그](https://github.com/Uanid/OfflineJudgment2#%EC%97%85%EB%8D%B0%EC%9D%B4%ED%8A%B8-%EB%A1%9C%EA%B7%B8)

-------------------

### 프로그램 개요
Python 코딩 과제 자동 채점 프로그램입니다.
교내의 BlackBoard시스템을 사용해 과제를 업로드 하고 다운받아 채점하게 되는데,
채점자인 제 입장에서 너무 채점하기가 귀찮아 개발하게 되었습니다.

프로그램 이름: OfflineJudment2

개발자: Uanid

기능: 블랙보드에 올라온 Python 과제파일 채점을 자동화 시켜 채점자의 부담을 줄여줌

언어: Java

지원 환경: **Windows10** JVM이 설치된 환경

사용 라이브러리:
- Snakeyaml (yaml.org)
- Apache POI (apache.org)
- stringsimilarity (github.com/tdebatty, Jaro-Winkler의 문자열비교 논문구현)
 
--------------------
### 사용 방법

Java기반으로 작동하는 코드이기에 실행시에는 당연히 JVM이 컴퓨터에 설치되어 있어야 합니다.
 
**Windows10**에서만 작동을 확인했습니다. 그리고 Mac에선 **작동하지 않는**것을 확인했습니다.

*아마 개발할 때 기본으로 설정된 CRLF나 EUC-KR이 문제를 일으키는거 같은데, 당시엔 이 문제를 해결하지 못했습니다.*
 
컴파일이 완료된 파일들과 사용방법은 [Release](https://github.com/Uanid/OfflineJudgment/releases)에서 다운로드 받을 수 있습니다.
*각 빌드마다 사용방법이 차이가 날 수 있으니 꼭 사용방법을 읽어주세요.*

#### 1. 과제 파일 정규화
명령: 1

블랙보드 -> 수업분반 -> 제어판 -> 성적관리센터 -> 과제 -> '3주차 기초 코딩' 화살표 클릭 -> 항목 다운로드 -> 전체 선택 후 다운로드

블랙보드에서 일괄적으로 다운로드 받은 과제 파일들을 **다운로드**폴더에 그대로 이동하고 실행합니다.

이 기능은 프로그램의 정규화 기능을 통해 코드 파일과 비 코드 파일로 분리하는 기능입니다.

분반 출석부와 연계해 누락된 학생들을 찾아내려면 분반 코드를 입력, 아니면 0

#### 2. 정규화된 파일 확인
제가 개발한 정규화 기능이 완벽하지 않기도 합니다만,
사실 제출한 과제들을 확인하다 보면 학생들 중 꼭 한두명씩은 제출 양식을 지키지 않습니다.

그렇기 때문에 사람이 일일히 확인해서 누락된 부분을 수정해야 합니다. **제출요약.xslsx**파일을 참고해서 누락된 학생들의 과제 파일을 옮겨줘야 합니다. 다만 이 때 학생별 폴더의 **학번 이름**형태가 유지되어야 합니다.

#### 3. 채점 하기
명령:2

정규화와 마찬가지로 분반을 추가로 입력하면 됩니다.

**테스트케이스**폴더 안에 있는 테스트 케이스들을 읽어들이기 때문에 명령 수행 전에 미리 수정해야 합니다.

테스트 케이스는 갯수 생성에 제한이 없고 ANSI인코딩을 이용합니다. (*확실하지 않음*)

파일 이름은 제한이 없지만 확장자는 **.testcase**로 통일해야 합니다.

내부 양식도 예시로 있는 파일들과 같이 지켜줘야 합니다.

채점 명령을 수행하면 실행 결과가 **엑셀 파일**로 나옵니다.

#### 4. 유사도 구하기
명령: 3

채점 후에 생성된 **Code Distance**폴더를 바탕으로 실행 결과가 **엑셀 파일**로 나옵니다.

유사도는 0 ~ 100 사이로 표시되며, 유사도가 80% ~ 100% 사이라면 확인을 해주세요.

상황에 따라선 70% 이상도 검사해야 합니다.

#### 5. 파일 삭제
명령: 4

프로그램 실행과 관계없는 데이터(채점 결과, 중간 파일 등)을 전부 삭제시켜 프로그램 파일만 남기는 기능입니다.

#### 6. 업로드 자동화
명령: 5

블랙보드에 일괄 업로드가 가능하도록 하는 업로드 파일을 만듭니다.

블랙보드에서 미리 파일을 다운로드 해야 합니다.

블랙보드 -> 수업분반 -> 제어판 -> 성적관리센터 -> 전체 성적관리센터 -> 우측 상단의 '업로드/다운로드'에서 다운로드 ->  데이터 -> 선택한 컬럼 -> '과제 선택' -> '이 컬럼의 코멘트 포함' 체크
옵션 -> 아무것도 건드리지 말 것
-> '확인' 버튼 클릭

다운받은 파일의 제목을 **업로드.xls**로 바꾸고 프로그램 최상단 폴더 안에 넣으면 됩니다.

결과물로 나온 **업로드종합.xls**을 블랙보드에 업로드하면 자동으로 과제 점수가 입력됩니다.

**하지만** 이 프로그램을 개발할 당시 블랙보드에 과제를 2회 이상 제출한 학생들의 업로드가 누락되는 버그가 있었습니다.

그리고 블랙보드 버전업에 따라 업로드 Form이 변경되었을지도 모릅니다. 

그 외에 기술적인 문제로 블랙보드에선 잘 인식하나 **Microsoft Office 2016 Excel**에선 열리지 않습니다. (*정확히는 열리면 다른 포맷으로 강제 변경되기에 열면 안됩니다*)

하지만 **한셀**이나 **노트패드 plus plus**로 열면 잘 열리니 값을 확인하거나 수정할 필요가 있다면 이 툴들을 이용해 수정하면 됩니다.

---------------------------
### 프로젝트 개요
Eclipse에서 사용하던 프로젝트를 그대로 업로드했습니다.
gitignore설정하는걸 까먹어서... 기타 잡다한 파일들도 그대로 올라가 있습니다.
대신, 별도 설정 없이 Eclipse에 그대로 불러올 수 있다는건 장점이겠죠?

----------------------
### 업데이트 로그
  1: OJ1버전 배포 및 소개
  - 테스트 케이스 1개로 자동채점
  - 파일 이름 정규화 기능(약함)
  - 유사도 검사
  - 결과 파일이 전부 csv파일
    
  2: OJ1에서 버그 수정
  - 정규화 버그 수정
  - 기타 설명 강화
  - 압축을 안 푼 경우 결과.xlsx파일에 적음
    
  3: OJ2로 판올림
  - 테스트 케이스 n개 입력 가능
  - 파일 이름 정규화 기능(강함)
  - 출석부와 연동
  - 유사도 검사 기능에 조건부 서식 추가
  - 결과 파일을 xlsx로 출력
    
  4: OJ2에서 버그 수정과 기능 추가
  - 학생 수가 0명일 경우 유사도에서 발생하는 오류 수정
  - 채점 결과에 조건부 서식 추가
  - 파일 지우기 기능 추가(명령 4)
  - 출력 메세지에 Swag 추가
    
  5: 블랙보드 일괄 업로드 기능 추가
  - 블랙보드로 업로드용 엑셀 파일 수정 기능 추가(명령 5)
  - 채점 결과 파일에 코멘트랑 점수 컬럼 추가
    
  6: 과제파일모음 기능 추가
  - 자동 채점한 과제 파일들은 한 폴더로 모아주는 기능을 채점과정 마지막에 추가
    
  7: 정규화 기능 개선
  - 정규화 후 압축을 자동으로 풀어서 hw폴더로 옮겨줌
    
  8: 채점 기능 개선
  - testcase 하나로 합침
  - 과제 파일에 대해서 자동 채점(사진 유무, 특정 변수 유무 등)
  - 채점 기능이 input, low, high, equal로 세분화
  - 채점 결과 파일에 전체 코드 요약해서 추가
  - config에 input("")로 만들기 기능 추가 
