---
title: для Statement (C) | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- for keyword [C]
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5f0090195506e26cab165e3ddadca0342c0b35b6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084059"
---
# <a name="for-statement-c"></a>Оператор for (C)

Оператор **for** позволяет повторить выполнение того или иного оператора или составного оператора заданное число раз. Тело оператора **for** выполняется ноль или более раз, пока необязательное условие не примет значение false. Внутри оператора **for** можно использовать необязательные выражения для инициализации и изменения значений во время выполнения этого оператора (**for**).

## <a name="syntax"></a>Синтаксис

*оператор-итерации*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**for** **(** *init-expression*<sub>opt</sub> **;** *cond-expression*<sub>opt</sub> **;** *loop-expression*<sub>opt</sub> **)** *statement*

Оператор **for** выполняется следующим образом:

1. Вычисляется выражение *init-expression* (если есть). Оно определяет инициализацию цикла. На тип выражения *init-expression* ограничений не накладывается.

2. Вычисляется выражение *cond-expression* (если есть). Это выражение должно иметь арифметический тип или тип указателя. Оно вычисляется перед каждой итерацией. Возможны три результата.

   - Если выражение *cond-expression* возвращает **true** (ненулевое значение), выполняется оператор *statement*, после чего вычисляется выражение *loop-expression* (если есть). Выражение *loop-expression* вычисляется после завершения каждой итерации. На его тип ограничений не накладывается. Побочные эффекты выполняются по порядку. Затем процесс начинается снова с вычисления выражения *cond-expression*.

   - Если выражение *cond-expression* опущено, оно (*cond-expression*) считается равным true, а выполнение продолжается согласно описанию в предыдущем абзаце. Выполнение оператора **for** без аргумента *cond-expression* завершается только при выполнении в его теле оператора **break** или **return** либо при выполнении оператора перехода **goto** к оператору с меткой вне тела оператора **for**.

   - Если значение *cond-expression* равно **false** (0), выполнение оператора **for** завершается и управление передается следующему оператору программы.

Выполнение оператора **for** может также завершаться, если в теле оператора выполняется оператор **break**, **goto** или **return**. Оператор **continue** в цикле **for** задает дальнейшее вычисление выражения *loop-expression*. При выполнении оператора **break** в цикле **for** выражение *loop-expression* не вычисляется и не выполняется. Оператор

```C
for( ; ; )
```

представляет общепринятый способ создания бесконечного цикла, выход из которого возможен только с помощью оператора **break**, **goto** или **return**.

## <a name="example"></a>Пример

В следующем примере показано использование оператора **for**:

```C
// c_for.c
int main()
{
   char* line = "H e  \tl\tlo World\0";
   int space = 0;
   int tab = 0;
   int i;
   int max = strlen(line);
   for (i = 0; i < max; i++ )
   {
      if ( line[i] == ' ' )
      {
          space++;
      }
      if ( line[i] == '\t' )
      {
          tab++;
      }
   }

   printf("Number of spaces: %i\n", space);
   printf("Number of tabs: %i\n", tab);
   return 0;
}
```

## <a name="output"></a>Вывод

```Output
Number of spaces: 4
Number of tabs: 2
```

## <a name="see-also"></a>См. также

[Операторы](../c-language/statements-c.md)