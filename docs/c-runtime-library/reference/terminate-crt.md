---
title: terminate (CRT) | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- terminate
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- terminate
dev_langs:
- C++
helpviewer_keywords:
- terminate function
- exception handling, termination
ms.assetid: 90e67402-08e9-4b2a-962c-66a8afd3ccb4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c743439b487f091b760e3747c47b471832e1ff3d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408678"
---
# <a name="terminate-crt"></a>terminate (CRT)

Вызовы [прервать](abort.md) или функции можно указать с помощью **set_terminate**.

## <a name="syntax"></a>Синтаксис

```C
void terminate( void );
```

## <a name="remarks"></a>Примечания

**Завершить** функция используется с обработкой исключений C++ и вызывается в следующих случаях:

- не удается найти подходящий обработчик catch для исключения C++;

- исключение создано деструктором во время очистки стека;

- стек поврежден после возникновения исключения.

**Завершение** вызовы [прервать](abort.md) по умолчанию. Это значение по умолчанию можно изменить, создав собственную функцию завершения и вызвав **set_terminate** с именем функции в качестве аргумента. **Завершение** вызывает последнюю функцию, заданную в качестве аргумента для **set_terminate**. Дополнительные сведения см. в разделе [Необработанные исключения C++](../../cpp/unhandled-cpp-exceptions.md).

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**terminate**|\<eh.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```cpp
// crt_terminate.cpp
// compile with: /EHsc
#include <eh.h>
#include <process.h>
#include <iostream>
using namespace std;

void term_func();

int main()
{
    int i = 10, j = 0, result;
    set_terminate( term_func );
    try
    {
        if( j == 0 )
            throw "Divide by zero!";
        else
            result = i/j;
    }
    catch( int )
    {
        cout << "Caught some integer exception.\n";
    }
    cout << "This should never print.\n";
}

void term_func()
{
    cout << "term_func() was called by terminate().\n";

    // ... cleanup tasks performed here

    // If this function does not exit, abort is called.

    exit(-1);
}
```

```Output
term_func() was called by terminate().
```

## <a name="see-also"></a>См. также

[Процедуры обработки исключений](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
