### TypeScript

_애증의 타입스크립트_

- 타입 지정하기

  이렇게 객체를 생성하면 추론적으로 타입이 지정된다.

        ```
        const User = {
            name: "Jun";
            age: 26;
        }
        ```

  명시적으로 나타내기 위해서 타입선언을 해줄 수 있다.

        ```
        const User: {name: string, age: number} = {
            name: "Jun";
            age: 26;
        }
        ```

  계속 사용할 타입을 지정해주기 위해서 'type'을 사용하거나 'interface'를 사용한다.

        ```
        type User = {
            name: string;
            age: number;
        }

        interface User {
            name: string;
            age: number;
        }
        ```

  'type'과 'interface'의 차이점은 공부를 해봐야 알 것 같다.
  현재는 'interface'는 'type'보다 확장하고 수정하기가 쉽다는 점만 알고 있다.

  배열에 타입을 지정하려면 대괄호를 붙여주거나, Tuple을 사용한다.

        ```
        const name : string[]
        name = ["Jun", "junghan", "mingyu"]

        const name : [string, number]
        name = ["Jun", 26]
        ```

  Union Type은 여러 타입 중 하나일 수 있다는 것을 의미한다.
  string 이거나 number 이거나

        ```
        const name : string | number
        name = "Jun"
        name = 26
        ```

  매개변수나 props로 넘겨줄 때 값이 없을 수도 있다면 '?' 옵셔널체이닝을 사용해준다.

        ```
        type User = {
            name: string;
            age?: number;
        }
        ```

  기본값을 정해주는 방법이 더 좋다.

        ```
        function printUser(name, age = 26) {
            console.log(name, age)
        }
        ```

  Type과 Type을 합쳐서 확장해줄 수 있다.

        ```
        type User = {
            name: string,
            age: number,
        };

        type Info = {
            email: string,
            address: string,
        };

        type UserAndInfo = User & Info;
        ```
