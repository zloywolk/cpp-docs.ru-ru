---
title: Макрос Activatableclass | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ActivatableClass
- ActivatableClassWithFactory
- ActivatableClassWithFactoryEx
dev_langs:
- C++
helpviewer_keywords:
- ActivatableClassWithFactory
- ActivatableClass
- ActivatableClassWithFactoryEx
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5c97d69bbca685ca64245d5d784452029c14f73f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393637"
---
# <a name="activatableclass-macros"></a>Макрос ActivatableClass

Заполняет внутренний кэш, содержащий фабрику, можно создать экземпляр указанного класса.

## <a name="syntax"></a>Синтаксис

```cpp
ActivatableClass(
   className
);

ActivatableClassWithFactory(
   className,
   factory
);

ActivatableClassWithFactoryEx(
   className,
   factory,
   serverName
);
```

### <a name="parameters"></a>Параметры

*className*<br/>
Имя создаваемого класса.

*фабрики*<br/>
Фабрика, которая будет создавать экземпляр указанного класса.

*Имя_сервера*<br/>
Имя, которое определяет подмножество фабрики в модуле.

## <a name="remarks"></a>Примечания

Не используйте эти макросы с помощью классической COM, если вы не используете `#undef` директиву, чтобы убедиться, что `__WRL_WINRT_STRICT__` удаляется определение макроса.

## <a name="requirements"></a>Требования

**Заголовок:** module.h

**Пространство имен:** Microsoft::WRL

## <a name="see-also"></a>См. также

[Класс Module](../windows/module-class.md)