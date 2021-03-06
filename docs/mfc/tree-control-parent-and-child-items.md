---
title: Родительский элемент управления и дочерние элементы древовидного | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parent items in CTreeCtrl [MFC]
- child items in tree control [MFC]
- CTreeCtrl class [MFC], parent and child items
- tree controls [MFC], parent and child items
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94bae5d06dd5b0e072d17588af045ec87a33fcc7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374714"
---
# <a name="tree-control-parent-and-child-items"></a>Родительские и дочерние элементы древовидного элемента управления

Любой элемент в виде дерева ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) может содержать список элементов, которые называются дочерние элементы, связанные с ней. Элемент, имеющий один или несколько дочерних элементов вызывается родительским элементом. Дочерний элемент отображается под его родительским элементом и отображается с отступом, чтобы указать, что он является подчиненным для родительского. Элемент, который не имеет родительского элемента в верхней части иерархии и вызывается корневой элемент.

В любой момент времени состояние родительского элемента списка дочерних элементов можно либо разворачивать и сворачивать. В развернутом состоянии дочерние элементы отображаются под родительским элементом. Если он свернут, дочерние элементы не отображаются. Список автоматически переключает между раскрытым и свернутым состояниями при двойном щелчке на родительский элемент, или, если у родительского **TVS_HASBUTTONS** стиль, при нажатии кнопки, связанной с родительским элементом. Приложение можно развернуть или свернуть дочерние элементы с помощью [Expand](../mfc/reference/ctreectrl-class.md#expand) функция-член.

Добавить элемент в дерево путем вызова [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) функция-член. Эта функция возвращает дескриптор **HTREEITEM** тип, который однозначно определяет элемент. При добавлении элемента, необходимо указать дескриптор нового элемента родительского элемента. Если указать **NULL** или **TVI_ROOT** значение вместо дескриптора родительского элемента в [TVINSERTSTRUCT](/windows/desktop/api/commctrl/ns-commctrl-tagtvinsertstructa) структуры или *hParent* параметр, элемент добавляется в качестве корневого элемента.

Отправляет элемент управления дерева [TVN_ITEMEXPANDING](/windows/desktop/Controls/tvn-itemexpanding) сообщение уведомления, когда родительский элемент списка дочерних элементов разворачивать и сворачивать. Уведомление можно отправить для предотвращения изменения или задания атрибутов родительского элемента, которые зависят от состояния списка дочерних элементов. После изменения состояния списка, дерева отправляет [TVN_ITEMEXPANDED](/windows/desktop/Controls/tvn-itemexpanded) сообщение уведомления.

При развертывании списка дочерних элементов отображается с отступом относительно родительского элемента. Величину отступа можно задать с помощью [SetIndent](../mfc/reference/ctreectrl-class.md#setindent) функция-член или получить текущей суммы с помощью [GetIndent](../mfc/reference/ctreectrl-class.md#getindent) функция-член.

## <a name="see-also"></a>См. также

[Использование CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Элементы управления](../mfc/controls-mfc.md)

