---
title: Ошибка компилятора C2488 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2488
dev_langs:
- C++
helpviewer_keywords:
- C2488
ms.assetid: cd435909-43e4-43c6-a57c-5d02468ef75f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f1bf2710acdc2a738b36ca9426ce55da9f6d769
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044345"
---
# <a name="compiler-error-c2488"></a>Ошибка компилятора C2488

«Идентификатор»: «naked» может применяться только для определения функций, не являющихся членами

[С атрибутом naked](../../cpp/naked-cpp.md) атрибут был применен к объявлению функции.

Следующий пример приводит к возникновению ошибки C2488:

```
// C2488.cpp
// compile with: /c
// processor: x86
__declspec( naked ) void func();   // C2488  declaration, not definition
__declspec( naked ) void i;   // C2488  i is not a function

__declspec( naked ) void func() {}   // OK
```