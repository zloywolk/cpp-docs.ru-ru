---
title: Ошибка компилятора C3732 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3732
dev_langs:
- C++
helpviewer_keywords:
- C3732
ms.assetid: 2d55a7e1-9c39-4379-a093-2f7beb27e2ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 187a7079eee1bc3b5ce36f29b8fbaef67c64fc59
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092795"
---
# <a name="compiler-error-c3732"></a>Ошибка компилятора C3732

«интерфейс»: настраиваемый интерфейс, порождающий COM-события не может наследовать от интерфейса IDispatch

Интерфейс, поддерживающий события COM не может наследовать от `IDispatch`. Дополнительные сведения см. в разделе [обработка событий в COM](../../cpp/event-handling-in-com.md).

Следующая ошибка приводит к возникновению ошибки C3732:

```
// C3732.cpp
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[module(name="test")];

// to resolve this C3732, use dual instead of object
// or inherit from IUnknown
[ object ]
__interface I : IDispatch
{
};

[ event_source(com), coclass ]
struct A
{
   __event __interface I;   // C3732
};

int main()
{
}
```