
a11y | Accessibility Guidelines 자료 정리

# Navigation (카테고리)

## 기존 구현 방식
마우스 오버 시 하위 메뉴 열림, 키보드 초점 이동 시 하위 메뉴 열림

<iframe width="100%" height="250" src="http://jsfiddle.net/hohoya33/7vynqbh4/embedded/result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

```js
$('.ctg_mall_lst').on('mouseenter focusin', '.ctg_top_mn', function(e){ ... });
```

## 카테고리 항목이 늘어나면..🤔
현재 웹 사이트에서 사용되는 이러한 기능은 장애가있는 일부 사용자, 특히 스크린리더기에 의존하는 사용자 및 마우스를 사용할 수없는 사용자에게는 유용하지 않음
<img src="img/category_all.png" width="90%" alt="">

## 초점이동 → 컨텐츠 탐색 (조작을 위한 이동)
* 의도하지 않은 기능 실행
* 의도하지 않은 정보 인식
* 정보의 선택권 보장 X


## 웹 접근성 지침
    <table>
        <colgroup>
        <col style="width:12%">
        <col style="width:88%">
        </colgroup>
        <thead>
            <tr>
                <td>원칙 3</td>
                <td>이해의 용이성</td>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>3.1</td>
                <td>가독성</td>
            </tr>
            <tr>
                <td>3.1.1</td>
                <td>기본 언어 표시 (주로 사용하는 언어를 명시해야 한다)</td>
            </tr>
            <tr>
                <td style="color:#13DAEC">3.2 </td>
                <td style="color:#13DAEC">예측 가능성 (콘텐츠의 기능과 실행결과는 예측 가능해야 한다)</td>
            </tr>
            <tr>
                <td style="color:#13DAEC">3.2.1</td>
                <td style="color:#13DAEC">사용자 요구에 따른 실행 - 사용자가 의도하지 않은 기능 (새 창, 초점 변화 등)은 실행되지 않아야 한다.</td>
            </tr>
            <tr>
                <td>3.3</td>
                <td>콘텐츠의 논리성 (콘텐츠는 논리적으로 구성해야 한다)</td>
            </tr>
            <tr>
                <td>3.3.1</td>
                <td>...</td>
            </tr>
        </tbody>
    </table>

## 예측 가능성 (사용자 요구에 따른 실행)
초점을 이동 하거나 마우스를 올리는 것은 항상 기능을 실행하기 위한 의도로 보기 어려움
사용자가 의도하지 않는 기능이 자동으로 실행 되지 않도록 개발

* 초점이동 → 기능 실행 NO
* Enter 입력 → 하위 메뉴 확장
* 하위 메뉴 확장 축소 시 적절한 피드백 제공

사용자가 실행하기 전까지는 문서를 갱신(이동, 추가, 삭제, 재배치)하거나, 팝업(새 창, 레이어)을 띄우거나, 초점을 다른 곳으로 옮기지 않는다.




## WAI-ARIA
* [W3C WAI-ARIA](https://www.w3.org/WAI/standards-guidelines/aria/)는 HTML의 접근성 문제를 보완하는 W3C 명세
* 스크린리더 사용자들이 웹 콘텐츠를 쉽게 이용할 수 있도록 새로운 방법을 정의
* HTML 요소에 role 또는 aria-* 속성을 추가
* 콘텐츠의 역할(roles), 상태(states), 속성(properties) 정보를 스크린리더에 제공
ARIA 역할(roles)
알럿(role="alert")
대화상자(role="dialog")
역할 특성을 사용하여 요소에 설정됩니다.
역할을 첨부하면 각 요소를 처리하는 방법에 대한 보조 기술 정보를 얻을 수 있습니다.

ARIA 속성(properties)
지정된 개체의 특성에 필수적이거나 개체와 관련된 데이터 값을 나타내는 속성.
팝업 상태(aria-haspopup="true")
요소에 의해 트리거 될 수있는 대화식 팝업 요소 (예 : 메뉴 또는 대화 상자)의 가용성 및 유형을 나타냅니다.
Role를 이용해 콘텐츠 블록에 고유의 식별자 지정
Role들을 사용하면 스크린리더 사용자들에게 현재 탐색하고 있는 콘텐츠 영역이 'Banner'영역인지 아니면 콘텐츠의 'Main'영역인지 등을 알려 줄 수 있습니다.

ARIA 상태(states)
숨김 상태(aria-hidden="true|false")
확장 상태(aria-expanded="true|false")
선택 상태(aria-selected="true|false")
상태는 사용자 작업 또는 자동화된 프로세스에 따라 변경될 수 있는 개체의 특성을 표현하는 동적 속성입니다.

aria-expanded, aria-haspopup, aria-hidden
버튼 혹은 링크를 눌렀을 때 레이어팝업이 열리거나 하위 목록이 펼쳐지는 형태. 
이런 류의 객체를 스크린리더 사용자들이 탐색할 때 마주치게 되는 문제는 해당 객체가 레이어를 열거나 하위 목록이 펼쳐지는 형태의 것인지 알기 어렵다는 것입니다. 이 문제를 해결하기 위하여 aria-expanded, aria-haspopup 를 사용


스크린리더 사용자들에게 정확한 정보를 제공하기 위한 목적으로 사용
웹 페이지에 WAI-ARIA가 적용 되었을 때 스크린리더 사용자들에게 어떤 도움을 줄 수 있는지에 대해


```html
<!-- 역할(roles) -->
<element role="tab">
<element role="dialog">
<element role="navigation">
...
<!-- 상태(states) -->
<element aria-haspopup="true|false">
<element aria-expanded="true|false">
<element aria-hidden="true|false">
...
<!-- 속성(properties) -->
<element aria-labelledby="ID reference list">
<element aria-label="string">
<element aria-describedby="ID reference list">
...
```

## WAI-ARIA 참고 사항
role 또는 aria-* 속성을 특정 HTML 요소에 사용할 수 있는지 HTML5 명세를 검토하면서 적용해야 합니다.

* 모든 HTML 요소에 무분별하게 사용 금지
* 대부분의 HTML 요소와 속성을 흉내 (WAI-ARIA 사용 최소화)
* 사용하기에 앞서 HTML을 의미 있게 사용했는지 충분히 검토

```html
<!-- Better: ARIA 역할과 유사한 의미를 가진 고유 HTML 요소를 사용 -->
<nav>...</nav>

<!-- Good -->
<div role="navigation">...</div>

<!-- Bad -->
<nav role="navigation">...</nav>
```


## 기대 효과
* 장애, 지적 장애 또는 지체 장애가 있는 사람들도 초점 및 문맥의 변화를 이해할 수 있게 된다
* 사용자에게 미리 하위 메뉴 보기 열림을 경고하면 하위 메뉴가 열린다는 사실을 알 수 있으므로 이용하는데 따른 혼란이 줄어든다





# SSG 통합 카테고리 개선

## 통합 카테고리 버튼
* **aria-haspopup="true"** 요소에 팝업 컨텍스트 메뉴 또는 하위 메뉴가 있음
* **aria-expanded="true|false"** 요소가 제어하는 ​​대상이 현재 확장 또는 축소 상태를 나타냄

```html
<button aria-expanded="false" aria-haspopup="true">
    통합 카테고리 보기
</button>
```
```js
// 레이어 열기
$('button').attr('aria-expanded', 'true');

// 레이어 닫기
$('button').attr('aria-expanded', 'false');
```

## VoiceOver 테스트
<iframe width="100%" height="570" src="http://jsfiddle.net/hohoya33/2mfs3a41/embedded/result,js,html/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

## 의미에 맞는 HTML 작성
* a 태그는 Enter 키만으로 실행
* button 태그는 Enter, Space 키로 실행 가능
* 스크린리더 사용자는 a 요소로부터 '버튼' 설명을 듣고 Space 키 입력 시 혼란
* 올바른 HTML의 선택은 사용자 경험과 접근성 측면에서 모두 중요
   

## 통합 카테고리 레이어
* **aria-hidden="true|false"** 화면에서 숨기면 true, 화면에 표시하면 false 
* true 값을 가지면 스크린리더 접근이 불가능 (포커스를 차단하지 않음)

```html
<div class="ctg_total_layer" aria-hidden="true" style="display:none">
    ...
</div>
```
```js
// 레이어 열림
$('.ctg_total_layer').show().attr('aria-hidden', 'false');

// 레이어 닫힘
$('.ctg_total_layer').hide().attr('aria-hidden', 'true');
```

## VoiceOver 테스트
<iframe width="100%" height="500" src="http://jsfiddle.net/hohoya33/37ja6u5o/embedded/result,html/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>


## 카테고리 메뉴 (depth. 1)
* aria-label="string" 간결한 설명
* role="navigation" 연결된 페이지를 탐색하기 위한 링크 모음
* 속성을 사용하기 전 HTML5 <nav> 요소를 먼저 고려

aria-label 속성을 장황하게 작성하면 안 됩니다. 자세한 설명은 aria-descibedby 속성을 사용합니다.
aria-label 속성은 현재 요소를 설명할 다른 참조(연결) 요소가 없는 경우에만 사용합니다.

레이블 요소(예를 들면 헤딩)가 있는 경우 aria-labelledby 속성으로 연결합니다. 레이블 요소(예를 들면 헤딩)가 없는 경우 aria-label 속성을 사용합니다.

```html
<ul class="ctg_mall_lst" role="navigation" aria-label="SSG 통합카테고리">
    <li class="ctg_top_mn">
        <a href="http://www.ssg.com" class="ctg_top_lnk">SSG.COM</a>
    </li>
</ul>
```


## 이전 카테고리 메뉴
* 예제) <a href="https://www.w3.org/TR/wai-aria-practices/examples/menubar/menubar-1/menubar-1.html" target="_blank">W3C Menubar</a>
* role="menubar"
* role="menuitem"
menubar 여러 menuitem 요소가 포함된 가로로 표시되는 메뉴
```html
<ul class="ctg_mall_lst" role="menubar" >
    <li class="ctg_top_mn">
        <a role="menuitem" aria-label="SSG.COM 바로가기" href="http://www.ssg.com" class="ctg_top_lnk">SSG.COM</a>
    </li>
</ul>
```


## 카테고리 메뉴 이슈
* 두 가지 용도로 사용되는 메뉴
* 해당 메뉴 클릭 시 링크 이동, 마우스 오버 시 하위 메뉴 열림
* 초점 이동 후, Enter 키 입력 시 링크 이동 되는 문제 (하위 메뉴 접근 불가)

## 해결 방법
* 하위 메뉴 열기/닫기 버튼을 별도로 추가 (기본 숨김)
* 키보드 포커스 접근 시(탭 키 입력) 버튼 노출


## 하위 메뉴 보기 버튼 추가
* a 태그 aria-label 몰 바로가기 설명 추가
* 키보드 포커스 접근 시, 하위 메뉴 보기 버튼 활성화

```html
...
<li class="ctg_top_mn">
    <a aria-label="SSG.COM 바로가기" href="http://www.ssg.com" class="ctg_top_lnk">SSG.COM</a>
    <!-- 하위 메뉴가 있으면 버튼 추가 -->
    <button style="display:none" aria-expanded="false" class="ctg_a11y_btn">
        <span class="blind">SSG.COM 하위 메뉴</span>
    </button>
</li>
```
```js
$('.ctg_mall_lst').on('focusin', '.ctg_top_mn', function(e){
    var welTarget = $(e.currentTarget);
    welTarget.find('>.ctg_a11y_btn').show();
});
```

## VoiceOver 테스트
<iframe width="100%" height="500" src="http://jsfiddle.net/hohoya33/dfewLs2x/embedded/result,js,html/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>


## 카테고리 하위 메뉴 (depth. 2)
* role="menubar" 일반적으로 가로로 표시되는 메뉴 모음
* role="menu" 사용자에게(실행) 선택 목록을 제공하는 유형 (세로방향)
* role="menuitem" menubar 또는 menu 모음에 포함된 옵션 항목

```html
<div class=" ctg_sub_area" aria-hidden="true">
    <ul class="ctg_sub_lst" role="menu">
        <li class="ctg_sub_mn">
            <a role="menuitem" aria-label="패션 바로가기" href="#" class="ctg_sub_lnk">패션</a>
            <button aria-expanded="false" class="ctg_a11y_btn">
                <span class="blind">패션 하위 메뉴 5개의 항목</span>
            </button>
        </li>
    </ul>
</div>
```


## 하위 메뉴 보기 버튼 이벤트
```js
$('.ctg_mall_lst').on('click', '.ctg_a11y_btn', function(e){
    var welTarget = $(e.currentTarget);
    var welParentList = welTarget.parent();

    if (welTarget.hasClass('on')) { //축소
        welParentList.find('>.ctg_sub_area').attr('aria-hidden', 'true');
        welTarget.removeClass('on').attr('aria-expanded', 'false');
    } else { //확장
        welParentList.find('>.ctg_sub_area').attr('aria-hidden', 'false');
        welParentList.siblings().find('.ctg_a11y_btn').removeClass('on').attr('aria-expanded', 'false').hide();
        welTarget.addClass('on').attr('aria-expanded', 'true');
    }
});
```

## 열렸을때 keydown 이벤트 추가
```js
$('.ctg_open_btn').on('click', function(e){
    var welTarget = $(e.currentTarget);

    if (welTarget.hasClass('on')) {
        $('.ctg_total_layer').hide().attr('aria-hidden', 'true').off('keydown.a11y');
    } else {
        $('.ctg_total_layer').show().attr('aria-hidden', 'false').on('keydown.a11y', function(e){
        //...
        });
    }
});
```

## 최종 결과물
<iframe width="100%" height="300" src="http://jsfiddle.net/hohoya33/3dyozftc/embedded/result,js,html/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>



# Modals

## 기존 방식

시각적으로 모든 동작이 명확하고 사용자는 대화 상자와 완벽하게 상호 작용

* 버튼 클릭 → 레이어 팝업 열림 → 레이어 팝업에 집중 하기 위해 배경을 어둡게 만듬
* 마우스 사용자는 레이어 팝업 이외의 나머지 부분과 상호 작용할 수 없음
* 작업이 끝나면 레이어 팝업 닫기


하지만 스크린리더 사용자의 경우 처음 부터 큰 장벽에 직면

버튼 클릭 → 레이어 팝업이 열린다는 정보 인지 불가
화면 위 레이어 팝업을 표시 했지만 여전히 초점은 배경 아래 페이지 부분에 위치

<iframe width="100%" height="600" src="http://jsfiddle.net/hohoya33/tegyap1x/embedded/result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>



마우스 사용자는 레이어 팝업이 열려 있는 동안 레이어팝업 이외의 나머지 부분과 상호 작용할 수 없음
버튼을 누른다. 팝업이 열린다. 닫기 버튼을 누른다. 팝업이 닫힌다.
대화 상자 열린다는 정보 인지 불가
단순히 페이지 위의 레이어팝업이 내용을 표시하지만 페이지의 나머지 부분은 완전히 작동합니다.
HTML, CSS 및 JS 에서 간단한 모달 윈도우 구성 요소를 만들었다 설명하기 위해

http://fiddle.jshell.net/hohoya33/tegyap1x/show/light/
Tab-key를 사용하여 버튼으로 이동하고 Enter 키를 누르면 모달 창이 나타납니다.
Tab-key 키를 다시 누르면 포커스가 모달 창 아래의 다음 링크로 이동합니다.
예상되는 동작은 다음 포커스 된 요소가 모달 창 내에있는 것입니다.
그러나 요소가 DOM 순서로 집중되고 모달 창은 문서의 맨 아래에 있기 때문에 아닙니다.
다음 화면 기록에서이를 볼 수 있습니다.



## 웹 접근성 지침
    <table>
        <colgroup>
        <col style="width:12%">
        <col style="width:88%">
        </colgroup>
        <thead>
            <tr>
                <td>원칙 2</td>
                <td>운용의 용이성</td>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td style="color:#13DAEC">2.1</td>
                <td style="color:#13DAEC">입력장치 접근성</td>
            </tr>
            <tr>
                <td style="color:#13DAEC">2.1.1</td>
                <td style="color:#13DAEC">키보드 사용 보장 - 모든 기능은 키보드만으로도 사용할 수 있어야 한다.</td>
            </tr>
            <tr>
                <td style="color:#13DAEC">2.1.2</td>
                <td style="color:#13DAEC">초점 이동 - 키보드에 의한 초점은 논리적으로 이동해야 하며 시각적으로 구별할 수 있어야 한다.</td>
            </tr>
        </tbody>
    </table>

    <table>
        <colgroup>
        <col style="width:12%">
        <col style="width:88%">
        </colgroup>
        <thead>
            <tr>
                <td>원칙 3</td>
                <td>이해의 용이성</td>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td style="color:#13DAEC">3.2 </td>
                <td style="color:#13DAEC">예측 가능성 (콘텐츠의 기능과 실행결과는 예측 가능해야 한다)</td>
            </tr>
            <tr>
                <td style="color:#13DAEC">3.2.1</td>
                <td style="color:#13DAEC">사용자 요구에 따른 실행 - 사용자가 의도하지 않은 기능 (새 창, 초점 변화 등)은 실행되지 않아야 한다.</td>
            </tr>
            <tr>
                <td>3.3</td>
                <td>콘텐츠의 논리성 (콘텐츠는 논리적으로 구성해야 한다)</td>
            </tr>
        </tbody>
    </table>



대화 상자 열린다는 정보 인지 불가 (예측 가능성)

마크업 위치에 따라 문서 탐색 시 링크(버튼)에 이어서 해당 대화 상자로 이동 되지 않음 (콘텐츠의 논리성)

(콘텐츠의 선형 구조) 콘텐츠는 논리적인 순서로 제공해야 한다.
콘텐츠는 보조 기술 사용자가 맥락을 이해할 수 있도록 논리적인 순서로 제공해야 한다.


대화 상자를 벗어나 배경 페이지로 초점 이동 (초점 이동)
대화 상자를 벗어나 배경 페이지로 이어지는 스크린리더 문서 탐색

(초점 이동) 키보드에 의한 초점은 논리적으로 이동해야 하며, 시각적으로 구별할 수 있어야 한다.

웹 페이지에서 제공하는 모든 기능을 키보드만으로 사용하는 경우에도 사용자 입력 간 의 초점 이동은 적절한 순서를 따라야 하며, 이 과정에서 콘텐츠는 조작이 불가능한 상태가 되거나 갑작스러운 페이지의 전환 등이 일어나지 않아야 한다.


## 접근성 향상
* 열기 버튼 클릭 → 레이어 팝업 오픈 시 적절한 피드백 제공
* 초점의 논리적 이동 → 레이어 팝업 내 초점 이동 후, 그 안에서 포커스 트랩
* 레이어 팝업 닫기 → 원래 위치했던 열기 버튼으로 초점 이동 










## DOM 위치 지정
* DOM에서 레이어 팝업을 배치해야 하는 일반적인 규칙 없음
* 요소에 초점을 맞출 수 있더라도 DOM 순서가 올바르지 않은 경우


일반적으로 대화 상자와 배경 요소를 모두 포함하는 탭 순서가 의미있는 토글러 버튼 가까이에 배치하는 것이 좋습니다.

모달 대화 상자의 경우 배경이 완전히 비활성화 role="dialog" 되어 위치가 중요하지 않을 수 있습니다.
하지만 지원하지 않는 장치와의 하위 호환성  role="dialog"(포커스를 잡아 내지 않음)을 위해
대화 상자를 토글러 단추 (non-modal dialogs 와 유사) 또는 페이지의 맨 아래에 배치하는 것이 현명 할 수 있습니다.


## HTML 5 대화 상자 요소
HTML 5에는 &lt;dialog&gt;컨테이너가 있습니다.
일부 브라우저에서는 아직 지원되지 않습니다.
따라서 접근성 측면에서 &lt;dialog&gt;(아직) 대신 사용자 정의 대화 상자를 사용하는 것이 좋습니다 .

## 일반 요구사항

* 잘 정립 된 모범 사례 <a href="https://www.w3.org/TR/wai-aria-practices/#dialog_modal" target="_blank">WAI-ARIA Authoring Practices: Dialog Modal (W3.org)</a>기반
* 대화 상자의 의미와 용도가 명확
* 대화 상자는 키보드 만 사용하고 화면 판독기 (Tab, Enter / Space, Esc, 화살표 키와 같은 기본 키의 합리적인 상호 작용)를 사용하여 작동 가능
* 초점은 열려있을 때 대화 상자 안에 있어야하며 닫을 때 다시 배치
* 대화 상자의 내용이 시작되는 곳과 끝나는 곳이 분명해야 한다.
* 대화 상자는 키보드 만 사용하고 화면 판독기 ()를 사용하여 작동 가능해야합니다.


각 대화 상자 토글 러에는 aria-expanded="false"속성이 있습니다.
 해당 값 ( true/ false)과 해당 대화 상자의 표시 여부는 JavaScript를 사용하여 전환됩니다.
 aria-expanded를 사용하여 요소 표시 확장 가능을 참조하십시오 .

대화 상자는 hidden속성을 사용하여 토글됩니다
대화 상자의 첫 번째 요소는 "대화 상자 닫기"버튼입니다. 레어어팝업 닫기 버튼 위치 (처음? 마지막?)

대화 상자를 열면이 단추에 포커스가 설정되고 캡션이 발표됩니다.

이 방법은 사용자가 즉시 대화에 있음을 즉시 알 수 있습니다.
버튼에는 보이는 SVG 아이콘 (비어있는 alt속성이 있는 이미지 )과 시각적으로 숨겨진 텍스트가 있습니다 (시각적으로 숨겨진 요소를 화면 밖으로 이동하여 숨기기 참조 ).

이 버튼을 클릭하면 대화 상자가 닫히고 대화 상자 토글 러 다시 버튼에 포커스가 설정되어 화면 판독기가 캡션을 알립니다.

이런 식으로 사용자는 대화 상자에서 빠져 나왔다는 것을 즉시 알 수 있습니다.
대화 상자의 마지막 요소는 "확인"버튼입니다.
이 버튼을 클릭하면 대화 상자가 닫히고 대화 상자 토글 러 다시 버튼에 포커스가 설정되어 화면 판독기가 캡션을 알립니다.


키보드 포커스는 첫 번째 및 마지막 버튼에서 가로 채기 Tab(및  Shift + Tab) 한 다음 포커스를 수동으로 앞뒤로 수동으로 이동하여 트랩됩니다 .
화면 판독기 커서는 대화 상자를 role="dialog"컨테이너와 컨테이너 로 둘러 쌈으로써 트랩됩니다
role="document".
role="dialog"컨테이너에 포커스 트랩 및 초점 모드에 남아 일부 화면 판독기를 강제로 (그래서 검색 가능한 콘텐츠를 읽을 수 없습니다).


키보드 포커스는 첫 번째 버튼과 마지막 버튼에서 탭(및 Shift + Tab)을 가로채서 포커스를 앞뒤로 수동으로 이동하여 캡처합니다.
화면 판독기 커서는 role="dialog" 컨테이너와 role="document" 컨테이너로 대화 상자를 둘러싸는 데 의해 갇힙니다.
role="dialog" 컨테이너는 포커스를 캡처하고 일부 화면 판독기가 포커스 모드로 유지되도록 합니다(따뜻한 콘텐츠를 읽을 수 없음).
role="document" 컨테이너는 찾아보기 모드로 전환을 다시 활성화합니다.









tabindex=”1″
문서 안에서 가장 먼저 초점을 받을 수 있습니다. 그러나 자연스러운 마크업 순서를 거스르기 때문에 주의해서 사용해야 합니다. 검색엔진 사이트에서 검색창에 사용하면 적합하지만(이 대신 autofocus=”autofocus” 속성이 더 적절할 듯 해요) 그 외 적합한 경우는 잘 떠오르지 않는군요.

tabindex=”0″
키보드 초점을 받을 수 없는 div, span과 같은 요소도 초점을 받을 수 있도록 만들어 줍니다. 초점을 받되 초점을 받는 순서는 자연스러운 마크업 순서를 따릅니다.

tabindex=”-1″
키보드 초점을 받을 수 있는 요소도 초점을 받을 수 없도록 만들어 줍니다. 초점을 받을 수 없기 때문에 “-1” 이외의 다른 음의 정수 값은 사실상 의미가 없습니다.


























