---
title: _snscanf, _snscanf_l, _snwscanf, _snwscanf_l | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _snwscanf
- _snscanf_l
- _snscanf
- _snwscanf_l
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
apitype: DLLExport
f1_keywords:
- _snscanf
- _snscanf_l
- _snwscanf
- snscanf_l
- snscanf
- _sntscanf_l
- _sntscanf
- _snwscanf_l
- sntscanf_l
- sntscanf
- snwscanf
- snwscanf_l
dev_langs:
- C++
helpviewer_keywords:
- snscanf_l function
- snwscanf function
- _sntscanf_l function
- sntscanf function
- _snwscanf_l function
- _sntscanf function
- _snscanf_l function
- sntscanf_l function
- strings [C++], reading data from
- snscanf function
- snwscanf_l function
- _snwscanf function
- reading data, strings
- strings [C++], reading
- _snscanf function
ms.assetid: da1ac890-f905-4cd7-954b-3c90957b5551
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d5d99cc7465f88c92588983d5356a004da466de4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408348"
---
# <a name="snscanf-snscanfl-snwscanf-snwscanfl"></a>_snscanf, _snscanf_l, _snwscanf, _snwscanf_l

Считывает форматированные данные указанной длины из строки. Существуют более безопасные версии этих функций; см. раздел [_snscanf_s, _snscanf_s_l, _snwscanf_s, _snwscanf_s_l](snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md).

## <a name="syntax"></a>Синтаксис

```C
int __cdecl _snscanf(
   const char * input,
   size_t length,
   const char * format,
   ...
);
int __cdecl _snscanf_l(
   const char * input,
   size_t length,
   const char * format,
   locale_t locale,
   ...
);
int __cdecl _snwscanf(
   const wchar_t * input,
   size_t length,
   const wchar_t * format,
   ...
);
int __cdecl _snwscanf_l(
   const wchar_t * input,
   size_t length,
   const wchar_t * format,
   locale_t locale,
   ...
);
```

### <a name="parameters"></a>Параметры

*Входные данные*<br/>
Входная строка для анализа.

*length*<br/>
Число символов для анализа в *ввода*.

*format*<br/>
Один или несколько описателей формата.

*...*<br/>
Необязательные переменные, которые будут использоваться для хранения значений, извлеченных из входной строки с помощью описателей формата в *формат*.

*locale*<br/>
Используемый языковой стандарт.

## <a name="return-value"></a>Возвращаемое значение

Каждая из этих функций возвращает количество полей, которые были успешно преобразованы и присвоены; возвращаемое значение не включает поля, которые были считаны, но не были присвоены. Возвращаемое значение 0 указывает, что поля не были назначены. Возвращает значение **EOF** при возникновении ошибки или при достижении конца строки до первого преобразования. Дополнительные сведения см. в разделе [sscanf](sscanf-sscanf-l-swscanf-swscanf-l.md).

Если *ввода* или *формат* — **NULL** указателя, или если *длина* меньше или равно нулю, вызывается обработчик недопустимого параметра, как описанные в [проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, эти функции возвращают **EOF** и задайте **errno** для **EINVAL**.

Дополнительные сведения об этих и других кодах ошибок см. в разделе [_doserrno, errno, _sys_errlist и _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Примечания

Эта функция аналогична **sscanf** за исключением того, что она обеспечивает возможность задать фиксированное число символов для анализа входной строки. Дополнительные сведения см. в разделе [sscanf](sscanf-sscanf-l-swscanf-swscanf-l.md).

Версии этих функций с **_l** суффиксом идентичны, за исключением того, что они используют переданный параметр языкового стандарта вместо языкового стандарта текущего потока.

### <a name="generic-text-routine-mappings"></a>Универсальное текстовое сопоставление функций

|Подпрограмма Tchar.h|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_sntscanf**|**_snscanf**|**_snscanf**|**_snwscanf**|
|**_sntscanf_l**|**_snscanf_l**|**_snscanf_l**|**_snwscanf_l**|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_snscanf**, **_snscanf_l**|\<stdio.h>|
|**_snwscanf**, **_snwscanf_l**|\<stdio.h> или \<wchar.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_snscanf.c
// compile with: /W3

#include <stdio.h>
int main( )
{
   char  str1[] = "15 12 14...";
   wchar_t  str2[] = L"15 12 14...";
   char  s1[3];
   wchar_t  s2[3];
   int   i;
   float fp;

   i = _snscanf( str1, 6,  "%s %f", s1, &fp); // C4996
   // Note: _snscanf is deprecated; consider using _snscanf_s instead
   printf("_snscanf converted %d fields: ", i);
   printf("%s and %f\n", s1, fp);

   i = _snwscanf( str2, 6,  L"%s %f", s2, &fp); // C4996
   // Note: _snwscanf is deprecated; consider using _snwscanf_s instead
   wprintf(L"_snwscanf converted %d fields: ", i);
   wprintf(L"%s and %f\n", s2, fp);
}
```

```Output
_snscanf converted 2 fields: 15 and 12.000000
_snwscanf converted 2 fields: 15 and 12.000000
```

## <a name="see-also"></a>См. также

[Спецификация ширины scanf](../../c-runtime-library/scanf-width-specification.md)<br/>
