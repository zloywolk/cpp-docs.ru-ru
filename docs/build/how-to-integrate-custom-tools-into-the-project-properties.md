---
title: 'Практическое: интеграция пользовательских средств в свойства проекта | Документация Майкрософт'
ms.custom: ''
ms.date: 04/27/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.howto.integratecustomtools
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: integrate custom tools'
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 800652b845294ebad4e1cca5310e0b95f6d79151
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720413"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>Практическое руководство. Интеграция пользовательских средств в свойства проекта

Можно добавить параметры пользовательских средств в Visual Studio **страницы свойств** окно путем создания базового файла схемы XML.

**Свойства конфигурации** раздел **страницы свойств** окне отображаются группы параметров, которые известны как *правила*. Каждое правило содержит параметры для средства или группы функций. Например **компоновщика** правило содержит параметры для средства компоновщика. Параметры в правиле можно разделить на *категории*.

В этом документе объясняется, как создать файл в заданном каталоге, который содержит свойства для пользовательского средства, чтобы свойства загружаются при запуске Visual Studio. Сведения о том, как изменить файл, см. в разделе [расширяемость платформы. часть 2](https://blogs.msdn.microsoft.com/vsproject/2009/06/18/platform-extensibility-part-2/) в блоге группы проекта Visual Studio.

### <a name="to-add-or-change-project-properties"></a>Чтобы добавить или изменить свойства проекта

1. В редакторе XML Создание XML-файла.

1. Сохраните файл в Visual Studio 2017 `VCTargets\1033` папки. У вас будет другой путь для каждого выпуска Visual Studio 2017, которая устанавливается и каждого языка. Например, путь к папке для Visual Studio Enterprise edition на английском языке — `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`. Измените путь для своего языка и выпуска Visual Studio. Каждое правило в **страницы свойств** представления окна XML-файл в этой папке. Убедитесь, что файл имеет уникальное имя в папке.

1. Скопируйте его содержимое `%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml`, закройте ее без сохранения изменений и вставьте содержимое в новом файле XML. Можно использовать любой файл схемы XML — это лишь одна, который может использоваться, чтобы начать с шаблона.

1. В новом файле XML измените содержимое в соответствии с требованиями. Не забудьте заменить **Имя_правила** и **Rule.DisplayName** в верхней части файла.

1. Сохраните изменения и закройте файл.

1. XML-файлы в `%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>` загружаются при запуске Visual Studio. Таким образом Чтобы проверить новый файл, перезапустите Visual Studio.

1. В **обозревателе решений**, щелкните правой кнопкой мыши проект и нажмите кнопку **свойства**. В **страницы свойств** в левой области окна убедитесь, что новый узел с именем правила.

## <a name="see-also"></a>См. также

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
