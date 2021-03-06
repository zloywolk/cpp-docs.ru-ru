---
title: Argtraitshelper-структура | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
dev_langs:
- C++
helpviewer_keywords:
- ArgTraitsHelper structure
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 314853b103d74bd7907fb665b806f386ed7bd44e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397474"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper - структура

Поддерживает инфраструктуру WRL и не предназначен для использования непосредственно из программного кода.

## <a name="syntax"></a>Синтаксис

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>Параметры

*TDelegateInterface*<br/>
Интерфейс делегата.

## <a name="remarks"></a>Примечания

Помогает определить общие характеристики аргументов делегата.

## <a name="members"></a>Участники

### <a name="public-typedefs"></a>Общедоступные определения типов

|Имя|Описание|
|----------|-----------------|
|`methodType`|Синоним для `decltype(&TDelegateInterface::Invoke)`.|
|`Traits`|Синоним для `ArgTraits<methodType>`.|

### <a name="public-constants"></a>Открытые константы

|name|Описание|
|----------|-----------------|
|[Константа ArgTraitsHelper::args](../windows/argtraitshelper-args-constant.md)|Помогает [ArgTraits::args](../windows/argtraits-args-constant.md) следить счетчик числа параметров `Invoke` метод для интерфейса делегата.|

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`ArgTraitsHelper`

## <a name="requirements"></a>Требования

**Заголовок:** event.h

**Пространство имен:** Microsoft::wrl:: Details

## <a name="see-also"></a>См. также

[Пространство имен Microsoft::WRL::Details](../windows/microsoft-wrl-details-namespace.md)