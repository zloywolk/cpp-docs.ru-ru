---
title: Структура TOOLTIPTEXT | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TOOLTIPTEXT
dev_langs:
- C++
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eeee8c7b0b3cd4977688b627cb27f73e39c7ea89
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437096"
---
# <a name="tooltiptext-structure"></a>Структура TOOLTIPTEXT

В письменной вашей [обработчик уведомлений подсказки](../mfc/handling-ttn-needtext-notification-for-tool-tips.md), необходимо использовать **TOOLTIPTEXT** структуры. Члены **TOOLTIPTEXT** структуры являются:

```cpp
typedef struct {
    NMHDR     hdr;        // required for all WM_NOTIFY messages
    LPTSTR    lpszText;   // see below
    TCHAR     szText[80]; // buffer for tool tip text
    HINSTANCE hinst;      // see below
    UINT      uflags;     // flag indicating how to interpret the
                          // idFrom member of the NMHDR structure
                          // that is included in the structure
} TOOLTIPTEXT, FAR *LPTOOLTIPTEXT;
```

*HDR*<br/>
Идентифицирует средство, которое требуется текст. Единственный член этой структуры, которые могут потребовать является идентификатор команды элемента управления. Идентификатор команды элемента управления будет находиться в *idFrom* членом **NMHDR** структуры, получить доступ с помощью синтаксиса `hdr.idFrom`. См. в разделе [NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr) обсуждение членами **NMHDR** структуры.

*lpszText*<br/>
Адрес строки для получения текста для средства.

*szText*<br/>
Буфер, получающий текст подсказки. Приложения можно скопировать текст в этот буфер в качестве альтернативы для указания строки адреса.

*hinst*<br/>
Дескриптор экземпляра, который содержит строку для использования в качестве текст подсказки. Если *lpszText* — это адрес текста подсказки, этот элемент имеет значение NULL.

При обработке `TTN_NEEDTEXT` уведомления сообщений, укажите строку для отображения в одном из следующих способов:

- Скопируйте текст в буфер, определяемое *szText* член.

- Скопируйте адрес буфера, который содержит текст, *lpszText* член.

- Скопируйте идентификатор строкового ресурса для *lpszText* член и копирования дескриптор экземпляра, содержащего ресурс *hinst* член.

## <a name="see-also"></a>См. также

[Подсказки в Windows, не являющиеся производными от CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

