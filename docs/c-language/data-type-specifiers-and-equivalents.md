---
title: Спецификаторы и эквиваленты типов данных | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type specifiers [C++], list
- widening integers
- data types [C++], equivalents
- sign-extending integral types
- zero-extending
- identifiers, data type
- data types [C++], specifiers
- simple types, names
- type names [C++], simple
ms.assetid: 0d4b515a-4f68-4786-83cf-a5d43c7cb6f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68444d5ac8944e3c6679fce6397226d48206037f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092730"
---
# <a name="data-type-specifiers-and-equivalents"></a>Спецификаторы и эквиваленты типов данных

В этой книге в большинстве случаев вместо полных форм спецификаторов типов используются формы, приведенные в следующей таблице. При этом предполагается, что тип `char` является знаковым по умолчанию. Таким образом, если в этой книге указывается тип `char`, то это означает то же, что и **signed char**.

### <a name="type-specifiers-and-equivalents"></a>Спецификаторы типов и их эквиваленты

|Спецификаторы типов|Эквиваленты|
|--------------------|---------------------|
|**signed char**1|**char**|
|**signed int**|**signed**, **int**|
|**signed short int**|**short**, **signed short**|
|**signed long int**|**long**, **signed long**|
|**unsigned char**|—|
|**unsigned int**|**unsigned**|
|**unsigned short int**|**unsigned short**|
|**unsigned long int**|**unsigned long**|
|**float**|—|
|**long double**2|—|

1 Если вы указали, что тип **char** по умолчанию является беззнаковым (указав параметр компилятора /J), то вы не можете сократить спецификатор типа **signed char** до **char**.

2 В 32- и 64-разрядных операционных системах компилятор Microsoft С устанавливает соответствие между типами **long double** и **double**.

**Блок, относящийся только к системам Microsoft**

При помощи параметра компилятора /J можно указать, что тип **char** по умолчанию является не беззнаковым, а знаковым. При использовании этого параметра спецификатор **char** означает то же, что и **unsigned char**. Для объявления знакового символьного значения необходимо использовать ключевое слово **signed**. Если значение **char** явным образом объявлено как знаковое, то параметр /J на него не влияет и его расширение до типа **int** выполняется с расширением знака. Расширение типа **char** до типа **int** выполняется с дополнением нулями.

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Спецификаторы типов C](../c-language/c-type-specifiers.md)