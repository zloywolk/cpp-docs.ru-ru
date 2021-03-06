---
title: '-EP (Предварительная обработка в stdout без директив #line) | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ep
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines
dev_langs:
- C++
helpviewer_keywords:
- copy preprocessor output to stdout
- preprocessor output, copy to stdout
- -EP compiler option [C++]
- EP compiler option [C++]
- /EP compiler option [C++]
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 598c202cbac0176cb77243c7f0f891ef94c3dcc6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714887"
---
# <a name="ep-preprocess-to-stdout-without-line-directives"></a>/EP (предварительная обработка в поток стандартных выходных файлов без директив #line)

Выполняет предварительную обработку исходными файлами C и C++ и копирует предварительно обработанных файлов на стандартное устройство вывода.

## <a name="syntax"></a>Синтаксис

```
/EP
```

## <a name="remarks"></a>Примечания

В процессе выполняются все директивы препроцессора, расширения макросов и комментарии будут удалены. Чтобы сохранить комментарии в предварительно обработанные выходные данные, используйте [/C (сохранять комментарии во время предварительной обработки)](../../build/reference/c-preserve-comments-during-preprocessing.md) с параметром **/EP**.

**/EP** параметр отменяет компиляцию. Отправьте предварительно обработанного файла для компиляции. **/EP** также подавляются выходные файлы из **/FA**, **/Fa**, и **/Fm** параметры. Дополнительные сведения см. в разделе [/FA, /Fa (файл листинга)](../../build/reference/fa-fa-listing-file.md) и [/Fm (имя файла сопоставления)](../../build/reference/fm-name-mapfile.md).

Ошибки, созданные в более поздних этапах обработки указан номер соответствующей строки из предварительно обработанного файла, а не исходный файл. Номера строк для ссылки на исходный файл, используйте [/E (Предварительная обработка до stdout)](../../build/reference/e-preprocess-to-stdout.md) вместо этого. **/E** добавляет параметр `#line` директивы в выходные данные для этой цели.

Для отправки предварительно обработанные выходные данные, с помощью `#line` директивы, в файл, используйте [/P (Предварительная обработка в файл)](../../build/reference/p-preprocess-to-a-file.md) вместо него.

Для отправки предварительно обработанные выходные данные в stdout, с помощью `#line` использовать директивы, **/P** и **/EP** друг с другом.

Нельзя использовать предкомпилированные заголовки с **/EP** параметр.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [Работа со свойствами проекта](../../ide/working-with-project-properties.md).

1. Откройте папку **C/C++** .

1. Нажмите кнопку **препроцессор** страницу свойств.

1. Изменить **Создание предварительно обработанного файла** свойство.

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.

## <a name="example"></a>Пример

Следующая командная строка выполняет предварительную обработку файла `ADD.C`, сохраняет комментарии и выводит результат на стандартное устройство вывода:

```
CL /EP /C ADD.C
```

## <a name="see-also"></a>См. также

[Параметры компилятора](../../build/reference/compiler-options.md)<br/>
[Настройка параметров компилятора](../../build/reference/setting-compiler-options.md)