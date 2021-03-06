---
title: Предупреждение компилятора C4694 | Документы Microsoft
ms.date: 10/25/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4694
dev_langs:
- C++
helpviewer_keywords:
- C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33852b76f23e007625f86969119a22ee81305187
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271459"
---
# <a name="compiler-warning-c4694"></a>Предупреждение компилятора C4694

> "*класса*": Запечатанный абстрактный класс не может иметь базового класса*base_class*"

Абстрактный и запечатанный класс не может наследовать от ссылочного типа; запечатанный и абстрактный класс не может ни реализовывать функции базового класса, ни разрешать использовать себя в качестве базового класса.

Дополнительные сведения см. в разделе [абстрактный](../../windows/abstract-cpp-component-extensions.md), [запечатанный](../../windows/sealed-cpp-component-extensions.md), и [классы и структуры](../../windows/classes-and-structs-cpp-component-extensions.md).

Это предупреждение автоматически повышается до ошибки. Если вы хотите изменить такое поведение, используйте [#pragma warning](../../preprocessor/warning.md).

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C4694.

```cpp
// C4694.cpp
// compile with: /c /clr
ref struct A {};
ref struct B sealed abstract : A {};   // C4694
```