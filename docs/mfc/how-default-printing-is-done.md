---
title: По умолчанию печать по | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- default printing
- printing [MFC], default
- defaults, printing
ms.assetid: 0f698459-0fc9-4d43-97da-29cf0f65daa2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f3616ba3fac4d5ed8ccca6b71d6fc04a2d5c106
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399903"
---
# <a name="how-default-printing-is-done"></a>Печать по умолчанию

В этой статье объясняется, по умолчанию процесс печати в Windows с точки зрения платформы MFC.

В приложениях MFC, класс представления имеет функцию-член с именем `OnDraw` , содержащий весь код рисования. `OnDraw` принимает указатель на [CDC](../mfc/reference/cdc-class.md) объект в качестве параметра. Что `CDC` представляет объект контекста устройства для получения изображений, полученных при `OnDraw`. При получении окна отображения документа [WM_PAINT](/windows/desktop/gdi/wm-paint) сообщений, платформа вызывает `OnDraw` и передает его контекста устройства для экрана ( [CPaintDC](../mfc/reference/cpaintdc-class.md) объекта, чтобы быть точным). Соответственно `OnDraw`выходных данных переходит на экран.

В программировании для Windows, отправляющего печати на принтере очень похоже на выходные данные отправляются на экране. Это обусловлено интерфейса графических устройств Windows (GDI) не зависит от оборудования. Просто, используя контекст подходящее устройство, можно использовать те же функции GDI для отображения на экране или печати. Если `CDC` объекта, `OnDraw` получает представляет принтер, `OnDraw`выходных данных возникает неполадка на принтер.

Это объясняет, как MFC приложения могут выполнять простой печати, не требуя дополнительных усилий со стороны пользователя. Платформа отвечает за отображение диалогового окна «Печать» и создание контекста устройства для принтера. Когда пользователь выбирает команду «Печать» из меню "файл", представление передает этот контекст устройства для `OnDraw`, который рисует документа на принтере.

Тем не менее существует ряд существенных отличий между печати и дисплеем. При печати, необходимо разделить на отдельные страницы и отображения их, по одному, а не отобразить любые части отображается в окне документа. Как следствие необходимо учитывать размер бумаги (будь то Letter, допустимый размер или конверта). Можно распечатать в различные ориентации, например в режиме альбомной или книжной ориентации. Библиотеки Microsoft Foundation Class невозможно предсказать, как приложение будет обрабатывать эти проблемы, обеспечивая протокол, можно добавить эти возможности.

Что в этой статье описывается протокол [Многостраничные документы](../mfc/multipage-documents.md).

## <a name="see-also"></a>См. также

[Печать](../mfc/printing.md)

