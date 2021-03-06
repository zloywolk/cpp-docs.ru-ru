---
title: Структура _ATL_MODULE70 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f84b90613bcf542a9ace44505565951819fcaa91
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108447"
---
# <a name="atlmodule70-structure"></a>Структура _ATL_MODULE70

Содержит данные, используемые каждого модуля ATL.

## <a name="syntax"></a>Синтаксис

```
struct _ATL_MODULE70 {
    UINT cbSize;
    LONG m_nLockCnt;
    _ATL_TERMFUNC_ELEM* m_pTermFuncs;
    CComCriticalSection m_csStaticDataInitAndTypeInfo;
};
```

## <a name="members"></a>Участники

`cbSize`<br/>
Размер структуры, используемые для управления версиями.

`m_nLockCnt`<br/>
Чтобы определить, как долго должны оставаться активным модуль счетчика ссылок.

`m_pTermFuncs`<br/>
Отслеживает функции, которые были зарегистрированы для вызова при закрытии ATL.

`m_csStaticDataInitAndTypeInfo`<br/>
Используется для управления доступом к внутренним данным в многопоточной ситуации.

## <a name="remarks"></a>Примечания

[_ATL_MODULE](atl-typedefs.md#_atl_module) определяется как typedef типа `_ATL_MODULE70`.

## <a name="requirements"></a>Требования

**Заголовок:** atlbase.h

## <a name="see-also"></a>См. также

[Классы и структуры](../../atl/reference/atl-classes.md)

