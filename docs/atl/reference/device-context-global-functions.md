---
title: Глобальные функции контекста устройства | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
dev_langs:
- C++
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac2e56e4b13f739f61df5b37ab70689784a39882
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077546"
---
# <a name="device-context-global-functions"></a>Глобальные функции контекста устройства

Эта функция создает контекст устройства для данного устройства.

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|Создает контекст устройства.|

##  <a name="atlcreatetargetdc"></a>  AtlCreateTargetDC

Создает контекст устройства для устройства, заданного в [DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice) структуры.

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>Параметры

*hdc*<br/>
[in] Существующий дескриптор контекста устройства, или значение NULL.

*ptd*<br/>
[in] Указатель на `DVTARGETDEVICE` структуру, содержащую сведения о целевом устройстве.

### <a name="return-value"></a>Возвращаемое значение

Возвращает дескриптор контекста устройства для устройства, заданного в `DVTARGETDEVICE`. Если устройство не указано, возвращает дескриптор для устройства отображения по умолчанию.

### <a name="remarks"></a>Примечания

Если структура имеет значение NULL и *hdc* имеет значение NULL, создает контекст устройства для устройства отображения по умолчанию.

Если *hdc* не равно NULL и *ptd* имеет значение NULL, функция возвращает существующий *hdc*.  

## <a name="requirements"></a>Требования

**Заголовок:** atlwin.h

## <a name="see-also"></a>См. также

[Функции](../../atl/reference/atl-functions.md)
