---
title: Ошибка средств компоновщика LNK1301 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1301
dev_langs:
- C++
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8646de5bb81120f6445e16b819b27da62ed9d5ec
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039950"
---
# <a name="linker-tools-error-lnk1301"></a>Ошибка средств компоновщика LNK1301

Найден, несовместимые с /LTCG:parameter модули среды LTCG clr

Модуле, скомпилированном с параметром/CLR и /GL передан компоновщику вместе с одной из профильной оптимизации (PGO) параметров/LTCG.

Оптимизация, управляемая профилями, не поддерживаются для модулей/CLR.

Дополнительные сведения:

- [/GL (оптимизация всей программы)](../../build/reference/gl-whole-program-optimization.md)

- [/LTCG (создание кода во время компоновки)](../../build/reference/ltcg-link-time-code-generation.md)

- [/clr (компиляция среды выполнения)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Профильная оптимизация](../../build/reference/profile-guided-optimizations.md)

### <a name="to-correct-this-error"></a>Исправление ошибки

1. Не компилировать с параметром/CLR или не создавать связь с одним из параметров профильной Оптимизации/LTCG.

## <a name="example"></a>Пример

В следующем примере возникает ошибка LNK1301:

```
// LNK1301.cpp
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj
// LNK1301 expected
class MyClass {
public:
   int i;
};
```