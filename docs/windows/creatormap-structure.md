---
title: Creatormap-структура | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
dev_langs:
- C++
helpviewer_keywords:
- CreatorMap structure
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0a622eaa40cedfd7bf22259cf81382290f20f3a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593738"
---
# <a name="creatormap-structure"></a>CreatorMap - структура

Поддерживает инфраструктуру библиотека шаблонов C++ среды выполнения Windows и не предназначен для использования непосредственно из программного кода.

## <a name="syntax"></a>Синтаксис

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>Примечания

Содержит сведения о том, как инициализировать, регистрации и отмены регистрации объектов.

**CreatorMap** содержит следующие сведения:

- Как инициализировать, регистрации и отмены регистрации объектов.

- Как сравнить данные активации, в зависимости от традиционную фабрику COM или среду выполнения Windows.

- Сведения об имени фабрики кэша и сервера для интерфейса.

## <a name="members"></a>Участники

### <a name="public-data-members"></a>Открытые члены данных

|Имя|Описание:|
|----------|-----------------|
|[Элемент данных CreatorMap::activationId](../windows/creatormap-activationid-data-member.md)|Представляет идентификатор объекта, который определяется либо идентификатор классического COM-класса, либо указать имя среды выполнения Windows.|
|[Элемент данных CreatorMap::factoryCache](../windows/creatormap-factorycache-data-member.md)|Сохраняет указатель на кэш фабрики для **CreatorMap**.|
|[Элемент данных CreatorMap::factoryCreator](../windows/creatormap-factorycreator-data-member.md)|Создает фабрику для указанного **CreatorMap**.|
|[Элемент данных CreatorMap::serverName](../windows/creatormap-servername-data-member.md)|Хранит имя сервера для **CreatorMap**.|

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`CreatorMap`

## <a name="requirements"></a>Требования

**Заголовок:** module.h

**Пространство имен:** Microsoft::wrl:: Details

## <a name="see-also"></a>См. также

[Пространство имен Microsoft::WRL::Details](../windows/microsoft-wrl-details-namespace.md)