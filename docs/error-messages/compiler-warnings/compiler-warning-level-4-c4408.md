---
title: Предупреждение компилятора (уровень 4) C4408 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4408
dev_langs:
- C++
helpviewer_keywords:
- C4408
ms.assetid: 8488a186-ed1d-425c-aaeb-c72472c1da68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7f804f8cbc3dce846783ce4937d7902d760511e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050194"
---
# <a name="compiler-warning-level-4-c4408"></a>Предупреждение компилятора (уровень 4) C4408

anonymousstruct или объединение не объявляет никаких элементов данных

У анонимной структуры или объединения должен быть по крайней мере один элемент данных.

Следующий пример приводит к возникновению ошибки C4408.

```
// C4408.cpp
// compile with: /W4 /LD
static union
{
   // int i;
};
// a named union can have no data members
// } MyUnion;
```