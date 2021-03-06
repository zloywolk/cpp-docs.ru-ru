---
title: Спецификатор final | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- final_CPP
dev_langs:
- C++
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e382bd75a734b205389b83455e3ab020f54ca6d3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066236"
---
# <a name="final-specifier"></a>Спецификатор final

Можно использовать **окончательный** ключевое слово для назначения виртуальных функций, которые не могут быть переопределены в производном классе. Можно также использовать это ключевое слово для назначения классов, которые невозможно наследовать.

## <a name="syntax"></a>Синтаксис

```
function-declaration final;
class class-name final base-classes
```

## <a name="remarks"></a>Примечания

**Окончательный** является контекстным и имеет специальное значение, только когда она используется после объявления функции или имени класса; в противном случае — значение, он не является зарезервированным ключевым словом.

Когда **окончательный** используется в объявлениях классов `base-classes` является необязательной частью объявления.

## <a name="example"></a>Пример

В следующем примере используется **окончательный** ключевое слово, чтобы указать, что виртуальная функция не может быть переопределен.

```cpp
class BaseClass
{
    virtual void func() final;
};

class DerivedClass: public BaseClass
{
    virtual void func(); // compiler error: attempting to
                         // override a final function
};
```

Сведения о том, как указать, что функции-члены могут быть переопределены, см. в разделе [спецификатор переопределения](../cpp/override-specifier.md).

В следующем примере используется **окончательный** ключевое слово, чтобы указать, что класс не может наследоваться.

```cpp
class BaseClass final
{
};

class DerivedClass: public BaseClass // compiler error: BaseClass is
                                     // marked as non-inheritable
{
};
```

## <a name="see-also"></a>См. также

[Ключевые слова](../cpp/keywords-cpp.md)<br/>
[Описатель override](../cpp/override-specifier.md)