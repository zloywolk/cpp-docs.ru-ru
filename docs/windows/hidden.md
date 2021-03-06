---
title: скрытые | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.hidden
dev_langs:
- C++
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 726a44a33be5fe82986d4696c5420e07d5c103ff
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416465"
---
# <a name="hidden"></a>hidden

Указывает, что элемент существует, но не должен отображаться в пользовательском браузере.

## <a name="syntax"></a>Синтаксис

```cpp
[hidden]
```

## <a name="remarks"></a>Примечания

**Скрытые** атрибут C++ имеет ту же функциональность, что [скрытые](/windows/desktop/Midl/hidden) описании атрибута MIDL.

## <a name="example"></a>Пример

См. в примере [bindable](../windows/bindable.md) пример демонстрирует использование **скрытые**.

## <a name="requirements"></a>Требования

### <a name="attribute-context"></a>Контекст атрибута

|||
|-|-|
|**Применение**|**интерфейс**, **класс**, **структуры**, метод, свойство|
|**Повторяемый**|Нет|
|**Обязательные атрибуты**|**Компонентный класс** (при применении к **класс** или **структуры**)|
|**Недопустимые атрибуты**|Нет|

Дополнительные сведения см. в разделе [Контексты атрибутов](../windows/attribute-contexts.md).

## <a name="see-also"></a>См. также

[Атрибуты IDL](../windows/idl-attributes.md)<br/>
[Атрибуты интерфейса](../windows/interface-attributes.md)<br/>
[Атрибуты классов](../windows/class-attributes.md)<br/>
[Атрибуты метода](../windows/method-attributes.md)  