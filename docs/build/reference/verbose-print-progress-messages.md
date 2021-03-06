---
title: -VERBOSE (Печать сообщений о ходе выполнения) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /verbose
- VC.Project.VCLinkerTool.ShowProgress
dev_langs:
- C++
helpviewer_keywords:
- -VERBOSE linker option
- linking [C++], session progress information
- Print Progress Messages linker option
- linker [C++], output dependency information
- /VERBOSE linker option
- dependencies [C++], dependency information in linker output
- VERBOSE linker option
ms.assetid: 9c347d98-4c37-4724-a39e-0983934693ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6acffba952ad46e2b6051aed7effeb4a613bfc65
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725612"
---
# <a name="verbose-print-progress-messages"></a>/VERBOSE (печать сообщений о ходе выполнения)

```
/VERBOSE[:{ICF|INCR|LIB|REF|SAFESEH|UNUSEDLIBS}]
```

## <a name="remarks"></a>Примечания

Компоновщик отправляет сведения о ходе выполнения сеанса компоновки для **вывода** окна. В командной строке данные отправляются в стандартный вывод и могут быть перенаправлены в файл.

|Параметр|Описание|
|------------|-----------------|
|/VERBOSE|Отображает подробные сведения о процессе компоновки.|
|/ VERBOSE: ICF|Отображает сведения о действиях компоновщика, полученный в результате применения [/OPT: ICF](../../build/reference/opt-optimizations.md).|
|/ VERBOSE: INCR|Отображает сведения о процессе компоновки.|
|/ VERBOSE: LIB|Отображает сообщения о ходе выполнения, указывающие только библиотеки, в котором выполняется поиск.<br /><br /> Отображаемая информация включает в себя процесс поиска библиотеки и списки имена библиотек и объектов (с указанием полного пути), символ, разрешаемый из библиотеки и список объектов, которые ссылаются на этот символ.|
|/ VERBOSE: REF|Отображает сведения о действиях компоновщика, полученный в результате применения [предотвратят](../../build/reference/opt-optimizations.md).|
|/ VERBOSE: SAFESEH|Отображает сведения о модулях, несовместимых с безопасной обработки, когда исключений [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md) не указан.|
|/ VERBOSE: UNUSEDLIBS|Отображает сведения обо всех файлах библиотеки, которые не используются при создании образа.|

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Задание данного параметра компоновщика в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [свойств проекта Visual C++ параметр](../../ide/working-with-project-properties.md).

1. Разверните **компоновщика** папки.

1. Выберите **командной строки** страницу свойств.

1. Добавить параметр, чтобы **Дополнительные параметры** поле.

### <a name="to-set-this-linker-option-programmatically"></a>Задание данного параметра компоновщика программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>.

## <a name="see-also"></a>См. также

[Настройка параметров компоновщика](../../build/reference/setting-linker-options.md)<br/>
[Параметры компоновщика](../../build/reference/linker-options.md)