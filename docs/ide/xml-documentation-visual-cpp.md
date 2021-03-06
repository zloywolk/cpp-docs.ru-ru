---
title: XML-документация (Visual C++) | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- XML documentation
- XML, documentation comments in source code
- comments, C++ source code files
- /// delimiter for C++ documentation
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de3df01d9e9bf5d63b4445956e4656687d0f4f2c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412292"
---
# <a name="xml-documentation-visual-c"></a>Документация XML (Visual C++)

В Visual C++ можно добавлять комментарии в исходный код, которые будут обработаны в виде XML-файла. Затем этот файл можно использовать в качестве входного для процесса, создающего документацию для классов в коде.

В файле кода Visual C++ комментарии XML-документации должны находиться непосредственно перед определением метода или типа. Комментарии можно использовать для заполнения подсказок по данным для кратких сведений IntelliSense в следующих сценариях:

1. при компиляции кода в качестве компонента среды выполнения Windows с сопутствующим файлом WINMD;

1. при включении исходного кода в текущий проект;

1. в библиотеке, объявления и реализации типов которой находятся в том же файле заголовка.

> [!NOTE]
>  В текущем выпуске комментарии к коду не обрабатываются для шаблонов или любых объектов, содержащих тип шаблона (например, функция, принимающая параметр как шаблон). Добавление таких комментариев приведет к неопределенному поведению.

Дополнительные сведения о создании XML-файла с комментариями документации см. в следующих разделах.

|Сведения|См.|
|---------------------------|---------|
|Используемые параметры компилятора|[/doc](../build/reference/doc-process-documentation-comments-c-cpp.md)|
|Теги, позволяющие реализовать часто используемые функции в документации|[Рекомендуемые теги для комментариев документации](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)|
|Строки идентификаторов, создаваемые компилятором для идентификации конструкций в коде|[Обработка XML-файла](../ide/dot-xml-file-processing.md)|
|Разделение тегов документации|[Разделители для тегов документации Visual C++](../ide/delimiters-for-visual-cpp-documentation-tags.md)|
|Создание XML-файла из одного или нескольких XDC-файлов.|[Справочник по XDCMake](../ide/xdcmake-reference.md)|
|Ссылки на сведения об XML, посвященные связи с областями компонентов Visual Studio|[XML в Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)|

Если вам нужно поместить специальные символы XML в текст комментария документации, следует использовать сущности XML или раздел CDATA.

## <a name="see-also"></a>См. также

[Расширения компонентов для платформ среды выполнения](../windows/component-extensions-for-runtime-platforms.md)