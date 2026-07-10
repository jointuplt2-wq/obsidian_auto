# E2E 테스트 (End-to-End Test) 완전 가이드

## 1. E2E 테스트란?

**한 줄 결론:** 실제 사용자처럼 앱을 처음부터 끝까지 테스트하는 방법입니다.

> 마치 식당 품질 검사관이 직접 들어가서 주문하고, 음식을 받고, 계산까지 해보는 것과 같습니다. 주방(백엔드)이나 재료(DB)를 따로 검사하는 게 아니라, **전체 경험**을 검사합니다.

---

## 2. 테스트 종류 비교

```
Unit Test       → 함수 하나 테스트        (부품 검사)
Integration Test → 모듈 간 연결 테스트    (조립 검사)
E2E Test        → 전체 흐름 테스트        (완성품 검사)
```

|구분|속도|비용|신뢰도|
|---|---|---|---|
|Unit|빠름|낮음|낮음|
|Integration|보통|보통|보통|
|**E2E**|**느림**|**높음**|**높음**|

---

## 3. 언제 E2E 테스트를 써야 하나?

**필수 적용 시나리오:**

- 로그인 / 회원가입 흐름
- 결제 프로세스
- 핵심 비즈니스 로직 (장바구니 → 주문 → 완료)
- 배포 전 smoke test

**굳이 안 써도 되는 경우:**

- 단순 UI 스타일 변경
- 유틸리티 함수 로직
- 단순 CRUD API

---

## 4. 주요 E2E 도구

### Playwright (현재 업계 표준 ✓)

```typescript
import { test, expect } from '@playwright/test'

test('로그인 후 대시보드 이동', async ({ page }) => {
  // 1. 페이지 이동
  await page.goto('https://myapp.com/login')

  // 2. 입력
  await page.fill('#email', 'user@example.com')
  await page.fill('#password', 'password123')
  await page.click('button[type="submit"]')

  // 3. 검증
  await expect(page).toHaveURL('/dashboard')
  await expect(page.locator('h1')).toContainText('환영합니다')
})
```

### Cypress (프론트엔드 친화적)

```javascript
describe('로그인', () => {
  it('성공적으로 로그인한다', () => {
    cy.visit('/login')
    cy.get('#email').type('user@example.com')
    cy.get('#password').type('password123')
    cy.get('button[type="submit"]').click()
    cy.url().should('include', '/dashboard')
  })
})
```

---

## 5. E2E 테스트 구조 (AAA 패턴)

```typescript
test('상품 구매 흐름', async ({ page }) => {
  // ARRANGE — 준비
  await page.goto('/products')

  // ACT — 행동
  await page.click('.product-card:first-child')
  await page.click('#add-to-cart')
  await page.click('#checkout')
  await page.fill('#card-number', '4242424242424242')
  await page.click('#pay-button')

  // ASSERT — 검증
  await expect(page.locator('.success-message'))
    .toContainText('주문이 완료되었습니다')
})
```

---

## 6. E2E 테스트 모범 사례

### ✅ 해야 할 것

```typescript
// 1. 역할 기반 선택자 사용 (안정적)
page.getByRole('button', { name: '로그인' })
page.getByLabel('이메일')
page.getByTestId('submit-btn')

// 2. 명시적 대기 (암묵적 sleep 금지)
await expect(page.locator('.result')).toBeVisible()  // ✓
await page.waitForSelector('.result')                // ✓

// 3. 테스트 격리 — 각 테스트는 독립적으로
test.beforeEach(async ({ page }) => {
  await page.goto('/login')
  // 초기화 로직
})
```

### ❌ 하면 안 되는 것

```typescript
// CSS 클래스 기반 선택자 (취약)
page.locator('.btn-primary.mt-4')  // ✗ 스타일 바뀌면 깨짐

// 하드코딩 sleep
await page.waitForTimeout(3000)   // ✗ 느리고 불안정

// 테스트 간 상태 공유
// ✗ 한 테스트의 결과가 다른 테스트에 영향
```

---

## 7. 실전 폴더 구조

```
tests/
├── e2e/
│   ├── auth/
│   │   ├── login.spec.ts
│   │   └── signup.spec.ts
│   ├── checkout/
│   │   └── purchase-flow.spec.ts
│   └── smoke/
│       └── critical-paths.spec.ts
├── fixtures/
│   └── test-data.json
└── playwright.config.ts
```

---

## 8. Playwright 설정 예시

```typescript
// playwright.config.ts
import { defineConfig } from '@playwright/test'

export default defineConfig({
  testDir: './tests/e2e',
  timeout: 30_000,
  retries: 2,           // 실패 시 2회 재시도
  workers: 4,           // 병렬 실행
  use: {
    baseURL: 'http://localhost:3000',
    screenshot: 'only-on-failure',  // 실패 시 스크린샷
    video: 'retain-on-failure',     // 실패 시 영상
    trace: 'on-first-retry',
  },
  projects: [
    { name: 'chromium', use: { ...devices['Desktop Chrome'] } },
    { name: 'mobile',   use: { ...devices['iPhone 13'] } },
  ],
})
```

---

## 9. CI/CD 파이프라인 통합

```yaml
# GitHub Actions 예시
- name: E2E Tests
  run: npx playwright test
  
- name: Upload Test Results
  uses: actions/upload-artifact@v3
  if: failure()
  with:
    name: playwright-report
    path: playwright-report/
```

---

## 10. 핵심 요약

|항목|내용|
|---|---|
|**목적**|사용자 관점의 전체 흐름 검증|
|**도구**|Playwright (권장), Cypress|
|**대상**|핵심 비즈니스 플로우|
|**패턴**|AAA (Arrange-Act-Assert)|
|**주의**|느림 → 핵심 경로만 선별|

더 궁금한 부분이 있으면 알려주세요! 특정 프레임워크(Next.js, React 등)에 맞는 구체적인 예시도 도와드릴 수 있습니다.