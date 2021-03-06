---
title: Члены структур и объединений | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- member-selection operators
- structure members, referencing
- -> operator, structure and union members
- dot operator (.)
- referencing structure members
- . operator
- operators [C], member selection
- structure member selection
ms.assetid: bb1fe304-af49-4f98-808d-afdc99b3e319
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a5b497745177bce165277e3a6e4ece2a3c47f20a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194879"
---
# <a name="structure-and-union-members"></a>Члены структур и объединений
Выражение выбора члена ссылается на члены структур и объединений. Такое выражение имеет значение и тип выбранного члена.  
  
> *postfix-expression* **.** *identifier*  
> *postfix-expression* **->** *identifier*
  
В следующем списке приводится описание двух форм выражений выбора члена.  
  
1.  В первой форме *postfix-expression* представляет значение типа **struct** или **union**, а *identifier* именует член указанной структуры или объединения. Значение операции совпадает с *identifier* и является l-значением, если *postfix-expression* является l-значением. Дополнительные сведения см. в разделе [Выражения l-значений и r-значений](../c-language/l-value-and-r-value-expressions.md).  
  
2.  Во второй форме *postfix-expression* представляет указатель на структуру или объединение, а *identifier* именует член указанной структуры или объединения. Это значение совпадает с *identifier* и является l-значением.  
  
 Две формы выражений выбора члена оказывают аналогичное влияние.  
  
 Фактически выражение, включающее оператор выбора члена (**->**), — это сокращенная версия выражения, использующего точку (**.**), если выражение перед точкой включает оператор косвенного обращения (<strong>\*</strong>), примененный к значению указателя. Поэтому  

```cpp
expression->identifier  
```

эквивалентно  

```cpp
(*expression).identifier
```

 если *expression* — значение указателя.  
  
## <a name="examples"></a>Примеры  
 Данное объявление структуры представлено в следующих примерах. Дополнительные сведения об операторе косвенного обращения (<strong>\*</strong>), используемом в этих примерах, см. в разделе [Операторы косвенного обращения и определения адреса](../c-language/indirection-and-address-of-operators.md).  
  
```  
struct pair   
{  
    int a;  
    int b;  
    struct pair *sp;  
} item, list[10];  
```  
  
 Выражение выбора члена для структуры `item` выглядит следующим образом.  
  
```  
item.sp = &item;  
```  
  
 В приведенном выше примере адрес структуры `item` присваивается члену `sp` структуры. Это означает, что `item` содержит указатель на себя.  
  
```  
(item.sp)->a = 24;  
```  
  
 В этом примере выражение указателя `item.sp` используется с оператором выбора члена (**->**) для присвоения значения члену `a`.  
  
```  
list[8].b = 12;  
```  
  
 На примере этого оператора показано, как выбрать отдельный член структуры из массива структур.  
  
## <a name="see-also"></a>См. также  
 [Операторы для доступа к членам: . и ->](../cpp/member-access-operators-dot-and.md)