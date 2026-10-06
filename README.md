# 나의 과외일지

학생·선생님·학부모가 **하나의 링크 + 공통 비밀번호**로 함께 쓰는 과외 학습 일지.
로그인·계정 없이 Firebase 공유 저장소에 실시간 저장. Vercel 정적 배포.

## 역할
| 역할 | 할 수 있는 일 |
|---|---|
| 🎒 STUDENT | 수업 기록 추가·수정·삭제 + 숙제완료 체크 |
| 👩‍🏫 TEACHER | 수업 기록 추가·수정·삭제 |
| 👪 PARENT | 보기 + 학부모 확인 체크 |

(역할 버튼은 화면 모드이며 기기별로 기억됩니다.)

## 기록 항목
회차 · 날짜 · 장소 · 시간 · 과목 · 학습 내용 · 숙제 · 이해도(★) · 한줄 소감
+ 상태: 숙제완료 · 학부모확인 / 다음 수업 D-day / 월별 정리

## 설정 (이미 반영됨)
- Firebase 프로젝트: `axolveedu-973e7` (설정값은 `index.html`에 입력 완료)
- 공통 비밀번호: `axolve` (변경하려면 index.html의 `const PASSCODE` 수정)

### Firestore 규칙 (Firebase 콘솔 → Firestore → 규칙 → 게시)
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /lessons/{docId} {
      allow read, write: if true;
    }
  }
}
```
> 주의: lessons 컬렉션을 공개로 둡니다. 링크·비밀번호를 가족/선생님 외부에 공유하지 마세요.

## 배포 (Vercel · GitHub 연동)
저장소: https://github.com/dyhan0528/tutor-log
- vercel.com → Add New → Project → `tutor-log` → Deploy (정적 HTML, 빌드 없음)
- 이후 git push 때마다 자동 재배포

## 파일
- `index.html` — 앱 전체(한 파일)
- `README.md` — 이 문서
