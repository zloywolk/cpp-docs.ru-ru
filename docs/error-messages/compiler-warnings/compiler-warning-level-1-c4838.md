---
title: Предупреждение (уровень 1) C4838 компилятора | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- C4838
dev_langs:
- C++
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1335d9c36f6764b54689a8334a91f11275ee3265
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025455"
---
# <a name="compiler-warning-level-1-c4838"></a>Компилятор предупреждение (уровень 1) C4838

Преобразование «type_1» в «type_2» требует сужающего преобразования

Неявное сужающее преобразование найден, при использовании статистического выражения или список инициализации.

Языка C разрешает неявные сужающие преобразования в назначения и инициализации и C++ соответствует масти, несмотря на то, что Непредвиденная сужающим является причиной многих ошибок кода. Чтобы сделать код безопаснее, стандарт языка C++ требует диагностическое сообщение при возникновении сужающего преобразования в списке инициализации. В Visual C++ — диагностические [Ошибка компилятора C2397](../../error-messages/compiler-errors-1/compiler-error-c2397.md) при использовании единообразная инициализация синтаксиса поддерживается начиная с Visual Studio 2015. Компилятор создает предупреждение C4838 при использовании списка или синтаксиса агрегатной инициализации, поддерживаемых Visual Studio 2013.

Сужающее преобразование может быть допустимо, если известно, что возможный диапазон значений может поместиться в целевом объекте. В этом случае вы знаете более, чем компилятор. Если сужающее преобразование намеренно, предметными свои намерения с помощью приведения статический. В противном случае это предупреждающее сообщение почти всегда указывает на наличие ошибки в коде. Вы можете исправить, убедившись, что объекты, которые необходимо инициализировать имеют типы, которые достаточно велики для обработки входных данных.

Следующий пример приводит к возникновению ошибки C4838 и показан один из способов ее устранения:

```
// C4838.cpp -- C++ narrowing conversion diagnostics
// Compile by using: cl /EHsc C4838.cpp

struct S1 {
    int m1;
    double m2, m3;
};

void function_C4838(double d1) {
    double ad[] = { 1, d1 }; // OK
    int ai[] = { 1, d1 };    // warning C4838
    S1 s11 = { 1, 2, d1 };   // OK
    S1 s12 { d1, 2, 3 };     // warning C4838
    S1 s13 { static_cast<int>(d1), 2, 3 }; // possible fix for C4838
}
```