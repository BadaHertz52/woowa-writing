# 성능 최적화

## 1. 성능 최적화 필요성

### UX와 고객 유치

성능을 개선하는 것은 고객 유치와 유지에 밀접한 관계가 있다. 사이트 속도가 빨라지면 운영 비용이 감소하고, 사용자 경험(UX)이 개선된다. 성능 개선 사례로 Tokopedia와 Pinterest의 성공적인 최적화 결과를 들 수 있다.

- **[Tokopedia](https://wpostats.com/2018/05/30/tokopedia-new-users.html)**: 3G 연결에서 렌더링 시간을 14초에서 2초로 줄여 방문자 19% 증가
- **[Pinterest](https://wpostats.com/2017/03/10/pinterest-seo.html)**: 페이지 성능을 개선해 대기 시간을 40% 줄이고 SEO 트래픽과 전환율이 각각 15% 증가

[구글의 연구](https://www.ascentkorea.com/core-web-vitals/)에서도 성능이 고객 유치에 얼마가 영향을 주는 지 알 수 있다. **코어 웹 바이탈**(Core Web Vitals)을 충족한 페이지는 방문자가 사이트를 떠날 확률이 24% 낮다. 모바일 기기의 경우 모바일 사이트의 53%가 로드하는데 3초 이상 걸리면 사용자는 해당 사이트를 떠났다.

- 코어 웹 바이탈(Core Web Vitals)?
  구글이 웹 콘텐츠 이용자의 사용자 경험에 영향르 미치는 다양한 값 중 중요시 여기는 3가지로,
  LCP(Largest Contentful Pain), FID(First Input Delay), CLS(Cumulative Layout Shift)가 있습니다.

### SEO (검색 최적화)

성능은 UX뿐만아니라 검색 엔진의 순위에도 영향을 준다.
2010년 구글은 사이트 속도가 검색 순위에 반영된다고 [발표](https://developers.google.com/search/blog/2010/04/using-site-speed-in-web-search-ranking)했습니다. 발표 이후 색 순위에서의 사이트 속도의 중요도는 점점 커졌다.

결국 성능 최적화를 진행하는 이유는 **'사용자에게 불편함 없는 서비스 제공해 비즈니스적 이점을 취하는 것'**에 있다.

<p align="center">
<img loading="lazy" src="./images/technicalWriting/performance_ux.jpeg" width="300"  alt="브라우저 렌더링 과정 설명">
</p>

## 2. 성능 측정

### 측정 항목

성능 최적화의 목표가 UX 증대이듯, [성능 측정 항목](https://web.dev/articles/user-centric-performance-metrics?hl=ko)도 사용자가 실직적으로 서비스를 사용하는 방식과 밀접한 관련이 있다.

- **인식된 로드 속도:** 페이지가 로드되고 모든 시각적 요소를 화면에 렌더링할 수 있는 속도
- **로드 응답성:** 구성요소가 사용자 상호작용에 빠르게 응답하기 위해 페이지가 필요한 자바스크립트 코드를 로드하고 실행할 수 있는 속도
- **런타임 응답성:** 페이지 로드 후 페이지가 사용자 상호작용에 얼마나 빠르게 반응할 수 있는가
- **시각적 안정성:** 페이지 요소가 사용자가 예상하지 못한 방식으로 전환되어 상호작용을 방해하는가
- **부드러움:** 전환 및 애니메이션이 일관된 프레임 속도로 렌더링되고 한 상태에서 다음 상태로 부드럽게 흐르는가?

### 측정 지표

웹 성능을 측정하는 중요한 지표에는 **LCP**, **FCP**, **CLS** 등이 있다. 이러한 지표를 사용하여 웹 페이지의 성능을 평가하고 개선할 수 있다.

| 지표                           | 설명                                                                         |
| ------------------------------ | ---------------------------------------------------------------------------- |
| LCP(Largest Contentful Paint)  | 페이지 로드 중 가장 큰 이미지나 텍스트 블록이 화면에 표시되는 시간           |
| FCP(First Contentful Paint)    | 페이지 로드 중 처음으로 화면에 텍스트나 이미지가 나타나는 시간               |
| CLS(Cumulative Layout Shift)   | 예기치 않은 레이아수 변화가 발생하는 빈도                                    |
| TTFB(Time to First Byte)       | 사용자가 요청 보낸 후 서버가 첫 번째 바이트를 응답하는 데 걸리는 시간        |
| INP(Interaction to Next Paint) | 사용자가 상호작용(클릭,탭등)을 하고 그에 따른 화면 갱신이 일어나는 지연 시간 |

#### PageSpeedTools의 품질 평가 기준

| 지표 | 좋음        | 개선 필요        | 나쁨        |
| ---- | ----------- | ---------------- | ----------- |
| FCP  | [0, 1800ms] | (1800ms, 3000ms] | 3000ms 초과 |
| LCP  | [0, 2500ms] | (2500ms, 4000ms] | 4000ms 초과 |
| CLS  | [0, 0.1]    | (0.1, 0.25]      | 0.25 초과   |

### 측정 도구

#### [Goggle Lighthouse](https://pagespeed.web.dev/)

웹 페이지의 종합적인 성능을 평가하고, 접근성, SEO, PWA 성능까지 측정 가능. 성능 최적화 방법도 제시한다. 모바일과 테스트톱 성능을 평가할 수있다.

- Lighthouse 성능 측정 결과
<p align="center">
  <img loading="lazy" src="./images/technicalWriting/light_house.jpeg" alt="lighthouse에서 성능 측정 결과" width="400"/>
</p>

#### [Page Speed Insights](https://pagespeed.web.dev/)

실사용자 데이터를 바탕으로 웹 페이지의 속도와 성능을 분석한다. 모바일과 테스트톱 성능을 평가할 수있다.

<p align="center">
  <img loading="lazy" src="./images/technicalWriting/pageSpeed.jpeg" alt="설명" width="400" />
</p>

### [WebPageTest](https://stratoflow.com/website-performance-metrics/)

다양한 국가, 브라우저, 기기에서 테스트 가능해 다양한 환경에서 성능을 테스트할 수 있다. 또한 세부적인 성능 병목을 분석하는 데 유용하다.

- webapage test에서 프랑스에서 3G 환경에서 테스트 결과

<p align="center">
  <img loading="lazy" src="./images/technicalWriting/webpage_test.jpeg" alt="webapage test에서 프랑스에서 3G 환경에서 테스트한 모습"  width="500"/>
</p>

### Chrome DevTools

크롬의 개발자 도구로, 개발자 도구를 통해 페이지 로딩 중 발생하는 다양한 작업의 타이밍,리소스 크기, 캐시 여부등을 분석할 수 있다. network, performance에서 네트워크나 cpu 감속에 따른 테스트도 진행할 수 있다. 크롬에서 제공하는 다양한 성능 측정 플러그인(ex [React Developer Tools](https://chromewebstore.google.com/detail/React%20Developer%20Tools/fmkadmapgofadopljbjfkapdkoienihi), [LCP&CLS Monitor](https://chromewebstore.google.com/detail/lcp-cls-monitor/lcifpchofigigpgmhpghagcifokadjaa))을 통해 확장된 여러 성능 측정이 가능하다.

- 개발자도구에서 cpu,네트워크 감속해서 성능 측정한 사진

 <p align="center">
    <img loading="lazy" src="./images/technicalWriting/dev_tools_performance.jpeg" alt="개발자도구에서 cpu,네트워크 감속해서 성능 측정한 모습" width="600">
</p>

#### [GTmetrix](https://gtmetrix.com/)

웹 페이지의 로딩 성능을 분석하고, 최적화 방안을 제시한다. 성능 이력 추적 및 세부적인 성능 분석 가능하다.

- GTmetrix 성능 측정한 모습
 <p align="center">
    <img loading="lazy" src="./images/technicalWriting/gtmetrix.jpeg" alt=" GTmetrix 성능 측정한 모습" width="600">
</p>

* 측정 도구별 주요 성능 측정 지표
  |도구|주요 성능 측정 지표|
  |----|------------------|
  |Google Lighthouse| LCP, FCP, CLS, TBT, INP, PWA 성능|
  |PageSpeed Insights| LCP, FCP, CLS, TBT, TTI|
  |WebPageTest| LCP, TTFB, CLS, Speed Index, First Byte, Time to Interactive|
  |Chrome DevTools Performance Panel| JavaScript 실행 시간, 리플로우, 리페인트, 네트워크 요청 시간|
  |GTmetrix| LCP, FCP, CLS, Page Load Time, Total Page Size, HTTP Requests|

### webpack-bundle-analyzer

Webpack을 사용 중이라면, webpack-bundle-analyzer를 사용해 번들링 된 리소스의 크기를 확인할 수 있다.

## 3. 브라우저 렌더링 과정

성능 저하의 원인과 개선 방법을 이야기에 앞서, 브라우저 렌더링 과정에 대한 이해가 필요하다.

<p align="center">
 <img  loading="lazy" src="./images/technicalWriting/browser_rendering.jpeg"  alt="브라우저 렌더링 과정 설명">
</p>

브라우저에는 여러 엔진이 있다. 그 중 브라우저 렌더링 과정과 직간접으로 영향이 있는 엔진은 렌더링 엔지과 자바스크립트 엔진이다. 렌더링 엔진은 리소스(html, css, 이미지등)를 파싱하여 웹 페이지에 그린다. 자바스크립트 엔진은 자바스크립트 코드를 파싱하여 페이지 상호작용 및 동적 변화를 처리한다.

렌더링 엔진에서 일어나는 브라우저 렌더링 과정은 다음과 같다.

### 렌더링 엔진의 브라우저 렌더링 과정

#### 과정

**1. 파싱 단계**
HTML 파일을 파싱해 DOM을 생성하고, CSS 파일을 파싱해 CSSOM을 생성한다.

**2. 레이아웃**
DOM과 CSSOM을 결합하여 렌더 트리를 구성하고, 각 요소의 위치와 크기를 계산한다.

**3. 페인팅**
요소들의 스타일을 적용하여 화면에 출력할 내용을 결정한다.

**4. 컴포지팅**
이전 단계에서 만든 여러 레이어를 결합나다.

**5. 화면에 표시**
컴포지팅 단계에서 끝낸 결과물은 GPU 프로세스가 화면에 그린다.

#### 리플로우,리페인팅,리컴포지팅

- 리플로우 : DOM 구조나 레이아웃이 변경될대 브라우저가 레이아웃을 다시 계산하는 과정
  <br/>
- 리페인팅: 레이아웃 변화 없이 시각적 스타일이 변경될 때 화면을 다시 그리는 과정
  <br/>
- 리컴포지팅 : 레이어가 변경되거나 애니메이션을 처리할 때 레이어를 GPU가 결합하는 과정

#### 자바스크립트에 의한 DOM,CSSOM 변경

자바스크립트의 파싱 작업이 실행되는 때는 자바스크립트를 실행하는 코드에 따라 다르다.

`head`태그나 `body`태그 시작점에 script 태그가 있다면, HTML 파싱 시 해당 코드를 만다면 HTML 파싱을 중단하고 자바스크립트 엔진이 자바스크립트 파일을 파싱힌다. 자바스크립트 파싱 작업이 끝난 후에 중단된 HTML 파싱을 재개한다.

`body`태그 끝에 있거나 `script`에서 `defer`을 사용했다면 HTML 파싱이 끝나 DOM이 생겨난 후에 자바스크립트 파싱 작업이 이루어진다.

`script`에 `async`를 사용했다면 HTML 파싱 작업에서 해당 태그를 만다면 js파일을 로드하다가 로드가 끝나면 HTML 파싱 작업을 중단하고 자바스크립트 파싱작업을 실행한다.

이렇게 **파싱된 자바스크립트 코드에 DOM,CSSOM에 변경을 주는 코드가 있다면, 리플로우와 리페인팅이 발생**한다.

## 4. 성능 저하 원인 및 해결 방법

### 로딩 성능

#### 원인

로딩하는 리소스 파일이 크거나 HTTP 요청 건수가 많거나 서버의 지연으로 인해 로딩 속도가 느려진다. 로딩 속도가 느리면 페이지 렌더링이 지연되어 성능 저하를 일으킨다.

#### 해결 방법

**1. 요청 리소스 크기를 줄이기**

> 💡자세한 성능 최적화 방법은 ['Webpack에서 성능 최적화 하기'파트](#optimization)에서 다루고 있다.

- JS 최적화: 번들 도구를 사용한 압축화 및 난독화, Code Spliting, Lazy Loading(동적 import), Tree Shaking
  <br/>
- CSS 최적화 : 번들 도구를 사용한 압축화 및 불필요한 코드 삭제
  <br/>
- 이미지 최적화 : 이미지 포맷, 반응형 이미지, 이미지 압축
  <br/>
- 폰트 최적화: 필요한 폰트만 로드,WOFF2,Font Display ,서브셋 사용

**2. 필요한 리소스 미리 요청하기**
`preconnect`, `preload`, `prefetch`, `prerender`등을 사용해 필요한 리소스를 미리 요청힐 수 있도록 한다.

| 속성               | 목적                                             | 사용 시점                        | 리소스 유형                       | 특징                                                                                                    |
| ------------------ | ------------------------------------------------ | -------------------------------- | --------------------------------- | ------------------------------------------------------------------------------------------------------- |
| **`preconnect`**   | 외부 리소스 서버와의 네트워크 연결을 미리 설정   | 리소스를 가져오기 전에           | 모든 리소스 (이미지, 스크립트 등) | DNS 조회, TCP 핸드셰이크, TLS 협상까지 미리 수행해 첫 요청 시간을 단축.                                 |
| **`preload`**      | 중요한 리소스를 우선적으로 미리 불러오기         | 페이지 로딩 중                   | JS, CSS, 글꼴, 이미지, 비디오 등  | 중요한 리소스의 우선순위를 설정하고 빠르게 가져오도록 브라우저에 지시.                                  |
| **`prefetch`**     | 미래에 사용할 리소스를 미리 불러오기             | 현재 페이지에서 나중에 필요할 때 | 모든 리소스                       | 나중에 사용할 가능성이 높은 리소스를 브라우저가 여유 있는 시간에 미리 다운로드하여 캐시에 저장.         |
| **`dns-prefetch`** | 외부 도메인에 대한 DNS 조회를 미리 수행          | 외부 리소스를 불러오기 전에      | 모든 리소스                       | DNS 조회만 미리 처리하여 첫 연결 시간을 단축. `preconnect`에 비해 범위가 제한됨.                        |
| **`prerender`**    | 미래에 방문할 가능성이 높은 페이지를 미리 렌더링 | 페이지 이동 전에                 | HTML 페이지                       | 해당 페이지 전체를 미리 로드하고 렌더링해두어, 페이지 전환을 빠르게 만듦. 많은 리소스가 소모될 수 있음. |

**3. 가까운 곳에 필요한 리소스를 가져오기**
CDN을 이용하면 리소스를 보다 가까운 곳에서 가져올 수 있다.
CDN은 콘텐츠를 사용자의 가까운 서버에서 제공하며 서버 분산을 통한 병목 현상 최소화등으로 지연 시간을 줄인다.

CDN 캐시와 API 요청에 대한 브라우저 캐시를 사용하면 origin 서버로 부터 데이터를 받지 않고 캐시된 데이터를 즉시 사용할 수 있다.

**3. 비동기 데이터 처리**
동기 방식으로 데이터를 처리하면, 데이터를 받아오는 동안 브라우저의 메인 스레드가 차단돼 페이지 렌더링이 지연된다.

이를 방지하기 위해 비동기 방식으로 데이터를 요청해야한다. 비동기 데이터 처리를 사용하면, 데이터 요청과 동시에 렌더링이 수행된다.

여기에 Suspense를 적용할 수 있다. 데이터 요청 중에는 Suspense가 실행되다가 데이터 요청이 만료되면 해당 부분만 업데이트만 되어, FCP나 FMP가 빨라진다.

- 비동기 처리 및 Suspense

```js
// App.jsx
function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <Suspense fallback={<LoadingSpinner />}>
        <DataComponentWrapper />
      </Suspense>
    </QueryClientProvider>
  );
}

// DataComponentWrapper.jsx
function DataComponentWrapper() {
  const { data } = useQuery("fetchData", fetchData);
  return <DataComponent data={data} />;
}
```

**4.Lazy Loading (지연 로딩)**
Lazy Loading은 모든 리소스를 한 번에 로드하지 않고 시용자가 필요할 때 로드하는 방식이다. Lazy Loading을 사용하면 해당 화면에서 필요한 리소스만 부르기 때문에 초기 로딩 시간이 단축된다.

이미지 지연 로딩, React.lazy, 옵저버를 사용한 방법등을 통해 Lazy Loading를 구현할 수 있다.

- 이미지 지연 로딩

```js
<img src="image.jpeg" loading="lazy" alt="Lazy Loaded Image">

```

- React.lazy로 특정 컴포넌트가 필요할 때 로드

```js
const LazyComponent = React.lazy(() => import("./MyComponent"));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </Suspense>
  );
}
```

- 옵저버를 사용해 뷰포트에 옵저버 관찰 대상이 들어 올 때 이미지 로드

```js
const imgObserver = new IntersectionObserver((entries, observer) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      const img = entry.target;
      img.src = img.dataset.src; // 실제 이미지 소스를 로드
      observer.unobserve(img); // 로드 후 관찰 중단
    }
  });
});

document.querySelectorAll("img[data-src]").forEach(img => {
  imgObserver.observe(img);
});
```

## 렌더링 성능

### 원인

### 방법 1: GPU 애니메이션 사용

렌더링 성능을 저하시키는 주원인은 CPU을 사용하는 레이아웃,페인팅 작업이다. 그래서 렌더링 성능을 개선하기 위해서는 CPU를 사용하는 리플로우와 리페인트보다 **GPU를 사용하는 리컴포지팅을 활용해 스타일을 변경해야한다.**

- CPU 애니메이션 사용 시 fram drop 일어난 모습

<p align="center">
  <img src="./images/technicalWriting/" alt="cpu 애니메이션 frame drop" loding="lazy" />
</p>

- GPU 애니메이션을 사용해 frame drop 해결한 모습
<p align="center">
  <img src="./images/technicalWriting/gpu_animation.jpeg" alt="gpu 애니메이션 frame drop" loding="lazy" />
</p>

#### 리플로우, 리페인트과 리컴포지팅을 유발하는 css 속성

| 과정                      | css 속성                                                                                                                       |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| 리플로우(Reflow)          | 크기(width, height), 위치(top, left), 마진(margin), 패딩(padding), 디스플레이(display), 플로트(float), 폰트 크기(font-size) 등 |
| 리페인트(Repaint)         | 배경색(background-color), 글꼴 색상(color), 테두리 색상(border-color), 그림자(box-shadow) 등                                   |
| 리컴포지팅(Recompositing) | 변환(transform), 투명도(opacity), 애니메이션(animation), 고정 위치 요소(position: fixed)                                       |

#### CPU보다 GPU를 사용한 작업의 성능이 더 좋은 이유

**1. GPU의 병렬 처리 능력**

GPU는 수천 개의 코어를 갖춘 병렬 처리에 특화되었다. GPU는 한 프레임의 각 픽셀을 동시에 계산할 수 있기 때문에 애니메이션이나 복잡한 화면 전환에서 성능이 훨씬 뛰어나다.

반면 CPU는 소수의 강력한 코어로 설계되어 직렬 처리에 특화되었다.

**2. GPU의 전용 하드웨어 최적화**

CPU가 범용 처리 장치인 반면에 GPU는 그래픽 렌더링과 관련된 작업을 처리하도록 설계된 전용 하드웨어다. 3D 모델링, 이미지 렌더링, 텍스처 매핑과 같은 작업에서 뛰어난 성능을 발휘한다.

**3. 리소스 분배 및 병목 현상 방지**

GPU를 사용하면 CPU와 GPU 간의 작업 분할이 이루어지기 때문에, CPU가 다른 작업(ex: 자바스크립트 실행, 이벤트 처리)에 집중할 수 있다. 이는 병목 현상을 방지하고 전체적인 시스템 성능을 향상시킨다.

가령 CPU가 레이아웃 계산을 하는 동안 GPU는 컴포지팅 작업을 처리해 더 빠른 렌더링이 가능하다.

**4. 애니메이션과 인터랙션에서의 부드러움**

GPU 가속을 사용하면 60fps(초당 프레임 수)와 같은 고주사율 애니메이션을 쉽게 처리할 수 있다. GPU는 각 프레임을 빠르게 계산하여 사용자에게 부드러운 애니메이션을 제공한다.

반면에 CPU기반 애니메이션은 계산이 시간이 더 소요되어 frame drop이나 jank(끊김 현상)이 발생할 가능성이 크다.

### 방법2: window.requestAnimationFrame

`window.requestAnimationFrame`을 애니메이션 최적화를 할 수 있다.

브라우저는 초당 60번 화면을 업데이트한다. `window.requestAnimationFrame`는 브라우저의 화면 업데이트 주기에 맞춰 콜백 함수를 실행해 애니메이션이 부드럽게 보이도록 한다.

- 버튼을 클릭해 box위치를 오른쪽으로 50px 이동하는 리액트 코드

```jsx
import React, { useState, useRef } from "react";

const MovingBox = () => {
  const [isAnimating, setIsAnimating] = useState(false);
  const positionXRef = useRef(0); // 현재 X 좌표
  const boxRef = useRef(null);

  const targetX = 50; // 이동할 거리 50px

  const animate = () => {
    if (positionXRef.current < targetX) {
      positionXRef.current += 1; // 1px씩 이동
      boxRef.current.style.transform = `translate3d(${positionXRef.current}px, 0, 0)`;
      requestAnimationFrame(animate); // 다음 프레임 요청
    } else {
      setIsAnimating(false); // 애니메이션 종료
    }
  };

  const handleClick = () => {
    if (!isAnimating) {
      setIsAnimating(true); // 애니메이션 시작
      positionXRef.current = 0; // 초기화
      requestAnimationFrame(animate); // 애니메이션 실행
    }
  };

  return (
    <div>
      <div
        ref={boxRef}
        style={{
          width: "50px",
          height: "50px",
          backgroundColor: "red",
          position: "absolute",
          top: "100px",
          transform: "translate3d(0, 0, 0)", // 초기 위치
        }}
      ></div>
      <button onClick={handleClick} style={{ marginTop: "200px" }}>
        Move Box
      </button>
    </div>
  );
};

export default MovingBox;
```

  </div>
</details>

### 방법2: 불필요한 렌더링 막는 메모이제이션

sns에서 새로운 피드를 보기 위해, 새로 고침을 했다고 가정해보자. 새로운 피드가 화면에 보일 것이고 이전에 있던 피드들도 여전히 화면에 있다. 렌더링 측면에서 이전 피드와 새로운 피드가 모두 재렌더링되는 것이 아닌, 새로운 피드만 새로 렌더링 되어는 것이 효율적이다.

이를 위해서 메모이제이션을 사용할 수 있다.
메모이제이션은 이전에 계산한 결과를 캐시해두고, 동일한 입력값이 호출되면 캐시된 값을 반환하는 방법이다.

- React.memo (메모이제이션)를 사용해 재렌더링 막은 화면
  <p align="center">
  <img src="./images/technicalWriting/memo.jpeg" alt="React.memo를 사용해 재렌더링 막은 화면" loading="lazy"  width="500"/>
</p>

#### React에서의 메모이제이션

리액트는 컴포넌트 기반 구조와 가상DOM을 활용한 렌더링 파이프라인을 통해서 이전 연산 결과를 기억(=캐싱)하는 메모이제이션 기법을 제공한다.

- 메모이제이션 방법

| 방법        | 설명                         |
| ----------- | ---------------------------- |
| React.memo  | 컴포넌트 자체를 메모이제이션 |
| useMemo     | 값의 메모이제이션            |
| useCallback | 함수의 메모이제이션          |

리액트 렌더딩 파이프라인은 렌더,조정,커밋의 단계로 진행된다.

**리액트 렌더링 파이프라인**

<p align="center">
  <img src="./images/technicalWriting/react_pipeline.jpeg" alt="리액트 렌더링 파이프라인 단계" loading="lazy"  width="500"/>
</p>

1. 렌더 단계: 상태,props 변경되면 새로운 가상 DOM을 생성하고 이를 기존 가상 DOM과 비교
2. 조정 단계: 가상 DOM 비교로 실제로 비교된 부분을 찾아 실제 DOM에 적용할지 결정
3. 커밋 단계: 변경 사항을 실제 DOM에 반영

상태,props가 변경되지 않으면 가상 DOM에서 캐싱된 값을 사용한다. 변경이 있다면 파이프라인을 통해 변경으로 인한 사항을 화면에 반영한다.

## 인터랙션 성능

너무 많은 JavaScript가 메인 스레드를 차지하면 사용자 인터랙션이 지연될 수 있다. 비동기 처리를 통해 **메인 스레드 블로킹** 문제를 해결하고, `debounce`나 `throttle`을 사용해 이벤트 핸들러를 최적화할 수 있다.

- 디바운스 적용 전 Layout shift, Frame drop
  <p align="center">
  <img src="./images/technicalWriting/no_debounce.jpeg" alt="디바운스 적용 전 Layout shift, Frame drop 발생" loading="lazy" />
</p>

- 디바운스 적용 후 Layout shift, Frame drop
  <p align="center">
  <img src="./images/technicalWriting/debounce.jpeg" alt="디바운스 적용 후 Layout shift, Frame drop 개선" loading="lazy" />
</p>

## 메모리 관리

메모리 누수와 불필요한 객체 생성을 방지하기 위해, 이벤트 리스너나 타이머를 적절히 관리하고, 객체를 재사용하여 메모리를 효율적으로 사용할 수 있다.

## <span id="optimization"> 5. Webpack에서 성능 최적화 하기</span>

### JS 최적화

#### Minification(압축화)

Webpack 5는 기본적으로 TerserPlugin을 사용하여 JavaScript 파일을 압축합니다. 추가적인 설정이 필요 없다면 mode: 'production'으로 설정하면 자동으로 압축이 적된다.

```js
// webpack.config.js
module.exports = {
  mode: "production", // 자동으로 TerserPlugin이 활성화됨
};
```

#### 난독화

난독화는 코드의 가독성을 낮추어 악의적인 사용자가 코드를 분석하거나 도용하는 것을 방지하기 위한 기법입니다. 난독화 과정에서 변수 이름이 짧아지기 때문에 번들 크기를 줄이는데 기여합니다.

Webpack 5에서 기본적으로 제공하는 TerserPlugin을 사용하여 난독화를 진행 할 수 있다.

```js
// webpack.config.js
const TerserPlugin = require("terser-webpack-plugin");

module.exports = {
  mode: "production", // 기본 압축 및 최적화 활성화
  optimization: {
    minimize: true, // production 모드에서 minimize의 기본값은 true
    minimizer: [
      new TerserPlugin({
        terserOptions: {
          mangle: true, // 변수 및 함수 이름 변경 (난독화)
          compress: {
            drop_console: true, // 콘솔 로그 제거
          },
          output: {
            comments: false, // 주석 제거
          },
        },
      }),
    ],
  },
};
```

#### Tree shaking (트리 쉐이킹)

Tree shaking은 dead code를 제거하는 기능이다. 이를 위해서는 ES6 모듈을 사용하고 코드에서 불필요한 코드를 없애는 것이 중요하다. 기본적으로 Webpack 5는 mode: 'production'에서 Tree shaking을 활성화된다.

#### Code splitting (코드 스플리팅)

Code splitting은 큰 애플리케이션을 작은 청크로 나누어 필요한 부분만 로딩하는 것을 말한다. 동적 import(dynamic import)를 이용하거나 Webpack의 splitChunks 옵션을 사용하면 Code splitting을 구현할 수 있다.

**동적 import(dynamic import)**
동적 import를 적용하면 해당 페이지에 필요한 컴포넌트만 불러온다.

- 리소스 비교
  동적 import를 적용하기 전에넌 모든 페이지가 합쳐진 bundle.js를 부른다면, 적용하면 페이지에 필요한 js파일만 부른다.

<p align="center">
  <img src="./images/technicalWriting/code_splitting.jpeg" loading="lazy" alt="code splitting이 적용 전과 적용 후 리소스 파일 비교" width="\700" />
</p>

- 코드

```js
const Home = lazy(() => import("./pages/Home/Home"));
const Search = lazy(() => import("./pages/Search/Search"));

import NavBar from "./components/NavBar/NavBar";
import Footer from "./components/Footer/Footer";

import "./App.css";
import { lazy, Suspense } from "react";
import LoadingBar from "./components/LoadingBar/LoadingBar";

const App = () => {
  return (
    <Router basename={"/"}>
      <NavBar />
      <Suspense fallback={<LoadingBar />}>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/search" element={<Search />} />
        </Routes>
        <Footer />
      </Suspense>
    </Router>
  );
};
```

**spliceChunks 옵션 사용**

```js
//Webpack.config.js
module.exports = {
  //....
  optimization: {
    splitChunks: {
      chunks: "all",
    },
  },
};
```

#### 모듈 압축(Gzip, Brotli)

압축 방식으로는 Gzip, 구글에서 개발한 Gzip보다 압축륙이 높은 Brotli가 있다.
모든 주요 브라우저(Chrome, Firefox, Edge, Safari등)는 Gzip과 Brotli 압축을 지원하며, 서버에서 압축된 파일을 전송하면 이를 자동으로 해제한다.

**CloudFront 자동 압축 활용하기**
CloudFront 배포 설정에서 `Compress objects automatically` 옵션을 키면 압축이 활성화된다.
압축 방식은 브라우저의 `Accept-Encoding`헤더에 따라 결정되며, Brotil가 Gzip보다 우선적으로 적용된다.

- Brotil 적용되는 헤더

```http
Accept-Encoding: br, gzip, deflate

```

- Gzip 적용되는 헤더

```http
Accept-Encoding: gzip, deflate

```

- CloudFront에서 Brotil로 압축해 보내 응답
<p align="center">
  <img src="./images/technicalWriting/refresh_cdn_cache.jpeg" alt="CloudFront에서 Brotil로 압축해 보내 응답" loading="lazy"/>
</p>

**Webpack을 사용한 Gzip 압축**

```js
//Webpack.config.js

const CompressionPlugin = require("compression-webpack-plugin");

module.exports = {
  plugins: [
    new CompressionPlugin({
      algorithm: "gzip",
      test: /\.(js|css|html|svg)$/, // 압축할 파일들
      threshold: 8192, // 최소 파일 크기 (8KB 이상일 때 압축)
      minRatio: 0.8, // 압축 후 원본 파일과 최소 비율
    }),
  ],
};
```

**Webpack을 사용한 Brotil 압축**

```js
//Webpack.config.js
const BrotliPlugin = require("brotli-webpack-plugin");

module.exports = {
  plugins: [
    new BrotliPlugin({
      asset: "[path].br[query]", // .br 확장자 설정
      test: /\.(js|jsx|ts|tsx|css|html|svg)$/, // 압축할 파일 유형
      threshold: 8196, // 8KB 이상의 파일만 압축
      minRatio: 0.8, // 압축 후 80% 이하로 줄어든 파일만 압축
      quality: 11, // 최대 압축률 (0~11 사이, 기본값: 11)
      deleteOriginalAssets: false, // 원본 파일을 삭제하지 않음
    }),
  ],
};
```

- Brotli 압축 결과
  아래 사진은 우테코 6기 팀프로젝트인 '리뷰미' 프로젝에서 BrotliPlugin으로 압축한 결과이다.

<p align="center">
  <img src="./images/technicalWriting/br.jpeg" alt="리뷰미 프로젝트에서 Brotli로 압축한 결과" />
</p>

CloudFront에서 실시간으로 모듈을 압축하는 것은 S3에 압축된 파일을 올리는 것보다 속도가 느리다. 그러나 브라우저의 `Accept-Encoding`헤더에 따라 적절한 방식의 응답을 제공할 수 있어 동적 콘텐츠나 자주 변경되는 캐시를 사용하는 파일에 유리하다.

따라서 정적 파일이라면 Webpack에서 미리 압축을 하고, 동적 콘텐츠라면 CloudFront의 실시간 압축을 사용하는 게 좋다. 단 **Webpack에서 압축을 한다면 서비스 지원 브라우저에서 사용하려는 압축 방식을 지원하는 지 살펴봐야한다.** 지원하는 브라우저에서 Gzip만을 지원하는데, S3에는 Brotli 압축 파일만 있다면 CloudFront는 응답을 보내지 않는다.

### CSS 최적화

CSS-in-JS는 JS최적화에서 진행되기 때문에 여기서는 `.css`확장자를 사용하는 CSS 파일 기반 스타일링에 대한 최적화 방법에 대해 살펴보자.

#### bundle.js에서 CSS 파일 별도 추출

Webpack에서 style-loader를 사용하면 CSS는 JS가 번들링된 bundle.js에 인라인으로 포함된다.

**CSS 파일을 별도로 추출해야하는 이유?**

브라우저 렌더링 과정을 떠올리면, JS파일과 CSS 파일의 로딩 방식은 다르며, 각각 렌더링 과정에 끼치는 영향도 다르다. CSS와 JS가 함께 bundle.js에 묶여 있으면 bundle.js를 모두 다운로드하고 파싱하는 과정이 끝나기 전까지 렌더링이 지연될 수 있다. 반면에 CSS 파일을 별도로 추출하면, 브라우저는 CSS와 JS를 병렬적으로 다운로드해 초기 페이지 로딩 성능이 개선된다. 또한 CSS가 별도의 파일로 추출되면 CSS 파일을 빠르게 로드할 수 있기 때문에 렌더링 차단을 줄일 수 있다.

CSS 파일을 bundle.js에 포함하면, JS파일이 조금만 변경되어도 전체 bundle.js가 다시 다운로드된다. 반면 CSS 파일을 따로 추출하면 CSS나 JS 중 하나가 변경되어도 각각의 파일만 새로 캐싱하여 다운로드할 수 있다. 이는 캐싱 효율성을 높여 성능 개선에도 도움이 된다.

| 비교 항목                        | CSS가 JS와 함께 있을 때 (bundle.js)                       | CSS가 별도로 있을 때                                  |
| -------------------------------- | --------------------------------------------------------- | ----------------------------------------------------- |
| **로딩 방식**                    | JS와 함께 다운로드되며, JS 파싱이 끝날 때까지 렌더링 지연 | CSS와 JS가 병렬로 다운로드되어 빠른 렌더링 가능       |
| **렌더링 차단**                  | JS 파싱이 끝날 때까지 CSS 적용이 지연됨                   | CSS가 빠르게 로드되어 렌더링 차단을 줄일 수 있음      |
| **병렬 다운로드**                | 병렬 다운로드 불가능, JS 파싱 후 CSS 적용                 | CSS와 JS가 병렬로 다운로드되어 초기 로딩 성능 개선    |
| **캐싱 효율성**                  | JS가 변경되면 CSS도 함께 다시 다운로드                    | CSS나 JS 중 하나만 변경되면 해당 파일만 다시 다운로드 |
| **코드 스플리팅**                | 어려움                                                    | 페이지별로 필요한 CSS만 로드 가능                     |
| **성능 측정 지표 (LCP, TTI 등)** | LCP 및 TTI 저하 가능성 있음                               | LCP 및 TTI 개선 가능                                  |
| **렌더링 속도**                  | 느림                                                      | 빠름                                                  |

** 별도 추출 방법**
`MiniCssExtractPlugin`을 사용하여 CSS를 별도의 파일로 추출할 수 있다.

```js
// Webpack.config.js
const MiniCssExtractPlugin = require("mini-css-extract-plugin");

module.exports = {
  module: {
    rules: [
      {
        test: /\.css$/,
        use: [MiniCssExtractPlugin.loader, "css-loader"],
      },
    ],
  },
  plugins: [
    new MiniCssExtractPlugin({
      filename: "[name].[contenthash].css", // 캐싱을 위해 contenthash 사용
    }),
  ],
};
```

#### CSS 파일 압축 및 중복 CSS 제거하기

`css-minimizer-webpack-plugin`을 사용하여 CSS 파일을 압축할 수 있다.
`purgecss-webpack-plugin`을 사용하여 사용하지 않는 CSS를 제거할 수 있다.

CSS 파일을 압축하거나 중복 CSS를 제거하면 CSS 파일 크기가 줄어서 로딩 속도가 빨라딘다.

```js
// Webpack.config.js
const CssMinimizerPlugin = require("css-minimizer-webpack-plugin");
const PurgeCSSPlugin = require("purgecss-webpack-plugin");
const glob = require("glob-all");
const path = require("path");

module.exports = {
  //....
  plugins: [
    new PurgeCSSPlugin({
      paths: glob.sync([
        path.join(__dirname, "src/**/*.js"),
        path.join(__dirname, "public/index.html"),
      ]),
    }),
  ],
  //....
  optimization: {
    minimize: true,
    minimizer: [
      `...`, // 기본적으로 제공되는 minimizer 설정을 확장
      new CssMinimizerPlugin(),
    ],
  },
};
```

### 이미지 최적화

#### 이미지 포맷 및 압축

**변경할 이미지 포맷 선정하기**
이미지 포맷 중 파일 크기가 작은 포맷들은 WebP, AVIF, 그리고 JPEG이다.

| 이미지 포맷 | 파일 크기 | 장점                                                                            | 단점                                                            | 지원 수준                                               |
| ----------- | --------- | ------------------------------------------------------------------------------- | --------------------------------------------------------------- | ------------------------------------------------------- |
| **AVIF**    | 가장 작음 | - 매우 높은 압축률로 파일 크기 작음 <br> - 고품질 이미지 유지 <br> - HDR 지원   | - 인코딩 속도가 느림 <br> - 지원 브라우저 및 도구가 아직 제한적 | 최신 브라우저 일부 (Chrome, Firefox 등)                 |
| **WebP**    | 작음      | - JPEG보다 25~34% 더 작은 파일 크기 <br> - 투명도 및 애니메이션 지원            | - 일부 오래된 브라우저에서 지원 부족                            | 최신 브라우저 대부분 (Chrome, Firefox, Edge, Safari 등) |
| **JPEG**    | 중간      | - 널리 사용됨 <br> - 모든 브라우저에서 지원 <br> - 손실 압축으로 크기 조정 가능 | - 무손실 압축 미지원 <br> - WebP 및 AVIF보다 파일 크기 큼       | 모든 브라우저 및 기기에서 지원                          |
| **PNG**     | 큼        | - 무손실 압축 <br> - 투명도 지원                                                | - 파일 크기가 큼 <br> - 손실 압축 미지원                        | 모든 브라우저 및 기기에서 지원                          |
| **GIF**     | 중간~큼   | - 애니메이션 지원 <br> - 간단한 이미지에 적합                                   | - 색상 제한(256색) <br> - 큰 파일 크기                          | 모든 브라우저 및 기기에서 지원                          |

이미지 파일 크기는 `AVIF < WebP < JPEG < PNG`순으로 크다. AVIF는 이미지 파일 크기가 가장 작지만,아직 지원하는 브라우저와 툴이 제한적이다. 그래서 무손실 압축이며 gif도 지원하고 대부분의 최신 브라우저가 지원하는 Webp가 좋은 대안이다.
단, Webp를 지원하지 않은 브라우저가 있기 때문에 `picture`태그나 `img`태그와 srcSect 조합과 함께 모든 브라우저에서 사용하는 JPEG를 같이 사용하는 것을 권한다.

<p align="center">
  <img src="./images/technicalWriting/image_format.jpeg" alt="이미지 형식 비교" />
</p>

**이미지 포맷 및 압축하기**
[`ImageMinimizerPlugin`](https://webpack.js.org/plugins/image-minimizer-webpack-plugin/)을 사용하면 이미지 파일을 크기가 작은 포맷으로 바꾸고 이미지 파일을 압축할 수 있다.

압축률은 `quality`옵션을 통해 결정된다. 압축률이 커질 수록 이미지 파일 크기는 줄지만 그 만큼 이미지의 해상도는 낮아지기 때문에, 무작정 높은 압축률은 피해야한다. 이미지 파일의 쓰임에 따라 그에 맞는 압축률을 선정해야한다.

- 디테일이 중요한 이미지 : 80~85
- 단순한 색상과 선으로 구성된 이미지 : 75~80
- 일반적으로 많이 사용되는 압축률 : 75-85

```js
//Webpack.config.js
module.exports = {
  //...
  optimization: {
    minimize: true,
    minimizer: [
      //...
      new ImageMinimizerPlugin({
        generator: [
          {
            //'?as=webp'를 넣어서, 해당 파일을 webp로 변경
            preset: "webp",
            implementation: ImageMinimizerPlugin.sharpGenerate,
            options: {
              encodeOptions: {
                webp: {
                  quality: 70,
                },
              },
            },
          },
          {
            //'?as=jpeg'를 넣어서, 해당 파일을 jpeg로 변경
            preset: "jpeg",
            implementation: ImageMinimizerPlugin.sharpGenerate,
            options: {
              encodeOptions: {
                jpeg: {
                  quality: 70,
                },
              },
            },
          },
        ],
        minimizer: {
          implementation: ImageMinimizerPlugin.sharpMinify,
          options: {
            encodeOptions: {
              webp: { quality: 70 },
              jpeg: { quality: 70 },
              gift: { quality: 70 },
            },
          },
        },
      }),
    ],
  },
};
```

- picture 태그 사용 예시

```jsx
//App.jsx
import webpImg from "./file.jpg?as=webp";
import jpegImg from "./file.jpg?as=jpeg";

//...
const App = () => {
  return (
    <div>
      <picture>
        {/* WebP 포맷이 지원되는 브라우저에서 이 이미지를 로드 */}
        <source srcSet={webpImg} type="image/webp" />
        {/* WebP 포맷이 지원되지 않으면 JPEG 이미지를 로드 */}
        <img src={jpegImg} alt="Sample" />
      </picture>
    </div>
  );
};
```

- image 태그와 srcSet조합 사용 예시

```jsx
import webpImg from "./file.jpg?as=webp"; // WebP 이미지
import jpegImg from "./file.jpg?as=jpeg"; // JPEG 이미지

const App = () => {
  return (
    <div>
      <img
        src={jpegImg} // 기본 이미지 폴백(JPEG)
        srcSet={`${webpImg} 1x, ${jpegImg} 2x`} // WebP를 우선 제공
        type="image/webp"
        alt="Sample"
      />
    </div>
  );
};

export default App;
```

#### 반응형 이미지

반응형 이미지는 사용자 화면 크기나 해상도에 맞춰 적절한 이미지를 제공하는 것을 말한다.
다양한 화면 크기와 해상도에 맞춰 최적화된 이미지를 제공하여 페이지 로딩 시간과 데이터 사용량을 줄일 수 있다.

`responsive-loader`를 사용하면 빌드 시 원하는 이미지 포맷,이미지 사이즈로 반응형 이미지 파일을 만들 수 있다.

**반응형 이미지 방법**

```jsx
//Webpack.config.js
module.exports = {
  module: {
    rules: [
      {
        test: /\.responsive.(jpg|jpe?g|png|webp)$/i,
        type: "javascript/auto",
        use: [
          {
            // webp로 변경하고, size에 맞는 반응형 이미지 파일 생성
            loader: "responsive-loader",
            options: {
              adapter: require("responsive-loader/sharp"),
              format: "webp",
              name: "[name]-[width]w.[ext]",
              sizes: [1440, 1020, 768, 425],
              placeholder: true,
              placeholderSize: 20,
              quality: 60,
              outputPath: "static",
            },
          },
        ],
      },
    ],
  },
};
```

```jsx
//App.jsx
import homeImage from "../../assets/images/home.responsive.png";

//homeImage.srcSect: "home-1440w.webp 1440w, home-1020w.webp 1020w,...,home-425w.webp 425w"

const App = () => {
  return (
    <picture>
      <source
        srcSet={homeImage.srcSet}
        type="image/webp"
        sizes="(max-width: 425px) 425px, (max-width: 768px) 768px,(max-width: 1024px) 1024px, (max-width: 1440px) 1440px, 100vw"
      />
      <img className={styles.heroImage} src={heroJpgImage} alt="Hero" />
    </picture>
  );
};
```

### Lazy Loading

`img`에 `loading="lazy"`를 설정하면, 화면에 보일 때 해당 이미지가 로드된다.
즉, 화면에 보이는 이미지들만 로드되고 화면에 아직 보일 필요가 없는 이미지는 로드되지 않아 렌더링 시간이 단축된다.

```html
<img src="image.jpg" alt="Lazy Loaded Image" loading="lazy" />
```
