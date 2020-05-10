# DOM API

자바스크립트를 통해 DOM 조작 ,수정, 생성 할 수 있다.

> DOM 요소 생성하기

* createElement\(태그이름\)

태그이름으로 노드를 생성한다.  
return : HTMLElement 상속받은 객체

* createTextNode\(문자열\)

텍스트 노드를 생성한다.  
return : text 객

* appendChild\(Node\)

인자로 전달한 노드를 자식노드로 추가한다.  
return : 추가한 노드 

```javascript
const div = document.createElement('div');
const text = document.createTextNode('자바스크립트');
div.appendChild(text);
document.body.appendChild(div);
```

div 노드를 생성하고 text객체를 div에 추가한 후 body에 div를 자식노드로 추가한다.

> 노드 제거하기

* removeChild\(Node\)

인자로 전달된 자식노드를 제거한다.

```javascript
const div = document.createElement('div');
const text = document.createTextNode('자바스크립트');
div.appendChild(text);
document.body.appendChild(div);


setTimeout(() => {
  document.body.removeChild(div);
}, 1000);

```

1초 후 body에 추가한 div 자식노드를 제거한다.

> DOM 요소에 접근하기

* document.getElementById\(id\)

id 어트리뷰트로 요소를 한 개 선택한다. 여러개 있다면 첫번째 요소 반환한다.

{% tabs %}
{% tab title="javascript" %}
```javascript
const js = document.getElementById('js');
console.log(js.id); //js
```
{% endtab %}

{% tab title="html" %}
```markup
<div id='js'>자바스크립트</div>

```
{% endtab %}
{% endtabs %}

반환된 객체 프로퍼티로 id에 접근하면 id인 js를 가져올 수 있다.

