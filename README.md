<h1>DOM Events and Event Listeners</h1>

الـDOM events هي إجراءات تحدث في المتصفح. والـ events هي ما يسمح لك بجعل مواقع الويب تفاعلية.

يتم بدء بعض DOM events بواسطة المستخدم، مثل النقر أو تحريك الماوس أو الكتابة على لوحة المفاتيح. والبعض الآخر يتم تشغيله بواسطة المتصفح، كما هو الحال عند انتهاء تحميل الصفحة.


<h2>Difference Between Event Listener and Event Handler</h2>

الـevent listener هو طريقة تتيح لك معرفة وقت وقوع حدث ما. يسمح لك "بالاستماع" أو مراقبة DOM events.  وبهذه الطريقة، عندما يحدث event ما، يمكنك القيام بشيء ما.

الـevent handler هو استجابة للـ event. إنها function يتم تشغيلها عند وقوع event ما.

على سبيل المثال، يمكنك إرفاق event listener بزر يتيح لك معرفة متى يقوم المستخدم بالنقر فوق هذا الزر. ثم يمكنك كتابة event handler (function) يطبع شيئًا ما على الشاشة في أي وقت يحدث فيه click event.

في هذه الحالة، event listener هو الذي يُعلم تطبيقك عند حدوث نقرة ثم يقوم بتشغيل الاستجابة. والاستجابة (الـ function التي يتم تشغيلها عند حدوث النقر) هي مثال لـ event handler.


<h2>Three Ways to Register Events in JavaScript</h2>

فيما يلي ثلاث طرق مختلفة يمكنك من خلالها الاستماع إلى DOM events والرد عليها باستخدام JavaScript.


<h3>Using inline event handlers:</h3>

يتم ذلك عند إضافة event listener كـ attribute لـ elements HTML.
في الأيام الأولى لـ JavaScript، كانت هذه هي الطريقة الوحيدة لاستخدام events. انظر المثال أدناه:
```ruby
/*Example of using an inline event handler*/

<button onclick="alert('Hello')">Click me!</button>
```

<h3>Using on-event handlers:</h3>

يمكنك استخدامها عندما يحتوي الـ element على event handler واحد فقط. عند إضافة أكثر من event handler باستخدام هذه الطريقة، سيتم تشغيل event handler الأخير فقط، لأنه سيتجاوز handlers الأخرى التي سبقته.
```ruby
/* An example of using an on-event handler*/

<button>Click me!</button>

<script>
  const myButton = document.querySelector('button')
	
  myButton.onclick = function() {
    console.log("Run first handler")
  }
	
  myButton.onclick = function() {
    console.log("Run second handler")
  }
</script>
```
![image](https://github.com/amzan1/DOM-Event/assets/105777472/f4e1b00b-682d-447d-a229-184ab1df3e9a)

 

كما ترون من النتيجة في console ، يقوم المتصفح بتشغيل التعليمات البرمجية لـ event handlerالثاني فقط.

<h3>Using the addEventListener method:</h3>

تتيح لك هذه الطريقة إرفاق أكثر من event handlers واحد لـ element ما. وسيتم تنفيذها بالترتيب الذي تمت إضافتها به.

كقاعدة عامة، يجب عليك الالتزام بـ addEventListener، إلا إذا كان لديك سبب مقنع لعدم القيام بذلك.
يأخذ الأسلوب addEventListener قيمتين. الأول هو الـ event الذي تريد الاستماع إليه، والثاني هو event handler وهو function التي تريد تشغيلها عند وقوع event.
```ruby
<!-- An example of using the addEventListener method -->

<button>Click me!</button>

<script>
  const myButton = document.querySelector('button')
	
  myButton.addEventListener('click', function() {
    console.log("Run first handler")
  })
	
  myButton.addEventListener('click', function() {
    console.log("Run second handler")
  })
</script>
 ```
![image](https://github.com/amzan1/DOM-Event/assets/105777472/f533c7b2-c09d-4fdb-b69d-4cfc26278987)


<h2>The Event Object</h2>

هذا هو JavaScript object الذي يمرره المتصفح كوسيطة event handler function في أي وقت يحدث فيه event. يتضمن object بعض الخصائص والأساليب المفيدة مثل ما يلي:

type:

نوع الـ eventالذي حدث (مثل click ، أو mouseover ، أو keydown ، وما إلى ذلك).

target:

الـ element الذي وقع عليه الـ event.

clientX and clientY:

الإحداثيات الأفقية والرأسية لمؤشر الماوس وقت وقوع الـ event.

preventDefault():

يمنع الإجراءات الافتراضية المرتبطة بالـevents مثل منع إرسال النموذج في eventالإرسال.

stopPropagation():

يمنع الـ event من الانتشار عبر DOM. المزيد عن ذلك لاحقًا.


<h2>Types of Events</h2>

هناك العديد من أنواع DOM events المختلفة التي تتيح للمتصفحات الاستماع إليها. وفيما يلي عدد من events الشائعة.

<h3>Mouse events:</h3>

Click:

عند النقر فوق الـ element.

dbclick:

عند النقر المزدوج على الـ element.

mouseover:

عندما يدخل مؤشر الماوس إلى الـ element.

mouseleave:

عندما يترك مؤشر الماوس الـ element.

mousedown:

عند الضغط بالماوس لأسفل فوق element ما.

mouseup:

عندما يتم تحرير الماوس فوق element ما.


<h3>Keyboard events:</h3>

keydown:

عند الضغط على أحد المفاتيح الموجودة على لوحة المفاتيح.
keyup: 
عندما يتم تحرير أحد المفاتيح الموجودة على لوحة المفاتيح.

keypress:

عند الضغط على مفتاح ويظهر المفتاح الفعلي الذي تم الضغط عليه. لاحظ أن هذا الحدث لا يتم تشغيله لجميع المفاتيح، وخاصة المفاتيح غير القابلة للطباعة.

<h3>Form events:</h3>


submit:

عند تقديم الـ form.

input:

عندما تتغير قيمة حقل الإدخال.

change: 

عندما تتغير قيمة element الـ formوتفقد التركيز.

<h3>Window events:</h3>


load:

عندما ينتهي المتصفح من تحميل الصفحة.

unload:

عندما يغادر المستخدم الصفحة.

resize:

عندما يتم تغيير حجم نافذة المتصفح.

scroll:

عندما يقوم المستخدم بالتمرير خلال المستند.

<h2>Event Flow in JavaScript</h2>

عند وقوع JavaScript event ، يتم نشر الـ event أو انتقاله إما من الهدف الذي وقع فيه الـ event إلى الـ element الخارجي في DOM أو العكس.

على سبيل المثال، لنفترض أنك قمت بالنقر فوق زر في الصفحة. من خلال النقر على الزر، تكون قد قمت أيضًا بالنقر فوق parent element الخاص به وأي element يوجد الزر بداخله ضمن التسلسل الهرمي لـ DOM.

