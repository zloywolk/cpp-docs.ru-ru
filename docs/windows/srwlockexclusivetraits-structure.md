---
title: Srwlockexclusivetraits-структура | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
dev_langs:
- C++
helpviewer_keywords:
- SRWLockExclusiveTraits structure
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 542ad92aa636c934e3250817931dd7f31d1fe85b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601607"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits - структура

Описывает общие характеристики `SRWLock` класс в режиме эксклюзивной блокировки.

## <a name="syntax"></a>Синтаксис

```cpp
struct SRWLockExclusiveTraits;
```

## <a name="members"></a>Участники

### <a name="public-typedefs"></a>Общедоступные определения типов

|Имя|Описание:|
|----------|-----------------|
|`Type`|Синоним для указателя на [SRWLOCK](../windows/srwlock-class.md) класса.|

### <a name="public-methods"></a>Открытые методы

|Имя|Описание:|
|----------|-----------------|
|[Метод SRWLockExclusiveTraits::GetInvalidValue](../windows/srwlockexclusivetraits-getinvalidvalue-method.md)|Извлекает **SRWLockExclusiveTraits** объект, который всегда является недопустимым.|
|[Метод SRWLockExclusiveTraits::Unlock](../windows/srwlockexclusivetraits-unlock-method.md)|Освобождает управлением указанного `SRWLock` объекта.|

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`SRWLockExclusiveTraits`

## <a name="requirements"></a>Требования

**Заголовок:** corewrappers.h

**Пространство имен:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>См. также

[Пространство имен Microsoft::WRL::Wrappers::HandleTraits](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)