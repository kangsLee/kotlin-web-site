---
type: doc
layout: reference
category: "Syntax"
title: "Packages"
---

# Packages (패키지)

소스 파일은 패키지 선언으로 시작됩니다.

``` kotlin
package foo.bar

fun baz() {}

class Goo() {}

// ...
```

소스 파일의 모든 내용은 (예 : 클래스와 함수 등) 선언 된 패키지에 포함되어 있습니다.
위의 예시에 따르면, `baz()` 의 전체 이름은 `foo.bar.baz()` 이고 , `Goo()` 의 전체 이름은 `foo.bar.Goo`입니다. 

패키지가 지정되지 않은 경우, 이러한 파일의 내용은 패키지 이름이 없는 "default"에 속합니다.

## Imports

default를 가져오는 것과는 별도로, 각 file은 기본적인 imports를 포함할 수 있습니다.
imports구문의 설명은 이 링크에 설명 되어있습니다. [grammar](grammar.html#import) 

우리는 하나의 이름을 가져올 수 있습니다, 예를 들면,

``` kotlin
import foo.Bar // Bar is now accessible without qualification
```

또는 범위에서 액세스 할 수있는 모든 내용 (package, class, object etc):

``` kotlin
import foo.* // everything in 'foo' becomes accessible
```

이름 충돌이있는 경우, 로컬 충돌하는 엔티티의 이름을 변경하려면 키워드*as* {: .keyword} 를 사용하여 명확하게 할 수 있습니다 :

``` kotlin
import foo.Bar // Bar is accessible
import bar.Bar as bBar // bBar stands for 'bar.Bar'
```

`import` 키워드는 클래스를 가져오는것에만 한정되지 않습니다. 당신은 또한 다른 선언을 가져 오는 데 사용할 수 있습니다 :

* 최상위 함수와 속성;
    *문법에 선언되어져 있는 함수와 속성. [object declarations](object-declarations.html#object-declarations);
* [enum constants](enum-classes.html)

자바와는 달리, 코틀린은 별도의 "import static"은 구문이 나누어져 있지 않습니다. 이 선언은 모두 정규`import` 키워드를 사용하여 가져옵니다.

## Visibility of Top-level Declarations ( 최 상위 선언 )

최상위 선언 *private*{: .keyword} 로 표시되어 있으면, ​​선언 된 파일에 대해 비공개입니다.(see [Visibility Modifiers](visibility-modifiers.html)).