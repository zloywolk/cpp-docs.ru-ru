---
title: Ошибка компилятора C2524 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2524
dev_langs:
- C++
helpviewer_keywords:
- C2524
ms.assetid: e71d17f5-2fc2-416b-8dbd-e9bed85eb33a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e091abdf9f61512d99625c0111f73d0d5fc5315
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060685"
---
# <a name="compiler-error-c2524"></a>Ошибка компилятора C2524

«деструктор»: метод завершения или деструктор должен иметь список параметров «void»

Деструктор или метод завершения бы список параметров, не [void](../../cpp/void-cpp.md). Другие типы параметров не разрешены.

## <a name="example"></a>Пример

Следующий код приводит к возникновению C2524.

```
// C2524.cpp
// compile with: /c
class A {
   A() {}
   ~A(int i) {}    // C2524
   // try the following line instead
   // ~A() {}
};
```

## <a name="example"></a>Пример

Следующий код приводит к возникновению C2524.

```
// C2524_b.cpp
// compile with: /clr /c
ref struct I1 {
protected:
   !I1(int i);   // C2524
   // try the following line instead
   // !I1();
};
```