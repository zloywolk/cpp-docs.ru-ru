---
title: Использование списков изображений с элементами управления заголовка | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 477ed175e6f8e81acdae5c873d1436e6c3dbbd60
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423563"
---
# <a name="using-image-lists-with-header-controls"></a>Использование списков изображений с элементами управления "Заголовок"

Элементы заголовка имеют возможность отображения изображения в элементе заголовка. Этот образ, хранящихся в списке нужный образ, 16 x 16 пикселей и имеет те же характеристики, как изображения значков, используемых в элементе управления списком. Чтобы успешно реализовать это поведение, необходимо сначала создать и инициализировать список изображений, связать с элементом управления заголовка списка и измените атрибуты элемента заголовка, который будет отображать изображения.

В следующей процедуре показано сведения, используя указатель на элемент управления заголовка (`m_pHdrCtrl`) и указатель на список изображений (`m_pHdrImages`).

### <a name="to-display-an-image-in-a-header-item"></a>Для отображения изображения в элементе заголовка

1. Создать список изображений (или использование существующего объекта списка изображений) с помощью [CImageList](../mfc/reference/cimagelist-class.md) конструктор, хранение результирующий указатель.

1. Инициализируйте новый объект списка образа путем вызова [CImageList::Create](../mfc/reference/cimagelist-class.md#create). Следующий код является примером этого вызова.

     [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]

1. Добавление изображений для каждого элемента заголовка. Следующий код добавляет два стандартных образов.

     [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]

1. Связать список изображений с элементом управления заголовка с помощью вызова [CHeaderCtrl::SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist).

1. Изменение элемента заголовка для отображения изображения в списке нужный образ. В следующем примере назначается первое изображение из `m_phdrImages`, к первому элементу заголовка, `m_pHdrCtrl`.

     [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]

Подробные сведения о значениях параметров, используемых, обратитесь к соответствующей [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md).

> [!NOTE]
>  Это может быть несколько элементов управления, используя тот же набор изображений. Например в элементе представления стандартного списка может быть используемые представления мелкого значка элемента управления представления списка и заголовок элемента управления представления списком списка изображений (из изображения 16 x 16 пикселей).

## <a name="see-also"></a>См. также

[Использование CHeaderCtrl](../mfc/using-cheaderctrl.md)

