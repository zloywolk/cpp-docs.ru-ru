---
title: Предупреждение средств компоновщика LNK4105 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4105
dev_langs:
- C++
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4411421741cf8bf7c714a6322d58bd177e7e7270
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024987"
---
# <a name="linker-tools-warning-lnk4105"></a>Предупреждение средств компоновщика LNK4105

не указаны аргументы параметра «параметр»; параметр игнорируется

Это предупреждение возникает только при [/LIBPATH](../../build/reference/libpath-additional-libpath.md) параметр имеет значение. Если каталог не указан с помощью этого параметра, компоновщик игнорирует параметр и создает это предупреждающее сообщение.

Если вам не нужно переопределить существующие параметры окружения библиотеки, удалите параметр/LIBPATH из командной строки компоновщика. Если вы хотите использовать поиска альтернативный путь для библиотек, укажите альтернативный путь после параметра/LIBPATH.

## <a name="example"></a>Пример

```
link /libpath:c:\filepath\lib bar.obj
```

компоновщиком для поиска необходимых библиотек в `c:\filepath\lib` перед поиском в расположениях по умолчанию.