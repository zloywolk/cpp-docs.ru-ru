---
title: Класс CComPtr | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
dev_langs:
- C++
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bba9e3cce5424fdba86c05c0fd94cb3a0d08a5bb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030928"
---
# <a name="ccomptr-class"></a>Класс CComPtr

Класс смарт-указатель для управления указателей интерфейса СОМ.

## <a name="syntax"></a>Синтаксис

```
template<class T>
class CComPtr
```

#### <a name="parameters"></a>Параметры

*T*<br/>
COM-интерфейс, указав тип указателя для сохранения.

## <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Описание|
|----------|-----------------|
|[CComPtr::CComPtr](#ccomptr)|Конструктор.|

### <a name="public-operators"></a>Открытые операторы

|Имя|Описание|
|----------|-----------------|
|[CComPtr::operator =](#operator_eq)|Присваивает указатель на указатель элемента.|

## <a name="remarks"></a>Примечания

Использует ATL `CComPtr` и [CComQIPtr](../../atl/reference/ccomqiptr-class.md) для управления указателей интерфейса СОМ. Оба являются производными от [CComPtrBase](../../atl/reference/ccomptrbase-class.md), и оба средства выполняют подсчет автоматических ссылок.

`CComPtr` И [CComQIPtr](../../atl/reference/ccomqiptr-class.md) классов может помочь избежать утечек памяти, выполняя подсчет автоматических ссылок.  Следующие функции оба выполняют те же логические операции; Тем не менее, обратите внимание, как вторая версия может быть меньше ошибок с помощью `CComPtr` класса:

[!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]

[!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]

В отладочных сборках свяжите atlsd.lib для трассировки кода.

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

`CComPtr`

## <a name="requirements"></a>Требования

**Заголовок:** atlbase.h

##  <a name="ccomptr"></a>  CComPtr::CComPtr

Конструктор.

```
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```

### <a name="parameters"></a>Параметры

*к пулу журналов*<br/>
Позволяет инициализировать указатель интерфейса.

*T*<br/>
COM-интерфейса.

##  <a name="operator_eq"></a>  CComPtr::operator =

Оператор присвоения.

```
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает указатель на обновленный `CComPtr` объекта

### <a name="remarks"></a>Примечания

Данная операция AddRefs новый объект и выпуски существующий объект, если он существует.

## <a name="see-also"></a>См. также

[CComPtr::CComPtr](#ccomptr)<br/>
[CComQIPtr::CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)<br/>
[Общие сведения о классе](../../atl/atl-class-overview.md)
