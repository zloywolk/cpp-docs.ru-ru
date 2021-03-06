---
title: / FA, /Fa (файл листинга) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AssemblerListingLocation
- VC.Project.VCCLCompilerTool.ConfigureASMListing
- VC.Project.VCCLWCECompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.AssemblerListingLocation
- /fa
- VC.Project.VCCLCompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
dev_langs:
- C++
helpviewer_keywords:
- FA compiler option [C++]
- /FA compiler option [C++]
- -FA compiler option [C++]
- listing file type
- assembly-only listing
ms.assetid: c7507d0e-c69d-44f9-b8e2-d2c398697402
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c9f1d205eff155b628081c5bc615570c44a88f08
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412812"
---
# <a name="fa-fa-listing-file"></a>/FA, /Fa (файл листинга)

Создает файл листинга, содержащий код ассемблера.

## <a name="syntax"></a>Синтаксис

> **/FA**[**c**\][**s**\][**u**] **/Fa**_pathname_

## <a name="remarks"></a>Примечания

**/FA** параметр компилятора создает файл листинга ассемблера для каждой записи преобразования в компиляции, что исходный файл C или C++ в целом соответствует. По умолчанию только сборщик данных включается в файл листинга, который кодируется как ANSI. Необязательный **c**, **s**, и **u** аргументы **/FA** управления ли машинного кода или исходный код выводятся вместе с ассемблер Вывод списка, и является ли список кодируется как UTF-8.

По умолчанию каждый файл получает такое же базовое имя исходного файла и имеет расширение .asm. Когда машинный код включается с помощью **c** параметр листинг файл имеет расширение .cod. Можно изменить имя и расширение файла листинга и каталог, где он создан с помощью **/Fa** параметр.

### <a name="fa-arguments"></a>/FA аргументов

Нет<br/>
Только язык ассемблера, включены в листинг.

**c**<br/>
Необязательный. Содержит машинный код в листинг.

**s**<br/>
Необязательный. Включает исходный код в листинг.

**u**<br/>
Необязательный. Кодирует файл листинга в формате UTF-8 и включает в себя метку порядка байтов. По умолчанию файл кодируется как ANSI. Используйте `u` создать файл листинга, отображаются правильно в любой системе, или если вы используете Юникода файлов исходного кода в качестве входных данных компилятора.

Если оба **s** и **u** указаны, а если файл исходного кода использует кодировку Юникод, отличные от UTF-8, а затем строк кода в ASM-файл может отображаться неправильно.

### <a name="fa-argument"></a>Аргумент /FA

Нет<br/>
Один *источника*ASM-файл создается для каждого файла исходного кода при компиляции.

*filename*<br/>
Файл с именем *filename*.asm помещается в текущем каталоге. Это допустимо только при компиляции одного файла исходного кода.

*файл имяфайла.расширение*<br/>
Файл с именем *файл имяфайла.расширение* помещается в текущем каталоге. Это допустимо только при компиляции одного файла исходного кода.

*Каталог*__\\__<br/>
Один *исходный_файл*ASM-файл, который помещается в указанном *directory* для каждого файла исходного кода при компиляции. Обратите внимание, требуется обратную косую черту. Допускаются только пути на текущем диске.

*каталог*__\\__*имя файла*<br/>
Файл с именем *filename*.asm помещается в указанном *directory*. Это допустимо только при компиляции одного файла исходного кода.

*каталог*__\\__*файл имяфайла.расширение*<br/>
Файл с именем *файл имяфайла.расширение* помещается в указанном *directory*. Это допустимо только при компиляции одного файла исходного кода.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [Работа со свойствами проекта](../../ide/working-with-project-properties.md).

2. Выберите **свойства конфигурации** > **C/C++** > **выходные файлы** страницу свойств.

3. Изменить **ассемблерного** задаваемое свойство **/FAc** и **параметра/FAs** параметры ассемблера, машины и исходный код. Изменить **использования Юникода для ассемблера листинг** задаваемое свойство **параметр/FAu** параметр для вывода ANSI или UTF-8. Изменить **местоположение ASM-списка** присвоить **/Fa** параметр для перечисления имя и расположение файла.

Обратите внимание, что установка **ассемблерного** и **использования Юникода для ассемблера листинг** свойства может привести к [Предупреждение командной строки D9025](../../error-messages/tool-errors/command-line-warning-d9025.md). Чтобы объединить эти параметры в интегрированной среде разработки, используйте **Дополнительные параметры** в **командной строки** странице свойств.

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. описания свойств <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A> и <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>. Чтобы указать **параметр/FAu**, см. в разделе <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="example"></a>Пример

Следующая команда создает объединенный исходный, и машинный код с именем HELLO.cod:

```cmd
CL /FAcs HELLO.CPP
```

## <a name="see-also"></a>См. также

[Параметры выходного файла (/F)](../../build/reference/output-file-f-options.md)<br/>
[Параметры компилятора](../../build/reference/compiler-options.md)<br/>
[Настройка параметров компилятора](../../build/reference/setting-compiler-options.md)<br/>
[Указание пути](../../build/reference/specifying-the-pathname.md)