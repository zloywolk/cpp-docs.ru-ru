---
title: Ошибка компилятора C3202 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3202
dev_langs:
- C++
helpviewer_keywords:
- C3202
ms.assetid: 23528a0c-5493-4804-9789-cd3c38e49fb9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 254843386943b677be6df2c1ab7f1da56265e1d8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070330"
---
# <a name="compiler-error-c3202"></a>Ошибка компилятора C3202

"имя_аргумента": недопустимый аргумент по умолчанию для параметра шаблона "параметр", требуется класс шаблона

Передан недопустимый аргумент по умолчанию для параметра шаблона.

Следующий пример приводит к возникновению ошибки C3202:

```
// C3202.cpp
template<typename T>
class X
{
};

class Z
{
};

template<template<typename U> class T1 = Z, typename T2> // C3202
class Y
{
};
```