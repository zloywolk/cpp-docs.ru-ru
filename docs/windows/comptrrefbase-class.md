---
title: Comptrrefbase-класс | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase
dev_langs:
- C++
helpviewer_keywords:
- ComPtrRefBase class
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3ca2cb8cdc748abcac61bd548491187095b71a3f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415321"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase - класс

Поддерживает инфраструктуру WRL и не предназначен для использования непосредственно из программного кода.

## <a name="syntax"></a>Синтаксис

```cpp
template <
   typename T
>
class ComPtrRefBase;
```

### <a name="parameters"></a>Параметры

*T*<br/>
Объект [ComPtr\<T >](../windows/comptr-class.md) тип или тип, производный от него, а не просто интерфейс, представленный **ComPtr**.

## <a name="remarks"></a>Примечания

Представляет базовый класс для [ComPtrRef](../windows/comptrref-class.md) класса.

## <a name="members"></a>Участники

### <a name="public-typedefs"></a>Общедоступные определения типов

|Имя|Описание|
|----------|-----------------|
|`InterfaceType`|Синоним для типа параметра-шаблона *T*.|

### <a name="public-operators"></a>Открытые операторы

|Имя|Описание|
|----------|-----------------|
|[Оператор ComPtrRefBase::operator IInspectable**](../windows/comptrrefbase-operator-iinspectable-star-star-operator.md)|Приводит текущие [ptr_](../windows/comptrrefbase-ptr-data-member.md) данные-член в указатель к a указатель to `IInspectable` интерфейс.|
|[Оператор ComPtrRefBase::operator IUnknown**](../windows/comptrrefbase-operator-iunknown-star-star-operator.md)|Приводит текущие [ptr_](../windows/comptrrefbase-ptr-data-member.md) данные-член в указатель к a указатель to `IUnknown` интерфейс.|

### <a name="protected-data-members"></a>Защищенные члены данных

|name|Описание|
|----------|-----------------|
|[Элемент данных ComPtrRefBase::ptr_](../windows/comptrrefbase-ptr-data-member.md)|Указатель на тип, заданный текущим параметром шаблона.|

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`ComPtrRefBase`

## <a name="requirements"></a>Требования

**Заголовок:** client.h

**Пространство имен:** Microsoft::wrl:: Details

## <a name="see-also"></a>См. также

[Пространство имен Microsoft::WRL::Details](../windows/microsoft-wrl-details-namespace.md)