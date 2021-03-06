---
title: Категории сообщений | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], categories
- control-notification messages [MFC]
- Windows messages [MFC], categories
- controls [MFC], notifications
- command messages [MFC]
- messages [MFC], Windows
- message handling [MFC], message types
ms.assetid: 68e1db75-9da6-4a4d-b2c2-dc4d59f8d87b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b1b8da6f6c1b94432d9cd4c91d88f6d844fbb27
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433053"
---
# <a name="message-categories"></a>Категории сообщений

Какие виды сообщений написать обработчики для делятся на три основные категории:

1. сообщения Windows

     Сюда входят в первую очередь сообщений, начиная с версии **WM_** префикс, за исключением WM_COMMAND. Сообщения Windows, обрабатываются по windows и представления. Часто эти сообщения имеют параметры, которые используются при определении способа для обработки сообщения.

1. Уведомления элементов управления

     Сюда входят WM_COMMAND-сообщения для уведомлений от элементов управления и других дочерних окон родительским окнам. Например элемент управления редактированием отправляет родительского WM_COMMAND сообщение, содержащее код EN_CHANGE уведомление элемента управления, когда пользователь перевел действие, которое может изменен текст в элементе управления. Обработчик окна сообщения отвечает на сообщение уведомления соответствующим образом, такие как извлечение текста в элементе управления.

     Платформа перенаправляет сообщения уведомление элемента управления, как другой **WM_** сообщений. Единственное исключение, однако является BN_CLICKED уведомление элемента управления сообщение от кнопки при нажатии пользователем кнопок. Это сообщение обрабатывается особым образом, как сообщение команды и маршрутизации, как и другие команды.

1. Сообщения команды

     Сюда входят WM_COMMAND-сообщения уведомления из объектов пользовательского интерфейса: меню, кнопки панели инструментов и сочетания клавиш. Платформа обрабатывает команды по-разному из других сообщений, и они могут обрабатываться несколько видов объектов, как описано в [целей команды](../mfc/command-targets.md).

##  <a name="_core_windows_messages_and_control.2d.notification_messages"></a> Сообщения Windows и уведомление элемента управления

Сообщений в категориях, 1 и 2 — Windows сообщений и уведомлений элементов управления, обрабатываются системой windows: объекты классов, производный от класса `CWnd`. Сюда входят `CFrameWnd`, `CMDIFrameWnd`, `CMDIChildWnd`, `CView`, `CDialog`, и свои собственные классы, производные от этих базовых классов. Такие объекты инкапсулировать `HWND`, дескриптор окна Windows.

##  <a name="_core_command_messages"></a> Сообщения команды

Сообщения в категории 3 — команды — могут быть обработаны широкий ряд объектов: документы, шаблоны документов и сам объект приложения, в дополнение к windows и представления. Когда команду напрямую влияет на некоторые конкретный объект, имеет смысл иметь этот объект обработать команду. Например, команду «Открыть» в меню "файл" логически связан с приложением: приложение открывает указанный документ при получении команды. Поэтому обработчик для команды «Открыть» является функцией-членом класса приложения. Дополнительные сведения о командах и способе их маршрутизации к объектам, см. в разделе [как платформа вызывает обработчик](../mfc/how-the-framework-calls-a-handler.md).

## <a name="see-also"></a>См. также

[Сообщения и команды платформы](../mfc/messages-and-commands-in-the-framework.md)

