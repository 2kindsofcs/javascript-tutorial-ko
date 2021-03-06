# 현대적인 모드, "use strict"

오랫동안 자바스크립트는 호환성 문제없이 발전해왔습니다. 자바스크립트에 새로운 기능이 추가되었으나, 오래된 기능은 변경되지 않았습니다.

이것은 기존의 코드를 절대 망가뜨리지 않는다는 장점을 갖고 있었습니다. 하지만 자바스크립트 창시자들이 했던 실수나 불완전한 결정이 자바스크립트 안에 영원히 존재하게 되었다는 단점이 있었습니다.

이것은 ECMAScript5(ES5)가 등장했던 2009년까지의 일이었습니다. ES5에서는 자바스크립트에 새로운 기능이 추가되었고 기존 기능 중 일부가 변경되었습니다. 이전의 오래된 코드가 계속 작동할 수 있도록, 대부분의 변경사항은 기본적으로 적용되지 않습니다. 변경사항을 적용하고 싶다면 `"use strict"`라는 특별한 지시어를 통해 명시적으로 활성화해야 합니다.

## "use strict"

지시어는 `"use strict"` 나 `'use strict'` 라는 문자열로 표현됩니다. 지시어를 스크립트 최상단에 작성하면, 스크립트 전체가 "현대적인" 방식으로 실행됩니다.

예를 들어

```js
"use strict";

// 이 코드는 현대적인 방식으로 실행됩니다.
...
```

우리는 함수(명령어들을 그룹화하는 방식)에 대해 곧 배울 것입니다.

`"use strict"`가 스크립트 대신 (대부분의) 함수의 시작 위치에 놓일 수 있다는 사실에 주목하세요. 그러면 엄격 모드(strict mode)가 오직 해당 함수에서만 활성화됩니다. 하지만 보통 사람들은 이 모드를 스크립트 전체를 위해 사용합니다.


````warn header="\"use strict\"는 반드시 상단에 위치시키세요."
`"use strict"`는 스크립트 최상단에 위치한다는 사실을 명심하세요. 그렇지 않으면, 엄격 모드는 활성화되지 않을 수도 있습니다.

다음 코드에서는 엄격 모드가 활성화되지 않습니다.:

```js no-strict
alert("some code");
// 하단에 위치한 "use strict"는 무시됩니다. 상단에 위치해야 합니다.

"use strict";

// 엄격 모드가 활성화되지 않습니다.
```

주석만 `"use strict"` 위에 위치할 수 있습니다.
````

```warn header="`use strict`를 취소할 방법은 존재하지 않습니다."
`"no use strict"`나 이와 비슷하게 생긴 지시어는 존재하지 않습니다. that would return the old behavior.

엄격 모드를 적용하면, 돌이킬 방법은 없습니다.
```

## 항상 "use strict"를 사용하세요.

`"use strict"`와 "default" 모드의 차이점에 대해 다뤄봐야 할 필요가 있습니다.

다음 챕터에서 자바스크립트의 기능에 대해 배울 때, 우리는 엄격 모드와 기본 모드의 차이점에 대해 알아볼 것입니다. 다행히도, 차이점은 많지 않습니다. 그리고 이 두 모드는 우리의 삶을 더욱 편리하게 만들어 줍니다.

현시점에서는 엄격 모드에 대해 이 정도만 알아도 충분합니다.:

1. `"use strict"` 지시어는 엔진을 "현대적인" 모드로 전환시키고 일부 내장된 기능을 변경합니다. 나중에 이 부분을 공부할 때 자세히 알아보도록 하겠습니다.
2. 엄격 모드는 상단에 위치한 `"use strict"`를 통해 활성화됩니다. 엄격 모드를 자동으로 활성화시키는 "클래스"와 "모듈" 같은 여러 기능도 존재합니다.
3. 엄격 모드는 모든 모던 브라우저에 의해 지원됩니다.
4. 항상 스크립트를 `"use script"`로 시작할 것을 권장합니다. 이 튜토리얼의 모든 예제는 (매우 드문) 특정한 상황이 아니라면 `"use script"`로 시작한다는 것을 전제합니다.
