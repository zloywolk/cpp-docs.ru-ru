---
title: Ошибка компилятора C2201 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2201
dev_langs:
- C++
helpviewer_keywords:
- C2201
ms.assetid: ed927659-6e9c-447d-9963-19969ae1e957
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b24e18d2f8ffdfa889cac3dae58e66dcb8d7dcc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107135"
---
# <a name="compiler-error-c2201"></a>Ошибка компилятора C2201

«Идентификатор»: для экспорта или импорта требуется внешняя компоновка

Тип экспортируемого идентификатора — `static`.

При компиляции следующего примера возникнет ошибка C2286:

```
// C2201.cpp
// compile with: /c
__declspec(dllexport) static void func() {}   // C2201 func() is static
__declspec(dllexport) void func2() {}   // OK
```

## <a name="see-also"></a>См. также

[Типы компоновки](../../cpp/types-of-linkage.md)