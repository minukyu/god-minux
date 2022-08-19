# god-minux
Android Test Application

## Naming Conventions
### Common
1. 한 단어 내에서는 대소문자 변경은 없다   
   ex) InVisible -> Invisible
2. 약어는 대문자를 사용한다   
   ex) Api -> API, Url -> URL   
3. 클래스 이름은 UpperCamelCase 로 작성한다   
   ex) SignInActivity, ImageUploaderService
4. Resources 이름은 lowercase_underscore로 작성한다  
   ex) activity_
<br/>
<br/>
   
### Method
메서드명은 동사구(동사원형 시작)을 사용한다   
* show : Invisible한 것을 Visible 하게 바꾸는 동작
* check : 어떤 것을 확인한 후 boolean 또는 값으로 반환하는 동작
* is : 어떤 것인지 확인한 후 boolean으로 반환하는 동작
* has: 어떤 것을 가지고 있는 확인 후 boolean으로 반환하는 동작
* handle: 어떤 이벤트나 행위에 대한 처리를 하는 동작
* on : 이벤트를 발생시키는 동작
<br/>
<br/>
   
### Layout
- `<WHAT>_<WHERE>`

| Prefix | 설명 |
| ------------- | ------------- |
| `activity_` | Activity에서 쓰이는 layout |
| `fragment_` | Fragment에서 쓰이는 layout |
| `dialog_` | Dialog에서 쓰이는 layout |
| `view_` | CustomView에서 쓰이는 layout |
| `item_` | RecyclerView, GridView, ListView등에서 ViewHolder에 쓰이는 layout |
| `layout_` | `<include/>`로 재사용되는 공통의 layout |
   
*EX.*  `activity_main`: MainActivity의 layout, `item_my_scooter` : 내스쿠터 목록에서 item layout
<br/>
<br/>
   
### ID
- `<WHAT>_<DESCRIPTION>`
- View의 대문자를 축약하여 `WHAT` 의 Prefix 로 사용한다

| View | Prefix |
| ------------- | ------------- |
| TextView | `tv_` |
| ImageView | `iv_` |
| CheckBox | `cb_` |
| RecyclerView | `rv_` |
| EditText | `et_` |
| ProgressBar | `pb_` |
| FrameLayout | `fl_` |
| NestedScrollView | `nsv_` |
| View | `view_` |
| Switch | `switch` |
| MyCustomView | `my_custom_view` |
| YourView | `your_view` |

*EX.* `tv_name` : 이름에 대한 TextView, `iv_scooter` : 스쿠터 ImageView
<br/>
<br/>
   
### Drawable
- `<WHAT>(_<WHERE>)_<DESCRIPTION>(_<SIZE>)`
- 이미지가 여러군데에서 활용될 경우, `<WHERE>`는 생략 가능하다.
- 이미지의 크기가 1개밖에 없는 경우, `<SIZE>`는 생략 가능하다.

| Prefix | 설명 |
| ------------- | ------------- |
| `btn_` | 버튼으로 쓰이는 이미지 |
| `ic_` | 버튼이 아닌 화면에 보여지는 이미지 |
| `bg_` | 버튼이 아닌 화면에 보여지는 이미지 |
| `img_` | 실제사진이거나 아이콘형태가 아닌 일러스트형태의 이미지 |
| `div_` | divider로 활용되는 이미지 |
<br/>
   
#### Background
- 배경색이 pressed상태에 따라서 white -> sky_blue로 변하는 경우는 `bg_white_to_sky_blue.xml`로 한다.
- 배경이 white색의 24dp로 테두리를 그리는 경우는 `bg_white_radius_24dp.xml`로 한다.
- 배경이 투명하며 배경의 선만을 sky_blue색의 8dp로 테두리를 그리는 경우는 `bg_stroke_sky_blue_radius_8dp.xml`로 한다.
<br/>
   
#### 기타
- `img_xxx`의 경우 파일의 크기가 큰경우가 많으므로 [tinypng](https://tinypng.com/)에서 파일크기를 줄인뒤에 추가 해주어야 한다. (GitHub [imgbot](https://github.com/marketplace/imgbot)을 사용한다면 생략 가능)
  - 대부분 용량이 큰 파일이어서 xxxhdpi에만 넣는다. 

*EX.*
- `btn_call_normal.png`: 전화걸기 버튼 이미지
- `btn_call_pressed.png`: 전화걸기 버튼 눌렸을때의 이미지
- `btn_call.xml`: 전화걸기 버튼 이미지의 selector xml
- `ic_dealer_gift.png`: 딜러가 보내준 기프티콘을 보여줄때 표시되는 이미지
- `img_splash_chart.png`: 스플래시 화면에서 보여지는 차트 이미지
<br/>
<br/>
   
### Dimension
- `<WHERE>_<DESCRIPTION>_<WHAT>`
- 여러 군데에서 재사용되는 개념이라면 변수로 정의해서 `@dimen/xxx`와 같이 사용
- 그렇지 않다면 명시적으로 `16dp`와 같이 작성
<br/>
   
#### Margin/Padding
- 대부분의 `margin/padding`은 아래 정의된 `space_xxx`로만 사용되도록 한다.
```xml
<dimen name="space_x_small">8dp</dimen>  
<dimen name="space_small">12dp</dimen>  
<dimen name="space_median">16dp</dimen>  
<dimen name="space_s_large">18dp</dimen>  
<dimen name="space_large">20dp</dimen>  
<dimen name="space_x_large">24dp</dimen>
```
- 그외에 특정 화면에서 위의 값을 따르지 않는경우, `<WHERE>_<DESCRIPTION>_<WHAT>`의 규칙으로 만든다.
```xml
<dimen name="register_car_item_car_model_start_padding">40dp</dimen>  
<dimen name="register_car_item_grade_start_padding">56dp</dimen>  
<dimen name="register_car_item_car_detail_start_padding">72dp</dimen>
```
- 2번이상 쓰이는경우는 dimen에 정의해주는 것을 강제하고 1번만 쓰이는경우에는 xml코드에 넣어도 괜찮은것으로 한다.
<br/>
   
#### Height/Size
- 높이만 지정할때는 `height`, 1:1 비율로 같은 값이 들어갈때는 `size`로 한다.
```xml
<dimen name="toolbar_height">56dp</dimen>
<dimen name="register_input_view_default_height">280dp</dimen>  
<dimen name="register_input_view_collapse_height">200dp</dimen>
<dimen name="dealer_profile_image_size">48dp</dimen>
```
<br/>
<br/>
   
### String
- `<WHERE>_<DESCRIPTION>`
- 특정화면에서 쓰이는 텍스트 아니라 여러군데에서 공통으로 재사용될 텍스트라면 `all_<DESCRIPTION>`로 이름을 짓는다

*EX.*
- `permission_dialog_camera_title`: 카메라권한을 요구하는 Dialog의 제목
- `permission_dialog_camera_description`: 카메라권한을 요구하는 Dialog의 설명내용
- `all_yes`: 네
- `all_ok_understand`: 여러 Dialog에서 `네, 알겠습니다`로 쓰이는 공통의 텍스트
<br/>
   
#### 문단
- 문단형태의 긴 문자열로 개행(`\n`)이 필요한 경우, `\n`을 다음줄의 앞에 쓴다.
```xml
 <string name="sample">문단 첫번째줄
        \n문단 두번째줄
        \n문단 세번째줄</string>
````
<br/>
<br/>
   
### Theme/Style
- Theme는 `theme.xml`, Style은 `style.xml`에 추가한다.
- 1번만 쓰이는 경우에는 style을 만들지 않는다.
(단, 앞으로 재사용될 가능성이 높은 경우에는 가능)
- 모든 style은 parent를 갖는다.
- style의 이름은 parent의 이름패턴과 맞춘다
```xml
<style name=”Widget.Alley.Button” parent=”@style/Widget.AppCompat.Button”>
...
</style>
```
- parent에서 일부 내용만 수정하고자 하는경우, parent이름 뒤에 달라진 내용의 내용을 추가해준다
```xml
<style name="Theme.Alley.Transparent" parent="Theme.Alley">
...
</style>
```
- Base Style과 Theme의 경우는 앞에 `Base`를 붙인다.
```xml
<style name="Base.Theme" parent="..." />
<style name="Base.Theme.Transparent">...</style>
<style name="AlleyTheme" parent="Base.Theme">...</style>
<style name="AlleyTheme.Transparent" parent="Base.Theme.Transparent" />

<style name="Base.TextAppearance.Alley" parent="...">...</style>
<style name="Base.TextAppearance.Alley.Headline">...</style>
<style name="TextAppearance.Alley.Headline1" parent="Base.TextAppearance.Alley.Headline">...</style>
<style name="TextAppearance.Alley.Headline2" parent="Base.TextAppearance.Alley.Headline">...</style>
```
<br/>
<br/>
   
### Attribute
- Attribute이름은 `camelCase`로 한다.
```xml
<attr name="numStars" format="integer" />
```

- 기존에 정의되어있는 `android:xxx`와 같은 동작을 유도하는 경우, 이 tag를 재사용한다.
```xml
<declare-styleable name="SpannedGridLayoutManager">  
 <attr name="android:orientation" />  
...
</declare-styleable>
```
<br/>
<br/>
   
### 기타
- `android:xxxLeft/android:xxxRight` 대신 `android:xxxStart/android:xxxEnd`로 사용한다.(기타 Left/Right로 사용하는 부분 모두)
<br/>
<br/>
<br/>
    

## Git flow
### Branch
- main <br/>
  모든 브랜치들의 base 브랜치 <br/>
  기능테스트/QA 는 main 브랜치에 목적브랜치가 병합할 때마다 진행한다 <br/>
  <br/>
  
- feature <br/>
  기능개발 브랜치 <br/>
  main에서 분할, 기능개발이 끝난 후 다시 main 으로 merge 하며 해당 브랜치는 삭제한다 <br/>
  feature/{xxxxxx} => 브랜치 이름은 모듈명으로 한다 <br/>
  ex) feature/login, feature/ride <br/>
  <br/>
  
- fix <br/>
  기능수정 브랜치 <br/>
  main에서 분할, 기능수정이 끝난 후 다시 main 으로 merge 하며 해당 브랜치는 삭제한다 <br/>
  fix/{xxxxxx} => 브랜치 이름은 모듈명으로 한다 <br/>
  ex) fix/signin, fix/map <br/>
  <br/>
  
- release <br/>
  배포브랜치 <br/>
  main 브랜치에서 QA 진행 후 main에서 분할, 유저에게 배포하는 브랜치. 다시 main 으로 병합하지 않고 형상고립시킨다 <br/>
  release/{버전명} => 브랜치 이름은 버전명으로 한다 <br/>
  ex) release/1.0.0 <br/>
  <br/>
  
- hotfix <br/>
  긴급수정 브랜치 <br/>
  (우케함..? 태우짱 도와줘잉) cherry-pick? <br/>
<br/>
<br/>


**pr 전략**
<br/>
모든 pr은 코드리뷰를 받기 위해 개발자들에게 알립니다.<br/>
main브랜치에 merge할 때는 반드시 미누스과 데릭의 코드리뷰(approve)가 진행되고 난 이후 진행합니다.<br/>
hotfix 브랜치의 경우 빠르게 모든 개발자들에게 사실을 알리고 미누스, 데릭 중 1인의 코드리뷰(approve)가 진행된 이후 머지합니다.<br/>
모든 pr은 작성자가 merge 함을 원칙으로 합니다.
<br/>
<br/>

**좋은 코드리뷰를 위해**
<br/>
무작정 코드리뷰를 요청하는 것은 좋지 못할 수 있습니다. 내가 만든 것을 남이 잘 봐주기 위해서는 자신의 노력이 많이 필요합니다.<br/>
코드를 잘 설명하기 위해 주석을 사용할 수도 있고, 사진같은 첨부자료를 사용할 수도 있고, 미팅을 요청해서 설명하는 시간이 있을 수도 있습니다.<br/>
<br/>
또한 코드리뷰를 요청해도 리뷰어는 모든 코드를 이해할 수 없음을 인정해야 합니다.<br/>
그리고 실력에 상관 없이 궁금한 점이 생기거나 필요한 것이 있다면 가감없이 이야기 해야 우리들의 성장에 도움이 될 수 있습니다.<br/>
<br/>
코드리뷰의 목적은 실수 방지, 코드의 팀적인 합의, 히스토리 공유 등등이 있지만 이번 프로젝트에서 가장 중요한 것은 서로의 실력 향상을 위함입니다.<br/>
<br/>
그래서 언제든 코드리뷰 혹은 어려운 점에 대한 해결을 요청하면 가능한한 빠른 시간에 도와주려고 노력할 것이니 편하게 이야기해주면 좋을 것 같습니다 :)
<br/>
## 커밋 룰

커밋은 기능이 문제 없이 동작하는 최소한의 단위로 진행하게 됩니다. <br/>
물론 이 기준이 모르겠고 명확하지 않을 수 있습니다. 그렇지만 한번 해보고 각자만의, 우리만의 커밋 룰을 만들어가면 좋을 것 같습니다 :)<br/>

### 커밋 컨벤션

'{type}: {xxxx: 주제} /n <br/>
{xxxxxxxxxxxxxxxxxxx: 커밋 세부 사항} /n <br/>
#{1: 이슈넘버}
<br/>
<br/>

### 커밋 타입

- feature <br/>
  기능에 대한 커밋입니다.

- fix <br/>
  수정에 대한 커밋입니다.

- design <br/>
  스타일(css)에 대한 커밋입니다.

- refactor <br/>
  코드를 리팩토링 했을 때 커밋입니다.

- chore <br/>
  기타 유저들에게 영향이 가지 않지만 변경되는 것들의(버전 수정, 문서 수정 등등) 커밋입니다.

- wip <br/>
  working in progress의 약자로 특정 기능을 완료하지 못했지만 중간 저장을 위해 사용하는 커밋입니다.

## issue

이슈를 발급하면 프로젝트에 이슈 사항에 대한 칸반보드를 함꼐 수정합니다.<br/>
issue를 발행하는 이유는 다른 개발자가 어떤 일을 어느정도 했는지 체크를 하기 위해서 사용합니다.<br/>

## fin

모든 코드는 코드리뷰를 진행하고 배포될 예정입니다.<br/>
코드리뷰를 하면 서로의 실력 향상에도 도움이 되지만 누군가 실수를 했을 때 그사람만의 잘못이 아닌 리뷰어의 문제도 함께 있다는 의미이기도 합니다!<br/>
<br/>
그러니 코드를 짜면서 생기는 다양한 문제는 우리가 함께 해결할 거니까 걱정하지말고 마음 껏 코딩해보고 마음껏 실수해보고 마음껏 망쳐보는 경험이 되길 바랍니다!
