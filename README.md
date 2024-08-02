### ESLint 설정값

기본적으로는 airbnb 를 따르며 이외는 커스텀 하여 사용.

<table>
    <thead>
    <tr>
    <th>속성명</th>
    <th>속성 설명</th>
    <th>변경 사유</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <td>"extends": ["airbnb", "airbnb/hooks", "next", "prettier"]</td>
    <td>프론트에서 가장 많이 사용하는 airbnb와 airbnb/hooks, prettier 적용</td>
    <td>코드 스타일을 린트를 통해 어느정도 맞추고, ESLint와 prettier 간 충돌을 방지하기 위해 prettier 확장함.</td>
    </tr>
    <tr>
    <td>"import/no-unresolved": [2, { "ignore": ["^@"] }]</td>
    <td>import 또는 require시 해당 모듈 파일을 파일 시스템에서 못 찾을 때 에러를 띄워줌</td>
    <td>절대 경로를 추적하지 못해 절대 경로에 대해서만 비활성화 처리</td>
    </tr>
    <tr>
    <td>"radix": ["error", "as-needed"]</td>
    <td>parseInt의 두 번째 인자인 진수를 명시해 혼란을 방지하는 목적의 옵션</td>
    <td>parseInt는 첫 번째 인자에 “0x”가 prefix로 붙는지에 따라 10진수, 16진수를 판단해 처리하기 때문에 필요 없을 것 같다고 판단되어, 유효하지 않은 문법으로 사용하는 경우에만 에러를 띄울 수 있도록 해당 값 지정</td>
    </tr>
    <tr>
    <td>"no-nested-ternary": "warn”</td>
    <td>삼항 연산자 중첩 사용 방지</td>
    <td>가독성에 안 좋긴 하나 상황에 따라 한 번의 중첩 정도는 괜찮다고 판단하여, warn으로 설정</td>
    </tr>
    <tr>
    <td>"react/jsx-filename-extension": "warn”(추후 변경예정)</td>
    <td>파일 내에서 컴포넌트를 사용하는데 js 확장자를 가진 경우 에러</td>
    <td>일부 유틸 함수에서 UI 로직을 반환하고 있어 warn 으로 설정</td>
    </tr>
    <tr>
    <td>"react/jsx-boolean-value": "warn"(추후 변경예정)</td>
    <td>boolean 타입의 props 전달 시 true / false를 명시적으로 전달하지 않는 것</td>
    <td>좋다고 생각되나 당장 도입하기엔 수정해야 할 컴포넌트들이 많고, 코드 스타일을 정해야하므로 이에 대해 논의 후 활성화</td>
    </tr>
    <tr>
    <td>"jsx-a11y/no-noninteractive-element-interactions": "warn"(추후 변경예정)</td>
    <td>상호작용 용도가 아닌 요소에 이벤트를 붙인 경우</td>
    <td>예외 케이스가 있을수도 있는 부분이라 판단되어 warn으로 설정</td>
    </tr>
    <tr>
    <td>"jsx-a11y/no-static-element-interactions": "warn”(추후 변경예정)</td>
    <td>div, span과 같은 시맨틱하지 않은 요소에 이벤트를 붙이면 스크린 리더가 해당 요소의 role을 인식할 수 없어서 이를 방지하는 옵션</td>
    <td>접근성을 지키는 것이 좋긴 하나, 이에 대해 팀원 전체가 추가적인 학습 필요 및 일관성 등 여러 부분이 관련되어 추후 활성화 예정</td>
    </tr>
    <tr>
    <td>"jsx-a11y/control-has-associated-label": "warn”</td>
    <td>button과 같은 대화형 요소에 aria-label등의 속성 값 명시를 강제하는 옵션</td>
    <td>당장 모든 곳에 적용하기에는 어려움이 있어 warn으로 설정</td>
    </tr>
    <tr>
    <td>"camelcase": "warn"</td>
    <td>카멜케이스 외 이름이 작명된 경우</td>
    <td>일부 백엔드 API, queryParameter (구글 접근) 등 프론트에서 제어할 수 없는 부분도 있기 때문에 warn으로 설정</td>
    </tr>
    <tr>
    <td>"no-console": ["warn", { "allow": ["warn", "error"] }]</td>
    <td>production 환경에서 console이 포함되는 것을 방지하는 옵션</td>
    <td>별도 프론트용 로깅 시스템을 사용하고 있지 않기 때문에 실시간 로그 확인을 하고 있어 console.warn, console.error는 허용, 그 외는 warn으로 표시되도록 처리</td>
    </tr>
    <tr>
    <td>"one-var": "off"</td>
    <td>다수의 변수 선언 시 키워드를 한번 혹은 여러번으로 사용하는 것을 강제하는 옵션</td>
    <td>불필요하다고 판단</td>
    </tr>
    <tr>
    <td>"import/order": "off”(추후 변경예정)</td>
    <td>import 구문의 순서 및 구분에 관한 옵션</td>
    <td>어떻게 구분할지에 대한 논의 후 적용 필요</td>
    </tr>
    <tr>
    <td>"no-useless-constructor": "off"</td>
    <td>class 내 constructor 생략 가능시 명시에 대한 옵션</td>
    <td>현재는 명시하고 있음</td>
    </tr>
    <tr>
    <td>"max-classes-per-file": "off”</td>
    <td>파일 당 클래스를 몇 개 선언할 수 있는지에 대한 옵션</td>
    <td>현재는 굳이 이에 대해 제한을 두고 있지 않음</td>
    </tr>
    <tr>
    <td>"class-methods-use-this": "off”</td>
    <td>클래스의 메소드 내부에서 무조건 this를 명시해야 하는 옵션</td>
    <td>this를 사용하지 않는 메소드라도 경고가 나타나기 때문에 off, 객체지향적 관점에서 필요하다고 생각은 되지만, 도입에 대해서 논의 필요</td>
    </tr>
    <tr>
    <td>"operator-assignment": "off”</td>
    <td>shorthand 연산자를 사용할 수 있다면 사용을 강제하는 옵션</td>
    <td>가독성을 지키기 위해 사용이 불필요한 경우도 있을 수 있다고 판단됨</td>
    </tr>
    <tr>
    <td>"import/prefer-default-export": "off”</td>
    <td>모듈 파일에 export default가 무조건 존재해야 된다고 강제하는 옵션</td>
    <td>필요없다고 판단</td>
    </tr>
    <tr>
    <td>"no-underscore-dangle": "off"</td>
    <td>네이밍에 언더바를 사용하지 못하도록 강제하는 옵션</td>
    <td>언더바를 기피하는게 좋은 방향이라고 생각되지만 당장 적용하기엔 논의가 필요함</td>
    </tr>
    <tr>
    <td></td>
    <td></td>
    <td></td>
    </tr>
    <tr>
    <td>"prefer-template": "off”</td>
    <td>템플릿 리터럴 문법을 강제하는 옵션</td>
    <td>가독성을 지키기 위해 사용이 불필요한 경우도 있을 수 있다고 판단됨</td>
    </tr>
    <tr>
    <td>"no-alert": "off”</td>
    <td>alert, confirm, prompt 사용시 에러</td>
    <td>빌트인 기능들을 사용하고 있음</td>
    </tr>
    <tr>
    <td>"prefer-destructuring": "off”</td>
    <td>배열, 객체의 요소에 접근할 때 구조 분해 할당을 강제하는 옵션</td>
    <td>상황에 따라 다를 수 있다고 판단</td>
    </tr>
    <tr>
    <td>"no-useless-concat": "off”</td>
    <td>문자열끼리 붙일 때 연산자로 붙이지 않도록 하는 옵션</td>
    <td>가독성을 위해 필요한 경우도 있다고 판단</td>
    </tr>
    <tr>
    <td>"consistent-return": "off”</td>
    <td>함수 내 return을 필수로 명시하도록 강제하는 옵션</td>
    <td>일관성이 있어 좋을 순 있으나 이에 대해 논의 필요</td>
    </tr>
    <tr>
    <td>"func-names": "off”</td>
    <td>함수를 사용할 때 함수명을 필수로 명시하도록 하는 옵션</td>
    <td>IIFE 나 변수에 할당되는 함수의 경우 필요하지 않다고 판단</td>
    </tr>
    <tr>
    <td>"no-plusplus": "off”</td>
    <td>증감 연산자 사용을 방지하는 옵션</td>
    <td>필요하지 않다고 판단</td>
    </tr>
    <tr>
    <td>"no-shadow": "off”</td>
    <td>외부 스코프의 변수와 같은 이름의 변수를 사용하지 못하도록 하는 옵션</td>
    <td>필요하지 않다고 판단</td>
    </tr>
    <tr>
    <td>"no-restricted-globals": "off”</td>
    <td>지정된 전역 변수에 직접 접근하는 것을 방지하는 옵션</td>
    <td>필요하지 않다고 판단</td>
    </tr>
    <tr>
    <td>"react/button-has-type": "off”</td>
    <td>버튼 요소 사용 시 type을 필수로 명시하도록 하는 옵션</td>
    <td>필요하지 않다고 판단</td>
    </tr>
    <tr>
    <td>"react/no-unstable-nested-components": "off”</td>
    <td>컴포넌트 내부에 불안정한 컴포넌트가 HOC 로 들어가는 경우</td>
    <td>학습 필요 후 필요하면 활성화</td>
    </tr>
    <tr>
    <td>"react/jsx-no-bind": "off”</td>
    <td>props로 함수를 넘기는 경우 this를 붙이도록 강제하는 옵션</td>
    <td>학습 필요 후 필요하면 활성화</td>
    </tr>
    <tr>
    <td>"react/require-default-props": "off”</td>
    <td>Component.defaultProps를 강제하는 옵션</td>
    <td>필요하지 않다고 판단 (추후 TS를 도입하게 되면 더욱 필요가 없다고 판단됨)</td>
    </tr>
    <tr>
    <td>"react/function-component-definition": "off”(추후 변경예정)</td>
    <td>함수형 컴포넌트를 정의 할 때에 관한 옵션</td>
    <td>일관성을 위해 해야 할 필요는 있으나, 어떤 것을 채택할지에 대한 논의가 필요</td>
    </tr>
    <tr>
    <td>"react/jsx-no-constructed-context-values": "off”</td>
    <td>Context API에 값을 전달할 때 useMemo를 사용하지 않고 넘기는 경우 방지</td>
    <td>학습 필요</td>
    </tr>
    <tr>
    <td>"react/jsx-props-no-spreading": "off”</td>
    <td>props를 넘길 때 가독성 및 props 파악이 용이하도록 전개 구문을 사용하지 않도록 강제하는 것</td>
    <td>필요하지 않다고 생각함. (현재 PropsTypes를 통해 명시하고 있기도 하고, TS 도입하면 더욱 필요가 없음.)</td>
    </tr>
    <tr>
    <td>"react/no-array-index-key": "off”</td>
    <td>컴포넌트의 키로 인덱스를 넣는 것을 방지하는 역할</td>
    <td>이해하고 사용하고 있기에 문제가 없다고 판단</td>
    </tr>
    <tr>
    <td>"react/destructuring-assignment": "off"</td>
    <td>함수형 컴포넌트의 매개변수 위치에서 바로 구조 분해 할당을 금지하는 옵션</td>
    <td>필요하지 않다고 판단</td>
    </tr>
    <tr>
    <td>"jsx-a11y/click-events-have-key-events": "off”(추후 변경예정)</td>
    <td>비대화형 요소(div, span)에 onClick 이벤트가 있는 경우,  onKeyUp, onKeyDown, onKeyPress도 같이 할당해주는 것</td>
    <td>활성화하면 좋으나 "jsx-a11y/no-noninteractive-element-interactions”, "jsx-a11y/no-static-element-interactions” 옵션과도 상관관계가 있어 이들과 함께 같이 변경</td>
    </tr>
    </tbody>
    </table>
