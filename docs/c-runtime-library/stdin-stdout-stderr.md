---
title: Потоки stdin, stdout, stderr | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- stdin
- stderr
- stdout
dev_langs:
- C++
helpviewer_keywords:
- stdout function
- standard output stream
- standard error stream
- stdin function
- standard input stream
- stderr function
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a36d5fd60a19222e6f802e5a14037fb01ff865f5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071982"
---
# <a name="stdin-stdout-stderr"></a>stdin, stdout, stderr

## <a name="syntax"></a>Синтаксис

```

      FILE *stdin; 
FILE *stdout; 
FILE *stderr; 
#include <stdio.h>
```

## <a name="remarks"></a>Примечания

Это стандартные потоки для ввода, вывода и вывода ошибок.

По умолчанию стандартный ввод — чтение с клавиатуры, в то время как стандартный вывод и стандартный вывод ошибок печатаются на экране.

Следующие указатели потока доступны для получения стандартных потоков:

|Указатель|Поток|
|-------------|------------|
|`stdin`|Стандартный ввод|
|**stdout**|Стандартный вывод|
|`stderr`|Стандартная ошибка|

Эти указатели можно использовать в качестве аргументов для функций. Некоторые функции, например **getchar** и `putchar`, используют `stdin` и **stdout** автоматически.

Эти указатели являются константами, и им не могут быть присвоены новые значения. Функцию `freopen` можно использовать, чтобы перенаправить потоки в файлы на диске или на другие устройства. Операционная система позволяет перенаправлять стандартный ввод и вывод программы на командном уровне.

## <a name="see-also"></a>См. также

[Потоковый ввод-вывод](../c-runtime-library/stream-i-o.md)<br/>
[Глобальные константы](../c-runtime-library/global-constants.md)