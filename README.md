### 구현할 기능 목록


> - [x] 첨부된 oas.yaml 파일을 토대로 Request, Response Type을 정의해요.
> - [x] React Query를 사용하지 말고 axios 를 사용해서 구현해요.
> - [x] 첨부된 oas.yaml 파일과 목 API URL을 사용하여 API를 구현해요.
> - [x] /api/v1/themes API를 사용하여 Section을 구현해요.
> - [x] /api/v1/ranking/products API를 사용하여 Section을 구현해요. (Axios 사용 가능)
> - [x] 필터 조건을 선택 하면 해당 조건에 맞게 API를 요청하여 보여지게 해요.
> - [x] url의 pathParams와 /api/v1/themes API를 사용하여 Section을 구현해요.
> - [x] /api/v1/themes/{themeKey}/products API를 사용하여 상품 목록을 구현해요.
> - [x] API 요청 시 한번에 20개의 상품 목록이 내려오도록 해요.
> - [x] 각 API에서 Loading 상태에 대한 UI 대응을 해요.
> - [x] 데이터가 없는 경우에 대한 UI 대응을 해요.
> - [x] Http Status에 따라 Error를 다르게 처리해요.




3주차 질문
- 질문 1. CORS 에러는 무엇이고 언제 발생하는지 설명해주세요. 이를 해결할 수 있는 방법에 대해서도 설명해주세요.
  ### CORS 에러란?
  CORS(Cross-Origin Resource Sharing) 에러는 웹 애플리케이션이 다른 도메인(출처)의 자원에 접근하려고 할 때 발생하는 문제입니다. 웹 브라우저는 보안상의 이유로, 자바스크립트가 다른 출처의 리소스에 접근하는 것을 기본적으로 차단합니다.
  예를 들어, http://example.com에서 실행되는 코드가 http://api.example.com의 데이터를 요청하려고 하면, 다른 출처이기 때문에 CORS 에러가 발생할 수 있습니다.

  ### CORS 에러가 발생하는 상황
  클라이언트가 서버로 데이터를 요청할 때, 서버와 클라이언트의 도메인, 포트 또는 프로토콜이 다를 때 발생합니다.
  예를 들어, 프론트엔드 애플리케이션이 http://localhost:3000에서 실행 중이고, 백엔드 서버가 http://localhost:5000에서 실행 중일 때, 서로 다른 출처로 간주됩니다.

  ### 프론트엔드에서 해결할 수 있는 방법
  ### 프록시 설정:
  개발 환경에서 프록시 서버를 사용하여 CORS 문제를 해결할 수 있습니다.
  예를 들어, package.json 파일에 프록시 설정을 추가할 수 있습니다.
  ```typscript
  "proxy": "http://localhost:5000"
  ```


- 질문 2. 비동기 처리 방법인 callback, promise, async await에 대해 각각 장단점과 함께 설명해주세요.
  ## 1. Callback
### 설명
콜백 함수는 어떤 작업이 완료된 후 실행될 함수를 의미합니다.

### 장점
단순함: 간단한 비동기 작업에는 매우 직관적이고 사용하기 쉽습니다.
다양한 사용 사례: 이벤트 핸들링, 타이머 등 다양한 상황에서 사용 가능합니다.

### 단점
콜백 지옥: 콜백 함수가 중첩되면 코드가 복잡해지고 가독성이 떨어지는 "콜백 지옥" 현상이 발생할 수 있습니다.

## 2. Promise
### 설명
Promise는 비동기 작업의 완료 또는 실패를 나타내는 객체입니다. 성공 시 then 메서드가, 실패 시 catch 메서드가 호출됩니다.

### 장점
가독성: 콜백 지옥을 방지하고 코드의 가독성을 높여줍니다.
체이닝: then과 catch를 체이닝하여 연속적인 비동기 작업을 관리할 수 있습니다.
에러 처리: 비동기 작업의 에러 처리가 더 명확합니다.

### 단점
코드가 길어질 수 있음: 복잡한 비동기 작업에서는 여전히 코드가 길어질 수 있습니다.
러닝 커브가 있음: 초보자에겐 이해하기 어려운 개념일 수 있습니다.

## 3. Async/Await
### 설명
async/await는 Promise를 더욱 간결하게 사용할 수 있게 해주는 문법입니다. async 함수 내에서 await 키워드를 사용하면, 해당 Promise가 해결될 때까지 기다립니다.

### 장점
가독성: 동기식 코드처럼 작성할 수 있어 가독성이 매우 좋습니다.
에러 처리: try/catch 블록을 사용하여 에러 처리가 직관적입니다.

### 단점
구버전 호환성: 구버전 브라우저에서는 지원하지 않습니다.
Promise에 의존: 내부적으로 여전히 Promise를 사용하므로, 자세한 동작을 이해하기 위해서는 기본적인 Promise 개념을 이해해야 합니다.



- 질문 3. react query의 주요 특징에 대해 설명하고, queryKey는 어떤 역할을 하는지 설명해주세요.

### React Query의 주요 특징
  **자동화된 데이터 페칭 및 캐싱:**
  React Query는 서버에서 데이터를 가져오는 작업을 자동화하고, 가져온 데이터를 캐싱하여 효율적으로 관리합니다. 이렇게 하여 동일한 데이터를 여러 번 요청하지 않아도 됩니다.
  
  **배경에서 데이터 동기화:**
  백그라운드에서 데이터를 자동으로 갱신하여 최신 상태를 유지합니다. 사용자는 항상 최신 데이터를 볼 수 있게 됩니다.
  
  **간편한 에러 핸들링:**
  비동기 작업에서 발생하는 에러를 쉽게 관리할 수 있도록 도와줍니다. 각 요청에 대해 성공, 실패, 로딩 상태를 손쉽게 처리할 수 있습니다.
  
  **재요청 및 무효화:**
  데이터가 변경되거나 특정 조건이 충족될 때 자동으로 데이터를 재요청할 수 있습니다. 이를 통해 데이터의 일관성을 유지합니다.
  
  **캐싱 전략 설정:**
  데이터의 유효 기간, 재요청 주기 등을 설정하여 다양한 캐싱 전략을 구현할 수 있습니다. 필요에 따라 데이터를 신선하게 유지하거나, 일정 시간 동안 캐시된 데이터를 사용하도록 조정할 수 있습니다.


### queryKey의 역할
queryKey는 React Query에서 각 쿼리를 식별하는 고유한 키입니다. 동일한 키를 가진 쿼리는 동일한 동작 및 데이터를 공유하게 됩니다.
  
  
