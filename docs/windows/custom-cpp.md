---
title: Custom (C++) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.custom
dev_langs:
- C++
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ec3ba8280ab481211d98c9dc5256c94e76e193e2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396453"
---
# <a name="custom-c"></a>custom (C++)

Определяет метаданные для объекта в библиотеке типов.

## <a name="syntax"></a>Синтаксис

```cpp
[ custom(
   uuid,
   value
) ];
```

### <a name="parameters"></a>Параметры

*uuid*<br/>
Уникальный идентификатор.

*значение*<br/>
Значение, которое можно поместить в тип variant.

## <a name="remarks"></a>Примечания

**Пользовательских** атрибут C++ приведет к сведения, которые нужно поместить в библиотеке типов. Вам потребуется средство, которое считывает пользовательское значение из библиотеки типов.

**Пользовательских** атрибут имеет ту же функциональность, что [пользовательских](/windows/desktop/Midl/custom) описании атрибута MIDL.

## <a name="requirements"></a>Требования

### <a name="attribute-context"></a>Контекст атрибута

|||
|-|-|
|**Применение**|COM не **интерфейс**, **класс**, **перечисления**s, `idl_module` методов, члены интерфейса, параметров интерфейса **typedef**s, **объединение**s, **структуры**s|
|**Повторяемый**|Да|
|**Обязательные атрибуты**|**Компонентный класс** (при использовании класса)|
|**Недопустимые атрибуты**|Нет|

Дополнительные сведения о контекстах атрибутов см. в разделе [Контексты атрибутов](../windows/attribute-contexts.md).

## <a name="see-also"></a>См. также

[Атрибуты IDL](../windows/idl-attributes.md)<br/>
[Изолированные атрибуты](../windows/stand-alone-attributes.md)<br/>
[Атрибуты Typedef, Enum, Union и Struct](../windows/typedef-enum-union-and-struct-attributes.md)<br/>
[Атрибуты параметра](../windows/parameter-attributes.md)<br/>
[Атрибуты метода](../windows/method-attributes.md)<br/>
[Атрибуты классов](../windows/class-attributes.md)<br/>
[Атрибуты интерфейса](../windows/interface-attributes.md)  