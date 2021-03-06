---
title: Укажите путь и переменные среды для построения из командной строки | Документация Майкрософт
ms.custom: conceptual
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- include
- Lib
- Path
dev_langs:
- C++
helpviewer_keywords:
- environment variables [C++]
- VCVARS32.bat file
- cl.exe compiler [C++], environment variables
- LINK tool [C++], environment variables
- PATH reserved word
- INCLUDE reserved word
- LINK tool [C++], path
- LIB environment variable
- compiling source code [C++], from command line
- environment variables [C++], CL compiler
ms.assetid: 99389528-deb5-43b9-b99a-03c8773ebaf4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3e4b24e3ec209273b0f547c99685e8e804a74bc0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724272"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Укажите путь и переменные среды для построения из командной строки

Средства сборки командной строки Visual C++ требуется несколько переменных среды, которые настраиваются для настройки установки и сборки. При установке рабочей нагрузки C++ с помощью установщика Visual Studio, он создает настраиваемые командные файлы или пакетных файлов, которые установлены необходимые переменные среды. Затем установщик использует эти командные файлы можно создавать ярлыки для меню Windows Пуск открыть окно командной строки разработчика. Следующие сочетания клавиш, настройте переменные среды для конкретной конфигурации построения. При вы хотите использовать средства командной строки, выполнив одну из этих клавиш, или можно открыть plain командную строку и выполните одну из пользовательских командных файлов, которые самостоятельно задать окружение конфигурации сборки. Дополнительные сведения см. в разделе [сборки кода C/C++ в командной строке](building-on-the-command-line.md).

Средства командной строки Visual C++ использовать переменные среды PATH, TMP, INCLUDE, LIB и LIBPATH, а также использовать другие переменные среды, относящиеся к установленных инструментов, платформ и пакетов SDK. Даже простую установку Visual Studio может задать двадцать или дополнительные переменные среды. Значения этих переменных среды, характерные для установки и выбора конфигурации сборки, и может изменяться при обновлении продукта, мы настоятельно рекомендуем использовать ярлык командной строки разработчика или один из настроить командные файлы для установки, а не настраивать их в среде Windows самостоятельно.

Чтобы увидеть, какие переменные среды задаются с помощью ярлыка командную строку разработчика, можно использовать команды SET. Откройте окно простой командной строки и записи выходных данных команды SET для базового плана. Откройте окно командной строки разработчика и записи выходных данных команды SET для сравнения. Средство различий, например в каталог, встроенные в интегрированной среде разработки Visual Studio можно использовать для сравнения переменных среды и увидеть, что по командной строке разработчика. Сведения о переменных среды, используемых компилятором и компоновщика, см. в разделе [переменные среды CL](../build/reference/cl-environment-variables.md) и [переменные среды инструмента LINK](../build/reference/link-environment-variables.md).

> [!NOTE]
>  Несколько средств командной строки или параметры средства может потребоваться разрешение администратора. При наличии проблем с разрешениями, при их использовании, мы рекомендуем открыть окно командной строки разработчика с помощью **Запуск от имени администратора** параметр. В Windows 10, щелкните правой кнопкой мыши, чтобы открыть контекстное меню для окна командной строки, а затем выберите **дополнительные**, **Запуск от имени администратора**.

## <a name="see-also"></a>См. также

[Создание кода C/C++ в командной строке](../build/building-on-the-command-line.md)<br/>
[Компоновка](../build/reference/linking.md)<br/>
[Параметры компоновщика](../build/reference/linker-options.md)<br/>
[Компиляция программы на C/C++](../build/reference/compiling-a-c-cpp-program.md)<br/>
[Параметры компилятора](../build/reference/compiler-options.md)