---
title: Вкладки свойств и страницы свойств (MFC) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], tabs
- property pages [MFC], property sheets
- CPropertyPage class [MFC], property sheets and pages
- CPropertySheet class [MFC], property sheets and pages
- property sheets, propert pages
ms.assetid: de8fea12-6c35-4cef-8625-b8073a379446
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cfb5bd849c79d64769cb13d854605292689dfe73
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441988"
---
# <a name="property-sheets-and-property-pages-mfc"></a>Вкладки свойств и страницы свойств (MFC)

MFC [диалоговое окно](../mfc/dialog-boxes.md) может принимать взгляд «вкладке диалогового окна» путем включения вкладки свойств и страницы свойств. Вызывается «страницы свойств» в MFC, такого рода диалоговое окно, аналогичную много диалоговых окон в Microsoft Word, Excel и Visual C++, кажется содержат стек страниц с вкладками, как стек папок с сверху вниз или группы windows каскадного. Элементы управления на вкладке "внешний" являются видимыми; только с меткой вкладка видна на задней панели вкладок. Страницы свойств обеспечивают особенно полезна для управления большим количеством свойств или настроек, которые довольно аккуратно разделить на несколько групп. Как правило одно окно свойств можно упростить пользовательский интерфейс, заменив нескольких разных диалоговых.

Начиная с MFC версии 4.0 вкладки свойств и страницы свойств реализуются с помощью стандартных элементов управления, входящих в состав Windows 95 и Windows NT 3.51 и более поздних версий.

Вкладки свойств реализуются с помощью классов [CPropertySheet](../mfc/reference/cpropertysheet-class.md) и [CPropertyPage](../mfc/reference/cpropertypage-class.md) (описано в разделе *Справочник по библиотеке MFC*). `CPropertySheet` Определяет общее диалоговое окно, которое может содержать несколько «страниц» на основе `CPropertyPage`.

Сведения о создании и работе со страницами свойств, см. в разделе [свойств](../mfc/property-sheets-mfc.md).

## <a name="see-also"></a>См. также

[Диалоговые окна](../mfc/dialog-boxes.md)<br/>
[Жизненный цикл диалогового окна](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Вкладки свойств и страницы свойств в MFC](../mfc/property-sheets-and-property-pages-in-mfc.md)<br/>
[Обмен данными](../mfc/exchanging-data.md)<br/>
[Создание немодальной страницы свойств](../mfc/creating-a-modeless-property-sheet.md)<br/>
[Обработка кнопки "Применить"](../mfc/handling-the-apply-button.md)

