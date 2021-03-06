---
title: Предупреждение компилятора (уровень 1) C4733 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4733
dev_langs:
- C++
helpviewer_keywords:
- C4733
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75b4aac2d71267b4ba012384fe83f167f44ec2d2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092938"
---
# <a name="compiler-warning-level-1-c4733"></a>Предупреждение компилятора (уровень 1) C4733

Присваивание для «FS:0»: обработчик не зарегистрирован как безопасный

Функция, изменив значение в FS:0, чтобы добавить новый обработчик исключений может не работать с безопасных исключений, поскольку обработчик не может быть зарегистрирован как допустимый обработчик исключений (см. в разделе [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)).

Чтобы устранить это предупреждение, либо удалите определения FS:0 или отключить это предупреждение и используйте [. SAFESEH](../../assembler/masm/dot-safeseh.md) для указания безопасных обработчиков исключений.

Следующий пример приводит к возникновению ошибки C4733:

```
// C4733.cpp
// compile with: /W1 /c
// processor: x86
#include "stdlib.h"
#include "stdio.h"
void my_handler()
{
   printf("Hello from my_handler\n");
   exit(1);
}

int main()
{
   _asm {
      push    my_handler
      mov     eax, DWORD PTR fs:0
      push    eax
      mov     DWORD PTR fs:0, esp   // C4733
   }

   *(int*)0 = 0;
}
```