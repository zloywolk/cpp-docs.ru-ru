---
title: Неустранимая ошибка C1107 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1107
dev_langs:
- C++
helpviewer_keywords:
- C1107
ms.assetid: 541a4d9f-10bc-4dd8-b68e-15e548f3dc0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc896f08ac161cae4e4fab5e991da810f3faf195
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016641"
---
# <a name="fatal-error-c1107"></a>Неустранимая ошибка C1107

не удалось найти сборку «файл»: укажите путь поиска сборок с помощью переключателя /AI или переменной среды LIBPATH

Файл метаданных был передан [#using](../../preprocessor/hash-using-directive-cpp.md) директивы, компилятору не удалось найти.

LIBPATH, который описан в разделе, посвященном `#using`и [/AI](../../build/reference/ai-specify-metadata-directories.md) параметр компилятора позволяют указать каталоги, в которых компилятор будет искать файлы метаданных, на который указывает ссылка.