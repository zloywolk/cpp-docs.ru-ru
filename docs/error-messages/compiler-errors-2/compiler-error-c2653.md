---
title: Ошибка компилятора C2653 | Документы Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2653
dev_langs:
- C++
helpviewer_keywords:
- C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8e1df7dd6337b1a3e363a5744181b12d94c879b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234971"
---
# <a name="compiler-error-c2653"></a>Ошибка компилятора C2653

> "*идентификатор*": не является именем класса или пространства имен

Синтаксис языка требует класса, структуры, объединения или имя пространства имен.

Эта ошибка может возникать при использовании имени, который не был объявлен как класс, структура, объединение или пространство имен перед оператором области действия. Чтобы устранить эту проблему, объявите имя или включать заголовок, который объявляет имя, прежде чем он используется.

C2653 можно также при попытке определить *составное пространство имен*, пространство имен, которое содержит одно или несколько имен вложенной области видимости пространства имен. Составные пространства имен определения не допускаются в C++ до C ++ 17. Составные пространства имен поддерживаются начиная с Visual Studio 2015 с обновлением 3, при указании [/std: c ++ последнюю](../../build/reference/std-specify-language-standard-version.md) параметр компилятора. Начиная с версии 15,5 2017 г. Visual C++, компилятор поддерживает составное пространство имен определения при [/std: c ++ 17](../../build/reference/std-specify-language-standard-version.md) параметра.

## <a name="examples"></a>Примеры

В этом примере приводит к возникновению ошибки C2653, так как используется имя области, но не объявлен. Компилятор ожидает класса, структуры, объединения или имя пространства имен перед оператором области действия (::).

```cpp
// C2653.cpp
// compile with: /c
class yy {
   void func1(int i);
};

void xx::func1(int m) {}   // C2653, xx is not declared
void yy::func1(int m) {}   // OK
```

В коде, который не компилируется для C ++ 17 или более поздней версии стандартов вложенные пространства имен необходимо использовать объявление явное пространство имен на каждом уровне вложенности:

```cpp
// C2653b.cpp
namespace a::b {int i;}   // C2653 prior to Visual C++ 2015 Update 3,
                          // C2429 thereafter. Use /std:c++17 or /std:c++latest to fix.

namespace a {             // Use this form for compliant code under /std:c++14 (the default)
   namespace b {          // or when using compilers before Visual Studio 2015 update 3.
      int i;
   }
}

int main() {
   a::b::i = 2;
}
```
