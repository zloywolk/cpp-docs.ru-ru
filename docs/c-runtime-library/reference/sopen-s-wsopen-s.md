---
title: _sopen_s, _wsopen_s | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _sopen_s
- _wsopen_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _sopen_s
- wsopen_s
- _wsopen_s
- sopen_s
dev_langs:
- C++
helpviewer_keywords:
- sopen_s function
- _wsopen_s function
- wsopen_s function
- opening files, for sharing
- files [C++], opening
- _sopen_s function
- files [C++], sharing
ms.assetid: 059a0084-d08c-4973-9174-55e391b72aa2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c94219ff0b357e7627528d68938ec430fd8dc14
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418488"
---
# <a name="sopens-wsopens"></a>_sopen_s, _wsopen_s

Открывает файл для общего доступа. Это версии функций [_sopen and _wsopen](sopen-wsopen.md) с усовершенствованной безопасностью, как описано в разделе [Функции безопасности в CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Синтаксис

```C
errno_t _sopen_s(
   int* pfh,
   const char *filename,
   int oflag,
   int shflag,
   int pmode
);
errno_t _wsopen_s(
   int* pfh,
   const wchar_t *filename,
   int oflag,
   int shflag,
   int pmode,
);
```

### <a name="parameters"></a>Параметры

*pfh*<br/>
Дескриптор файла или значение -1 в случае ошибки.

*filename*<br/>
Имя файла.

*oflag*<br/>
Разрешенные типы операций.

*shflag*<br/>
Разрешенные типы общего доступа.

*pmode*<br/>
Настройка разрешений.

## <a name="return-value"></a>Возвращаемое значение

Ненулевое возвращаемое значение указывает на ошибку; в этом случае **errno** присваивается одно из следующих значений.

|Значение errno|Условие|
|-|-|
**EACCES**| Заданный путь является каталогом, или файл доступен только для чтения, однако была выполнена попытка операции открытия для записи.
**EEXIST**| **_O_CREAT** и **_O_EXCL** указаны флаги, но *filename* уже существует.
**EINVAL**| Недопустимый *oflag*, *shflag*, или *pmode* аргумент, или *pfh* или *filename* является пустым указателем.
**EMFILE**|Больше нет доступных дескрипторов файлов.
**ENOENT**|Файл или путь не найден.

Если в функцию передается недопустимый аргумент, вызывается обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, **errno** равно **EINVAL** и **EINVAL** возвращается.

Дополнительные сведения об этих и других кодах возврата см. в разделе [errno, _doserrno, _sys_errlist и _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

В случае ошибки, возвращается значение -1 через *pfh* (если только не *pfh* является пустым указателем).

## <a name="remarks"></a>Примечания

**_Sopen_s** функция открывает файл, указанный параметром *filename* и готовит файл для общего чтения или записи, в соответствии с определением *oflag* и *shflag* . **_wsopen_s** — это двухбайтовая версия **_sopen_s**; *filename* аргумент **_wsopen_s** представляет собой строку расширенных символов. **_wsopen_s** и **_sopen_s** ведут себя идентично.

### <a name="generic-text-routine-mappings"></a>Универсальное текстовое сопоставление функций

|Подпрограмма Tchar.h|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen_s**|**_sopen_s**|**_sopen_s**|**_wsopen_s**|

Целочисленное выражение *oflag* образуется путем объединения одной или нескольких констант манифеста, определенных в \<fcntl.h >. Когда несколько констант манифеста формируют аргумент *oflag*, они объединяются с помощью оператора побитового или ( **&#124;** ).

|*oflag* константой|Поведение|
|-|-|
**_O_APPEND**|Перемещает указатель файла в конец файла перед каждой операцией записи.
**_O_BINARY**|Открывает файл в двоичном режиме (без преобразования). (Описание двоичного режима см. в разделе [fopen](fopen-wfopen.md).)
**_O_CREAT**|Создает файл и открывает его для записи. Имеет смысл, если файл, указанный параметром *filename* существует. *Pmode* аргумент является обязательным, если **_O_CREAT** указано.
**_O_CREAT** &AMP;#124; **_O_SHORT_LIVED**|Создает файл в качестве временного файла и, по возможности, не сбрасывает его на диск. *Pmode* аргумент является обязательным, если **_O_CREAT** указано.
**_O_CREAT** &AMP;#124; **_O_TEMPORARY**|Создает файл в качестве временного файла; файл удаляется при закрытии последнего дескриптора файла. *Pmode* аргумент является обязательным, если **_O_CREAT** указано.
**_O_CREAT**&AMP;#124; ` _O_EXCL`|Возвращает значение ошибки, если файл, указанный параметром *filename* существует. Применяется только при использовании с **_O_CREAT**.
**_O_NOINHERIT**|Предотвращает создание общего дескриптора файла.
**_O_RANDOM**|Указывает, что кэширование оптимизировано для случайного доступа с диска, но не ограничивается им.
**_O_RDONLY**|Открывает файл только для чтения. Нельзя указывать вместе с **_O_RDWR** или **_O_WRONLY**.
**_O_RDWR**|Открывает файл для чтения и записи. Нельзя указывать вместе с **_O_RDONLY** или **_O_WRONLY**.
**_O_SEQUENTIAL**|Указывает, что кэширование оптимизировано для последовательного доступа с диска, но не ограничивается им.
**_O_TEXT**|Открывает файл в текстовом режиме (с преобразованием). (Дополнительные сведения см. в разделах [Файловый ввод-вывод в текстовом и двоичном режиме](../../c-runtime-library/text-and-binary-mode-file-i-o.md) и [fopen](fopen-wfopen.md).)
**_O_TRUNC**|Открывает файл и обрезает его до нулевой длины; необходимо разрешение на запись в файл. Нельзя указывать вместе с **_O_RDONLY**. **_O_TRUNC** с **_O_CREAT** открывает существующий файл или создает файл. **Примечание:** **_O_TRUNC** флаг удаляет содержимое указанного файла.
**_O_WRONLY**|Открывает файл только для записи. Нельзя указывать вместе с **_O_RDONLY** или **_O_RDWR**.
**_O_U16TEXT**|Открывает файл в режиме Юникода UTF-16.
**_O_U8TEXT**|Открывает файл в режиме Юникода UTF-8.
**_O_WTEXT**|Открывает файл в режиме Юникода.

Чтобы указать режим доступа к файлу, необходимо указать либо **_O_RDONLY**, **_O_RDWR**, или **_O_WRONLY**. Для режима доступа нет значения по умолчанию.

Если файл открыт в режиме Юникода с помощью **_O_WTEXT**, **_O_U8TEXT**, или **_O_U16TEXT**ввода функции преобразуют данные, считываемые из файла в данные UTF-16 хранимые с типом **wchar_t**. Функции, записи в файл, открытый в режиме Юникода, ожидают буферы, содержащие данные UTF-16, хранимые с типом **wchar_t**. Если кодировка файла — UTF-8, при его записи данные UTF-16 преобразуются в UTF-8, а содержимое файла с кодировкой UTF-8 преобразуется в данные UTF-16 при его считывании. Попытка чтения или записи нечетного числа байт в режиме Юникода приводит к возникновению ошибки проверки параметра. Для чтения или записи данных, хранимых в программе в кодировке UTF-8, используйте режим текстового или двоичного файла вместо режима Юникода. Вам необходимо реализовать все обязательные преобразования кодировки.

Если **_sopen_s** вызывается с **_O_WRONLY** | **_O_APPEND** (режим добавления) и **_O_WTEXT**, **_O_ U16TEXT**, или **_O_U8TEXT**, сначала пытается открыть файл для чтения и записи, чтения Спецификации, а затем снова открыть ее только для записи. Если происходит сбой открытия файла для чтения и записи, файл открывается только для записи и для параметра режима Юникода используется значение по умолчанию.

Аргумент *shflag* — это константное выражение, которое состоит из одной из следующих констант манифеста, определенных в \<share.h >.

|*shflag* константой|Поведение|
|-|-|
**_SH_DENYRW**|Запрещает доступ на чтение и запись.
**_SH_DENYWR**|Запрещает доступ на запись.
**_SH_DENYRD**|Запрещает доступ на чтение.
**_SH_DENYNO**|Разрешает доступ на чтение и запись.

*Pmode* аргумент всегда является обязательным, в отличие от в **_sopen**. При указании **_O_CREAT**, если файл не существует, *pmode* задает параметры разрешений файла, которые настраиваются при закрытии нового файла первый раз. В противном случае *pmode* учитывается. *pmode* — это целочисленное выражение, которое содержит одну или обе константы манифеста **_S_IWRITE** и **_S_IREAD**, которые определены в \<sys\stat.h >. Если заданы обе константы, они объединяются с помощью битового оператора ИЛИ. Значение *pmode* выглядит следующим образом.

|*pmode*|Значение|
|-|-|
**_S_IREAD**|Разрешено только чтение.
**_S_IWRITE**|Разрешена запись. (Если действует, разрешает чтение и запись.)
**_S_IREAD** &AMP;#124; **_S_IWRITE**|Разрешены чтение и запись.

Если разрешение на запись не предоставлено, файл остается доступным только для чтения. В операционной системе Windows все файлы доступны для чтения; невозможно предоставить разрешение только на запись. Поэтому режимы **_S_IWRITE** и **_S_IREAD** | **_S_IWRITE** эквивалентны.

**_sopen_s** применяет текущую маску разрешений файла к *pmode* до настройки разрешений. (См. [_umask](umask.md).)

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|Необязательный заголовок|
|-------------|---------------------|---------------------|
|**_sopen_s**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|
|**_wsopen_s**|\<io.h> или \<wchar.h>|\<fcntl.h>, \<sys/types.h>, \<sys/stat.h>, \<share.h>|

**_sopen_s** и **_wsopen_s** являются расширениями Майкрософт. Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

См. пример для [_locking](locking.md).

## <a name="see-also"></a>См. также

[Низкоуровневый ввод-вывод](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fsopen, _wfsopen](fsopen-wfsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
