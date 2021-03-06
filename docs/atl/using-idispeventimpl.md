---
title: Использование IDispEventImpl (ATL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IDispEventImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventImpl class, using
ms.assetid: 82d53b61-9d0d-45c5-aff9-2fafa468a9ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48afac392d02edfd3d312583642367bc6726e536
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106796"
---
# <a name="using-idispeventimpl"></a>Использование IDispEventImpl

При использовании `IDispEventImpl` для обработки событий, вам потребуется:

- Наследование класса из [IDispEventImpl](../atl/reference/idispeventimpl-class.md).

- Добавьте картой приемника событий к классу.

- Добавьте записи в карте приемника событий с помощью [SINK_ENTRY](reference/composite-control-macros.md#sink_entry) или [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex) макрос.

- Реализуйте методы, что вы заинтересованы в обработке.

- Уведомлений и негативной рекомендации источника события.

## <a name="example"></a>Пример

В приведенном ниже примере показано, как обрабатывать `DocumentChange` события, инициированные средой Word **приложения** объекта. Это событие определяется как метод на `ApplicationEvents` disp-интерфейса.

Пример взят из [ATLEventHandling пример](../visual-cpp-samples.md).  

```cpp
[ uuid(000209F7-0000-0000-C000-000000000046), hidden ]
dispinterface ApplicationEvents {
properties:
methods:
    [id(0x00000001), restricted, hidden]
    void Startup();

    [id(0x00000002)]
    void Quit();

    [id(0x00000003)]
    void DocumentChange();
};
```

В примере используется `#import` для создания файлов обязательный заголовок из библиотеки типов в Word. Если вы хотите использовать этот пример с другими версиями Word, необходимо указать правильный mso dll-файла. Например Office 2000 предоставляет mso9.dll и OfficeXP предоставляет mso.dll. Этот код является упрощенной версией stdafx.h:

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventimpl_1.h)]

В NotSoSimple.h отображается следующий код. Соответствующий код указан с комментариями:

[!code-cpp[NVC_ATL_EventHandlingSample#2](../atl/codesnippet/cpp/using-idispeventimpl_2.h)]

## <a name="see-also"></a>См. также

[Обработка событий](../atl/event-handling-and-atl.md)<br/>
[Пример ATLEventHandling](../visual-cpp-samples.md)

