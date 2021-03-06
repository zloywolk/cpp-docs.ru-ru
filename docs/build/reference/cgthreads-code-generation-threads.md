---
title: -cgthreads (потоки создания кода) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /cgthreads
dev_langs:
- C++
helpviewer_keywords:
- /cgthreads compiler option (C++)
- -cgthreads compiler option (C++)
- cgthreads compiler option (C++)
- cgthreads
ms.assetid: 64bc768c-6caa-4baf-9dea-7cfa1ffb01c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb6849a4b30e903d05b5ac3d37fce558074110a5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719632"
---
# <a name="cgthreads-code-generation-threads"></a>/cgthreads (потоки создания кода)

Задает число потоков cl.exe, используемых для оптимизации и создания кода.

## <a name="syntax"></a>Синтаксис

```
/cgthreads[1-8]
```

## <a name="arguments"></a>Аргументы

*номер*<br/>
Максимальное число потоков, используемых cl.exe, — в диапазоне от 1 до 8.

## <a name="remarks"></a>Примечания

**/Cgthreads** параметр указывает максимальное число потоков cl.exe использует в параллельном режиме для оптимизации и кода на этапы создания компиляции. Обратите внимание на то, что не может быть пробела между **/cgthreads** и `number` аргумент. По умолчанию cl.exe использует четыре потока, как если бы **/cgthreads4** были указаны. Если доступно больше ядер процессора, увеличение значения `number` может ускорить сборку. Этот параметр особенно полезен, когда он объединяется с [/GL (оптимизация всей программы)](../../build/reference/gl-whole-program-optimization.md).

Для сборки можно указать несколько уровней параллелизма. Параметр msbuild.exe **/maxcpucount** указывает число процессов MSBuild, которые могут выполняться параллельно. [/MP (построить с несколькими процессами)](../../build/reference/mp-build-with-multiple-processes.md) флаг компилятора указывает число процессов cl.exe, которые одновременно компилируют исходные файлы. **/Cgthreads** определяет число потоков, используемых каждым процессом cl.exe. Так как число потоков, одновременно выполняемых процессором, не может превышать число ядер процессора, указывать более высокие значения для всех этих параметров бессмысленно. Более того, это может иметь обратный эффект. Дополнительные сведения о построении проектов в параллельном режиме, см. в разделе [параллельное построение нескольких проектов](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [Работа со свойствами проекта](../../ide/working-with-project-properties.md).

1. Выберите **свойства конфигурации**, **C/C++** папки.

1. Выберите **командной строки** страницу свойств.

1. Изменить **Дополнительные параметры** свойство **/cgthreads**`N`, где `N` представляет собой значение от 1 до 8, а затем выберите **ОК**.

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>См. также

[Параметры компилятора](../../build/reference/compiler-options.md)<br/>
[Настройка параметров компилятора](../../build/reference/setting-compiler-options.md)