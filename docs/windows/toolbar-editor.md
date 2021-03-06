---
title: Редактор панелей инструментов (C++) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.toolbar.F1
dev_langs:
- C++
helpviewer_keywords:
- resource editors [C++], Toolbar editor
- editors, toolbars
- toolbars [C++], editing
- Toolbar editor
ms.assetid: aa9f0adf-60f6-4f79-ab05-bc330f15ec43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0bb329b60b72aae268252ae3ddbcc2c63d4a18f6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389697"
---
# <a name="toolbar-editor-c"></a>Редактор панелей инструментов (C++)

**Инструментов** редактор позволяет создавать ресурсы панелей инструментов C++ и преобразовывать растровые изображения в ресурсы панелей инструментов. **Инструментов** редактор использует графическое изображение для отображения панели инструментов и кнопок, в значительной степени напоминают как они будут выглядеть в готовое приложение.

С помощью **инструментов** редактор, вы можете:

- [создавать панели инструментов и кнопки;](../windows/creating-new-toolbars.md)

- [преобразовывать растровые изображения в ресурс панели инструментов;](../windows/converting-bitmaps-to-toolbars.md)

- [создавать, перемещать и изменять кнопки на панели инструментов;](../windows/creating-moving-and-editing-toolbar-buttons.md)

- [создавать всплывающие подсказки.](../windows/creating-a-tool-tip-for-a-toolbar-button.md)

**Инструментов** окно редактора отображается в двух представлениях изображения кнопки, таким же, как в окне редактора изображений. Две области разделены разделителем. Чтобы изменить соотношение областей, переместите разделитель в нужную сторону. Активная панель окружена границами, как выделенная область. Над представлениями изображения размещена тематическая панель инструментов.

![Редактор панелей инструментов](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")  
Редактор панелей инструментов

**Инструментов** редактор аналогичен **изображение** редактор функциональных возможностей. Пункты меню, графические средства и сетка растрового изображения имеют такие же, как в **изображение** редактора. Команда меню **изображение** меню, чтобы можно было переключаться между **инструментов** редактора и **изображение** редактора. Дополнительные сведения об использовании **графики** инструментов **цвета** палитре, или **изображение** меню, см. в разделе [редактор изображений](../windows/image-editor-for-icons.md).

Сведения о добавлении ресурсов в управляемые проекты см. в разделе [ресурсы в приложениях для настольных систем](/dotnet/framework/resources/index) в *руководства разработчика .NET Framework*. Сведения о вручную добавлять файлы ресурсов в управляемые проекты, осуществлять доступ к ресурсам, отображать статические ресурсы и присваивать строки ресурсов свойствам, см. в разделе [Создание файлов ресурсов для приложений рабочего стола](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Сведения о глобализации и локализации ресурсов в управляемых приложениях, см. в разделе [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Требования

MFC или ATL

## <a name="see-also"></a>См. также

[Редакторы ресурсов](../windows/resource-editors.md)<br/>
[Меню и другие ресурсы](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)