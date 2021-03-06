---
title: char, wchar_t, char16_t, char32_t | Документация Майкрософт
ms.custom: ''
ms.date: 02/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- char_cpp
- char16_t_cpp
- wchar_t_cpp
- char32_t_cpp
dev_langs:
- C++
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9855dc406c56f82eb3ed87248316103397e44007
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112659"
---
# <a name="char-wchart-char16t-char32t"></a>char, wchar_t, char16_t, char32_t

Типы **char**, **wchar_t**, **char16_t** и **char32_t** встроенные типы, представляющие буквенно-цифровые символы, а также не буквенно-цифровых глифы и непечатаемые символы.

## <a name="syntax"></a>Синтаксис

```cpp
char     ch1{ 'a' };  // or { u8'a' }
wchar_t  ch2{ L'a' };
char16_t ch3{ u'a' };
char32_t ch4{ U'a' };
```

## <a name="remarks"></a>Примечания

**Char** тип был исходным символьным типом в C и C++. Тип **unsigned char** часто используется для представления *байтов*, который не является встроенным типом в C++. **Char** типа может использоваться для хранения символов из набора символов ASCII, или любой из наборов символов ISO-8859 и индивидуальных байтов многобайтовых символов, таких как Shift-JIS или кодировку UTF-8 в кодировку Юникод. Строки **char** типа называются *сузить* строк, даже в том случае, если используемый для кодирования многобайтовых символов. В компиляторе Microsoft **char** тип 8-разрядное.

**Wchar_t** тип является типом определяемого реализацией расширенных символов. В компиляторе Microsoft, он представляет 16-разрядное расширенный символ, используемый для хранения Юникода в кодировке UTF-16LE, собственный символ типа в операционных системах Windows. Расширенный символ версиях использование функции библиотеки универсальной среды выполнения C (UCRT) **wchar_t** и ее указатель и массива типов как параметры и возвращаемые значения, как расширенный символ версиях собственного API Windows.

**Char16_t** и **char32_t** типы представляют 16-разрядных и 32-разрядных расширенных символов, соответственно. Юникод в кодировке UTF-16 могут храниться в **char16_t** тип и Юникод в кодировке UTF-32 могут храниться в **char32_t** типа. Строки из этих типов и **wchar_t** являются все называются *широкий* строк, то, что этот термин часто применяется в частности в строки **wchar_t** типа.

В стандартной библиотеке C++ `basic_string` типа является специальным для узким и широким строк. Используйте `std::string` при символы имеют тип **char**, `std::u16string` при символы имеют тип **char16_t**, `std::u32string` при символы имеют тип **char32_t** , и `std::wstring` при символы имеют тип **wchar_t**. Другие типы, представляющие текст, включая `std::stringstream` и `std::cout` имеют специализации для строк.