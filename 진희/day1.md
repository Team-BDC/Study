# JSX&Props

## 2.1. Component

- react with component 모든 것은 component로 되어 있음
- component : HTML(<div />같은 걸로 감싸져 있어야 함.)을 반환하는 함수
- JSX : javascript+HTML개념.
- how do we make component?

    src 폴더 안에 새 .js파일을 만들어유(모든 파일에는 import React from "react";는 필수여~)

    그 안에 function을 만들어유 (대문자로 시작하는 함수)

    주의사항! react application은 하나의 component만을 rendering해야함.⇒여러 개 하고 싶으면 최종적으로 렌더링할 component안에 다른 component를 넣어놓으면 됨.

## 2.2. Property(parent⇒children으로 정보 전달)

- props.fav == {fav}
- function Component(props)하면 모든 property 가져옴(접근법 : props.propertyName)
- 특정 property 가져오고 싶다면(여기서 propertyName이라고 하자) props대신 function Component({propertyName})이케 불러오면 됨. 사용할 때도 걍 {propertyName}이케 하면 돼

- 동적 property
- map을 이용해 동적으로 component를 렌더링 할 수 있음.
- map : array의 각 item에서 function을 실행해서 새 list를 만들어줌

    ex)

    ```jsx
    friends=["dal","mark","lynn","jh"]
    friends.map(function(current){
    		console.log(current)
        return current+"♥";})

    //result
    dal
    mark
    lynn
    jh
    //return result
    ["dal","mark","lynn","jh"]

    //map함수는
    //이케 array안의 하나의 요소에 순차적으로 function 적용 후
    //그 return 값으로 다시 array만들어서 반환해줌
    ```

    이걸로 한 component에 여러 property를 넘겨 줄 때 귀찮게 반복으로 안하고 밑에처럼 할 수 있음

    ```jsx
    function App() {
      return (
        <div className="App">
            {foodILike.map(dish=> <Food name={dish.name} picture={dish.image}/>)}
        </div>
      );
    //foodILike array에 있는 요소들이 Food component에 순차적으로 props로 전달됨.
    }
    ```

## 2.3. Map Recap

react의 property는 유일해야 함. 그래서 key가 필요함.

⇒key로 인해 unique함을 잃어버리지 않을 수 있음.

property로 key를 설정해주자! 유일하도록!