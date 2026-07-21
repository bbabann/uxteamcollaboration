# Retail Intelligence Dashboard — Design System v1.0

> **이 문서의 용도**
> Claude 공유 프로젝트 지식베이스에 등록해 팀 전원이 동일한 기준으로 UI를 만들기 위한 단일 기준 문서입니다.
> UI 작업 시 **이 문서에 정의된 토큰과 컴포넌트만** 사용합니다. 여기에 없는 값이 필요하면 임의로 만들지 말고 먼저 질문하세요.
>
> **현재 상태** — 규칙은 전부 확정. 색상값은 Tailwind 표준 램프에 스냅되어 확정. 치수(간격·폰트 크기)는 Figma 실측 후 §12의 절차로 교체 예정이며, 그전까지는 이 문서의 값을 그대로 사용합니다.

---

## 1. 제품 정의

브랜드 리테일 매장의 방문자 행동·체험앱·키워드를 분석하는 **B2B 애널리틱스 대시보드**.

사용자는 리테일 전략·CX 담당자이며, 하루에 여러 번 긴 시간 화면을 봅니다.

- **데이터가 주인공, UI는 배경.** 색은 데이터를 구분하기 위해 쓰고, 장식으로 쓰지 않습니다.
- **밀도 있게, 그러나 답답하지 않게.** 정보량이 많으므로 여백보다 정렬과 위계로 숨통을 틔웁니다.
- **화면이 달라도 조작법은 같게.** 필터·탭·내보내기의 위치와 생김새는 모든 페이지에서 동일합니다.

---

## 2. 컬러 토큰

전 토큰을 Tailwind 표준 램프에 스냅했습니다. shadcn/ui를 `baseColor: slate`로 설치하면 기본값과 그대로 맞물립니다.

**병합 이력** — 아래 6개 토큰은 기존 값과 사실상 동일해 제거되었습니다.

| 제거된 토큰 | 병합된 곳 | 사유 |
|---|---|---|
| `sidebar` (배경) | `foreground` | 동일 색 (`#151A2E` ≈ `#111827`) |
| `sidebar-accent` | `neutral-strong` | 동일 색 (`#262C42` ≈ `#1E2438`) |
| `rank-1` | `chart-7` | 동일 금색 |
| `rank-2` | `placeholder` | 동일 회색 |
| `rank-3` | `chart-5` | 동일 주황 |
| `rank-rest` | `primary-subtle` | 동일 연청 |

### 2.1 Neutral (slate)

| 토큰 | 값 | 용도 |
|---|---|---|
| `--background` | `#F8FAFC` | 콘텐츠 영역 배경 |
| `--muted` | `#F1F5F9` | 비활성 칩, 입력 보조 배경 |
| `--border` | `#E2E8F0` | 모든 구분선·입력 테두리 |
| `--sidebar-foreground` | `#CBD5E1` | 사이드바 기본 메뉴 텍스트 |
| `--placeholder` | `#94A3B8` | 플레이스홀더, 메타 정보, **순위 2위 배지** |
| `--muted-foreground` | `#64748B` | 본문 보조, 필터 라벨 |
| `--neutral-strong` | `#1E293B` | 실행 액션 버튼, 세그먼트 활성, **사이드바 활성 배경** |
| `--foreground` | `#0F172A` | 제목, 핵심 수치, **사이드바 배경** |
| `--card` / `--header` | `#FFFFFF` | 카드·패널·헤더 밴드 |

### 2.2 Brand (blue)

| 토큰 | 값 | 용도 |
|---|---|---|
| `--primary-subtle` | `#EFF6FF` | 선택 배경, 카운트 배지, **순위 4위 이하 배지** |
| `--primary` | `#2563EB` | 활성 탭, 링크, 플로우 화살표, **활성 메뉴 텍스트** |
| `--primary-hover` | `#1D4ED8` | 호버 |

### 2.3 Status

| 토큰 | 값 | 용도 |
|---|---|---|
| `--success` | `#16A34A` | 상승 지표 |
| `--danger` | `#DC2626` | 하락 지표, 삭제 |

### 2.4 Chart (고정 순서)

`--chart-1` `#8B5CF6` · `--chart-2` `#EC4899` · `--chart-3` `#3B82F6` · `--chart-4` `#22C55E` · `--chart-5` `#F97316` · `--chart-6` `#14B8A6` · `--chart-7` `#F59E0B`

**규칙**
- 카테고리 색은 항상 이 순서대로 배정합니다. 화면마다 다른 순서로 쓰면 같은 존이 다른 색으로 보입니다.
- 색은 **엔티티에 귀속**됩니다. 필터링해도 색이 다시 칠해지면 안 됩니다.
- 8개 이상이 필요하면 색을 추가하지 말고 "기타"로 묶습니다.

### 2.5 순위 배지 (전용 토큰 없음)

| 순위 | 배경 | 텍스트 |
|---|---|---|
| 1위 | `--chart-7` | `#FFFFFF` |
| 2위 | `--placeholder` | `#FFFFFF` |
| 3위 | `--chart-5` | `#FFFFFF` |
| 4위 이하 | `--primary-subtle` | `--foreground` |

### 2.6 globals.css

```css
:root {
  --background:        #F8FAFC;
  --foreground:        #0F172A;
  --card:              #FFFFFF;
  --card-foreground:   #0F172A;
  --popover:           #FFFFFF;
  --primary:           #2563EB;
  --primary-foreground:#FFFFFF;
  --primary-hover:     #1D4ED8;
  --primary-subtle:    #EFF6FF;
  --secondary:         #F1F5F9;
  --muted:             #F1F5F9;
  --muted-foreground:  #64748B;
  --placeholder:       #94A3B8;
  --neutral-strong:    #1E293B;
  --border:            #E2E8F0;
  --input:             #E2E8F0;
  --ring:              #2563EB;
  --success:           #16A34A;
  --destructive:       #DC2626;

  --sidebar:                    #0F172A;
  --sidebar-foreground:         #CBD5E1;
  --sidebar-accent:             #1E293B;
  --sidebar-accent-foreground:  #FFFFFF;
  --sidebar-primary:            #2563EB;

  --chart-1: #8B5CF6;
  --chart-2: #EC4899;
  --chart-3: #3B82F6;
  --chart-4: #22C55E;
  --chart-5: #F97316;
  --chart-6: #14B8A6;
  --chart-7: #F59E0B;

  --radius: 0.5rem;
}
```

`--sidebar`와 `--foreground`가 같은 값인 것은 의도된 병합입니다. shadcn의 sidebar 컴포넌트가 별도 변수를 요구하므로 별칭으로만 유지합니다.

---

## 3. 타이포그래피

**서체** — 산세리프 단일 패밀리 (Pretendard 권장, 영문 폴백 Inter).
수치에는 `font-variant-numeric: tabular-nums`를 적용해 자릿수가 흔들리지 않게 합니다.

**굵기는 400과 600 두 가지만** 사용합니다. 500·700은 쓰지 않습니다.

| 토큰 | 크기 / 굵기 | 용도 |
|---|---|---|
| `text-metric` | 28 / 600 | KPI 대표 수치 |
| `text-page-title` | 24 / 600 | 브레드크럼 페이지 제목 |
| `text-section` | 20 / 600 | 섹션 제목 |
| `text-brand` | 18 / 600 | 사이드바 최상단 제품명 |
| `text-subsection` | 16 / 600 | 카드 내 소제목 |
| `text-body` | 14 / 400 | 기본 본문, 목록 항목 |
| `text-label` | 14 / 600 | 필터 라벨, 버튼 |
| `text-meta` | 12 / 400 | 카드 메타, 슬라이더 눈금 |

위계가 부족하다고 느껴지면 **크기를 추가하지 말고 색과 굵기로 해결**합니다.

---

## 4. 스페이싱 & 레이아웃

### 4.1 스페이싱 스케일 (4px 기준)

`4 · 8 · 12 · 16 · 20 · 24 · 32 · 40 · 48 · 64`

이 값 외의 간격은 사용하지 않습니다.

### 4.2 Radius

| 토큰 | 값 | 용도 |
|---|---|---|
| `--radius-sm` | 6px | 배지, 작은 칩, 아이콘 버튼 |
| `--radius-md` | 8px | 버튼, 입력, 셀렉트 |
| `--radius-lg` | 12px | 카드, 패널 |
| `--radius-full` | 9999px | 세그먼트 컨트롤, 필터 칩, 순위 원형 배지 |

카드는 모두 `--radius-lg`로 통일합니다. (기존 화면 간 편차 해소)

### 4.3 그리드

| 항목 | 값 |
|---|---|
| 사이드바 폭 | 240px 고정 |
| 콘텐츠 좌우 패딩 | 32px |
| 헤더 밴드 상하 패딩 | 24px |
| 카드 내부 패딩 | 24px |
| 카드 간 간격 | 16px |
| KPI 카드 | 4열 균등 |
| 미디어 그리드 | `repeat(auto-fill, minmax(240px, 1fr))` |

### 4.4 Elevation

카드에는 **테두리(`--border`)만** 사용하고 그림자는 쓰지 않습니다. 그림자는 팝오버·드롭다운·모달 등 떠 있는 레이어에만 사용합니다.

---

## 5. 내비게이션 구조 (통합 확정)

기존 두 벌의 메뉴 체계를 하나로 병합했습니다. **서술형 명칭**을 기준으로 하고, 흩어져 있던 하위 항목을 의미에 맞는 그룹으로 재배치했습니다.

```
Global Retail Intelligence
├─ Planogram Review
├─ Visitor Journey Analysis
│  ├─ Overview
│  ├─ Path Analytics
│  └─ Engagement Metrics
├─ Experience App Analysis
│  ├─ App Library
│  └─ Flow Analysis
├─ Visitor Keyword Analysis
│  ├─ Keywords by CXP
│  ├─ Data Comparison by CXP
│  └─ Price-Related Keywords
├─ Retail Store Research
│  ├─ Store Image & Video Library
│  ├─ Store Layout Analysis
│  └─ Visual Attention Analysis
└─ Cross-brand Research
   └─ Cross-Brand Benchmarking
```

**변경 사항**
- `Ex App` / `Exp App` 혼용 → `Experience App Analysis`로 통일
- 축약형(`Planogram`, `Keyword`) → 서술형으로 통일
- `Cross-Brand Benchmarking`이 `Retail Store Research` 아래 있던 것을 `Cross-brand Research`로 이동
- 부모·자식 명칭 중복(`Experience App Analysis > Experience App Analysis`) 해소를 위해 자식을 `App Library` / `Flow Analysis`로 축약
- 사이드바 제품명은 `Global Retail Intelligence` 고정 (플레이스홀더 `Title` 제거)

> 최종 문구는 일괄 카피 작업 시 조정 가능합니다. **구조와 계층은 고정**이고, 문구만 교체 대상입니다.

### 5.1 사이드바 상태 규격

| 상태 | 표현 |
|---|---|
| 그룹 기본 | `--sidebar-foreground` 텍스트, 배경 없음, 우측 chevron |
| 그룹 열림 | `--neutral-strong` 배경, 흰색 텍스트, chevron 180° 회전 |
| 하위 기본 | `--sidebar-foreground` 텍스트 |
| 하위 활성 | **`--primary` 텍스트, 밑줄 없음** |
| 호버 | `--neutral-strong` 배경 |

**밑줄 활성 표시는 폐기합니다.** 링크로 오인되고, 제품 전반에서 파란색이 이미 활성 상태를 뜻하고 있어 중복입니다.

**하위메뉴 트리 선(`─`)은 폐기합니다.** 들여쓰기 16px만으로 계층이 충분히 전달됩니다.

---

## 6. 페이지 구조 (모든 화면 공통)

```
┌───────────┬──────────────────────────────────────────────────┐
│           │  브레드크럼 제목            [Upload] [Export]     │  ← 헤더 밴드 (흰색)
│  사이드바  ├──────────────────────────────────────────────────┤
│  (네이비)  │  탭1  탭2                                        │
│           ├──────────────────────────────────────────────────┤
│           │  Brand ▾  Country ▾  Store ▾  📅 기간   [⊞ ☰]   │
│           ├──────────────────────────────────────────────────┤
│           │                                                  │  ← 콘텐츠 (연회색)
│           │   ┌────────────────────────────────────────┐     │
│           │   │  카드 (흰색)                            │     │
│           │   └────────────────────────────────────────┘     │
└───────────┴──────────────────────────────────────────────────┘
```

**고정 규칙**
1. `Upload` / `Export`는 항상 헤더 우측 상단, `outline` 버튼, 아이콘 + 라벨.
2. 페이지 제목은 항상 `상위메뉴 > 현재메뉴` 브레드크럼.
3. **브레드크럼의 상위 세그먼트는 §5 트리의 그룹명과 정확히 일치**해야 합니다. 트리에 없는 이름을 쓰지 않습니다.
4. 필터 바 순서 `Brand → Country → Store → 기간 → (시간)` 고정.
5. 뷰 전환 토글은 필터 바 최우측.
6. 흰색 헤더 밴드 → 연회색 콘텐츠 → 흰색 카드의 3층 구조 유지.

---

## 7. 필터 규격 (통합 확정)

**모든 필터는 좌측 외부 라벨 + 사각 셀렉트**로 통일합니다. 라운드 pill + 라벨 없는 방식은 폐기합니다. 값을 지우면 무엇을 고르는 필터인지 알 수 없기 때문입니다.

```
Brand  [ All Brands        ▾ ]   Country  [ All Countries    ▾ ]
```

| 속성 | 값 |
|---|---|
| 라벨 | `text-label`, `--muted-foreground`, 셀렉트 좌측 8px |
| 셀렉트 높이 | 36px |
| 셀렉트 radius | `--radius-md` |
| 셀렉트 테두리 | `0.5px solid --border` |
| 필터 간 간격 | 20px |
| 기본값 표기 | `All {대상}` |
| 날짜 | 좌측 분리된 아이콘 박스 + 범위 입력 |
| 시간 | 날짜와 동일 패턴, 시계 아이콘 |

라운드 pill 형태는 **필터 칩(카테고리 토글)에만** 남겨둡니다. 이 둘은 역할이 다릅니다 — 셀렉트는 값 선택, 칩은 범위 좁히기.

---

## 8. 액션 위계 (통합 확정)

| 역할 | 색 | 컴포넌트 | 예시 |
|---|---|---|---|
| **상태 / 선택** | `--primary` (파랑) | 탭 언더라인, 활성 메뉴, 링크, 플로우 화살표 | 활성 탭, Path Analytics 메뉴 |
| **실행 액션** | `--neutral-strong` (네이비) | `button` default, 활성 세그먼트 | Compare, All Time |
| **보조 액션** | 투명 + 테두리 | `button` outline | Upload, Export |

파랑과 네이비가 둘 다 "강조"로 쓰이던 문제를 역할 분리로 해결합니다. 파랑은 **지금 어디에 있는지**, 네이비는 **무엇을 실행하는지**를 나타냅니다.

---

## 9. 컴포넌트 규격 및 shadcn/ui 매핑

새 컴포넌트를 만들기 전에 이 표에 해당 항목이 있는지 먼저 확인하세요.

| 화면 요소 | shadcn 컴포넌트 | 규격 / 비고 |
|---|---|---|
| 좌측 내비게이션 | `sidebar` | 다크 변형, 240px 고정 |
| 메뉴 그룹 펼침 | `collapsible` | 우측 chevron, 열림 시 회전 |
| 페이지 제목 | `breadcrumb` | 2단계 고정 |
| Upload / Export | `button` `variant="outline"` | 높이 36px, 아이콘 좌측 |
| 실행 액션 | `button` `variant="default"` | `--neutral-strong` 배경 |
| 상단 탭 | `tabs` | 언더라인, 활성 `--primary` |
| 기간 세그먼트 | `toggle-group` `type="single"` | pill, 활성 `--neutral-strong` |
| 카테고리 칩 | `toggle-group` `type="single"` | pill, `variant="outline"` |
| Brand/Country/Store | `select` | §7 규격 |
| 날짜 범위 | `popover` + `calendar` | 아이콘 박스 분리 |
| 시간 범위 | `popover` + `input` | 날짜와 동일 패턴 |
| 그리드/리스트 전환 | `toggle-group` | 아이콘 전용, `aria-label` 필수 |
| 미디어 카드 | `card` + `aspect-ratio` | 썸네일 16:9 |
| 카드 더보기 (⋮) | `dropdown-menu` | 카드 우상단 |
| 미디어 타입 오버레이 | `badge` | 썸네일 좌하단 |
| 브랜드/국가 패싯 | `accordion` + `badge` | 항목명 + 우측 카운트 |
| 카운트 배지 | `badge` `variant="secondary"` | `--primary-subtle` 배경 |
| 순위 배지 | `badge` 커스텀 | §2.5 |
| KPI 카드 | `card` | 대문자 소제목 + 수치 + 증감 |
| 슬라이더 | `slider` | 하단 좌우 끝 최소/최대 라벨 |
| 리스트 뷰 | `table` | 그리드 뷰의 대안 |

**도입 순서**
1. §2.6의 CSS 변수를 `globals.css`에 먼저 정의
2. `components.json`에서 `baseColor: slate` 설정
3. 컴포넌트 설치

순서를 바꾸면 shadcn 기본 색이 섞여 들어갑니다.

**shadcn 컴포넌트 파일을 직접 수정하지 않습니다.** 필요한 변형은 `variant`로 추가합니다.

---

## 10. 금지 사항

- ❌ §2에 없는 색상값 생성 — 회색이 필요하면 기존 회색 중에서 고릅니다
- ❌ §3에 없는 폰트 크기 추가, 굵기 500·700 사용
- ❌ §4.1 스케일에 없는 간격 (14px, 18px, 22px 등)
- ❌ 카드에 그림자 사용
- ❌ 같은 기능에 다른 컴포넌트 사용
- ❌ 카테고리 색을 화면마다 다른 순서로 배정
- ❌ 활성 상태를 밑줄로 표시
- ❌ 라벨 없는 필터 셀렉트
- ❌ §5 트리에 없는 이름을 브레드크럼에 사용
- ❌ 아이콘 전용 버튼에 `aria-label` 누락
- ❌ **아티팩트(채팅 미리보기)에서 Tailwind 임의값 클래스 사용** — §11 참고

---

## 11. 실행 환경별 제약

같은 코드라도 어디서 실행하느냐에 따라 되는 것과 안 되는 것이 다릅니다. 특히 채팅 아티팩트는 **에러 없이 조용히 어긋나는** 경우가 있어 주의가 필요합니다.

| 항목 | 저장소 (Vite/Next 등) | 채팅 아티팩트 |
|---|---|---|
| 로컬 `import './data'` | ✅ | ❌ 단일 파일만 |
| shadcn/ui 전체 | ✅ | ⚠️ 일부만. `Breadcrumb`·`Select`·`Tabs`는 없을 수 있음 |
| Tailwind 임의값 `text-[28px]` | ✅ | ❌ **에러 없이 무시됨** |
| `localStorage` | ✅ | ❌ |
| 대용량 에셋(base64 등) | ✅ | ❌ 용량 초과로 로드 실패 |

### 아티팩트에서 UI를 실험할 때

1. **임의값 클래스 금지.** `text-[28px]`, `max-w-[74ch]`, `w-[192px]` 등 대괄호 클래스는 컴파일러가 없어 무시됩니다. 에러가 나지 않고 크기·여백만 틀리게 나오므로 발견이 늦습니다. 코어 유틸리티(`text-sm`, `gap-4`)로 표현되지 않는 값은 **인라인 스타일**로 씁니다.
2. **토큰은 JS 객체로.** 아티팩트에는 `globals.css`가 없어 `var(--primary)`가 해석되지 않습니다. §2 값을 담은 상수 객체를 파일 안에 두고 참조합니다.
3. **데이터와 에셋은 분리하거나 대체.** 실험 단계에서는 이미지 자리에 자리표시자를 두고, 레이아웃과 토큰만 검증합니다.
4. **shadcn 의존을 최소화.** 실험 버전은 같은 규격으로 직접 구현하고, 저장소로 옮길 때 §9 매핑표대로 shadcn 컴포넌트로 교체합니다.

> **원칙** 아티팩트는 **디자인 검증용**, 저장소는 **구현용**입니다. 두 버전의 토큰·타이포·간격·구조는 반드시 같아야 하며, 다른 것은 컴포넌트 구현 방식과 에셋뿐입니다.

---

## 12. 이후 갱신 절차

**치수 확정 (Figma 실측)**
1. Figma에서 Local Variables로 색·타이포·간격 등록
2. Design Tokens 또는 Tokens Studio 플러그인으로 JSON export
3. JSON을 이 프로젝트에 업로드해 §3·§4의 값을 실측값으로 교체
4. 색상은 §2로 이미 확정되었으므로 Figma 쪽을 §2에 맞춥니다 (역방향 아님)

**카피 일괄 변경**
§5의 구조는 유지한 채 문구만 교체합니다. 교체 시 §6-3(브레드크럼 = 트리 그룹명)을 함께 갱신해야 합니다.

기존 확인된 오타는 카피 작업 시 함께 처리: `Overivew` → `Overview`, `Freature II` → `Feature II` (2곳), `Sqaure` → `Square`.

---

## 13. 프로젝트 인스트럭션 (복사용)

공유 프로젝트의 커스텀 인스트럭션에 아래를 붙여넣으세요.

```
UI 작업 시 지식베이스의 design-system.md를 유일한 기준으로 사용한다.

- §2에 정의된 컬러 토큰만 사용한다. 새 색상값을 만들지 않는다.
- §3의 타이포 스케일과 §4.1의 스페이싱 스케일만 사용한다.
- §9 매핑표에 있는 shadcn/ui 컴포넌트를 우선 사용하고,
  없는 경우에만 새로 만든다.
- §5의 내비게이션 트리에 없는 메뉴명을 사용하지 않는다.
- §10의 금지 사항을 위반하지 않는다.
- 문서에 정의되지 않은 값이 필요하면 임의로 정하지 말고 먼저 질문한다.
- 코드 작성 전, 어떤 토큰과 컴포넌트를 쓸 것인지 먼저 요약해 보여준다.
```
