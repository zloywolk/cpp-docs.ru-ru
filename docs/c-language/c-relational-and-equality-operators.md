---
title: Операторы отношения и равенства в C | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- relational operators, syntax
- equality operator
- operators [C], equality
- equality operator, syntax
- operators [C], relational
ms.assetid: c89a3815-a65e-4e0d-8333-0e8dc7fdb30b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac6503b2c684b5acb921fe13ebf0b0ca11adbf04
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387587"
---
# <a name="c-relational-and-equality-operators"></a>Операторы отношения и равенства C
Операторы отношения и равенства сравнивают свои первые и вторые операнды для проверки истинности указанного отношения. Результат выражения отношения равен 1, если проверенное отношение истинно, или 0, если отношение ложно. Результат имеет тип `int`.  
  
 **Синтаксис**  
  
 *relational-expression*:  
 *shift-expression*  
  
 *relational-expression*  **\<**  *shift-expression*  
  
 *relational-expression*  **>**  *shift-expression*  
  
 *relational-expression*  **\<=**  *shift-expression*  
  
 *relational-expression*  **>=**  *shift-expression*  
  
 *equality-expression*:  
 *relational-expression*  
  
 *equality-expression*  **==**  *relational-expression*  
  
 *equality-expression*  **!=**  *relational-expression*  
  
 Операторы отношения и равенства проверяют следующие отношения.  
  
|Оператор|Проверяемое отношение|  
|--------------|-------------------------|  
|**\<**|Первый операнд меньше второго операнда|  
|**>**|Первый операнд больше второго операнда|  
|**\<=**|Первый операнд меньше или равен второму операнду|  
|**>=**|Первый операнд больше или равен второму операнду|  
|`==`|Первый операнд равен второму операнду|  
|`!=`|Первый операнд не равен второму операнду|  
  
 Первые четыре оператора в приведенном выше списке имеют более высокий приоритет, чем операторы равенства (`==` и `!=`). Сведения о приоритетах приведены в таблице [Приоритет и ассоциативность операторов C](../c-language/precedence-and-order-of-evaluation.md).  
  
 Операнды могут быть целыми числами, числами с плавающей запятой или указателями. Типы операндов могут быть разными. Операторы отношения выполняют обычные арифметические преобразования с операндами целого типа и типа с плавающей запятой. Кроме того, с операторами отношения и равенства можно использовать следующие сочетания типов операндов:  
  
-   Оба операнда любого оператора отношения или равенства могут быть указателями на один и тот же тип. Для операторов равенства (`==`) и неравенства (`!=`) результат сравнения показывает, указывают ли оба указателя на один и тот же адрес в памяти. Для других операторов отношения (**\<**, **>**, **\<**= и **>**=), результат сравнения показывает относительное положение двух адресов памяти для объектов, на которые указывают указатели. Операторы отношения сравнивают только смещения.  
  
     Сравнение указателей определено только для частей одного и того же объекта. Если указатели относятся к элементам массива, сравнение аналогично сравнению соответствующих индексов. Адрес первого элемента массива "меньше" адреса последнего элемента. В случае структур указатели на те члены структуры, которые были объявлены позже, "больше" указателей на члены, объявленные в структуре ранее. Указатели на члены одного объединения эквивалентны.  
  
-   Значение указателя можно сравнивать с постоянным значением 0 на равенство (`==`) или неравенство (`!=`). Указатель со значением 0 называется указателем "null"; иными словами, он не указывает на допустимое расположение в памяти.  
  
-   В операторах равенства используются те же правила, что и для операторов отношения, но допускаются дополнительные возможности: указатель можно сравнить с постоянным целочисленным выражением, имеющим значение 0, или с указателем на `void`. Два указателя "null" при сравнении считаются равными. Операторы равенства сравнивают как сегмент, так и смещение.  
  
## <a name="examples"></a>Примеры  
 Ниже показаны примеры операторов отношения и равенства.  
  
```  
int x = 0, y = 0;  
if ( x < y )  
```  
  
 Поскольку `x` и `y` равны, выражение в этом примере возвращает значение 0.  
  
```  
char array[10];  
char *p;  
  
for ( p = array; p < &array[10]; p++ )  
    *p = '\0';  
```  
  
 Фрагмент в этом примере задает для каждого элемента массива `array` постоянное символьное значение null.  
  
```  
enum color { red, white, green } col;  
   .  
   .  
   .  
   if ( col == red )  
   .  
   .  
   .  
```  
  
 Эти операторы объявляют переменную перечисления с именем `col` и тегом `color`. В любой момент времени эта переменная может содержать целочисленное значение 0, 1 или 2, которое представляет один из элементов перечисления `color`: красный, белый или зеленый цвет, соответственно. Если переменная `col` содержит значение 0 при выполнении оператора **if**, будут выполнены все операторы, зависящие от этого оператора **if**.  
  
## <a name="see-also"></a>См. также  
 [Операторы отношения: \<, >, \<= и >=](../cpp/relational-operators-equal-and-equal.md)   
 [Операторы равенства: == и !=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)