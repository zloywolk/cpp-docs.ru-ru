---
title: 'Синтаксис описания формата: функции printf и wprintf | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- format specification fields for printf function
- printf function format specification fields
- flag directives, printf function
- type fields, printf function
- width fields, printf function
- precision fields, printf function
ms.assetid: 664b1717-2760-4c61-bd9c-22eee618d825
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cfb885a5d29c26f4a40d5b93490a06652eff1ffc
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216676"
---
# <a name="format-specification-syntax-printf-and-wprintf-functions"></a>Синтаксис описания формата: функции printf и wprintf

Различные функции `printf` и `wprintf` принимают строку формата и необязательные аргументы и создают форматированную последовательность символов для выходных данных. Строка формата не содержит ни одной или содержит несколько *директив*, которые являются либо литеральными символами для выходных данных, либо закодированными *спецификациями преобразования*, описывающими способ форматирования аргумента в выходных данных. В этом разделе описывается синтаксис, используемый для кодирования спецификаций преобразования в строке формата. Список этих функций см. в разделе [Потоковый ввод-вывод](../c-runtime-library/stream-i-o.md).

Спецификация преобразования состоит из необязательных и обязательных полей, имеющих следующий вид:

**%**[[*flags*](#flags)][[*width*](#width)][.[*precision*](#precision)][[*size*](#size)][*type*](#type)

Каждое поле спецификации преобразования — это символ или число, указывающее конкретный параметр формата или описатель преобразования. Обязательное поле *type* определяет тип преобразования, которое применяется к аргументу. Необязательные поля *flags*, *width* и *precision* управляют дополнительными аспектами формата, такими как начальные пробелы или нули, выравнивание и отображаемая точность. Поле *size* указывает размер использованного и преобразованного аргумента.

Базовая спецификация преобразования содержит только символ процента и символ *type*. Например, `%s` определяет преобразование строк. Чтобы вывести символ знака процента, используйте `%%`. Если за символом процента следует символ, который не имеет смысла в поле формата, вызывается обработчик недопустимого параметра. Дополнительные сведения см. в разделе [Проверка параметров](../c-runtime-library/parameter-validation.md).

> [!IMPORTANT]
> Для обеспечения безопасности и стабильности убедитесь, что строки спецификации преобразования не определяются пользователем. Например, рассмотрим программу, которая предлагает пользователю ввести имя и сохраняет введенные данные в строковой переменной с именем `user_name`. Для печати переменной `user_name` не используйте следующий код:
>
> `printf( user_name ); /* Danger!  If user_name contains "%s", program will crash */`
>
> Вместо этого используйте следующий код:
>
> `printf( "%s", user_name );`

<a name="type"></a>

## <a name="type-conversion-specifier"></a>Спецификатор преобразования типов

Символ спецификации преобразования *type* определяет, как должен интерпретироваться соответствующий аргумент: как символ, строка, указатель, целое число или число с плавающей запятой. Символ *type* — единственное обязательное поле спецификации преобразования; он указывается после всех необязательных полей.

Аргументы, которые следуют за строкой формата, интерпретируются согласно соответствующему символу *type* и необязательному префиксу [size](#size). Преобразования для символьных типов `char` и `wchar_t` определяются с помощью символов **c** или **C**; однобайтовые и многобайтовые строки или строки с расширенными символами указываются с помощью символа **s** или **S**, в зависимости от используемой функции форматирования. Символьные и строковые аргументы, указанные с использованием **c** и **s**, интерпретируется как `char` и `char*` функциями семейства `printf` или как `wchar_t` и `wchar_t*` функциями семейства `wprintf`. Символьные и строковые аргументы, указанные с использованием **C** и **S**, интерпретируется как `wchar_t` и `wchar_t*` функциями семейства `printf` или как `char` и `char*` функциями семейства `wprintf`. Такое поведение относится только к системам Майкрософт.

Целочисленные типы, такие как `short`, `int`, `long`, `long long` и их варианты `unsigned` указываются с помощью символов **d**, **i**, **o**, **u**, **x** и **X**. Типы с плавающей запятой, такие как `float`, `double` и `long double`, указываются с помощью символов **a**, **A**, **e**, **E**, **f**, **F**, **g** и **G**. По умолчанию, если не применяется префикс поля *size*, целочисленные аргументы приводятся к типу `int`, а аргументы с плавающей запятой приводятся к типу `double`. В 64-разрядных системах тип `int` является 32-разрядным значением; поэтому 64-разрядные целые числа будут усекаться при форматировании для вывода, если не используется префикс *size* со значением **ll** или **I64**. Для типов указателей, которые указываются с помощью символа**p**, используется размер указателя по умолчанию для платформы.

> [!NOTE]
> **Блок, относящийся только к системам Microsoft**  
> Символ типа **Z**, а также поведение символов типа **c**, **C**, **s** и **S** при использовании с функциями `printf` и `wprintf` представляют собой расширения Майкрософт. C стандарта ISO постоянно использует **c** и **s** для узких символов и строк, и **C** и **S** — для расширенных символов и строк во всех функциях форматирования.

### <a name="type-field-characters"></a>Символы поля типа

|Символ типа|Аргумент|Формат вывода|
|--------------------|--------------|-------------------|
|**c**|Знак|При использовании с функциями `printf` определяет однобайтовый символ; при использовании с функциями `wprintf` определяет расширенный символ.|
|**C**|Знак|При использовании с функциями `printf` определяет расширенный символ; при использовании с функциями `wprintf` определяет однобайтовый символ.|
|**d**|Целое число|Десятичное целое число со знаком.|
|**i**|Целое число|Десятичное целое число со знаком.|
|**o**|Целое число|Восьмеричное целое число без знака.|
|**u**|Целое число|Десятичное целое число без знака.|
|**x**|Целое число|Шестнадцатеричное целое число без знака, используются буквы "abcdef".|
|**X**|Целое число|Шестнадцатеричное целое число без знака, используются буквы "ABCDEF".|
|**e**|С плавающей запятой|Значение со знаком, имеющее формат [–]*d.dddd*__e±__*dd*[*d*], где *d* — одна десятичная цифра, *dddd* — одна или несколько десятичных цифр в зависимости от указанной точности или шесть по умолчанию, *dd*[*d*] — две или три десятичные цифры в зависимости от [формата вывода](../c-runtime-library/set-output-format.md) и размера показателя степени.|
|**E**|С плавающей запятой|Аналогичен формату **e**, за исключением того, что вместо **e** порядок величины представляет символ **E**.|
|**f**|С плавающей запятой|Значение со знаком, имеющее формат [–]*dddd*__.__*dddd*, где *dddd* — одна или несколько десятичных цифр. Количество цифр перед десятичной запятой зависит от величины числа, а количество знаков после десятичной запятой зависит от указанной точности либо используется шесть по умолчанию.|
|**F**|С плавающей запятой|Идентичен формату **f**, за исключением того, что выходные данные бесконечности и NaN пишутся прописными буквами.|
|**g**|С плавающей запятой|Значения со знаком отображаются в формате **f** или **e** в зависимости от того, какой формат является более компактным для заданного значения и точности. Формат **e** используется только в том случае, когда порядок значения меньше –4 или больше или равен значению аргумента *precision*. Нули в конце отбрасываются, а десятичная запятая отображается только в том случае, если за ней следует хотя бы одна цифра.|
|**G**|С плавающей запятой|Аналогичен формату **g**, за исключением того, что вместо**e** порядок величины представляет символ **E** (где это необходимо).|
|**a**|С плавающей запятой|Шестнадцатеричное значение с плавающей запятой двойной точности со знаком, которое имеет формат [−]0x*h.hhhh*__p±__*dd*, где *h.hhhh* — шестнадцатеричные цифры мантиссы (с использованием строчных букв) и *dd* — одна или более цифр порядка величины. Точность определяет количество цифр после запятой.|
|**A**|С плавающей запятой|Шестнадцатеричное значение с плавающей запятой двойной точности со знаком, которое имеет формат [−]0X*h.hhhh*__P±__*dd*, где *h.hhhh* — шестнадцатеричные цифры мантиссы (с использованием заглавных букв) и *dd* — одна или более цифр порядка величины. Точность определяет количество цифр после запятой.|
|**n**|Указатель на целое число|Число символов, которые успешно записаны на данный момент в поток или буфер. Это значение хранится в целом числе, адрес которого указан в качестве аргумента. Размер целого числа со знаком, на который существует указатель, может управляться префиксом спецификации размера аргумента. Спецификатор **n** отключен по умолчанию. Дополнительные сведения см. в примечании по безопасности.|
|**p**|Тип указателя|Отображает аргумент как адрес в шестнадцатеричных цифрах.|
|**s**|String|При использовании с функциями `printf` определяет строку однобайтовых или многобайтовых символов; при использовании с функциями `wprintf` определяет строку расширенных символов. Символы отображаются до первого нулевого символа или до тех пор, пока не будет достигнуто значение *precision*.|
|**S**|String|При использовании с функциями `printf` определяет строку расширенных символов; при использовании с функциями `wprintf` определяет строку однобайтовых или многобайтовых символов. Символы отображаются до первого нулевого символа или до тех пор, пока не будет достигнуто значение *precision*.|
|**Z**|Структура `ANSI_STRING` или `UNICODE_STRING`|Если в качестве аргумента передается адрес структуры [ANSI_STRING](/windows/desktop/api/ntdef/ns-ntdef-_string) или [UNICODE_STRING](https://msdn.microsoft.com/library/windows/hardware/ff564879.aspx), отображается строка, содержащаяся в буфере, на который указывает поле `Buffer` структуры. Используйте префикс-модификатор *size* для **w**, чтобы указать аргумент `UNICODE_STRING`, например `%wZ`. Поле `Length` структуры должно содержать значение длины строки в байтах. Поле `MaximumLength` структуры должно содержать значение длины буфера в байтах.<br /><br /> Как правило, символ типа **Z** используется только в функциях отладки драйвера, которые используют спецификацию преобразования, таких как `dbgPrint` и `kdPrint`.|

Начиная с Visual Studio 2015, если аргумент, соответствующий описателю преобразования с плавающей запятой (**a**, **A**, **e**, **E**, **f**, **F**, **g**, **G**), равен бесконечности, не определен или не является числом (NaN), выводится форматированный результат, соответствующий стандарту C99. В этой таблице перечислены форматированные выходные данные.

|Значение|Вывод|
|-----------|------------|
|infinity|`inf`|
|Несигнальное значение NaN|`nan`|
|Сигнальное значение NaN|`nan(snan)`|
|Неопределенное значение NaN|`nan(ind)`|

Любое из этих значение может иметь префикс в виде знака. Если символ описателя преобразования *type* с плавающей запятой является прописной буквой, выходные данные форматируются также прописными буквами. Например, если спецификатором формата является `%F` вместо `%f`, бесконечность форматируется как `INF` вместо `inf`. Функции `scanf` могут также анализировать эти строки, поэтому эти значения могут совершать круговой путь через функции `printf` и `scanf`.

До выхода Visual Studio 2015 в среде CRT использовался другой нестандартный формат для выходных данных значений бесконечности, неопределенных значений и значений NaN.

|Значение|Вывод|
|-----------|------------|
|+ бесконечность|`1.#INF` *случайные цифры*|
|- infinity|`-1.#INF` *случайные цифры*|
|Неопределенное (то же, что и не число без вызова исключения)|*цифра* `.#IND` *случайные цифры*|
|NaN|*цифра* `.#NAN` *случайные цифры*|

Любое из этих значений могло иметь префикс в виде знака и могло быть отформатировано немного иначе в зависимости от ширины поля и точности (иногда с необычными эффектами). Например, `printf("%.2f\n", INFINITY)` выводит `1.#J`, поскольку #INF округляется до точности 2 знаков.

> [!NOTE]
> Если аргумент, который соответствует `%s` или `%S`, или поле `Buffer` аргумента, который соответствует `%Z`, является указателем NULL, отображается значение "(NULL)".

> [!NOTE]
> Во всех экспоненциальных форматах минимальное отображаемое количество цифр показателя степени по умолчанию равно двум (три используются только при необходимости). С помощью функции [_set_output_format](../c-runtime-library/set-output-format.md) можно задать три отображаемых знака для обеспечения обратной совместимости с кодом, написанным для Visual Studio 2013 и более ранних версий.

> [!IMPORTANT]
> Поскольку формат `%n` является небезопасным, по умолчанию он запрещен. Если в строке формата имеется символ `%n`, вызывается обработчик недопустимого параметра, как описано в разделе [Проверка параметров](../c-runtime-library/parameter-validation.md). Чтобы включить поддержку `%n`, изучите раздел [_set_printf_count_output](../c-runtime-library/reference/set-printf-count-output.md).

<a name="flags"></a>

## <a name="flag-directives"></a>Директивы флагов

Первое необязательное поле в спецификации преобразования содержит *директивы флагов*, ни одного или несколько символов флага, указывающих выравнивание выходных данных и управляющих выводом символов, пустых значений, начальных нулей, десятичных запятых и восьмеричных и шестнадцатеричных префиксов. В спецификации преобразования может быть указано несколько директив флагов, и символы флагов могут размещаться в любом порядке.

### <a name="flag-characters"></a>Символы флагов

|Flag|Значение|Значение по умолчанию|
|----------|-------------|-------------|
|**-**|Выравнивание результата по левому краю в пределах заданной ширины поля.|Выравнивание по правому краю.|
|**+**|Если выходное значение имеет тип со знаком, используйте для него префикс + или –.|Знак отображается только для отрицательных значений со знаком –.|
|**0**|Если *width* предшествует префикс **0**, добавляется несколько ведущих нулей для достижения минимальной ширины. Если отображаются **0** и **-**, **0** игнорируется. Если **0** указывается в целочисленном формате (**i**, **u**, **x**, **X**, **o**, **d**) и в сочетании со спецификацией точности, (например, `%04.d`), знак **0** игнорируется. Если **0** указывается в формате плавающей запятой **a** или **A**, в начало мантиссы добавляются ведущие нули после префикса `0x` или `0X`.|Без заполнения.|
|**пустой** (" ")|Используйте пустой префикс для положительных выходных значений со знаком. Пустой префикс игнорируется, если одновременно с ним присутствует флаг +.|Пустой префикс не отображается.|
|**#**|Если используется в сочетании с форматом **o**, **x** или **X**, флаг **#** выводит префикс 0, 0x или 0X соответственно для всех ненулевых выходных значений.|Пустой префикс не отображается.|
||Если используется в сочетании с форматом **e**, **E**, **f**, **F**, **a**или **A**, флаг **#** принудительно добавляет десятичный разделитель к выходному значению.|Десятичный разделитель появляется, только если после него есть цифры.|
||Если используется в сочетании с форматом **g** или **G**, флаг **#** принудительно добавляет десятичный разделитель к выходному значению и запрещает отбрасывать конечные нули.<br /><br /> Флаг игнорируется в сочетании с форматами **c**, **d**, **i**, **u** или **s**.|Десятичный разделитель появляется, только если после него есть цифры. Конечные нули отбрасываются.|

<a name="width"></a>

## <a name="width-specification"></a>Спецификация ширины

В спецификации преобразования необязательное поле спецификации ширины отображается после любых символов *флага*. Аргумент *width* — неотрицательное целое десятичное число, управляющее минимальным количеством выводимых символов. Если количество символов в выходном значении меньше заданной ширины, к значениям слева или справа (в зависимости от того, определен ли флаг выравнивания по левому краю (**-**)) добавляются пробелы, в количестве, необходимом для достижения минимальной ширины. Если параметр *width* имеет префикс 0, при преобразовании к целому числу или числу с плавающей запятой добавляются начальные нули до тех пор, пока не будет достигнута минимальная ширина, кроме случаев преобразования в бесконечность или NaN (не число).

Спецификация ширины никогда не вызывает усечения значения. Если количество символов в выходном значении больше указанной ширины или если параметр *width* не указан, все символы значения выводятся в соответствии со спецификацией *точности*.

Если в качестве спецификации ширины указана звездочка (`*`), значение ширины задается аргументом `int` из списка аргументов. Аргумент *width* должен предшествовать форматируемому значению в списке аргументов, как показано в следующем примере:

`printf("%0*f", 5, 3);  /* 00003 is output */`

Отсутствующее или небольшое значение параметра *width* в спецификации преобразования не приводит к усечению выходного значения. Если количество символов в результате преобразования больше значения параметра *width*, поле расширяется, чтобы вместить результат преобразования.

<a name="precision"></a>

## <a name="precision-specification"></a>Спецификация точности

В спецификации преобразования третье необязательное поле является спецификацией точности. Эта спецификация состоит из точки (.), за которой следует неотрицательное целое десятичное число, которое, в зависимости от типа преобразования, определяет количество символов строки, количество десятичных разрядов или количество значащих цифр для вывода.

В отличие от спецификации ширины, спецификация точности может вызывать либо усечение выходного значения, либо округление значения с плавающей запятой. Если аргумент *precision* указан как 0 и значение, которое требуется преобразовать, равно 0, результатом будет отсутствие выведенных символов, как показано в следующем примере:

`printf( "%.0d", 0 );      /* No characters output */`

Если спецификация точности представляет собой звездочку (\*), аргумент `int` из списка аргументов предоставляет значение. В списке аргументов аргумент *precision* должен предшествовать форматируемому значению, как показано в следующем примере:

`printf( "%.*f", 3, 3.14159265 );  /* 3.142 output */`

Символ *type* определяет либо интерпретацию аргумента *precision*, либо точность по умолчанию при опущенном аргументе *precision*, как показано в следующей таблице.

### <a name="how-precision-values-affect-type"></a>Влияние значений точности на тип

|Тип|Значение|Значение по умолчанию|
|----------|-------------|-------------|
|**a**, **A**|Точность определяет количество цифр после запятой.|Точность по умолчанию — 13. Если точность равна 0, десятичная запятая не выводится, если не используется флаг **#**.|
|**c**, **C**|Точность не применяется.|Символ выводится.|
|**d**, **i**, **o**, **u**, **x**, **X**|Точность определяет минимальное выводимое количество цифр. Если количество цифр в аргументе меньше значения *precision*, выходное значение дополняется слева нулями. Значение не усекается, когда количество цифр превышает значение *precision*.|Точность по умолчанию — 1.|
|**e**, **E**|Выводимое количество знаков дробной части задается спецификацией точности. Последняя выводимая цифра округляется.|Точность по умолчанию — 6. Если аргумент *precision* равен 0 или присутствует точка (.) без числа после нее, десятичная запятая не выводится.|
|**f**, **F**|Значение точности задает количество цифр после десятичной запятой. Если десятичная запятая присутствует, перед ней присутствует по крайней мере одна цифра. Значение округляется до соответствующего количества цифр.|Точность по умолчанию — 6. Если аргумент *precision* равен 0 или если присутствует точка (.) без числа после нее, десятичная запятая не выводится.|
|**g**, **G**|Точность определяет максимальное выводимое количество значащих цифр.|Выводятся шесть значащих цифр, а конечные нули усекаются.|
|**s**, **S**|Точность определяет максимальное количество выводимых символов. Если количество символов превышает значение *precision*, "лишние" символы не выводятся.|Символы выводятся до тех пор, пока не будет обнаружен нуль-символ.|

<a name="size"></a>

## <a name="argument-size-specification"></a>Спецификация размера аргумента

В спецификации преобразования поле *size* — это модификатор длины аргумента для описателя преобразования *type*. Префиксы поля *size* для поля *type* (**hh**, **h**, **j**, **l** (строчная L), **L**, **ll**, **t**, **w**, **z**, **I** (прописная i), **I32** и **I64**) определяют "размер" соответствующего аргумента — длинный или короткий, 32- или 64-разрядный, однобайтовый или расширенный символ — в зависимости от описателя преобразования, который они модифицируют. Эти префиксы размера используются с символами *type* в семействах функций `printf` и `wprintf` для определения интерпретации размеров аргументов, как показано в следующей таблице. Поле *size* является необязательным для некоторых типов аргументов. Если префикс размера не указан, модуль форматирования использует целые аргументы, например подписанные или не подписанные `char`, `short`, `int`, `long` и типы перечисления как 32-разрядные типы `int`, а аргументы `float`, `double` и `long double` с плавающей запятой используются как 64-разрядные типы `double`. Это соответствует правилам повышения аргументов по умолчанию для списков аргументов переменных. Дополнительные сведения о повышении аргументов см. раздел Ellipses and Default Arguments (Многоточия и аргументы по умолчанию) в статье [Postfix expressions](../cpp/postfix-expressions.md) (Постфиксные выражения). Как в 32-разрядной, так и в 64-разрядной системах спецификация преобразования 64-разрядного целого аргумента должна включать префикс размера **ll** или **I64**. В противном случае поведение модуля форматирования не определено.

Некоторые типы имеют разный размер в 32-разрядном и 64-разрядном коде. Например, `size_t` на 32 бита длиннее в коде, скомпилированном для x86, и на 64 бита длиннее в коде, скомпилированном для x64. Чтобы создать код форматирования для типов с переменным количеством байт, не зависящий от платформы, можно использовать модификатор размера аргумента с переменным количеством байт. Кроме того, можно использовать 64-разрядный модификатор размера аргумента и явно повысить тип аргумента с переменным количеством байт до 64 бит. Присущий Майкрософт модификатор размера аргумента **I** (прописная i) обрабатывает целочисленные аргументы переменной ширины, но для обеспечения переносимости рекомендуется использовать характерные для типа модификаторы **j**, **t** и **z**.

### <a name="size-prefixes-for-printf-and-wprintf-format-type-specifiers"></a>Префиксы размера для описателей формата функций printf и wprintf

|Чтобы указать|Используемый префикс|Со спецификатором типа|
|----------------|----------------|-------------------------|
|`char`<br />`unsigned char`|**hh**|**d**, **i**, **o**, **u**, **x** или **X**|
|`short int`<br />`short unsigned int`|**h**|**d**, **i**, **o**, **u**, **x** или **X**|
|`__int32`<br />`unsigned __int32`|**I32**|**d**, **i**, **o**, **u**, **x** или **X**|
|`__int64`<br />`unsigned __int64`|**I64**|**d**, **i**, **o**, **u**, **x** или **X**|
|`intmax_t`<br />`uintmax_t`|**j** или **I64**|**d**, **i**, **o**, **u**, **x** или **X**|
|`long double`|**l** (строчная L) или **L**|**a**, **A**, **e**, **E**, **f**, **F**, **g** или **G**|
|`long int`<br />`long unsigned int`|**l** (строчная L)|**d**, **i**, **o**, **u**, **x** или **X**|
|`long long int`<br />`unsigned long long int`|**ll** (строчные LL)|**d**, **i**, **o**, **u**, **x** или **X**|
|`ptrdiff_t`|**t** или **I** (прописная i)|**d**, **i**, **o**, **u**, **x** или **X**|
|`size_t`|**z** или **I** (прописная i)|**d**, **i**, **o**, **u**, **x** или **X**|
|Однобайтовый символ|**h**|**c** или **C**|
|Расширенный символ|**l** (строчная L) или **w**|**c** или **C**|
|Строка однобайтовых символов|**h**|**s**, **S** или **Z**|
|Строка расширенных символов|**l** (строчная L) или **w**|**s**, **S** или **Z**|

Типы `ptrdiff_t` и `size_t` являются `__int32` или `unsigned __int32` на 32-разрядных платформах и `__int64` или `unsigned __int64` на 64-разрядных платформах. Префиксы размера **I** (прописная i), **j**, **t** и **z** принимают правильное значение ширины аргументов для платформы.

В Visual C++ хотя `long double` является отдельным типом, он имеет то же внутреннее представление, что и тип `double`.

Спецификатор типа **hc** или **hC** аналогичен **c** в функциях `printf` и **C** в функциях `wprintf`. Спецификатор типа **lc**, **lC**, **wc** или **wC** аналогичен **C** в функциях `printf` и **c** в функциях `wprintf`. Спецификатор типа **hs** или **hS** аналогичен **s** в функциях `printf` и **S** в функциях `wprintf`. Спецификатор типа **ls**, **lS**, **ws** или **wS** аналогичен **S** в функциях `printf` и **s** в функциях `wprintf`.

> [!NOTE]
> **Блок, относящийся только к системам Microsoft**  
> Префиксы модификатора размера аргумента **I** (прописная i), **I32**, **I64** и **w** являются расширениями Майкрософт и не совместимы с C стандарта ISO. Префикс **h** при использовании с данными типа `char` и префикс **l** (строчная L) при использовании с данными типа `double` являются расширениями Майкрософт.

## <a name="see-also"></a>См. также

[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)  
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)  
[Позиционные параметры printf_p](../c-runtime-library/printf-p-positional-parameters.md)  