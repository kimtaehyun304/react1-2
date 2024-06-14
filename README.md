# 김태현 202030411

## 6월 11일 강의
합성: 여러개의 컴포넌트를 합쳐서 새로운 컴포넌트를 만드는 것  
+합성 방법: Containment, Specialization, Containment+Specialization  

1) Containment (포함)
하위 컴포넌트르 포함하는 형태의 합성 방법이다.
2) Specialization(전문화)
범용적인 개념을 구별이 되게 구체화 하는것이다. ex) 상속과 비슷하다


## 6월 5일 강의
State 끌어올리기: 하나의 데이터를 여러개의 컴포넌트에서 표현해야할 때, 각 컴포넌트의 state에서 데이터를 보관하지않고,  
가장 가까운 공토 부모 컴포넌트에서 보관하여 공유한다. (공유 컴포넌트라고 부름)  
EX)온도를 섭씨 또는 화씨로 표현하거나. 2를 곱하거나 3를 곱하는 등의 사용하는 데이터는 같지만 결과를 얻기위한 연산만 다른 경우에 사용한다.  

## 5월 29일 강의
제어 컴포넌트: 리액트의 통제를 받는 input form element를 의미한다. ex) <input> <textarea> <select>
HTML 폼은 엘리먼트가 자체적으로 state를 관리하기 떄문에, JS 코드로 각각의 값에 접근하기 어렵다.  
그래서 리액트는 제어 컴포넌트의 모든 데이터를 한 곳의 state에서 관리한다.  

## 5월 22일 강의
여러개의 컴포넌트 렌더링 하는 방법: map() 함수 이용  
리스트와 키: 키는 리스트에서 아테임을 구분하기 위한 문자열이고, 키의 값은 고유해야한다. ex)인덱스 사용  
★키를 명시적으로 넣지 않으면, 기본적으로 인덱스를 키 값으로 사용한다.  

## 5월 8일 강의
조건부 렌더링은 리액트에서 조건에 따라(IF절) 다른 엘리트를를 보여주는 기술이다.  
엘리먼트 변수: 말 그대로, 리액트 엘리먼트를 변수처럼 다루는 방법이다.  
인라인 조건: if문을 사용하지 않고 조건문을 코드 안에 집어 넣는 방법 (삼항 연산자와 비슷)  
컴포넌트 렌더링 막기: null을 반환하거나 조건부로 return을 사용하여 렌더링을 막을 수 있다.  

## 5월 1일 강의
이벤트 핸들링은 HTML 이벤트와 비슷하다. 다른점은 리액트의 이벤트 이름은 캐멀 케이스로 작성 EX)onClick, onChange  
이벤트 핸들러는 메서드 형태로 정의되며, JSX에서는 해당 메서드 이름만을 이벤트 핸들러로 전달한다.  
참고: 이벤트 핸들러는 이벤트 리스너라고도 부른다.  

## 4월 17일 강의
훅: 함수 컴포넌트에서 state를 정의해서 사용하거나 컴포넌트의 생명주기에 맞춰 어떤 코드가 실행되도록 지원함. 훅은 use전치사를 사용한다. Ex) useState()  
클래스 컴포넌트 state VS 함수 컴포넌트 state  
ㄴ클래스 컴포넌트: setState() 함수 하나를 사용해서 모든 state값을 업데이트할 수 있다.  
ㄴ함수 컴포넌트: useState()를 사용하여 변수 각각에 대해 set함수가 존재한다.  

1) useState() 훅  
언제 쓰나? -> state를 사용할 때 쓴다.  
형태: const [변수명, set함수명] = useState(초깃값);   

2) useEffect() 훅  
언제 쓰나? -> 사이드 이펙트를 사용할 때 쓴다.  
사이드 이펙트: 리액트에서는 렌더링이 끝나고 실행되야하는 작업을 의미  
형태: useEffect(이펙트 함수, 의존성 배열)  
useEffect( ( ) =>  
    //컴포넌트가 마운트 된 이후와 업데이트마다 실행되는 부분  
    return() => {//컴포넌트가 언마운트 될 때 실행되는 부분}  
}, [의존성 배열])

구체적으로 언제 쓰나? -> 배열의 값이 변경되었을 때 함수를 실행하게 하고 싶을 때 쓴다.  
기타 사용법  
    a) 컴포넌트가 업데이트될 때(state가 바뀔 때)마다 함수를 실행하게 하고싶으면 배열을 생략한다.   
    
기타 내용  
    a)	이펙트 함수는 컴포넌트가 생성될 때도 실행된다  
    b)	빈 배열을 넣으면 이펙트함수는 마운트와 언마운트에만 실행된다.   
    
3) useMemo() 훅  
언제 쓰나? -> memoized value를 사용하고 싶을 때 쓴다.  
memoized value 란? 함수가 실행된 결과다. 연산 비용이 높은 함수의 대책으로, 입력 값이 같으면 함수를 실행하지 않고 저장된 결과를 반환하는 것이다.

useMemo( ) => {return compute(a, b)}, [의존성 배열]   

기타 내용  
    a)	함수는 렌더링이 일어나는 동안 실행된다.  
    b)	빈 배열을 넣으면 함수는 마운트 시에만 실행된다.  
    c)	배열은 반드시 넣자.  
eslinet-plugin-react-hooks 패키지: 설치하면 useMemo() 훅에 배열을 안 넣으면 경고를 표시한다.  

4) useCallBack() 훅
useMemo()훅과 같은 역할을 한다. 다른 점은 값이 아닌 함수를 반환한다.  
기타 사용법: ref와 태그가 연결된 후에 함수를 실행하고 싶을 때 쓴다.   

5) useRef() 훅  
변경 가능한 current 속성을 가진 하나의 상자이다. 태그와 매핑할 때 쓴다.  
Current 속성을 변경해도 재렌더링이 안 일어난다.  
useRef() 안 써도 태그에 ref 속성만 있으면 태그와 변수를 매핑할 수 있다.   

## 4월 11일 강의
국회의원 투표날이라서 휴강

## 4월 3일 강의
컴포넌트 종류: 함수 컴포넌트, 클래스 컴포넌트  
요즘은 주로 함수형 컴포넌트 사용한다. 함수 컴포넌트를 개선하는 과정에서 개발된 것이 훅이다.

함수형  
function welcome(props){
    return 태그
}  

함수형은 import react 안해도댐  


클래스형  
DOM.render(){
    
}  

컴포넌트 넣을때 index.js에 직접 넣지 말고 App.js에 넣기  

컴포넌트 종류: 함수 컴포넌트, 클래스 컴포넌트

컴포넌트 합성: 여러 개의 컴포넌트를 합쳐서 또 다른 컴포넌트를 만든다.
컴포넌트 추출: 복잡한 컴포넌트를 쪼개서 여러 개의 컴포넌트를 나눈다.

생명주기: 클래스 컴포넌트와 관련된 내용
State: 리액트 컴포넌트 상태이고 그냥 자바 스크립트 객체다.
State를 변경하고자 할 때에는 setState() 함수를 사용해야한다.
컴포넌트 생명주기: 컴포넌트가 계속 존재하는 것이 아니라, 시간의 흐름에 따라 생성되고
업데이트되다가 사라진다.
ㄴ마운트: 컴포넌트가 실행된 시점
ㄴ업데이트: 컴포넌트의 props가 변경되거나 setState()함수 호출에 의해 state가 변경될 때 일어남
ㄴ언마운트: 상위 컴포넌트에서 현재 컴포넌트를 더 이상 화면에 표시하지 안게 될 때 일어남

VS CODE 코드 정렬 단축키: 알트+쉬프트+F
리액트로 개발할 때에는 크롬 개발자 도구보다 React Developr Tools이 좋다

## 3월 27일 강의
JSX: 자바스크립트 확장 문법  

옳바른 워킹 디렉토리  
ㄴ프로젝트1  
ㄴ프로젝트2  
ㄴREADME.MD  

리액트는 리얼타임이기때문에, 디렉토리 열면 바로 NPM START  

리액트 엘리먼트: Virtual DOM
DOM 엘리먼트: 페이지의 모든 정보를 갖고 있어 무겁다.

엘리먼트: 태그의 속성도 포함  
마크다운 br: 뒤에 공백두개  

export default 함수에 안붙이고 밑에 다 해도댐 (class 형식을 쓴 옜날 방식) 

리액트 구조: 하나의 컴포넌트를 root로해서 하위 컴포넌트들이 존재하는 구조
리액트 장점: 변경된 내용을 빠르게 사용자에게 보여줄 수 있다.
리액트 특징: 컴포넌트 기반 구조다. 모든 페이지가 컴포넌트로 구성되어 있다.
ㄴ하나의 컴포넌트는 또 다른 여러 개의 컴포넌트의 조합으로 구성될 수 있다.
State: 컴포넌트 상태 

JSX: HTML을 자바스크립트로 바꾼다. 내부적으로 createElement() 함수를 사용한다.
JSX: 렌더링하기 전에 문자열로 변환하기 때문에, XSS를 방어한다. 

어디서든 컴포넌트(JSX) 내 함수를 태그처럼 쓸 수 있다.
ㄴ컴포넌트 엘리먼트는 첫 글자가 대문자다. Ex)<Button></Button>

## 3월 20일 강의
모바일이 유행하면서 클릭 방식은 저물고, 스크롤 방식이 히트했다.
리액트는 바뀐 부분만 건드는 Virtual DOM이라 렌더링 속도가 빠르다 (비동기식 기술 사용)
npm은 Node.js를 설치하면 자동으로 함께 설치된다.

[npm err exit handler never called 에러 해결]  
npm install -g npm@latest  
npx create-react-app my-app  

안되면 create 명령어 여러번  

## 3월 13일 강의
교수님 짱짱맨
