---
title: источник (C++) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.source
dev_langs:
- C++
helpviewer_keywords:
- source attribute
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d3f4cacd380a86138095b0f8b3bf67f860d45cda
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390543"
---
# <a name="source-c"></a>source (C++)

В классе, задает интерфейсы COM-объекта источника для точек подключения. На свойства или метода указывает, что член возвращает объект или переменная типа VARIANT, являющейся источником событий.

## <a name="syntax"></a>Синтаксис

```cpp
[ source(
   interfaces
) ]
```

### <a name="parameters"></a>Параметры

*interfaces*<br/>
Один или несколько интерфейсов, укажите при применении исходного атрибута к классу. Этот параметр не используется, когда источника применяется к свойству или методу.

## <a name="remarks"></a>Примечания

**Источника** атрибут C++ имеет ту же функциональность, что [источника](/windows/desktop/Midl/source) описании атрибута MIDL.

Можно использовать [по умолчанию](../windows/default-cpp.md) атрибут для указания интерфейсе источника по умолчанию для объекта.

## <a name="example"></a>Пример

```cpp
// cpp_attr_ref_source.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid(11111111-1111-1111-1111-111111111111)]
__interface b
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT get_I([out, retval]long *i);
};

[object, uuid(11111111-1111-1111-1111-111111111131)]
__interface c
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT et_I([out, retval]long *i);
};

[coclass, default(c), uuid(11111111-1111-1111-1111-111111111132)]
class N : public b
{
};

[coclass, source(c), default(b, c), uuid(11111111-1111-1111-1111-111111111133)]
class NN : public b
{
};
```

## <a name="requirements"></a>Требования

### <a name="attribute-context"></a>Контекст атрибута

|||
|-|-|
|**Применение**|**Класс**, **структуры**, **интерфейс**|
|**Повторяемый**|Нет|
|**Обязательные атрибуты**|`coclass` (когда применимы к классам или структурам)|
|**Недопустимые атрибуты**|Нет|

Дополнительные сведения о контекстах атрибутов см. в разделе [Контексты атрибутов](../windows/attribute-contexts.md).

## <a name="see-also"></a>См. также

[Атрибуты IDL](../windows/idl-attributes.md)<br/>
[Атрибуты классов](../windows/class-attributes.md)<br/>
[Атрибуты метода](../windows/method-attributes.md)<br/>
[coclass](../windows/coclass.md)  