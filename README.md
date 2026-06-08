# 📄 paper-to-obsidian

> **Claude Code 스킬** — PDF 논문을 읽고, AI가 3가지 핵심 항목으로 요약해서 Obsidian에 자동 저장합니다.

---

## 어떤 스킬인가요?

연구자가 논문 PDF 경로를 알려주면:

1. Claude가 논문 전체를 읽고
2. 아래 **3가지 섹션**으로 한국어 요약을 작성하고
3. Obsidian 볼트에 `논문제목(연도).md` 파일로 자동 저장합니다

```
1. 해결하고자 한 핵심 문제
   ↳ 선행 연구의 한계와 본 논문의 해결 방향

2. 사용한 구체적 방법론 (툴/알고리즘)
   ↳ 모델명·알고리즘·성능 수치 포함

3. 서론에 인용하기 좋은 핵심 문장 한 줄
   ↳ 인용 자리 [ ] 포함, 바로 붙여넣기 가능
```

---

## 사용 방법

Claude Code 대화창에서 PDF 경로와 함께 한 마디:

```
"D:\논문폴더\paper.pdf 요약해서 옵시디언에 저장해줘"
```

또는 경로를 붙여넣고:

```
"이 논문 요약해서 옵시디언에 저장해줘"
```

### 트리거 키워드 (이 중 하나만 말해도 자동 실행)

- 논문 요약해줘
- 옵시디언에 저장해줘
- 이 PDF 노트 만들어줘
- 논문 정리해줘

---

## 출력 예시

**파일명:** `Automated CV-Based Construction Progress Monitoring(Buildings2022).md`

```markdown
1. 해결하고자 한 핵심 문제 
    기존 CV 기반 CPM 연구들은 서브프로세스 1~2개만 개별 다루고,
    이들 간 연결성과 전체 자동화 수준을 통합 평가한 연구가 없음.
    
    - 서브프로세스 간 inter-connectivity 부재 → 실제 현장 도입 어려움
    - 기술 타당성 검증 수준에 머물러 건설 관리팀 의사결정과 미연계

2. 사용한 구체적 방법론 (툴/알고리즘)
    PRISMA 체계적 문헌 리뷰 (Scopus + WoS, 2011~2021, 180편).
    CNN + 감시 카메라 조합이 가장 높은 자동화 수준 제공.
    DAQ / SfM·CNN·SVM / BIM Registration(ICP) / Color Labels 4단계 분류.

3. 서론에 인용하기 좋은 핵심 문장 한 줄
    CV 기반 시공 진척도 모니터링은 DAQ, 정보 추출, 진척도 추정,
    결과 시각화의 네 서브프로세스로 구성되며[ ], 서브프로세스 간
    연결성 부재가 핵심 도입 장벽으로 지적된다[ ].
```

---

## 설치 방법

### Claude Code 스킬로 설치

1. 이 레포를 클론하거나 파일을 다운로드합니다

2. `SKILL.md`와 `references/` 폴더를 Claude Code의 스킬 디렉토리에 복사합니다:
   ```
   C:\Users\[username]\.claude\plugins\cache\anthropic-agent-skills\
   document-skills\[version]\skills\paper-to-obsidian\
   ```

3. **Obsidian 볼트 경로를 `SKILL.md`에서 수정합니다:**
   ```
   Default: C:\Users\[your-username]\Documents\Obsidian Vault\
   ```

4. Claude Code를 재시작하면 스킬이 자동으로 인식됩니다

---

## 파일 구조

```
paper-to-obsidian/
├── SKILL.md                    # 스킬 메인 파일 (Claude가 읽는 지침)
├── references/
│   └── note-template.md        # 노트 형식 템플릿 + 실제 예시
├── examples/
│   └── example-output.md       # 실제 생성된 노트 예시
└── demo/
    └── paper-to-obsidian-intro.pptx  # 스킬 소개 프레젠테이션
```

---

## 커스터마이징

`SKILL.md`에서 다음 항목을 수정할 수 있습니다:

| 항목 | 기본값 | 수정 방법 |
|---|---|---|
| Obsidian 볼트 경로 | `C:\Users\lihwa\Documents\Obsidian Vault\` | `SKILL.md` 상단 경로 변경 |
| 요약 언어 | 한국어 | `SKILL.md` Language Rules 수정 |
| 노트 형식 | 3섹션 고정 | `references/note-template.md` 수정 |
| 저장 폴더 | 볼트 루트 | 대화 시 "VR_reference 폴더에 저장해줘" |

---

## 요구사항

- [Claude Code](https://claude.ai/code) 설치
- Obsidian 설치 및 볼트 생성
- PDF 파일 접근 권한

---

## 개발 배경

경희대학교 AI+BIM 연구실에서 MR 기반 시공편차 탐지 연구를 진행하며,  
매일 쌓이는 reference 논문을 효율적으로 관리하기 위해 만든 개인용 Claude 스킬입니다.

`references/note-template.md`의 노트 형식은 실제 연구 노트 작성 패턴을 반영합니다.
