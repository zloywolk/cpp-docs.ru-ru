---
title: Общие сведения о трансляции файлов | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- file translation [C++], about file translation
- translation [C++]
- translation phases
- files [C++], translation
- programs [C++], lexical conventions of
- preprocessing translation phase
ms.assetid: 5036c7b7-ccff-4e2c-b052-a9ea6c71af87
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 829afe53d5fde976b7877475cf577b6204be8aed
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051091"
---
# <a name="overview-of-file-translation"></a>Общие сведения о трансляции файлов

Программы на языке C++ подобно программам на языке C состоят из одного или нескольких файлов. Каждый из этих файлов преобразуется в указанном ниже концептуальном порядке (реальный порядок соответствует правилу "как если бы": преобразование должно происходить так, как если бы соблюдался следующий порядок действий).

1. Лексический анализ. На этом этапе преобразования сопоставляются символы, обрабатываются триграфы, соединяются строки и выполняется разбивка на лексемы.

2. Предварительная обработка. Этом этапе преобразования вводятся вспомогательные исходные файлы ссылается `#include` директивы, обрабатывает «преобразования в строку» и «преобразования в символы» директивы и выполняет маркера вставки и расширение макроса (см. в разделе [директивы препроцессора](../preprocessor/preprocessor-directives.md) в *справочника по препроцессору* Дополнительные сведения). Результат этапа предварительной обработки — последовательность токенов, которые в совокупности определяют "запись преобразования".

     Директивы препроцессора всегда начинаются со знака решетки (**#**) символ (то есть первый непробельный символ в строке, необходимо решетки). В строке может присутствовать только одна директива препроцессора. Пример:

    ```cpp
    #include <iostream>  // Include text of iostream in
                         //  translation unit.
    #define NDEBUG       // Define NDEBUG (NDEBUG contains empty
                         //  text string).
    ```

3. Создание кода. На этом этапе преобразования токены, созданные на этапе предварительной обработки, используются для создания объектного кода.

     Выполняется синтаксическая и семантическая проверка исходного кода.

См. в разделе [этапы преобразования](../preprocessor/phases-of-translation.md) в *справочника по препроцессору* Дополнительные сведения.

Препроцессор C++ — это строгое надмножество препроцессора ANSI C, но имеет ряд отличий. Ниже указано несколько различий между препроцессорами ANSI C и C++.

- Поддерживаются однострочные комментарии. См. в разделе [комментарии](../cpp/comments-cpp.md) Дополнительные сведения.

- Один предустановленный макрос `__cplusplus`, определяется только для C++. См. в разделе [предустановленные макросы](../preprocessor/predefined-macros.md) в *справочника по препроцессору* Дополнительные сведения.

- Препроцессор C не распознает операторы C++: **.** <strong>\*</strong>, **->** <strong>\*</strong>, и **::**. См. в разделе [операторы](../cpp/cpp-built-in-operators-precedence-and-associativity.md) и [выражения](../cpp/expressions-cpp.md), Дополнительные сведения об операторах.

## <a name="see-also"></a>См. также

[Лексические соглашения](../cpp/lexical-conventions.md)