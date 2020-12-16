# basics-of-JS-language

<p align="center"><img src="https://scontent-sea1-1.xx.fbcdn.net/v/t1.0-9/127142444_1292068024474820_2603593254457549792_n.jpg?_nc_cat=102&ccb=2&_nc_sid=09cbfe&_nc_ohc=lNfmQJfCcfsAX8gUG9A&_nc_ht=scontent-sea1-1.xx&oh=3c479f78bd67447aba87782e3e0b6fe8&oe=5FEEA4FC" width="200" alt="Агеев Дмитрий"></p>

### "Есть всего две бесконечные вещи - Вселенная и изучение JavaScript. Хотя насчет вселенной я не уверен", - кажется, Альберт Эйнштейн что-то такое говорил)
    

## Функции, объекты: определение и вызов.

Функция — это именованная часть кода. Она позволяет описать участок кода в одном месте и затем обращаться к нему из другого. Это структурирует код и делает его читаемее. Но главное: функции позволяют использовать один и тот же код повторно.
Функция имеет имя и тело. Чтобы объявить функцию, пишут ключевое слово function, имя функции с круглыми скобками, а затем — её тело внутри фигурных скобок:

кодJAVASCRIPT

function имяФункции() {
    // тело функции
} 

Опишем функцию, которая рисует в консоли котёнка:

кодJAVASCRIPT

function consoleKitten() {

    let a = '  Λ _ Λ';
    let b = ' (=චᆽච=)==∫';
    let c = '   ˉ ˉ   ˉ ˉ';

    console.log(a); 
    console.log(b); 
    console.log(c);
} 
Функция рисования котёнка готова. Но котёнка в консоли пока не оказалось. Дело в том, что пока мы только описали функцию, но не запустили её. Чтобы тело функции выполнилось, функцию нужно вызывать. Для этого пишут её имя и затем ставят круглые скобки:

кодJAVASCRIPT

consoleKitten();

//  Λ _ Λ
// (=චᆽච=)==∫
//  ˉ ˉ ˉ ˉ 
Параметры функции
Параметры — это переменные, которыми может пользоваться только сама функция.
В коде тела функции прописываются действия с ними, как с обычными переменными.
Объявим функцию keepScore, которая сообщает итог матча. Она принимает два параметра — ours и theirs. Это число голов, забитое «нашими» и соперником.

кодJAVASCRIPT

function keepScore(ours, theirs) {

    // Проверим, забили наши больше голов или нет:
    if (ours > theirs) {
        console.log('Выиграли! 😃 Счёт ' + ours + ':' + theirs);

        // Если наши забили не больше голов,
        // то может столько же? Проверим:
    } else if (ours === theirs) {
        console.log('Ничья. 😐 Счёт ' + ours + ':' + theirs);

        // Если два предыдущих условия не выполнены,
        // стало быть, наши забили меньше голов :(
    } else {
        console.log('Продули... 😢 Счёт ' + ours + ':' + theirs);
    }
} 
Результат матча можно указать прямо в коде вызова:

кодJAVASCRIPT

keepScore(10, 8);
// функция keepScore подставит вместо переменной ours значение 10,
// а вместо theirs — значение 8. Затем выполнит все проверки и выдаст результат:
// 'Выиграли! 😃 Счёт 10:8' 
При вызове функции можно передать ей как параметры значения переменных. Для этого параметры перечисляют внутри круглых скобок при вызове:
Скопировать кодJAVASCRIPT
let a = 10; 
let b = 8;

keepScore(a, b); 
Возвращаемое значение
Функции могут намного больше, чем просто выводить сообщения в консоль. Самое главное, что функция по своему алгоритму превращает исходные данные, такие как параметры или аргументы, в результаты.
Функциям обычно поручают преобразовывать данные, но не определять, где они применяются — в консоли, во всплывающем окне или где-то ещё. Преобразованные данные возвращают скрипту для дальнейшего использования.
Возвращаемые значения указывает оператор return:

кодJAVASCRIPT

function sayHello(name) {

    // Преобразуем входные данные
    let greeting = 'Привет, ' + name;
    // Возвращаем результат
    return greeting;    
}

let alisaGreeting = sayHello('Алиса');

console.log(alisaGreeting); // "Привет, Алиса" 
В примере функция добавляет к строке 'Привет, ' параметр, который мы передаём при вызове ('Алиса'). Получившаяся строка должна стать результатом работы функции. На это указывает оператор return. Он сообщает, чтó должно стать результатом работы функции.
Когда функция вызвана, мы получаем этот результат и решаем, что с ним делать. В примере мы сначала записали его в переменную, а затем вывели в консоль.
Приветствие может понадобиться снова. Не обязательно в консоли, например, в интерфейсе сайта. Мы легко сможем вызвать sayHello ещё раз.
Как прервать работу функции
Директива return означает выход из функции. В теле функции код ниже строки с оператором return не исполняется:

кодJAVASCRIPT

function sayHello(name) {    

    let greeting = 'Привет, ' + name;    
    return greeting;

    // этот код не выполнится,
    // так как он после return    
    console.log(greeting);
} 
А return без значения просто говорит функции «хватит»:

кодJAVASCRIPT

function sayHello(name) {

    if (name === '') {
        return; // если имя — пустая строка, выйдем из функции
    }

    let greeting = 'Привет, ' + name;    
    return greeting;
} 
Если передать такой функции пустую строку, она прекратит работу. Функция при этом вернёт специальное значение undefined:

кодJAVASCRIPT

let emptyGreeting = sayHello('');

console.log(emptyGreeting); // undefined 


## Объекты.

Объекты — важнейшая концепция JavaScript. Они представляют собой структуру для хранения данных: чисел, строк, массивов, других объектов и даже функций. Объекты применяют повсеместно, потому что они позволяют организовать любой набор данных в иерархическую структуру. Мы будем ещё много говорить об объектах и часто ими пользоваться. Поэтому прочитайте этот урок очень внимательно.
Объекты состоят из пар «ключ — значение». Значение — это данные, которые мы хотим записать. Значением может быть строка, число, булево значение, массив, другой объект или функция. Ключ — это уникальное имя этого значения. Ключ играет ту же роль, что и имя переменной. По нему мы можем обратиться к значению.
Создадим объект myObject с четырьмя ключами:

let myObject = {

    stringKey: 'значение',
    numberKey: 4,
    booleanKey: true,
  methodKey: function consoleKitten() {
  
        console.log('kitten!');
    }
}; 

Пары «ключ — значение» делятся на два типа: свойства и методы.
Если значение представляет собой функцию, такую пару называют методом.
Если значение — строка, число, булево значение, массив или объект, такую пару называют свойством.

let myObject = {

    stringKey: 'значение', // это свойство
    numberKey: 4, // это тоже свойство
    booleanKey: true, // и это свойство
  
  methodKey: function consoleKitten() {   // а вот это метод
  
        console.log('kitten!');
    }
}; 
Создав объект, мы наполняем его свойствами и методами. Затем пользуемся ими — вызываем методы и получаем доступ к свойствам. Чтобы получить доступ к свойству, его имя записывают через точку после имени объекта:

myObject.stringKey; 

Другой способ обратиться к свойству — указать имя свойства в кавычках и в квадратных скобках:

myObject['numberKey']; 

Если объект уподобить ящику с инструментами, то фигурные скобки — стенки ящика. После них нужна точка с запятой. Лежащие внутри ящика инструменты — пары «ключ-значение» — разделены запятыми. Это очень важно, без запятой ничего работать не будет.

## Заключение

JavaScript — язык программирования, который используется в вебе. Эта тема была о программировании: вы изучили типы данных, переменные, условия, циклы. Всё это — концепции языка.
Чтобы применять это в реальных проектах, нужно научиться связывать JavaScript с элементами веб-страницы и браузера. Это позволит вам управлять сайтом из JS-кода

