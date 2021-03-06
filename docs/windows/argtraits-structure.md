---
title: Argtraits-структура | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits
dev_langs:
- C++
helpviewer_keywords:
- ArgTraits structure
ms.assetid: 58ae4115-c1bc-48c8-b01b-e60554841c30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 047754338566d476fa8e832d58dd2d4cd0776a63
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418402"
---
# <a name="argtraits-structure"></a>ArgTraits - структура

Поддерживает инфраструктуру WRL и не предназначен для использования непосредственно из программного кода.

## <a name="syntax"></a>Синтаксис

```cpp
template<typename TMemberFunction>
struct ArgTraits;
template<typename TDelegateInterface>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(void)>;
template<
   typename TDelegateInterface,
   typename TArg1
>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1)>;
template<
   typename TDelegateInterface,
   typename TArg1,
   typename TArg2
>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2)>;
template<
   typename TDelegateInterface,
   typename TArg1,
   typename TArg2,
   typename TArg3
>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3)>;
template<
   typename TDelegateInterface,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4
>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4)>;
template<
   typename TDelegateInterface,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5
>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5)>;
template<
   typename TDelegateInterface,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6
>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5, TArg6)>;
template<
   typename TDelegateInterface,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7
>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7)>;
template<
   typename TDelegateInterface,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8
>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8)>;
template<
   typename TDelegateInterface,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8,
   typename TArg9
>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8, TArg9)>;
```

### <a name="parameters"></a>Параметры

*TMemberFunction*<br/>
Параметр имени типа для структуры ArgTraits, который не соответствует ни одному `Invoke` сигнатуру метода.

*TDelegateInterface*<br/>
Интерфейс делегата.

*TArg1*<br/>
Тип первого аргумента `Invoke` метод.

*TArg2*<br/>
Тип второго аргумента `Invoke` метод.

*TArg3*<br/>
Тип третьего аргумента `Invoke` метод.

*TArg4*<br/>
Тип четвертого аргумента `Invoke` метод.

*TArg5*<br/>
Тип пятого аргумента `Invoke` метод.

*TArg6*<br/>
Тип шестого аргумента `Invoke` метод.

*TArg7*<br/>
Тип седьмого аргумента `Invoke` метод.

*TArg8*<br/>
Тип восьмого аргумента `Invoke` метод.

*TArg9*<br/>
Тип девятого аргумента `Invoke` метод.

## <a name="remarks"></a>Примечания

**ArgTraits** структура объявляет указанный делегат, интерфейс и анонимную функцию-член, имеющий указанное число параметров.

## <a name="members"></a>Участники

### <a name="public-typedefs"></a>Общедоступные определения типов

|Имя|Описание|
|----------|-----------------|
|`Arg1Type`|Typedef для TArg1.|
|`Arg2Type`|Typedef для TArg2.|
|`Arg3Type`|Typedef для TArg3.|
|`Arg4Type`|Typedef для TArg4.|
|`Arg5Type`|Typedef для TArg5.|
|`Arg6Type`|Typedef для TArg6.|
|`Arg7Type`|Typedef для TArg7.|
|`Arg8Type`|Typedef для TArg8.|
|`Arg9Type`|Typedef для TArg9.|

### <a name="public-constants"></a>Открытые константы

|name|Описание|
|----------|-----------------|
|[Константа ArgTraits::args](../windows/argtraits-args-constant.md)|Ведет статистику, число параметров `Invoke` метод для интерфейса делегата.|

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`ArgTraits`

## <a name="requirements"></a>Требования

**Заголовок:** event.h

**Пространство имен:** Microsoft::wrl:: Details

## <a name="see-also"></a>См. также

[Пространство имен Microsoft::WRL::Details](../windows/microsoft-wrl-details-namespace.md)