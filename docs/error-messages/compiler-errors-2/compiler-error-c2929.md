---
title: Ошибка компилятора C2929 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2929
dev_langs:
- C++
helpviewer_keywords:
- C2929
ms.assetid: 11134027-6adc-4733-b6bd-b94486bd1933
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d7eee14296178fb90d4a3c34a28926032fcb04b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102831"
---
# <a name="compiler-error-c2929"></a>Ошибка компилятора C2929

"идентификатор": явное создание экземпляра; не удается принудительно использовать и запретить создание экземпляра члена класса-шаблона

Невозможно явно создать экземпляр идентификатора и при этом запретить его создание.

Следующий пример приводит к возникновению ошибки C2929:

```
// C2929.cpp
// compile with: /c
template<typename T>
class A {
public:
   A() {}
};

template A<int>::A();

extern template A<int>::A();   // C2929
```