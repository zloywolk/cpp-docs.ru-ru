---
title: Вставка промежутка между кнопками на панели инструментов (C++) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Toolbar editor [C++], spacing toolbar buttons
- toolbar buttons [C++], space between buttons
ms.assetid: 4925ea6b-5d3a-4949-a920-bf371a37e529
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c4c205d6f800682cb67749a73f57b1c35d03de61
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397459"
---
# <a name="inserting-a-space-between-buttons-on-a-toolbar-c"></a>Вставка промежутка между кнопками на панели инструментов (C++)

Как правило чтобы вставить промежутка между кнопками, просто перетащите их друг от друга на панели инструментов. Чтобы удалить пространство, перетащите их к друг с другом.

### <a name="to-insert-a-space-before-a-button-that-is-not-followed-by-a-space"></a>Чтобы вставить пробел перед кнопкой, не разделенных пробелами

1. Перетащите кнопку вправо или вниз, пока он перекрывает "Далее" о посередине.

### <a name="to-insert-a-space-before-a-button-which-is-followed-by-a-space-and-to-retain-that-trailing-space"></a>Позволяет вставлять пробел перед кнопкой, разделенных пробелами, сохранив этот пробел

1. Перетащите кнопку до правого или нижнего края коснулся "Далее", или даже перекрыл ее.

### <a name="to-insert-a-space-before-a-button-that-is-followed-by-a-space-and-close-up-that-following-space"></a>Вставлять пробел перед кнопкой, за которой следуют пробел и закрыть следующие пространство

1. Перетащите кнопку вправо или вниз, пока он перекрывает "Далее" о посередине.

Сведения о добавлении ресурсов в управляемые проекты см. в разделе [ресурсы в приложениях для настольных систем](/dotnet/framework/resources/index) в *руководства разработчика .NET Framework*. Сведения о вручную добавлять файлы ресурсов в управляемые проекты, осуществлять доступ к ресурсам, отображать статические ресурсы и присваивать строки ресурсов свойствам, см. в разделе [Создание файлов ресурсов для приложений рабочего стола](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Сведения о глобализации и локализации ресурсов в управляемых приложениях, см. в разделе [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Требования

MFC или ATL

## <a name="see-also"></a>См. также

[Создание, перемещение и редактирование кнопок на панели инструментов](../windows/creating-moving-and-editing-toolbar-buttons.md)<br/>
[Редактор панелей инструментов](../windows/toolbar-editor.md)