---
title: Ошибка компилятора C3645 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3645
dev_langs:
- C++
helpviewer_keywords:
- C3645
ms.assetid: 346da528-ae86-4cd0-9654-f41bee26ac0d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d310ab3a9a4bd0b31b9e6295a93a571a54f585b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068914"
---
# <a name="compiler-error-c3645"></a>Ошибка компилятора C3645

«функция»: __clrcall невозможно использовать с функциями, скомпилированными в машинный код

Наличие некоторые ключевые слова в функции вызовет функцию для компиляции в машинный код.

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C3645.

```
// C3645.cpp
// compile with: /clr /c
#pragma unmanaged
int __clrcall dog() {}   // C3645
```