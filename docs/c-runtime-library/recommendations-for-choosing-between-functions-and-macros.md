---
title: Рекомендации по выбору между функциями и макросами | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.functions
dev_langs:
- C++
helpviewer_keywords:
- functions [CRT], vs. macros
- macros, vs. functions
ms.assetid: 18a633d6-cf1c-470c-a649-fa7677473e2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e347da977b58621529564f6e6d8646bd72063a0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023271"
---
# <a name="recommendations-for-choosing-between-functions-and-macros"></a>Рекомендации по выбору между функциями и макросами

Большинство подпрограмм библиотеки времени выполнения Microsoft — это скомпилированные или собранные функции, но некоторые подпрограммы реализованы в виде макросов. Если в файле заголовка для подпрограммы объявляется и функция, и макрос, определение макроса имеет приоритет, поскольку оно всегда находится после объявления функций. При вызове подпрограммы, которая реализована и как функция, и как макрос, можно заставить компилятор использовать функцию двумя способами:

- Заключить имя подпрограммы в скобки.

    ```C
    #include <ctype.h>
    a = _toupper(a);    // Use macro version of toupper.
    a = (_toupper)(a);  // Force compiler to use
                        // function version of toupper.
    ```

- Отменить определение макроса с помощью директивы `#undef`:

    ```C
    #include <ctype.h>
    #undef _toupper
    ```

Если необходимо выбрать между реализацией библиотечной подпрограммы в виде функции или макроса, учитывайте следующие компромиссы:

- **Скорость или размер.** Основным преимуществом использования макросов является меньшее время выполнения. Во время предварительной обработки макрос разворачивается (заменяется его определением) в тексте программы каждый раз, когда он используется. Определение функции задается только один раз независимо от количества вызовов. Макросы могут увеличить размер кода, но не создают дополнительную служебную нагрузку, связанную с вызовами функции.

- **Вычисление функции.** Функция может вычисляться как адрес, а макрос — нет. Поэтому невозможно использовать имя макроса в контекстах, где требуется указатель. Например, можно объявить указатель на функцию, но не указатель на макрос.

- **Проверка типов.** При объявлении функции компилятор может проверить типы аргументов. Поскольку невозможно объявить макрос, компилятор не может проверить типы аргументов макроса; хотя он может проверить количество аргументов, передаваемых макросу.

## <a name="see-also"></a>См. также

[Функции библиотеки CRT](../c-runtime-library/crt-library-features.md)