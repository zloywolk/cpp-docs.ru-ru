---
title: Ошибка компилятора C2048 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2048
dev_langs:
- C++
helpviewer_keywords:
- C2048
ms.assetid: 44704726-85fc-42f0-afb9-194df8c4ca7c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dca0cf7e95f2a876760415d5c628287fab47227c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055836"
---
# <a name="compiler-error-c2048"></a>Ошибка компилятора C2048

несколько вариантов, используемых по умолчанию

Оператор `switch` содержит несколько меток `default` . Удалите одну из меток `default` для устранения этой ошибки.

В следующем примере возникает ошибка C2048:

```
// C2048.cpp
int main() {
   int a = 1;
   switch (a) {
      case 1:
         a = 0;
      default:
         a = 2;
      default:   // C2048
         a = 3;
   }
}
```

Возможное решение

```
// C2048b.cpp
int main() {
   int a = 1;
   switch (a) {
      case 1:
         a = 0;
      default:
         a = 2;
   }
}
```