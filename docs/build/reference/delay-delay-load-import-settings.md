---
title: -DELAY (параметры отложенной загрузки импортов) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /delay
- VC.Project.VCLinkerTool.DelayNoBind
- VC.Project.VCLinkerTool.SupportUnloadOfDelayLoadedDLL
- VC.Project.VCLinkerTool.DelayUnload
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, /DELAY option
- DELAY linker option
- /DELAY linker option
- -DELAY linker option
ms.assetid: 9334b332-cc58-4dae-b10f-a4c75972d50c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ce585f9dc8439a02a2883229e8d9ec006c29c24
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717695"
---
# <a name="delay-delay-load-import-settings"></a>/DELAY (параметры отложенной загрузки импортов)

```
/DELAY:UNLOAD
/DELAY:NOBIND
```

## <a name="remarks"></a>Примечания

Параметр/DELAY управляет [отложенной загрузки](../../build/reference/linker-support-for-delay-loaded-dlls.md) библиотек DLL:

- Квалификатор UNLOAD предписывает вспомогательной функции отложенной загрузки поддерживать явную выгрузку DLL. Таблица адресов импорта (IAT) восстанавливается в своем первоначальном виде; это приводит к тому, что указатели IAT становятся недействительными и перезаписываются.

   Если вы не выберете UNLOAD, любой вызов [FUnloadDelayLoadedDLL](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md) завершится ошибкой.

- Квалификатор NOBIND предписывает компоновщику не включать связываемую таблицу IAT в окончательный образ. По умолчанию задано создание связываемой таблицы IAT для библиотек DLL, загружаемых с задержкой. Полученный в результате образ не может быть статически привязан. (Образы с привязываемыми таблицами IAT могут быть статически привязаны перед выполнением.) См. в разделе [/BIND](../../build/reference/bind.md).

   Если библиотека DLL привязана, вспомогательная функция будет пытаться использовать данные привязки вместо вызова метода [GetProcAddress](https://msdn.microsoft.com/library/windows/desktop/ms683212.aspx) на каждого из импортов, на который указывает ссылка. Если метка времени или предпочтительный адрес не соответствуют таковым в загружаемой библиотеке DLL, то вспомогательная функция будет предполагать, что привязанная таблица IAT устарела, и продолжать обработку так, будто привязанной таблицы IAT не существует.

   Применение квалификатора NOBIND приведет к увеличению образа программы, но зато может уменьшить время загрузки библиотеки DLL. Если привязка библиотеки DLL не предполагалась, то NOBIND предотвратит создание привязанной таблицы IAT.

Чтобы указать библиотеки DLL с отложенной загрузкой, используйте [/DELAYLOAD](../../build/reference/delayload-delay-load-import.md) параметр.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Задание данного параметра компоновщика в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Сведения см. в разделе [работа со свойствами проекта](../../ide/working-with-project-properties.md).

1. Разверните **свойства конфигурации**, **компоновщика**, а затем выберите **Дополнительно**.

1. Изменить **Отложенно загружаемые DLL** свойство.

### <a name="to-set-this-linker-option-programmatically"></a>Задание данного параметра компоновщика программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.

## <a name="see-also"></a>См. также

[Настройка параметров компоновщика](../../build/reference/setting-linker-options.md)<br/>
[Параметры компоновщика](../../build/reference/linker-options.md)