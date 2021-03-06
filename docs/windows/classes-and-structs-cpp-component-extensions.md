---
title: Классы и структуры (расширения компонентов C++) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ref class keyword [C++]
- value class keyword [C++]
- value struct keyword [C++]
- ref struct keyword [C++]
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 60e388e18e6d3607dac1946c3fd9a511e948afd4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448380"
---
# <a name="classes-and-structs--c-component-extensions"></a>Классы и структуры (расширения компонентов C++)

Объявляет класс или структура, *время жизни объекта* администрируется автоматически. Когда объект больше не доступен или выходит за пределы области, Visual C++ автоматически отменяет память, выделенную для этого объекта.

## <a name="all-runtimes"></a>Все среды выполнения

### <a name="syntax"></a>Синтаксис

```cpp
      class_access
      ref class
      name
      modifier :  inherit_accessbase_type {};
class_accessref structnamemodifier :  inherit_accessbase_type {};
class_accessvalue classnamemodifier :  inherit_accessbase_type {};
class_accessvalue structnamemodifier :  inherit_accessbase_type {};

```

### <a name="parameters"></a>Параметры

*class_access*<br/>
(Необязательно) Доступность класса или структуры вне сборки. Возможные значения: **открытый** и **частного** (**частного** используется по умолчанию). Вложенные классы и структуры не могут иметь *class_access* спецификатор.

*name*<br/>
Имя класса или структуры.

*Модификатор*<br/>
(Необязательно) [абстрактный](../windows/abstract-cpp-component-extensions.md) и [запечатанный](../windows/sealed-cpp-component-extensions.md) Допустимые модификаторы.

*inherit_access*<br/>
(Необязательно) Доступность *base_type*. Единственная разрешенная доступность — **открытый** (**открытый** используется по умолчанию).

*base_type*<br/>
(Необязательно) Базовый тип. Однако тип значения не может действовать как базовый тип.

Дополнительные сведения см. в разделе описания конкретного языка этого параметра в общие Runtimesections языка и параметров времени выполнения Windows.

### <a name="remarks"></a>Примечания

Доступность членов по умолчанию объекта, объявленного с **ссылочного класса** или **класса значений** — **частного**. И доступность по умолчанию членов объекта, объявленных с **структура ссылки** или **структура значения** — **открытый**.

Если ссылочный тип наследует от другого ссылочного типа, виртуальные функции в базовом классе необходимо явно переопределить (с [переопределить](../windows/override-cpp-component-extensions.md)) или скрытый (с [new (новый слот в vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)). Функции производного класса должны быть явно помечены как **виртуального**.

Для обнаружения во время компиляции, является ли тип **ссылочного класса** или **структура ссылки**, или **класса значений** или **структура значения**, использовать `__is_ref_class (type)`, `__is_value_class (type)`, или `__is_simple_value_class (type)`. Дополнительные сведения см. в разделе [поддержка характеристик типов компилятором](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

Дополнительные сведения о классах и структурах см. в разделе

- [Создание экземпляров классов и структур](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)

- [Семантика стека C++ для ссылочных типов](../dotnet/cpp-stack-semantics-for-reference-types.md)

- [Классы, структуры и объединения](../cpp/classes-and-structs-cpp.md)

- [Деструкторы и методы завершения в разделе: определение и использование классов и структур (C + +/ CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)

- [Пользовательские операторы (C++/CLI)](../dotnet/user-defined-operators-cpp-cli.md)

- [Заданные пользователем преобразования (C++/CLI)](../dotnet/user-defined-conversions-cpp-cli.md)

- [Практическое руководство. Создание программы-оболочки собственного класса для использования в C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

- [Универсальные классы (C++/CLI)](../windows/generic-classes-cpp-cli.md)

## <a name="windows-runtime"></a>Среда выполнения Windows

### <a name="remarks"></a>Примечания

См. в разделе [классы и структуры ссылки](../cppcx/ref-classes-and-structs-c-cx.md) и [классы и структуры значений](https://msdn.microsoft.com/library/windows/apps/hh699861.aspx).

### <a name="parameters"></a>Параметры

*base_type*<br/>
(Необязательно) Базовый тип. Объект **ссылочного класса** или **структура ссылки** могут наследовать несколько интерфейсов и ноль или один **ref** типов. Объект **класса значений** или **структура значения** может наследовать только от ноль или несколько интерфейсов.

При объявлении объекта с помощью **ссылочного класса** или **структура ссылки** ключевые слова, объекту осуществляется путем дескриптор объекта, то есть указателю счетчика ссылок на объект. Если объявленная переменная выходит за пределы области, компилятор автоматически удаляет базовый объект. Когда объект используется в качестве параметра в вызове или хранится в переменной, фактически передается или хранится только его дескриптор.

При объявлении объекта с помощью **класса значений** или **структура значения** ключевые слова, время жизни объявленного объекта не защищено. Этот объект аналогичен любому другому стандартному классу или структуре C++.

### <a name="requirements"></a>Требования

Параметр компилятора: `/ZW`

## <a name="common-language-runtime"></a>Среда CLR

### <a name="remarks"></a>Примечания

В следующей таблице перечислены отличия от синтаксиса, показанного в **все среды выполнения** раздел, относящиеся к C + +/ CLI.

### <a name="parameters"></a>Параметры

*base_type*<br/>
(Необязательно) Базовый тип. Объект **ссылочного класса** или **структура ссылки** может наследовать от нуля или нескольких управляемых интерфейсов и ноль или одного типа ссылки. Объект **класса значений** или **структура значения** может наследовать только от нуля или более управляемых интерфейсов.

**Ссылочного класса** и **структура ссылки** ключевые слова сообщают компилятору, класс или структура должны выделяться в куче. Когда объект используется в качестве параметра в вызове или хранится в переменной, фактически передается или хранится только ссылка на него.

**Класса значений** и **структура значения** ключевые слова сообщает компилятору, что значение выделенного класса или структуры передается функциям или сохраняется в членах.

### <a name="requirements"></a>Требования

Параметр компилятора: `/clr`

## <a name="see-also"></a>См. также

[Расширения компонентов для платформ среды выполнения](../windows/component-extensions-for-runtime-platforms.md)