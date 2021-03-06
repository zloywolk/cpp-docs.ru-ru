---
title: Оператор typeid | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db9e019c3c9cc7e7e71726a8bd11e83ca4c99cdf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020671"
---
# <a name="typeid-operator"></a>Оператор typeid

## <a name="syntax"></a>Синтаксис

```
typeid(type-id)
typeid(expression)
```

## <a name="remarks"></a>Примечания

**Typeid** оператор разрешает тип объекта определяется во время выполнения.

Результат **typeid** является `const type_info&`. Значение является ссылкой на `type_info` объект, представляющий либо *идентификатор типа* или тип *выражение*, в зависимости от используемой формы **typeid** используется. См. в разделе [класс type_info](../cpp/type-info-class.md) Дополнительные сведения.

**Typeid** оператор не работает с управляемыми типами (абстрактными деклараторами или экземплярами), см. в разделе [typeid](../windows/typeid-cpp-component-extensions.md) сведения о получении <xref:System.Type> указанного типа.

**Typeid** делает оператор проверки во время выполнения, когда применяется к l значению полиморфного типа классов, где невозможно определить истинный тип объекта, предоставленной статической информации. К таким случаям относятся следующие.

- Ссылка на класс

- Указатель, разыменован с \*

- Указатель индекса (например, [ ]). (Обратите внимание, что, как правило, небезопасно использовать индекс с указателем на полиморфный тип.)

Если *выражение* указывает на тип базового класса, но объект фактически имеет тип, производный от базового класса, `type_info` ссылки для производного класса является результатом. *Выражение* должен указывать на полиморфный тип (класс с виртуальными функциями). В противном случае результатом является `type_info` для статического класса, который ссылается *выражение*. Более того, необходимо отменить ссылку на указатель, чтобы использовать объект, на который указывает этот указатель. Без разыменование указателя, это приведет к появлению `type_info` для указателя, не на который он указывает. Пример:

```cpp
// expre_typeid_Operator.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <typeinfo.h>

class Base {
public:
   virtual void vvfunc() {}
};

class Derived : public Base {};

using namespace std;
int main() {
   Derived* pd = new Derived;
   Base* pb = pd;
   cout << typeid( pb ).name() << endl;   //prints "class Base *"
   cout << typeid( *pb ).name() << endl;   //prints "class Derived"
   cout << typeid( pd ).name() << endl;   //prints "class Derived *"
   cout << typeid( *pd ).name() << endl;   //prints "class Derived"
   delete pd;
}
```

Если *выражение* на указатель, и что значение указателя равно нулю, **typeid** вызывает [исключение bad_typeid](../cpp/bad-typeid-exception.md). Если указатель не указывает на допустимый объект, `__non_rtti_object` исключения, обозначая попытку проанализировать RTTI, вызвавший ошибку (например, нарушение прав доступа), так как объект каким-либо образом недопустимо (недопустимый указатель или код не был скомпилирован с [/GR](../build/reference/gr-enable-run-time-type-information.md)).

Если *выражение* не указатель или ссылку на базовый класс объекта, в результате `type_info` ссылка, представляющая статический тип *выражение*. *Статический тип* выражения относится к типу выражения, известное во время компиляции. Семантика исполнения игнорируется при оценке статического типа выражения. Кроме того, ссылки по возможности игнорируются при определении статического типа выражения:

```cpp
// expre_typeid_Operator_2.cpp
#include <typeinfo>

int main()
{
   typeid(int) == typeid(int&); // evaluates to true
}
```

**typeid** также может использоваться в шаблонах для определения типа параметра шаблона:

```cpp
// expre_typeid_Operator_3.cpp
// compile with: /c
#include <typeinfo>
template < typename T >
T max( T arg1, T arg2 ) {
   cout << typeid( T ).name() << "s compared." << endl;
   return ( arg1 > arg2 ? arg1 : arg2 );
}
```

## <a name="see-also"></a>См. также

[Сведения о типах среды выполнения](../cpp/run-time-type-information.md)<br/>
[Ключевые слова](../cpp/keywords-cpp.md)