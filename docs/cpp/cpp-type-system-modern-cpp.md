---
title: Тип системы C++ (современный C++) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 553c0ed6-77c4-43e9-87b1-c903eec53e80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 63af117df6f53f2b280dc990d58a099441679f44
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060295"
---
# <a name="c-type-system-modern-c"></a>Тип системы C++ (современный C++)

Концепция *тип* очень важно в C++. Каждая переменная, аргумент функции и возвращаемое значение функции должны иметь тип, чтобы их можно было скомпилировать. Кроме того, перед вычислением каждого выражения (включая литеральные значения) компилятор неявно назначает ему тип. Некоторые примеры типов **int** для хранения целых значений **двойные** для хранения значений с плавающей запятой (также называется *скалярные* типы данных), или класс стандартной библиотеки [std::basic_string](../standard-library/basic-string-class.md) для хранения текста. Можно создать свой собственный тип, определив **класс** или **структуры**. Тип определяет объем памяти, выделяемой для переменной (или результата выражения), типы значений, которые могут храниться в этой переменной, способ интерпретации значений (например, битовые шаблоны), и операции, допустимые с переменной. Эта статья содержит неформальный обзор основных особенностей системы типов C++.

## <a name="terminology"></a>Терминология

**Переменной**: символьную имя количество данных, чтобы имя может использоваться для доступа к данным, которые он ссылается на для области кода, в которой она определена. В C++ *переменной* обычно используется для обращения к экземплярам скалярных типов данных, в то время как экземпляры других типов обычно называются *объектов*.

**Объект**: для простоты и согласованности в этой статье используется термин *объект* для ссылки на любом экземпляре класса или структуры, а также при использовании в общем смысле включает все типы, том числе скалярные переменные.

**Тип POD** (обычные старые данные): Эта Неофициальная категория типов данных в C++ относится к скалярным типам (см. в разделе базовых типов) или *классам POD*. Класс POD не содержит статических данных-членов, которые не являются типами POD, а также не содержит пользовательских конструкторов, пользовательских деструкторов или пользовательских операторов присваивания. Кроме того, класс POD не имеет виртуальных функций, базового класса и ни закрытых, ни защищенных нестатических данных-членов. Типы POD часто используются для внешнего обмена данными, например с модулем, написанным на языке С (в котором имеются только типы POD).

## <a name="specifying-variable-and-function-types"></a>Указание типов переменных и функций

C++ — *строго типизированным* языка и при этом *статически типизированным*; каждый объект имеет тип и, тип никогда не изменяется (не следует путать со статическими объектами данных).
**При объявлении переменной** в коде, необходимо явно задать ее тип, либо использовать **автоматически** ключевое слово, чтобы указать компилятору вывести тип из инициализатора.
**При объявлении функции** в коде, необходимо указать тип каждого аргумента и возвращаемого значения, или **void** Если значение не возвращается функцией. Исключением является использование шаблонов функции, которые допускают аргументы произвольных типов.

После объявления переменной изменить ее тип впоследствии уже невозможно. Однако можно скопировать значения переменной или возвращаемое значение функции в другую переменную другого типа. Такие операции называются *преобразования типов*, — они иногда необходимы, но также являются потенциальными источниками потери данных или некорректности.

При объявлении переменной типа POD настоятельно рекомендуется инициализировать ее, т. е. указать начальное значение. Пока переменная не инициализирована, она имеет "мусорное" значение, определяемое значениями битов, которые ранее были установлены в этом месте памяти. Необходимо учитывать эту особенность языка C++, особенно при переходе с другого языка, который обрабатывает инициализацию автоматически. При объявлении переменной типа, не являющегося классом POD, инициализация обрабатывается конструктором.

В следующем примере показано несколько простых объявлений переменных с небольшим описанием для каждого объявления. В примере также показано, как компилятор использует сведения о типе, чтобы разрешить или запретить некоторые последующие операции с переменной.

```cpp
int result = 0;              // Declare and initialize an integer.
double coefficient = 10.8;   // Declare and initialize a floating
                             // point value.
auto name = "Lady G.";       // Declare a variable and let compiler
                             // deduce the type.
auto address;                // error. Compiler cannot deduce a type
                             // without an intializing value.
age = 12;                    // error. Variable declaration must
                             // specify a type or use auto!
result = "Kenny G.";         // error. Can’t assign text to an int.
string result = "zero";      // error. Can’t redefine a variable with
                             // new type.
int maxValue;                // Not recommended! maxValue contains
                             // garbage bits until it is initialized.
```

## <a name="fundamental-built-in-types"></a>Базовые (встроенные) типы

В отличие от некоторых других языков, в C++ нет универсального базового типа, от которого наследуются все остальные типы. Реализация языка Visual C++ включает множество *фундаментальные типы*, также известных как *встроенные типы*. Сюда входят числовые типы, такие как **int**, **двойные**, **long**, **bool**, а также **char** и **wchar_t** типами для символов ASCII и ЮНИКОДА, соответственно. Большинство базовых типов (за исключением **bool**, **двойные**, **wchar_t** и связанных типов) имеют беззнаковые версии с другим диапазон значений, которые можно хранить в переменной. Например **int**, который хранит 32-разрядное знаковое целое число, может представлять значение от -2147483648 до 2147483647. **Unsigned int**, который также хранится в виде 32-разрядного значения, можно хранить значение от 0 до 4 294 967 295. Общее количество возможных значений в каждом случае одинаково, отличается только диапазон.

Базовые типы распознаются компилятором, в котором предусмотрены встроенные правила, управляющие операциями, выполняемыми с такими типами, а также преобразованием в другие базовые типы. Полный список встроенных типов и их размер и предельных числовых значений, см. в разделе [фундаментальные типы](../cpp/fundamental-types-cpp.md).

На следующем рисунке показаны относительные размеры встроенных типов:

![Размер в байтах созданных&#45;в типах](../cpp/media/built-intypesizes.png "Built-inTYpeSizes")

В следующей таблице перечислены наиболее часто используемые базовые типы:

|Тип|Размер|Комментарий|
|----------|----------|-------------|
|int|4 байта|Выбор по умолчанию для целочисленных значений.|
|double|8 байт|Выбор по умолчанию для значений с плавающей запятой.|
|bool|1 байт|Представляет значения, которые могут быть или true, или false.|
|char|1 байт|Используйте для символов ASCII в старых строках в стиле C или в объектах std::string, которые никогда не будут преобразовываться в Юникод.|
|wchar_t|2 байта|Представляет "расширенные" символы, которые могут быть представлены в формате Юникод (UTF-16 в Windows, в других операционных системах возможно другое представление). Это символьный тип, используемый в строках типа `std::wstring`.|
|unsigned char|1 байт|В C++ нет встроенного типа `byte`.  Для представления байтовых значений используйте тип unsigned char.|
|unsigned int|4 байта|Вариант по умолчанию для битовых флагов.|
|длинное длинное|8 байт|Представляет очень большие целочисленные значения.|

## <a name="the-void-type"></a>Тип void

**Void** тип — это особый тип; невозможно объявить переменную типа **void**, но можно объявить переменную типа `void *` (указатель на **void**), который является Иногда необходимыми при выделении низкоуровневой (нетипизированной) памяти. Однако указатели на **void** являются не типобезопасным и обычно их использование настоятельно не рекомендуется в современном с ++. В объявлении функции **void** возвращаемое значение означает, что функция не возвращает значение; это распространенное и допустимое использование **void**. Хотя язык, необходимый функции C ноль параметров, чтобы объявить **void** в списке параметров, например, `fou(void)`, такой подход не рекомендуется в современном C++ и должен быть объявлен `fou()`. Дополнительные сведения см. в разделе [преобразования типов и безопасность типов](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="const-type-qualifier"></a>Квалификатор типа const

Любой встроенный или пользовательский тип может квалифицироваться ключевым словом const. Кроме того, функции-члены могут быть **const**-полное и даже **const**-перегружен. Значение **const** тип нельзя изменить после инициализации.

```cpp

const double PI = 3.1415;
PI = .75 //Error. Cannot modify const variable.

```

**Const** квалификатор широко используется в объявлениях функций и переменных и «правильности константы» является важным принципом в C++; по сути это означает использование **const** гарантировать во время компиляции значения не исключения непреднамеренного изменения. Дополнительные сведения см. в разделе [const](../cpp/const-cpp.md).

Объект **const** тип отличается от ее версии неконстантной; например, **const int** является отдельным типом из **int**. Можно использовать C++ **const_cast** оператор в редких случаях, когда необходимо отменить *неизменность* из переменной. Дополнительные сведения см. в разделе [преобразования типов и безопасность типов](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="string-types"></a>Строковые типы

Строго говоря язык C++ не указан встроенный строковый тип; **char** и **wchar_t** хранятся отдельные символы — необходимо объявить массив этих типов, чтобы приблизить строку, добавив конечное значение null (например, ASCII `'\0'`) к элементу массива за последним знаком (также называется *строки в стиле C*). Строки в стиле C требовали написания гораздо большего объема кода или использования внешних библиотек служебных функций. Но в современном с ++, у нас есть стандартные библиотечные типы `std::string` (для 8-разрядное **char**-символьных строк типа) или `std::wstring` (для 16-разрядных **wchar_t**-символьных строк типа). Эти контейнеры стандартной библиотеки C++ можно рассматривать как собственные строковые типы, так как они являются частью стандартных библиотек, включенных в любой совместимой среде сборки C++. Просто используйте директиву `#include <string>`, чтобы эти типы были доступны в программе. (При использовании MFC или ATL также доступен класс CString, но он не является частью стандарта C++.) В современном языке C++ настоятельно не рекомендуется использовать массивы символов с завершающим значением NULL (вышеупомянутые строки в стиле C).

## <a name="user-defined-types"></a>Пользовательские типы

При определении **класс**, **структуры**, **объединение**, или **перечисления**, эта конструкция используется в остальной части кода, как если бы это был базовый тип . Он имеет известный размер в памяти, и в его отношении действуют определенные правила проверки во время компиляции и во время выполнения в течение срока использования программы. Основные различия между базовыми встроенными типами и пользовательскими типами указаны ниже:

- Компилятор не имеет встроенных сведений о пользовательском типе. Он изучает типа при его первом появлении его определения, во время компиляции.

- Пользователь определяет, какие операции можно выполнять с типом и как его можно преобразовать в другие типы, задавая (через перегрузку) соответствующие операторы, либо в виде членов класса, либо в виде функций, не являющихся членами. Дополнительные сведения см. в разделе [перегрузка функций](function-overloading.md).

- Они не обязательно должны быть статически типизированы (правило, согласно которому тип объекта не изменяется). Через механизмы *наследования* и *полиморфизм*, переменная, объявленная как определяемого пользователем типа класса (называется экземпляр объекта класса) может принадлежать к разным типам во время выполнения чем на время компиляции. Дополнительные сведения см. в разделе [Наследование](../cpp/inheritance-cpp.md).

## <a name="pointer-types"></a>типы указателей;

Как и самые ранние версии языка C, язык C++ по-прежнему позволяет объявить переменную типа указателя с помощью специального декларатора `*` (звездочка). Тип указателя хранит адрес расположения в памяти, в котором хранится фактическое значение данных. В современном C++ они называются *необработанных указателей*и осуществляется в коде осуществляется через специальные операторы `*` (звездочка) или `->` (дефис со знаком больше-чем). Это называется *разыменование*, и какой из них, используемом зависит от того, разыменовываемого указатель на скаляр или указатель на член в объекте. Работа с типами указателя долгое время была одним из наиболее трудных и непонятных аспектов разработки программ на языках C и C++. В этом разделе приводятся некоторые факты и рекомендации, помогающие использовать необработанные указатели, если вы хотите, чтобы, но в современном C++, он больше не требуется (и рекомендуется) использовать необработанные указатели для владения объектом, связи с развитием [смарт-указатель](../cpp/smart-pointers-modern-cpp.md) () Подробнее см. в конце этого раздела). Все еще полезно и безопасно использовать необработанные указатели для отслеживания объектов, но если требуется использовать их для владения объектом, необходимо делать это с осторожностью и после тщательного анализа процедуры создания и уничтожения объектов, которые им принадлежат.

Первое, что необходимо знать, — это то, что при объявлении переменной необработанного указателя выделяется только память, необходимая для хранения адреса расположения памяти, на который будет ссылаться указатель при разыменовывании. Выделение памяти для самого значения данных (также называется *резервным хранилищем*) еще не произведено. Другими словами, объявив переменную необработанного указателя, вы создаете переменную адреса памяти, а не фактическую переменную данных. Разыменовывание переменной указателя до проверки того, что она содержит действительный адрес в резервном хранилище, приведет к неопределенному поведению (обычно неустранимой ошибке) программы. В следующем примере демонстрируется подобная ошибка:

```cpp
int* pNumber;       // Declare a pointer-to-int variable.
*pNumber = 10;      // error. Although this may compile, it is
                    // a serious error. We are dereferencing an
                    // uninitialized pointer variable with no
                    // allocated memory to point to.
```

Пример разыменовывает тип указателя без выделения памяти для хранения фактических целочисленных данных или без выделенного допустимого адреса памяти. В следующем коде исправлены эти ошибки:

```cpp
    int number = 10;          // Declare and initialize a local integer
                              // variable for data backing store.
    int* pNumber = &number;   // Declare and initialize a local integer
                              // pointer variable to a valid memory
                              // address to that backing store.
...
    *pNumber = 41;            // Dereference and store a new value in
                              // the memory pointed to by
                              // pNumber, the integer variable called
                              // "number". Note "number" was changed, not
                              // "pNumber".
```

В исправленном примере кода используется локальной память стека для создания резервного хранилища, на который указывает указатель `pNumber`. Базовый тип используется для простоты. На практике резервное хранилище для указателей являются большинства часто определяемые пользователем типы, динамически выделяемые в области памяти, которая называется *кучи* (или *свободного хранилища*) с помощью **новый** ключевого выражения (в стиле программирования C, более старый `malloc()` использовалась функция библиотеки времени выполнения C). После выделения памяти эти переменные, обычно называются объектами, особенно в том случае, если они основаны на определении класса. Память, выделенную с **новый** должна быть удалена соответствующим **удалить** инструкцию (или, если вы использовали `malloc()` функцию, чтобы выделить его на функцию среды выполнения C `free()`).

Тем не менее, это легко забыть удалить динамически выделенный объект — особенно в сложном коде, что приводит к ошибке ресурсов под названием *утечки памяти*. По этой причине в современном С++ настоятельно не рекомендуется использовать необработанные указатели. Почти всегда лучше создать необработанный указатель в [смарт-указатель](../cpp/smart-pointers-modern-cpp.md), который автоматически освобождает память при вызове его деструктора (когда код выходит за пределы области действия для смарт-указателя); с помощью интеллектуальных указателей вы практически исключается целый класс ошибок в программах с ++. В следующем примере предположим, что `MyClass` — это пользовательский тип, который имеет открытый метод `DoSomeWork();`

```cpp
void someFunction() {
    unique_ptr<MyClass> pMc(new MyClass);
    pMc->DoSomeWork();
}
  // No memory leak. Out-of-scope automatically calls the destructor
  // for the unique_ptr, freeing the resource.
```

Дополнительные сведения об интеллектуальных указателях см. в разделе [интеллектуальные указатели](../cpp/smart-pointers-modern-cpp.md).

Дополнительные сведения о преобразованиях указателей см. в разделе [преобразования типов и безопасность типов](../cpp/type-conversions-and-type-safety-modern-cpp.md).

Как правило, Дополнительные сведения об указателях см. в разделе [указатели](../cpp/pointers-cpp.md).

## <a name="windows-data-types"></a>Типы данных Windows

В классическом программировании Win32 на языке C и C++ для указания типов параметров и возвращаемых значений в большинстве функций используются специально предназначенные для Windows определения typedef и макросы #define (определенные в `windef.h`). Эти типы данных Windows большей части являются лишь специальными названиями (псевдонимы), учитывая встроенные типы данных C/C++. Полный список этих определений typedef и определений препроцессора, см. в разделе [типы данных Windows](/windows/desktop/WinProg/windows-data-types). Некоторые из этих определений typedef, например HRESULT и LCID, удобны и содержат полезные сведения. Другие, такие как INT, не имеют особого смысла и просто являются псевдонимами для базовых типов C++. Прочие типы данных Windows имеют имена, которые сохранились с эпохи программирования на языке C для 16-разрядных процессоров, и не имеют смысла или значения на современном оборудовании или в современных операционных системах. Существуют также специальные типы данных связанных с библиотекой среды выполнения Windows, в списке [базовые типы среды выполнения Windows](/windows/desktop/WinRT/base-data-types). В современном языке C++ в целом рекомендуется использовать базовые типы C++, за исключением случаев, когда тип Windows сообщает некоторые дополнительные сведения о том, как следует интерпретировать значение.

## <a name="more-information"></a>Дополнительные сведения

Дополнительные сведения о системе типов C++ см. в следующих разделах.

|||
|-|-|
|[Типы значений](../cpp/value-types-modern-cpp.md)|Описывает *типы значений* вместе с проблемами, связанными с их использованием.|
|[Преобразования типов и безопасность типов](../cpp/type-conversions-and-type-safety-modern-cpp.md)|Описание типовых проблем преобразования типов и способов их избежать.|

## <a name="see-also"></a>См. также

[Возвращение к C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Справочник по языку C++](../cpp/cpp-language-reference.md)<br/>
[Стандартная библиотека C++](../standard-library/cpp-standard-library-reference.md)