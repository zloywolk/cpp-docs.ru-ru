---
title: Mutextraits-структура | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits
dev_langs:
- C++
helpviewer_keywords:
- MutexTraits structure
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 529265c4b1e5f510a92295a1ceff6d0a012163fe
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584175"
---
# <a name="mutextraits-structure"></a>MutexTraits - структура

Определяет общие характеристики [мьютекс](../windows/mutex-class1.md) класса.

## <a name="syntax"></a>Синтаксис

```cpp
struct MutexTraits : HANDLENullTraits;
```

## <a name="members"></a>Участники

### <a name="public-methods"></a>Открытые методы

|Имя|Описание:|
|----------|-----------------|
|[Метод MutexTraits::Unlock](../windows/mutextraits-unlock-method.md)|Освобождает управлением общего ресурса.|

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`HANDLENullTraits`

`MutexTraits`

## <a name="requirements"></a>Требования

**Заголовок:** corewrappers.h

**Пространство имен:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>См. также

[Пространство имен Microsoft::WRL::Wrappers::HandleTraits](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)