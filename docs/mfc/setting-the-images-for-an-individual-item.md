---
title: Установка изображений для отдельного элемента | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ddf2f3a57511e227a934f11262f46b528dc20aa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373494"
---
# <a name="setting-the-images-for-an-individual-item"></a>Установка изображений для отдельного элемента

Различные типы изображений, используемых элементом поле Расширенное поле со списком определяются по значениям в *iImage*, *iSelectedImage*, и *iOverlay* членами [ COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema) структуры. Каждое значение является индекс изображения в списке связанное изображение элемента управления. По умолчанию эти члены имеют значение 0, вызывает элемент управления для отображения нет изображения для элемента. Если вы хотите использовать образы для конкретного элемента, можно изменить структуру соответствующим образом, при вставке элемента поля со списком или путем изменения существующего элемента поле со списком.

## <a name="setting-the-image-for-a-new-item"></a>Задание изображения для элемента

При вставке нового элемента, инициализировать *iImage*, *iSelectedImage*, и *iOverlay* членов с соответствующими значениями структуры и вставьте элемент с помощью вызова [CComboBoxEx::InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem).

В следующем примере вставляется новый элемент поле Расширенное поле со списком (`cbi`) в поле Расширенное поле со списком (`m_comboEx`), указав индексов для всех трех изображения состояния:

[!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]

## <a name="setting-the-image-for-an-existing-item"></a>Задание изображения для существующего элемента

Если вы изменяете существующий элемент, необходимо работать с *маска* членом **COMBOBOXEXITEM** структуры.

#### <a name="to-modify-an-existing-item-to-use-images"></a>Чтобы изменить существующий элемент, чтобы использовать образы

1. Объявите **COMBOBOXEXITEM** структурировать и задать *маска* элемента данных к значениям вы заинтересованы в изменение.

1. Эта структура вызова с [CComboBoxEx::GetItem](../mfc/reference/ccomboboxex-class.md#getitem).

1. Изменить *маска*, *iImage*, и *iSelectedImage* членами вновь возвращаемой структуры, используя соответствующие значения.

1. Вызвать [CComboBoxEx::SetItem](../mfc/reference/ccomboboxex-class.md#setitem), передавая измененной структуры.

В следующем примере показано эту процедуру путем замены изображений выбранном и невыбранном третий элемент поле Расширенное поле со списком:

[!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]

## <a name="see-also"></a>См. также

[Использование CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Элементы управления](../mfc/controls-mfc.md)

