---
title: Ошибка компилятора C2511 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2511
dev_langs:
- C++
helpviewer_keywords:
- C2511
ms.assetid: df999efe-fe2b-418b-bb55-4af6a0592631
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b628adda383baee0f2ec03ace715d94c6cca764c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058150"
---
# <a name="compiler-error-c2511"></a>Ошибка компилятора C2511

«Идентификатор»: перегруженная функция-член не найден в «class»

Версия функции не объявлено с указанными параметрами.  Возможные причины:

1. Функция переданы неверные параметры.

1. Параметры, переданные в неверном порядке.

1. Неверное написание имен параметров.

Следующий пример приводит к возникновению ошибки C2511:

```
// C2511.cpp
// compile with: /c
class C {
   int c_2;
   int Func(char *, char *);
};

int C::Func(char *, char *, int i) {   // C2511
// try the following line instead
// int C::Func(char *, char *) {
   return 0;
}
```