---
title: Ошибка компилятора C2883 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2883
dev_langs:
- C++
helpviewer_keywords:
- C2883
ms.assetid: 5c6d689d-ed42-41ad-b5c0-e9c2e0b8c356
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50cc5b2abb34fae21bea78aa146e74b9aa9491c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019267"
---
# <a name="compiler-error-c2883"></a>Ошибка компилятора C2883

«name»: объявление функции вступает в конфликт с «идентификатор», представленное в объявление using

Предпринята попытка определить функцию более одного раза. Первое определение был сделан из пространства имен с `using` объявления. Вторая была локальное определение.

Следующий пример приводит к возникновению ошибки C2883:

```
// C2883.cpp
namespace A {
   void z(int);
}

int main() {
   using A::z;
   void z(int);   // C2883  z is already defined
}
```