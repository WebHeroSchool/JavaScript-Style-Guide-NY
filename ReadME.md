### JavaScript Style Guide NY(c)

##### __1. Отдавайте предпочтение стрелочным функциям__
>##### Стрелочные функции делают синтаксис лаконичным и устраняют некоторые трудности с ним. Отдавайте предпочтение стрелочным функциям, вместо ключевого слова function, особенно для вложенных функций.
Честно говоря, я думал, что стрелочные функции хороши только тем, что они более краткие и приятны глазу. Оказывается, они также служат очень важной цели.

    //bad
    [1, 2, 3].map(function(x)){
    const y = x + 1;
    return x*y
    });

    //good
    [1, 2, 3].map(x) => {
    const y = x + 1;
    return x * y
    });
 
##### __2. Используйте шаблонные строки вместо конкатенации.__
>##### Используйте шаблонные строки (разделённые символом `) вместо конкатенации комплексных строк, особенно если используется несколько строковых литералов. Шаблонные строки могут занимать несколько строк.

    //bad
    function sayHi(name){
    return 'How are you, ' + name + '?';
    };

    //good
    function sayHi(name){
    return `How are you, ${name}?`;
    }; 

##### __3. Не используйте line continuations для длинных строк.__
>##### Не прерывайте строку внутри строкового литерала обратной косой чертой, в обычных или шаблонных строковых литералах. Несмотря на то, что ES5 допускает это, могут появится неприятные ошибки, если после косой черты окажется пробел. Это будет незаметно при чтении.
Google рекомендует объединять более длинные строки (как показано ниже), а руководство по стилю Airbnb, рекомендует ничего с ними не делать и позволить длинным строкам продолжаться столько, сколько им нужно.

    //bad
    const longString = 'This is a very lot of string that \
    far exceeds  the 80 column limit. It unfortunately \
    contains long stretches of spaces due  to how the \
    continued lines are indented.';

    //good
    const longString = 'This is a very lot of string that ' +
    'far exceeds  the 80 column limit. It does not contain ' +
    'long stretches of spaces since the concatenated' +
    'strings are cleaner';

##### __4. Используйте одинарные кавычки, а не двойные__
>##### Обычные строковые литералы разделяются одинарными кавычками (‘), а не двойными (“).
>##### __Совет:__ если строка содержит символ одинарной кавычки, попробуйте использовать шаблонные строки, чтобы не экранировать кавычки.
    //bad
    let directive = "No identification of self or mission."
    let saying = 'Say it ain\u0027t so.';

    //good
    let directive = 'No identification of self or mission.'
    let saying = `Say it ain't so.`;

##### __5. Имена констант должны быть ЗАГЛАВНЫМИ_БУКВАМИ и через нижнее подчёркивание__
>##### Для неизменных величин — НЕИЗМЕННО_ПРАВИЛО: всё заглавными, а слова через подчёркивание.
Если вы абсолютно уверены, что переменная не должна изменяться, вы можете указать ее, написав имя константы. Это подчёркивает неизменность константы, во всём коде.
    //bad
    const number = 5;

    //good
    const NUMBER = 5;

##### __6. Не используйте eval()__
>##### Не используйте eval или функцию (…string) конструктор (кроме загрузчиков кода). Эти функции потенциально опасны и просто не работают в средах CSP.
На [страничке MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/eval) для eval() даже есть пометка — “Don’t use eval!”

    //bad
    let obj = { a : 20, b : 30};
    let propName = getPropName(); \\return "a" or "b"
    eval('var result = obj.' + propName);

    //good
    let obj = { a : 20, b : 30};
    let propName = getPropName(); \\return "a" or "b"
    let result = obj [propName];

##### __7. Одна переменная за раз__
>##### Каждое объявление локальной переменной объявляет только одну переменную: такие объявления, как let a = 1, b = 2; не используются.

    //bad
    let a = 1, b = 2, c = 3;

    //good
    let a = 1;
    let b = 2;
    let c = 3;

##### __8. Не используйте var__
>##### Объявляйте все переменные с помощью const или let. Используйте const по умолчанию, если переменная не требует переназначения. Ключевое слово var не должно использоваться.

    //bad
    var example = 63;

    //good
    let example = 63;

##### __9. Горизонтальное выравнивание не рекомендуется (но и не запрещается)__
>##### Такая практика допустима, но, в целом, не рекомендуется «стилем» Google. Не следует продолжать горизонтальное выравнивание даже в местах, где оно уже применялось.
Горизонтальное выравнивание — это практика добавления дополнительных пробелов в коде, чтобы определённые значения, отображались непосредственно под другими значениями в предыдущих строках.

    //bad
    {
        tiny:    42,
        longer:  435,
    }

    //good
    {
        tiny: 42,
        longer: 435,
    }

##### __10. Используйте пробелы вместо табуляции__
>##### Помимо символа конца строки, символ горизонтального пробела ASCII (0x20), единственный разделитель, который следует использовать в любом месте исходного файла. Это означает, что символы табуляции не используются для отступов.

   //bad
   function foo(){
       let name;
   }
   //bad
   function foo(){
    let name;
   }
    //good :)
   function foo(){
     let name;
   }
