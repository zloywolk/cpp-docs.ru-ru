---
title: Разрешение имен зависимых типов | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 34066bb4-0c79-4fd8-bda7-539a60a277ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c17a29f0287ee25517ed72f1c98caa2d38a96195
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040188"
---
# <a name="name-resolution-for-dependent-types"></a>Разрешение имен зависимых типов

Используйте **typename** для полных имен в определениях шаблонов, чтобы сообщить компилятору, что заданное полное имя определяет тип. Дополнительные сведения см. в разделе [typename](../cpp/typename.md).

```cpp
// template_name_resolution1.cpp
#include <stdio.h>
template <class T> class X
{
public:
   void f(typename T::myType* mt) {}
};

class Yarg
{
public:
   struct myType { };
};

int main()
{
   X<Yarg> x;
   x.f(new Yarg::myType());
   printf("Name resolved by using typename keyword.");
}
```

```Output
Name resolved by using typename keyword.
```

Имя поиске зависимых имен проверяются имена из контекста определения шаблона, в следующем примере этот контекст осуществляет поиск `myFunction(char)`— и контекст экземпляра шаблона. В следующем примере создается шаблон в основной части кода; Таким образом `MyNamespace::myFunction` видна с момента создания экземпляра и выбирается как более подходящее сопоставление. В случае переименования функции `MyNamespace::myFunction` вместо нее будет вызываться функция `myFunction(char)`.

Разрешение имен выполняется так, как если бы они были зависимыми. Однако при наличии любой возможности конфликта рекомендуется использовать полные имена.

```cpp
// template_name_resolution2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

void myFunction(char)
{
   cout << "Char myFunction" << endl;
}

template <class T> class Class1
{
public:
   Class1(T i)
   {
      // If replaced with myFunction(1), myFunction(char)
      // will be called
      myFunction(i);
}
};

namespace MyNamespace
{
   void myFunction(int)
   {
      cout << "Int MyNamespace::myFunction" << endl;
   }
};

using namespace MyNamespace;

int main()
{
   Class1<int>* c1 = new Class1<int>(100);
}
```

### <a name="output"></a>Вывод

```Output
Int MyNamespace::myFunction
```

### <a name="template-disambiguation"></a>Устранение неоднозначности шаблона

Visual Studio 2012 обеспечивает C ++ 98/03/11 стандартные правила для устранения неоднозначности с ключевым словом «шаблон». В следующем примере Visual C++ 2010 принимали несоответствующие строки и соответствующие строки.  Visual Studio 2012 принимает только соответствующие строки.

```cpp
#include <iostream>
#include <ostream>
#include <typeinfo>
using namespace std;

template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    #if defined(NONCONFORMANT)
        typedef typename AY::Rebind<X>::Other AX; // nonconformant
    #elif defined(CONFORMANT)
        typedef typename AY::template Rebind<X>::Other AX; // conformant
    #else
        #error Define NONCONFORMANT or CONFORMANT.
    #endif
};

int main() {
    cout << typeid(Container<int, Allocator<float>>::AX).name() << endl;
}
```

Соответствие правилам устранения неоднозначности необходимо соблюдать, поскольку по умолчанию C++ предполагает, что `AY::Rebind` не является шаблоном, в результате чего компилятор интерпретирует знак "`<`" как "меньше чем". Чтобы компилятор мог правильно интерпретировать знак "`Rebind`" как угловую скобку, он должен знать, что `<` — это шаблон.

## <a name="see-also"></a>См. также

[Разрешение имен](../cpp/templates-and-name-resolution.md)