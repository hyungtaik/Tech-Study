### [1] 파이썬이란 무엇인가?

<hr>

#### 1. 파이썬이란?

- 인터프리터 언어

  - 한 줄씩 소스 코드를 해석해서 그때 그때 실행해 결과를 바로 확인할 수 있는 언어
  - 입력과 출력이 번갈아 이어지는 것이 마치 대화하는 것처럼 느껴지기 때문에 파이썬 '대화형' 인터프리터라고도 부른다.

- 파이썬 프로그램은 공동 작업과 유지 보수가 매우 쉽고 편하다. 

  - 이로 인해 다른 언어로 작성된 많은 프로그램과 모듈이 파이썬으로 재구성되고 있다.

    

#### 2. 파이썬의 특징

- **파이썬은 인간다운 언어이다. (직관적인 문법)**
  - 프로그래밍이란 인간이 생각하는 것을 컴퓨터에 지시하는 행위
  - 파이썬은 사람이 생각하는 방식을 그대로 표현할 수 있는 언어이다. 
    - 굳이 컴퓨터의 사고 체계에 맞추어서 프로그래밍을 하려고 애쓸 필요가 없다.
- **문법이 쉬워 빠르게 배울 수 있다**
  - 문법 자체가 아주 쉽고, 간결하며 사람의 사고 체계와 매우 닮아 있다.
- **무료이지만 강력하다**
  - 오픈소스 : 저작권자가 소스 코드를 공개하여 누구나 별다른 제한 없이 자유롭게 사용, 복제, 배포, 수정할 수 있는 소프트 웨어
  - 시스템 프로그래밍이나 하드웨어 제어와 같은 매우 복잡하고 반복 연산이 많은 프로그램은 파이썬과 어울리지 않는다. 하지만 **파이썬은 이러한 약점을 극복할 수 있게끔 다른 언어로 만든 프로그램을 파이썬 프로그램에 포함시킬 수 있다.**
  - C와의 궁합이 좋다. 즉 프로그램의 전반적인 뼈대는 파이썬으로 만들고, 빠른 실행 속도가 필요한 부분은 C로 만들어서 파이썬 프로그램 안에 포함시키는 것이다. 사실 파이썬 라이브러리 중에는 순수 파이썬만으로 제작된 것도 많지만 C로 만든 것도 많다. C로 만든 것은 대부분 속도가 빠르다. 
    - 파이썬 라이브러리는 파이썬 프로그램을 작성할 때 불러와 사용할 수 있는 미리 만들어 놓은 파이썬 파일 모음이다.
- **간결하다**
  - 소스 코드가 한눈에 들어와 이해하기 쉽기 때문에 공동 작업과 유지 보수가 아주 쉽고 편하다.
  - 파이썬은 줄을 맞추지 않으면 실행되지 않는다. (들여쓰기) - Tab or Spacebar 4번
    - 가독성에 크게 도움이 된다.

#### 3. 파이썬으로 무엇을 할 수 있을까?

- 시스템 유틸리티 제작
  - 파이썬은 운영체제의 시스템 명령어를 사용할 수 있는 각종 도구를 갖추고 있기 때문에 이를 바탕으로 갖가지 시스템 유틸리티를 만드는데 유리하다.
    - 유틸리티: 컴퓨터 사용에 도움을 주는 여러 소프트웨어를 일컫는다.
- GUI 프로그래밍
  - Graphic User Interface 프로그래밍이란 화면에 또 다른 윈도우 창을 만들고 그 창에 프로그램을 동작시킬 수 있는 메뉴, 버튼, 그림 등을 추가하는 것이다.
  - 파이썬은 GUI 프로그래밍을 위한 도구들이 잘 갖추어져있다.
    - Tkinter(티케이인터) : 5줄의 소스코드만으로 윈도우 창을 띄울 수 있다.
- C/C++와의 결합
  - 파이썬은 접착(glue) 언어라고도 부르는데, 그 이유는 다른 언어와 잘 어울려 결하해서 사용할 수 있기 때문이다.
- 웹 프로그래밍
- 수치 연산 프로그래밍
  - Numpy라는 수치 연산 모듈을 제공한다. (C로 작성했기 때문에 파이썬에서도 수치 연산을 빠르게 할 수 있다.)
    - 수치가 복잡하고 연산이 많다면 C같은 언어로 하는 것이 더 빠르다.
- 데이터베이스 프로그래밍
  - 데이터베이스에 접근하기 위한 도구를 제공한다.
  - Pickle(피클)이라는 모듈을 제공.
    - 자료를 변형없이 그대로 파일에 저장하고 불러오는 일을 한다.
- 데이터 분석, 사물 인터넷
  - Pandas(판다스) 모듈을 사용하여 데이터 분석을 더 쉽고 효과적으로 할 수 있다.
    - 데이터 분석에 특화된 'R'이라는 언어를 많이 사용하고 있지만, 판다스 등장 이후로 사용하는 경우가 점점 증가하고 있다.
  - 리눅스 기반의 라즈베리파이를 제어하는도구로 사용한다.

<hr>

**파이썬으로 할 수 없는 일**

```
1. 시스템과 밀접한 프로그래밍 영역
- 리눅스 같은 OS, 엄청난 횟수의 반복과 연산이 필요한 프로그램 또는 데이터 압축 알고리즘 개발 프로그램 등을 만드는 것은 어렵다. 즉 대단히 빠른 속도를 요구하거나 하드웨어를 직접 건드려야 하는 프로그램에는 어울리지 않는다.

2. 모바일 프로그래밍
 - 안드로이드 앱(App)을 개발하는 것은 어렵다. 
```



### [2] 파이썬  프로그래밍의 기초, 자료형

<hr>

#### 1. 숫자형

- 정수 : 123, -345, 0
- 실수 : 123.45, -123.45, 3.4e10
- 8진수 : 0o34, 0O34
- 16진수 : 0x2A, 0xFF
- 제곱 연산자 : **
- 나눗셈 후 몫을 반환하는 연산자 : //

#### 2. 문자열 자료형

- 문자열 만드는 방법 4가지

  - 큰 따옴표(")로 양쪽 둘러싸기
  - 작은 따옴표(')로 양쪽 둘러싸기
  - 큰 따옴표 3개를 연속으로(""") 써서 양쪽 둘러싸기
  - 작은 따옴표 3개를 연속으로(''') 써서 양쪽 둘러싸기

- 문자열 안에 작은 따옴표나 큰 따옴표를 포함시키고 싶을 때

  - \ (백슬래쉬) 를 함께 포함시키기

- 여러 줄인 문자열을 변수에 대입하고 싶을 때

  - 이스케이프 코드 (\n) 삽입하기
    - 이스케이프 코드란 프로그래밍할 때 사용할 수 있도록 미리 정의해 둔 "문자 조합"이다. 주로 출력물을 보기 좋게 정렬하는 용도로 사용한다.
  - 연속된 작은 따옴표 혹은 큰 따옴표 3개 사용하기 

- 문자열 연산하기

  - 문자열 더해서 연결
  - 문자열 숫자 곱해서 반복
  - 문자열 길이 구하기 - len(변수)

- 문자열 슬라이싱

  - ```python
    >>> a = "Life is too short, You need Python"
    >>> a[0:4]
    'Life'
    ```

    - 0<= a < 4

- 문자열 자료형은 그 요솟값을 변경할 수 없다. 그래서 immutable한 자료형이라고도 부른다.

- 문자열 포매팅

  - ```python
    >>> "I eat %d apples." % 3
    'I eat 3 apples.'
    ```

  - ```python
    >>> "I eat %s apples." % "five"
    'I eat five apples.'
    ```

  - ```python
    >>> number = 10
    >>> day = "three"
    >>> "I ate %d apples. so I was sick for %s days." % (number, day)
    'I ate 10 apples. so I was sick for three days.'
    ```

- 문자열 포맷 코드

  - %s : 문자열

  - %c : 문자 1개 (character)

  - %d : 정수

  - %f : 부동 소수(floating-point)

  - %o : 8진수

  - %x : 16진수

  - %% : Literal % (문자 % 자체)

  - ```python
    # 전체 길이가 10개인 문자열 공간에서 대입되는 값을 오른쪽 정렬하고 그 앞의 나머지는 공백으로 남겨두라는 의미
    # 왼쪽 정렬은 %-10s
    
    >>> "%10s" % "hi"
    '        hi'
    ```

- format 함수를 사용한 포매팅

  - ```python
    >>> "I eat {0} apples".format(3)
    'I eat 3 apples'
    
    >>> "I eat {0} apples".format("five")
    'I eat five apples'
    
    >>> number = 3
    >>> "I eat {0} apples".format(number)
    'I eat 3 apples'
    
    >>> number = 10
    >>> day = "three"
    >>> "I ate {0} apples. so I was sick for {1} days.".format(number, day)
    'I ate 10 apples. so I was sick for three days.'
    
    >>> "I ate {number} apples. so I was sick for {day} days.".format(number=10, day=3)
    'I ate 10 apples. so I was sick for 3 days.'
    ```

  - ```python
    # 왼쪽 정렬
    >>> "{0:<10}".format("hi")
    'hi     '
    
    # 오른쪽 정렬
    >>> "{0:>10}".format("hi")
    '        hi'
    
    # 가운데 정렬
    >>> "{0:^10}".format("hi")
    '    hi    '
    
    # 공백 채우기 + 가운데(^) 정렬
    >>> "{0:=^10}".format("hi")
    '====hi===='
    
    # 공백 채우기 + 왼쪽(<) 정렬
    >>> "{0:!<10}".format("hi")
    'hi!!!!!!!!'
    ```

- f 문자열 포매팅

  - 파이썬 3.6 버전부터는 f 문자열 포매팅 기능을 사용할 수 있다. 파이썬 3.6 미만 버전에서는 사용할 수 없는 기능이므로 주의해야 한다.

  - ```python
    >>> name = '홍길동'
    >>> age = 30
    >>> f'나의 이름은 {name}입니다. 나이는 {age}입니다.'
    '나의 이름은 홍길동입니다. 나이는 30입니다.'
    
    >>> age = 30
    >>> f'나는 내년이면 {age+1}살이 된다.'
    '나는 내년이면 31살이 된다.'
    
    # 딕셔너리는 Key와 Value라는 것을 한 쌍으로 갖는 자료형이다. 
    >>> d = {'name':'홍길동', 'age':30}
    >>> f'나의 이름은 {d["name"]}입니다. 나이는 {d["age"]}입니다.'
    '나의 이름은 홍길동입니다. 나이는 30입니다.'
    ```

- 문자열 관련 함수들

  - 문자 개수 세기 (count)

  - 위치 알려주기 

    - ```python
      # find
      >>> a = "Python is the best choice"
      >>> a.find('b')
      14
      >>> a.find('k')
      -1
      
      # index
      >>> a = "Life is too short"
      >>> a.index('t')
      8
      >>> a.index('k')
      Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
      ValueError: substring not found
      ```

  - 문자열 삽입 (join)

    - ```python
      >>> ",".join('abcd')
      'a,b,c,d'
      ```

  - 소문자를 대문자로 바꾸기 (upper)

  - 대문자를 소문자로 바꾸기 (lower)

  - 왼쪽 공백 지우기 (lstrip)

  - 오른쪽 공백 지우기 (rstrip)

  - 양쪽 공백 지우기 (strip)

  - 문자열 바꾸기 (replace)

  - 문자열 나누기 (split)

#### 3.리스트 자료형

- 리스트명 = [요소1, 요소2, 요소3, ...]

- 비어 있는 리스트는 a = list()로 생성할 수도 있다.

- str 함수는 정수나 실수를 문자열의 형태로 바꾸어 주는 파이썬의 내장 함수이다.

- del 함수를 사용해 리스트 요소 삭제

  - ```python
    >>> a = [1, 2, 3]
    >>> del a[1]
    >>> a
    [1, 3]
    
    >>> a = [1, 2, 3, 4, 5]
    >>> del a[2:]
    >>> a
    [1, 2]
    ```

- 리스트에 요소 추가 (append) - 맨 마지막에 추가

- 리스트 정렬

  - ```python
    # 정렬
    >>> a = [1, 4, 3, 2]
    >>> a.sort()
    >>> a
    [1, 2, 3, 4]
    
    # 뒤집기(reverse)
    >>> a = ['a', 'c', 'b']
    >>> a.reverse()
    >>> a
    ['b', 'c', 'a']
    ```

- 위치 반환 (index)

- 리스트에 요소 삽입

  - insert(a,b) : 리스트의 a번째 위치에 b를 삽입하는 함수

- 리스트 요소 제거 (remove) - 요소 삭제

- 리스트 요소 끄집어내기 (pop)

  - pop은 리스트의 맨 마지막 요소를 돌려주고 그 요소는 삭제

- 리스트에 포함된 요소 x의 개수 세기(count)

  - count(x)는 리스트 안에 x가 몇 개 있는지 조사하여 그 개수를 돌려주는 함수

- 리스트 확장 (extend)

  - extend(x)에서 x는 리스트만 올 수 있고, 원래 a 리스트에 x 리스트를 더한다.

  - ```python
    >>> a = [1,2,3]
    >>> a.extend([4,5])
    >>> a
    [1, 2, 3, 4, 5]
    >>> b = [6, 7]
    >>> a.extend(b)
    >>> a
    [1, 2, 3, 4, 5, 6, 7]
    ```

#### 4. 튜플 자료형

- 리스트와 비슷하지만 튜플은 ( ) 으로 둘러싸고, 리스트는 해당 값의 생성, 삭제, 수정이 가능하지만 튜플은 그 값을 바꿀 수 없다.
  - 리스트의 항목 값은 변화가 가능하고 튜플의 항목 값은 변화가 불가능하다.
  - 프로그램이 실행되는 동안 그 값이 항상 변하지 않기를 바란다거나 값이 바뀔까 걱정하고 싶지 않다면 주저하지 말고 튜플을 사용해야 한다. 이와는 반대로 수시로 그 값을 변화시켜야할 경우라면 리스트를 사용해야 한다. 실제 프로그램에서는 값이 변경되는 형태의 변수가 훨씬 많기 때문에 평균적으로 튜플보다는 리스트를 더 많이 사용한다.
- 단지 1개의 요소만을 가질때 (1, ) 와 같이 요소 뒤에 콤마를 반드시 붙여야 한다.
- 괄호를 생략해도 무방하다.

#### 5. 딕셔너리 자료형

- 딕셔너리는 Key와 Value를 한 쌍으로 갖는 자료형이다. 

- 리스트나 튜플처럼 순차적으로(sequential) 해당 요솟값을 구하지 않고 Key를 통해 Value를 얻는다.

- {Key1:Value1, Key2:Value2, Key3:Value3, ...}

  - Key에는 변하지 않는 값을 사용하고, Value에는 변하는 값과 변하지 않는 값 모두 사용할 수 있다.

- ```python
  # 딕셔너리 쌍 추가
  >>> a['name'] = 'pey'
  >>> a
  {1: 'a', 2: 'b', 'name': 'pey'}
  
  >>> a[3] = [1,2,3]
  >>> a
  {1: 'a', 2: 'b', 'name': 'pey', 3: [1, 2, 3]}
  
  # 딕셔너리 요소 삭제
  >>> del a[1]
  >>> a
  {2: 'b', 'name': 'pey', 3: [1, 2, 3]}
  ```

- Key를 사용해 Value 얻기

  - ```python
    >>> grade = {'pey': 10, 'julliet': 99}
    >>> grade['pey']
    10
    >>> grade['julliet']
    99
    ```

- 주의 사항

  - 딕셔너리에서 Key는 고유한 값이므로 중복되는 Key 값을 설정해 놓으면 하나를 제외한 나머지 것들이 모두 무시된다.
  - Key에 리스트는 쓸 수 없다.

- 딕셔너리 관련 함수

  - Key 리스트 만들기 (keys)

    - ```python
      >>> a = {'name': 'pey', 'phone': '0119993323', 'birth': '1118'}
      >>> a.keys()
      dict_keys(['name', 'phone', 'birth'])
      ```

    - >파이썬 2.7 버전까지는 a.keys() 함수를 호출할 때 반환 값으로 dict_keys가 아닌 리스트를 돌려준다. 리스트를 돌려주기 위해서는 메모리 낭비가 발생하는데 파이썬 3.0 이후 버전에서는 이러한 메모리 낭비를 줄이기 위해 dict_keys 객체를 돌려준다. 다음에 소개할 dict_values, dict_items 역시 파이썬 3.0 이후 버전에서 추가된 것들이다. 만약 3.0 이후 버전에서 반환 값으로 리스트가 필요한 경우에는 `list(a.keys())`를 사용하면 된다. dict_keys, dict_values, dict_items 등은 리스트로 변환하지 않더라도 기본적인 반복(iterate) 구문(예: for문)을 실행할 수 있다.

    - ```python
      # dict_keys 객체를 리스트로 변환
      >>> list(a.keys())
      ['name', 'phone', 'birth']
      ```

  - Value 리스트 만들기 (values)

    - ```python
      >>> a.values()
      dict_values(['pey', '0119993323', '1118'])
      ```

  - Key, Value 쌍 얻기(items)

    - ```python
      >>> a.items()
      dict_items([('name', 'pey'), ('phone', '0119993323'), ('birth', '1118')])
      ```

  - Key: Value 쌍 모두 지우기 (clear)

    - clear 함수는 딕셔너리 안의 모든 요소를 삭제한다. 빈 리스트를 [ ], 빈 튜플을 ( )로 표현하는 것과 마찬가지로 빈 딕셔너리도 { }로 표현한다.

  - Key로 Value얻기 (get)

    - ```python
      >>> a = {'name':'pey', 'phone':'0119993323', 'birth': '1118'}
      >>> a.get('name')
      'pey'
      >>> a.get('phone')
      '0119993323'
      ```

    - 존재하지 않는 키(nokey)로 값을 가져오려고 할 경우 a['nokey']는 Key 오류를 발생시키고 a.get('nokey')는 None을 돌려준다는 차이가 있다.

    - 딕셔너리 안에 찾으려는 Key 값이 없을 경우 미리 정해 둔 디폴트 값을 대신 가져오게 하고 싶을 때에는 get(x, '디폴트 값')을 사용하면 디폴트 값이 출력된다.

  - 해당 Key가 딕셔너리 안에 있는지 조사하기 (in)

    - ```python
      >>> a = {'name':'pey', 'phone':'0119993323', 'birth': '1118'}
      >>> 'name' in a
      True
      >>> 'email' in a
      False
      ```

#### 6. 집합 자료형

- 집합(set)은 파이썬 2.3부터 지원하기 시작한 자료형으로, 집합에 관련된 것을 쉽게 처리하기 위해 만든 자료형이다.

- ```python
  >>> s1 = set([1,2,3])
  >>> s1
  {1, 2, 3}
  
  >>> s2 = set("Hello")
  >>> s2
  {'e', 'H', 'l', 'o'}
  ```

  - 비어 있는 집합 자료형은 s = set()로 만들수 있다.

- 집합 자료형의 특징

  - 중복을 허용하지 않는다.

  - 순서가 없다.

    - 리스트나 튜플은 순서가 있기(ordered) 때문에 인덱싱을 통해 자료형의 값을 얻을 수 있지만 set 자료형은 순서가 없기(unordered) 때문에 인덱싱으로 값을 얻을 수 없다. (딕셔너리 역시 순서가 없다.)

    - set 자료형에 저장된 값을 인덱싱으로 접근하려면 다음과 같이 리스트나 튜플로 변환한후 해야 한다.

      - ```python
        >>> s1 = set([1,2,3])
        >>> l1 = list(s1)
        >>> l1
        [1, 2, 3]
        >>> l1[0]
        1
        >>> t1 = tuple(s1)
        >>> t1
        (1, 2, 3)
        >>> t1[0]
        1
        ```

- set 자료형을 정말 유용하게 사용하는 경우는 교집합, 합집합, 차집합을 구할 때이다.

  - 교집합

    - ```python
      >>> s1 = set([1, 2, 3, 4, 5, 6])
      >>> s2 = set([4, 5, 6, 7, 8, 9])
      
      # 교집합
      >>> s1 & s2
      {4, 5, 6}
      
      >>> s1.intersection(s2)
      {4, 5, 6}
      ```

  - 합집합

    - ```python
      >>> s1 | s2
      {1, 2, 3, 4, 5, 6, 7, 8, 9}
      
      >>> s1.union(s2)
      {1, 2, 3, 4, 5, 6, 7, 8, 9}
      ```

  - 차집합

    - ```python
      >>> s1 - s2
      {1, 2, 3}
      >>> s2 - s1
      {8, 9, 7}
      
      >>> s1.difference(s2)
      {1, 2, 3}
      >>> s2.difference(s1)
      {8, 9, 7}
      ```

- 집합 자료형 관련 함수들

  - 값 1개 추가하기 (add)

    - ```python
      >>> s1 = set([1, 2, 3])
      >>> s1.add(4)
      >>> s1
      {1, 2, 3, 4}
      ```

  - 값 여러개 추가하기 (update)

    - ```python
      >>> s1 = set([1, 2, 3])
      >>> s1.update([4, 5, 6])
      >>> s1
      {1, 2, 3, 4, 5, 6}
      ```

  - 특정 값 제거하기 (remove)

    - ```python
      >>> s1 = set([1, 2, 3])
      >>> s1.remove(2)
      >>> s1
      {1, 3}
      ```

      

#### 7.불 자료형

- 불(bool) 자료형이란 참(True)과 거짓(False)을 나타내는 자료형이다. 불 자료형은 다음 2가지 값만을 가질 수 있다.

  - True / False

- ```python
  >>> type(a)
  <class 'bool'>
  >>> type(b)
  <class 'bool'>
  ```

- 문자열, 리스트, 튜플, 딕셔너리 등의 값이 비어 있으면(" ", [ ], ( ), { }) 거짓

- None은 거짓

- bool 내장 함수를 사용하면 자료형의 참 거짓을 식별할 수 있다.

  - ```python
    >>> bool('python')
    True
    
    >>> bool('')
    False
    ```

    

#### 8. 자료형의 값을 저장하는 공간, 변수

- 변수를 만들 때는 =(assignment) 기호를 사용한다.

- 다른 프로그래밍 언어인 C나 JAVA에서는 변수를 만들 때 자료형을 직접 지정해야 한다. 하지만 파이썬은 변수에 저장된 값을 스스로 판단하여 자료형을 지정하기 때문에 더 편리하다.

- 변수 : 파이썬에서 사용하는 변수는 객체를 가리키는 것이라고도 말할 수 있다. 객체란 우리가 지금껏 보아 온 자료형과 같은 것을 의미한다.

  - `a = [1, 2, 3]`이라고 하면 `[1, 2, 3]` 값을 가지는 리스트 자료형(객체)이 자동으로 메모리에 생성되고 변수 a는 `[1, 2, 3]` 리스트가 저장된 메모리의 주소를 가리키게 된다.

  - 메모리란 컴퓨터가 프로그램에서 사용하는 데이터를 기억하는 공간이다.

  - ```python
    >>> a = [1, 2, 3]
    >>> id(a)
    4303029896
    ```

    - id 함수는 변수가 가리키고 있는 객체의 주소 값을 돌려주는 파이썬 내장 함수이다. 즉 여기에서 필자가 만든 변수 a가 가리키는 `[1, 2, 3]` 리스트의 주소 값은 4303029896 임을 알 수 있다.

- 리스트 복사

  - [:] 이용

    - ```python
      >>> a = [1, 2, 3]
      >>> b = a[:]
      >>> a[1] = 4
      >>> a
      [1, 4, 3]
      >>> b
      [1, 2, 3]
      ```

  - copy 모듈 이용

    - ```python
      >>> from copy import copy
      >>> b = copy(a)
      ```

- 변수를 만드는 여러 가지 방법

  - ```python
    # 튜플
    >>> a, b = ('python', 'life')
    >>> (a, b) = 'python', 'life'
    
    # 리스트
    >>> [a,b] = ['python', 'life']
    >>> a = b = 'python'
    
    # 변수의 값 바꾸기
    >>> a = 3
    >>> b = 5
    >>> a, b = b, a
    >>> a
    5
    >>> b
    3
    ```

    



### [3] 프로그램의 구조를 쌓는다. 제어문

#### 1. if문

- 프로그래밍에서 조건을 판단하여 해당 조건에 맞는 상황을 수행하는 데 사용

- 들여쓰기 중요

- 파이썬이 다른 언어보다 보기 쉽고 소스 코드가 간결한 이유는 바로 콜론(:)을 사용하여 들여쓰기(indentation)를 하도록 만들었기 때문이다.

- x and y, x or y, not x 사용 

- x in s, x not in s - 리스트, 튜플, 문자열에 사용

- pass를 사용하여 아무 일도 하지 않도록 설정

- 다양한 조건을 판단하는 elif

- 조건부 표현식

  - 조건문이 참인 경우` if `조건문 ` else `조건문이 거짓인 경우

    - 가독성에 유리하고, 한 줄로 작성할 수 있어 활용성이 좋다.

  - ```python
    if score >= 60:
        message = "success"
    else:
        message = "failure"
        
    message = "success" if score >= 60 else "failure"
    ```

    

#### 2. while문

- 반복해서 문장을 수행해야 할 경우 while문을 사용

- ```python
  >>> number = 0
  >>> while number != 4:
  ...     print(prompt)
  ...     number = int(input())
  ...
  
  1. Add
  2. Del
  3. List
  4. Quit
  
  Enter number:
  ```

- break로 while문 강제로 빠져나가기

- continue로 while문의 맨 처음으로 돌아가기

- Ctrl+C로 무한 루프 탈출

#### 3. for문

- 매우 유용하고 문장 구조가 한눈에 쏙 들어온다는 장점이 있다.

- ```python
  for 변수 in 리스트(또는 튜플, 문자열):
      수행할 문장1
      수행할 문장2
      ...
      
  # Example
  >>> a = [(1,2), (3,4), (5,6)]
  >>> for (first, last) in a:
  ...     print(first + last)
  ...
  3
  7
  11
  ```

- range 함수 : 숫자 리스트를 자동으로 만들어 주는 함수

  - ```python
    >>> a = range(10)
    >>> a
    range(0, 10)
    
    # Example
    >>> add = 0 
    >>> for i in range(1, 11): 
    ...     add = add + i 
    ... 
    >>> print(add)
    55
    ```

  - range(10)은 0부터 10 미만의 숫자를 포함하는 range 객체를 만들어 준다.

- 리스트 내포 

  - 리스트 안에 for문을 포함하는 리스트 내포(List comprehension)를 사용하면 좀 더 편리하고 직관적인 프로그램을 만들 수 있다.

  - ```python
    # a 리스트의 각 항목에 3을 곱한 결과를 result 리스트에 담는 예제
    >>> a = [1,2,3,4]
    >>> result = []
    >>> for num in a:
    ...     result.append(num*3)
    ...
    >>> print(result)
    [3, 6, 9, 12]
    
    # 리스트 내포
    >>> a = [1,2,3,4]
    >>> result = [num * 3 for num in a]
    >>> print(result)
    [3, 6, 9, 12]
    
    >>> a = [1,2,3,4]
    >>> result = [num * 3 for num in a if num % 2 == 0]
    >>> print(result)
    [6, 12]
    ```

  - ```python
    >>> result = [x*y for x in range(2,10)
    ...               for y in range(1,10)]
    >>> print(result)
    [2, 4, 6, 8, 10, 12, 14, 16, 18, 3, 6, 9, 12, 15, 18, 21, 24, 27, 4, 8, 12, 16,
    20, 24, 28, 32, 36, 5, 10, 15, 20, 25, 30, 35, 40, 45, 6, 12, 18, 24, 30, 36, 42
    , 48, 54, 7, 14, 21, 28, 35, 42, 49, 56, 63, 8, 16, 24, 32, 40, 48, 56, 64, 72,
    9, 18, 27, 36, 45, 54, 63, 72, 81]
    ```

    

### [4]  프로그램의 입력과 출력은 어떻게 해야 할까?

<hr>

#### 1. 함수

- 입력값을 가지고 어떤 일을 수행한 다음에 그 결과물을 내어놓는 것

- 함수를 사용하는 이유

  - 반복되는 부분이 있을 경우 "반복적으로 사용되는 가치 있는 부분"을 한 뭉치로 묶어서 "어떤 입력값을 주었을 때 어떤 결괏값을 돌려준다"라는 식의 함수로 작성하는 것
  - 자신이 만든 프로그램을 함수화하면 프로그램 흐름을 일목요연하게 볼 수 있기 때문이다.
  - 프로그램 흐름도 잘 파악할 수 있고 오류가 어디에서 나는지도 바로 알아차릴 수 있다.

- ```python
  # 함수의 구조
  def 함수명(매개변수):
      <수행할 문장1>
      <수행할 문장2>
      ...
      
  # Example
  def add(a, b): 
      return a + b
  ```

- 매개변수와 인수

  - 매개 변수 : 함수에 입력으로 전달된 값을 받는 변수를 의미

  - 인수 : 함수를 호출할 때 전달하는 입력 값

  - ```python
    def add(a, b):  # a, b는 매개변수
        return a+b
    
    print(add(3, 4))  # 3, 4는 인수
    
    >>> result = add(b=5, a=3)  # b에 5, a에 3을 전달
    >>> print(result)
    8
    ```

- 여러 개의 입력값을 받는 함수 만들기

  - ```python
    >>> def add_many(*args): 
    ...     result = 0 
    ...     for i in args: 
    ...         result = result + i 
    ...     return result 
    
    >>> result = add_many(1,2,3)
    >>> print(result)
    6
    >>> result = add_many(1,2,3,4,5,6,7,8,9,10)
    >>> print(result)
    55
    
    >>> def add_mul(choice, *args): 
    ...     if choice == "add": 
    ...         result = 0 
    ...         for i in args: 
    ...             result = result + i 
    ...     elif choice == "mul": 
    ...         result = 1 
    ...         for i in args: 
    ...             result = result * i 
    ...     return result 
    ... 
    >>>
    ```

  - 키워드 파라미터 kwargs ( kwargs는 keyword arguments)

  - ```python
    >>> def print_kwargs(**kwargs):
    ...     print(kwargs)
    ...
    
    >>> print_kwargs(a=1)
    {'a': 1}
    >>> print_kwargs(name='foo', age=3)
    {'age': 3, 'name': 'foo'}
    ```

    - 매개변수 이름 앞에 `**`을 붙이면 매개변수 kwargs는 딕셔너리가 되고 모든 `key=value` 형태의 결괏값이 그 딕셔너리에 저장된다.

- 매개변수에 초깃값 미리 설정하기

  - ```python
    def say_myself(name, old, man=True): 
        print("나의 이름은 %s 입니다." % name) 
        print("나이는 %d살입니다." % old) 
        if man: 
            print("남자입니다.")
        else: 
            print("여자입니다.")
    ```

  - 초기화시키고 싶은 매개변수를 항상 뒤쪽에 놓지않으면 오류가 발생한다.

- 함수 안에서 함수 밖의 변수를 변경하는 방법

  - return 사용하여 대입하여 변경

  - global 명령어 사용

    - 프로그래밍을 할 때 global 명령어는 사용하지 않는 것이 좋다. 왜냐하면 함수는 독립적으로 존재하는 것이 좋기 때문이다. 외부 변수에 종속적인 함수는 그다지 좋은 함수가 아니다.

    - ```python
      a = 1 
      def vartest(): 
          global a 
          a = a+1
      
      vartest() 
      print(a)
      ```

- lambda

  - 함수를 생성할 때 사용하는 예약어로 def와 동일한 역할

  - 함수를 한줄로 간결하게 만들 때 사용

  - ```python
    >>> add = lambda a, b: a+b
    >>> result = add(3, 4)
    >>> print(result)
    7
    ```

  - lambda 예약어로 만든 함수는 return 명령어가 없어도 결괏값을 돌려준다.

#### 2. 사용자 입력과 출력

- 사용자 입력

  - input의 사용 - 입력되는 모든 것을 문자열로 취급

    - ```python
      >>> number = input("숫자를 입력하세요: ")
      숫자를 입력하세요: 3
      >>> print(number)
      3
      >>>
      ```

      

- print

  - ```
    >>> a = [1, 2, 3]
    >>> print(a)
    [1, 2, 3]
    
    # 큰따옴표로 둘러싸인 문자열은 + 연산과 동일
    >>> print("life" "is" "too short") # ①
    lifeistoo short
    >>> print("life"+"is"+"too short") # ②
    lifeistoo short
    
    #문자열 띄워쓰기는 콤마로 한다.
    >>> print("life", "is", "too short")
    life is too short
    
    # 한 줄에 결과값 출력하기
    >>> for i in range(10):
    ...     print(i, end=' ')
    ...
    0 1 2 3 4 5 6 7 8 9
    ```

    

#### 3. 파일 읽고 쓰기

- 파일 생성하기

  - ```python
    # 파일 생성을 위해 내장 함수 open 사용
    f = open("새파일.txt", 'w') # r: 읽기 모드, w: 쓰기모드, a: 추가 모드
    f.close() # 열려있는 파일 객체를 닫아주는 역할
    		  # 쓰기모드로 열었던 파일을 닫지 않고 다시 사용하려고 하면 오류가 발생
    ```

- 파일을 쓰기 모드로 열어 출력값 적기

  - ```python
    # writedata.py
    f = open("C:/doit/새파일.txt", 'w')
    for i in range(1, 11):
        data = "%d번째 줄입니다.\n" % i
        f.write(data)
    f.close()
    ```

- 프로그램의 외부에 저장된 파일을 읽는 여러가지 방법

  - readline() 함수를 이용하기

    - ```python
      f = open("C:/doit/새파일.txt", 'r')
      line = f.readline()
      print(line)
      f.close()
      
      # 모든 줄 읽어서 화면에 출력
      f = open("C:/doit/새파일.txt", 'r')
      while True:
          line = f.readline()
          if not line: break
          print(line)
      f.close()
      ```

  - readlines() 함수 사용하기 

    - 파일의 모든 줄을 읽어서 각각의 줄을 요소로 갖는 리스트로 돌려준다.

    - ```python
      f = open("C:/doit/새파일.txt", 'r')
      lines = f.readlines()
      for line in lines:
          print(line)
      f.close()
      ```

  - read 함수 사용하기

    - 파일의 내용 전체를 문자열로 돌려준다.

    - ```python
      f = open("C:/doit/새파일.txt", 'r')
      data = f.read()
      print(data)
      f.close()
      ```

- 파일에 새로운 내용 추가하기

  - ```python
    f = open("C:/doit/새파일.txt",'a')
    for i in range(11, 20):
        data = "%d번째 줄입니다.\n" % i
        f.write(data)
    f.close()
    ```

- with문과 함께 사용하기

  - with문을 사용하면 with 블록을 벗어나는 순간 열린 파일 객체 f가 자동으로 close되어 편리하다.

  - ```python
    with open("foo.txt", "w") as f:
        f.write("Life is too short, you need python")
    ```

- sys 모듈로 매개변수 주기

  - ```python
    import sys
    
    args = sys.argv[1:]
    for i in args:
        print(i)
        
    # cmd 결과
    C:\doit>python sys1.py aaa bbb ccc
    aaa
    bbb
    ccc
    ```

    







