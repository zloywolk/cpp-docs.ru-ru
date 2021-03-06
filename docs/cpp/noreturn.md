---
title: noreturn | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noreturn_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6133fc70c5c2b8bb8f794746c1d5ca11be97b817
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031045"
---
# <a name="noreturn"></a>noreturn

## <a name="microsoft-specific"></a>Блок, относящийся только к системам Microsoft

Это **__declspec** атрибут сообщает компилятору, что функция не возвращает. Как следствие, компилятор знает, что код, следующий вызов **__declspec(noreturn)** функция недоступен.

Если компилятор обнаруживает функцию с путем элемента управления, которая не возвращает значение, он создает предупреждение (C4715) или сообщение об ошибке (C2202). Если путь управления становится недоступным из-за функции, которая никогда не возвращает, можно использовать **__declspec(noreturn)** во избежание этого предупреждения или ошибки.

> [!NOTE]
>  Добавление **__declspec(noreturn)** на функцию, которая возвращает может привести к неопределенному поведению.

## <a name="example"></a>Пример

В следующем примере **else** предложение не содержит оператор return.  Объявление `fatal` как **__declspec(noreturn)** позволяет избежать ошибки или предупреждения.

```cpp
// noreturn2.cpp
__declspec(noreturn) extern void fatal () {}

int main() {
   if(1)
     return 1;
   else if(0)
     return 0;
   else
     fatal();
}
```

## <a name="see-also"></a>См. также

[__declspec](../cpp/declspec.md)<br/>
[Ключевые слова](../cpp/keywords-cpp.md)