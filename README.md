# 🚌 버스: 실시간 버스 혼잡도 및 경로 정보 서비스

~~

**버스**는 사용자가 실시간으로 버스 혼잡도를 미리 확인하고, 경로 정보를 탐색할 수 있는 웹 서비스입니다. 이 서비스를 통해 혼잡한 버스를 피하고, 더 쾌적한 대중교통 경험을 제공합니다.

## 🌟 주요 기능

- **실시간 버스 혼잡도 예측**: 현재, 이전, 그리고 이후 정류장의 혼잡도를 예측하고 표시
- **버스 경로 검색**: 버스 번호를 검색하여 경로와 혼잡도를 빠르게 확인
- **최근 검색 및 즐겨찾기 기능**: 자주 이용하는 버스를 저장하고 쉽게 조회
- **경기/서울 간 경로 탐색**: 서울 및 경기도 간의 다양한 버스 경로 제공
- **API 기반 데이터 처리**: 경기도 버스 노선 API를 활용한 실시간 정보 제공

## 🚀 프로젝트 구조

```bash
📁 frontend-osori/
├── 📁 src
│   ├── 📂 assets
│   ├── 📂 components
│   ├── 📂 router
│   ├── 📂 views
│   ├── App.vue
│   ├── main.js
│   └── utils/
│       └── API/
│           └── gyeonggiBusAPI.js    # 경기도 버스 API 관련 함수
├── 📂 public
│   └── index.html
└── package.json
```



## **🛠 기술 스택**
* ** Frontend**: Vue.js 3, Vue Router
* **State Management**: Vuex, Pinia
* **API**: 경기도 버스노선조회 API
* **CSS**: SCSS, P
* **Build Tool**: Webpack  

## **📋 설치 및 실행**
### **1. 프로젝트 클론**
```bash
git clone https://github.com/your-repo/bus-miri.git
cd bus-miri/frontend-osori
```
### **2. 패키지 설치**
```bash
npm install
```
### **3. 개발 서버 실행**
```bash
npm run serve
```
개발 서버가 실행되면 `http://localhost:8080`에서 프로젝트를 확인할 수 있습니다.  

## **📊 API 사용**
본 프로젝트는 경기도 버스 노선 조회 API를 사용합니다. API 호출 예시는 다음과 같습니다.

```javascript
import { getBusRouteList } from '@/utils/API/gyeonggiBusAPI.js'

const busRoutes = await getBusRouteList('5000')
console.log(busRoutes)
```  
## **🎨 스타일 가이드**
* **코딩 스타일**: ESLint, Prettier 적용
* **디자인**: 폰트를 사용하여 일관된 UX를 제공
* **컴포넌트 구조**: 컴포넌트는 최대한 분리하고, 재사용성을 고려한 설계  

## **📜 API 키 설정**
API를 사용하려면 발급받은 서비스 키를 `gyeonggiBusAPI.js`에 추가해야 합니다.  

```javascript
const serviceKeyEncoded = '발급받은_인코딩된_API_키';
```  
## **🐛 버그 및 기능 요청**
버그나 기능 요청 사항이 있다면 Issues 탭을 통해 알려주세요!  

## **📞 문의**
궁금한 점이 있으시면 아래로 연락해 주세요:
* 이메일: example@example.com
* 깃허브: study2895<br><br>

***
이 프로젝트를 통한 더 나은 대중교통 경험을 위해 기여해 주셔서 감사합니다! 😊
