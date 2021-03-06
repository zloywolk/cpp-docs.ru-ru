---
title: Предупреждение (уровень 4) C4459 компилятора | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4459
dev_langs:
- C++
helpviewer_keywords:
- C4459
ms.assetid: ee9f6287-9c70-4b10-82a0-add82a13997f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca0fc86be746bafdf4987a7492c59d9686535cef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040899"
---
# <a name="compiler-warning-level-4-c4459"></a>Компилятор предупреждение (уровень 4) C4459

> объявление "*идентификатор*" скрывает глобальное объявление

Объявление *идентификатор* в локальной области видимости скрывает объявление с идентичными именами *идентификатор* в глобальной области видимости. Это предупреждение позволяет узнать, что для ссылок *идентификатор* в этой области, разрешены с использованием локально объявленным версии, не глобальных версии, что может не соответствовать намерениям. Как правило мы рекомендуем свести к минимуму использование глобальных переменных в качестве стандартами разработки. Чтобы свести к минимуму засорения глобального пространства имен, рекомендуется использование именованного пространства имен для глобальных переменных.

Это предупреждение появился в Visual Studio 2015, в Visual C++ версии компилятора 18.00. Чтобы отключить предупреждения из этой версии компилятора или более поздней версии, при переносе кода, используйте [/Wv:18](../../build/reference/compiler-option-warning-level.md) параметр компилятора.

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C4459:

```cpp
// C4459_hide.cpp
// compile with: cl /W4 /EHsc C4459_hide.cpp
int global_or_local = 1;

int main() {
    int global_or_local; // warning C4459
    global_or_local = 2;
}
```

Один из способов решения этой проблемы является создание пространства имен для вашей глобальные переменные, но не используют `using` директиву, чтобы перевести это пространство имен в область, поэтому все ссылки должны использовать однозначный полные имена:

```cpp
// C4459_namespace.cpp
// compile with: cl /W4 /EHsc C4459_namespace.cpp
namespace globals {
    int global_or_local = 1;
}

int main() {
    int global_or_local; // OK
    global_or_local = 2;
    globals::global_or_local = 3;
}
```
