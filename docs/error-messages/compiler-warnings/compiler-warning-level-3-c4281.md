---
title: Предупреждение (уровень 3) C4281 компилятора | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4281
dev_langs:
- C++
helpviewer_keywords:
- C4281
ms.assetid: a9771261-5725-4fc6-87b6-16cf92113a25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 106269be7d63126854aa1396bd6045532b4102ed
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079145"
---
# <a name="compiler-warning-level-3-c4281"></a>Предупреждение компилятора (уровень 1) C4281

произошла рекурсия «operator ->» через тип «тип»

Код разрешает **operator ->** вызывать самого себя.

Следующий пример приводит к возникновению ошибки C4281:

```
// C4281.cpp
// compile with: /W3 /WX
struct A;
struct B;
struct C;

struct A
{
   int z;
   B& operator->();
};

struct B
{
   C& operator->();
};

struct C
{
   A& operator->();
};

void f(A p)
{
   int i = p->z; // C4281
}
```