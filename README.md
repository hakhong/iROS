# 🖥️ iROS — Imaginary Retro OS Simulator
### 1950~1960년대 컴퓨터 역사 교육용 시뮬레이터

> 재미있었습니다. 끝. — 만든 사람

---

## 이름에 대하여

```
Imaginary = ① 허수(虛數, √-1)
              실수처럼 보이지만 실수가 아님
              → 진짜처럼 보이지만 진짜 컴파일러/하드웨어 아님

            ② 상상의, 가상의
              → 1960년대 컴퓨터 환경을 상상으로 재현

iROS = Imaginary Retro OS Simulator
       두 의미가 동시에 적용됨
```

---

## ⚠️ 솔직한 고백 (먼저 읽으세요)

```
진짜인 것:
  ✓ 홀러리스 천공카드 구멍 위치 (IBM 026 실제 표준)
  ✓ FORTRAN II 컬럼 배열 (COL 1-5/6/7-72/73-80)
  ✓ COBOL-60 컬럼 배열 (COL 1-6/7/8-11/12-72/73-80)
  ✓ 역사 샘플 코드 (당시 실제 사용된 프로그램)
  ✓ 라운드로빈 CPU 스케줄링 개념
  ✓ Dartmouth BASIC 인터프리터 실행

가짜였던 것 (제거됨):
  ✗ IR 중간언어 표현
  ✗ 기계어 바이너리 표현
  ✗ 가짜 배치 실행 시뮬레이션
  ✗ JS 파서 (버그 있어서 제거)

실행 연동:
  FORTRAN → godbolt.org gfortran API (자동 변환 후 실행)
  COBOL   → jdoodle.com GnuCOBOL (COBOL-60→GnuCOBOL 변환 후 클립보드)
```

---

## 🔧 COBOL-60 → GnuCOBOL 자동 변환

```
시퀀스 번호(COL 1-6) 제거     000100 IDENT... → IDENT...
주석 형식 변환                 000500*         → *>
PIC A(N) → PIC X(N)           PIC A(20)       → PIC X(20)
obsolete 단락 주석 처리        DATE-WRITTEN.   → *> [OBSOLETE]
```

## 🔧 FORTRAN II → gfortran 자동 변환

```
C 주석 → ! 주석               C COMMENT  → ! COMMENT
컬럼 제거 (자유형식)           [col7-72]  → 그대로
연속행 처리                    컬럼6 숫자 → &
```

---

## 📁 구조

```
iROS/
├── stage1-batch/
│   └── punchcard_unified.html        # 천공카드 시뮬레이터
├── stage2-interactive/
│   └── dartmouth_basic.html          # Dartmouth BASIC 터미널
├── stage3-timesharing/
│   └── timesharing_os.html           # 시분할 OS 시뮬레이터
├── assets/
│   └── punchcard_reference.pdf           # 천공카드 정밀 재현 + 홀러리스 참조표
│                                          # (71페이지, FORTRAN/COBOL 카드 1장씩)
├── devlog.pdf                        # 개발 과정 대화 기록
├── index.html                        # 랜딩 페이지
├── README.md
└── LICENSE
```

---

## 📄 Assets (참조 자료)

### punchcard_reference.pdf (0.2MB, 4페이지)
- FORTRAN II / COBOL-60 카드 정밀 재현 (A4 가로, 카드 1장/페이지)
- 홀러리스 인코딩 전체 참조표 포함 (A~Z, 0~9, 특수문자 구멍 위치)
- FORTRAN 컬럼 영역 색상 구분 (레이블/연속/코드/식별)
- COBOL 컬럼 영역 색상 구분 (시퀀스/지시자/Area A/Area B)
- 실제 홀러리스 구멍 위치 + 하단 필드 분석 포함

> 브라우저에서 열고 **인쇄 → PDF 저장** 하면 고화질로 저장됩니다.

---

## 🚀 실행

서버 불필요. 브라우저에서 바로 열기:

https://hakhong.github.io/iROS/


---

## 🕰️ 역사

```
1890  홀러리스 천공카드 발명
1957  FORTRAN II — IBM 704, 천공카드 일괄처리
1959  COBOL-60   — 그레이스 호퍼, 비즈니스용
1964  BASIC      — 다트머스, 최초 일반인용
1967  Multics    — MIT, 시분할 OS
1969  Unix       — Bell Labs, 현대 OS의 시작
```

---

## 🛠️ 알려진 한계

| 항목 | 상태 |
|------|------|
| FORTRAN 실행 | godbolt.org gfortran API (실제) |
| COBOL 실행 | jdoodle.com GnuCOBOL (클립보드 복사) |
| BASIC 실행 | JS 인터프리터 (기본 문법만) |
| 기계어/IR | 제거됨 (가짜였음) |
| GE-645/IBM 7094 | 시뮬레이션 아님 |

**PR 환영합니다. 단 저는 안 합니다. **

---

## 📄 라이선스

MIT License · Copyright (c) 2026 [kthdemon@naver.com]
Generated with **Claude Sonnet 4.6** (Anthropic)

Not affiliated with IBM Corporation.
홀러리스 인코딩: Public Domain (Herman Hollerith, 1890)

*"과거가 궁금하신 분은 박물관 가세요."*
