---
title: Объекты окон | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], window
- Windows window [MFC]
- MFC, windows
- frame windows [MFC], C++ window objects
- window objects [MFC]
- windows [MFC], C++ window objects
- window messages [MFC]
- HWND
- messages [MFC], Windows
- Visual C++, window objects [MFC]
- HWND, window objects [MFC]
ms.assetid: 28b33ce2-af05-4617-9d03-1cb9a02be687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 429ac52218af2e158df91c6c79f8ec67bcac3f5d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395587"
---
# <a name="window-objects"></a>Объекты окон

MFC предоставляет класс [CWnd](../mfc/reference/cwnd-class.md) для инкапсуляции `HWND` дескриптор окна. `CWnd` Объект является объектом окна C++, отличающийся от `HWND` , представляющий Windows окно, но содержащий его. Используйте `CWnd` для формирования собственных дочернего окна классов, или воспользуйтесь одним из многих классов MFC, производный от `CWnd`. Класс `CWnd` является базовым классом для всех окон, включая окна фрейма, диалоговые окна, дочерние окна, элементы управления и панели элементов управления, таких как панели инструментов. Хорошо понимать [связь между объектом окна C++ и HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md) имеет решающее значение для эффективной программирование с использованием MFC.

MFC предоставляет некоторые функциональные возможности по умолчанию и управления windows, но можно создать собственный класс, от `CWnd` и применять свои функции-члены для адаптации предоставленный функциональные возможности. Вы можете создавать дочерние окна, создав `CWnd` объекта и вызова его [создать](../mfc/reference/cwnd-class.md#create) член функции, а затем настройте в дочерние окна с помощью `CWnd` функций-членов. Вы можете внедрить объектов, производных от [CView](../mfc/reference/cview-class.md), например формы представления или представления в виде дерева, в окне фрейма. И может поддерживать несколько представлений документов с помощью разделителя области, предоставляемым классом [CSplitterWnd](../mfc/reference/csplitterwnd-class.md).

Каждый объект, производный от класса `CWnd` содержит схему сообщений, через который можно сопоставить сообщения Windows или идентификаторы команд для собственных обработчиков.

Общие литературе о программировании для Windows — это хороший ресурс для обучения использованию `CWnd` функции-члены, которые инкапсулируют `HWND` API-интерфейсы.

## <a name="functions-for-operating-on-a-cwnd"></a>Функции для работы с CWnd

`CWnd` и его [производные классы окон](../mfc/derived-window-classes.md) предоставляют конструкторы, деструкторы и функции-члены для инициализации объекта, Создание базовых структур Windows и доступ к инкапсулированный `HWND`. `CWnd` также предоставляет функции-члены, которые инкапсулируют API-интерфейсы Windows для отправки сообщений, доступ к состоянию окна, преобразование координат, обновление, прокрутка, доступ к буфера обмена, а также множество других задач. Большинство интерфейсов API управления окнами Windows, принимающий `HWND` аргумент инкапсулированы в виде функций-членов `CWnd`. Имена функций и их параметры сохраняются в `CWnd` функция-член. Дополнительные сведения о Windows API-интерфейсах, инкапсулированных в `CWnd`, см. в разделе класса [CWnd](../mfc/reference/cwnd-class.md).

## <a name="cwnd-and-windows-messages"></a>CWnd и сообщений Windows

Одно из основных целей `CWnd` заключается в предоставлении интерфейса для обработки сообщений Windows, таких как WM_PAINT или wm_mousemove и. Многие функции-члены `CWnd` являются обработчики для стандартных сообщений, начинающихся с идентификатором **afx_msg** и префикс «On», такие как `OnPaint` и `OnMouseMove`. [Обработка и сопоставление сообщений](../mfc/message-handling-and-mapping.md) охватывает сообщения и сообщения, обработка подробно. Существует информация также применима платформы windows и создать самостоятельно для особых целей.

### <a name="what-do-you-want-to-know-more-about"></a>Выберите для получения дополнительных сведений

- [Связь между объектом окна C++ и HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)

- [Производные классы окон](../mfc/derived-window-classes.md)

- [Создание окон](../mfc/creating-windows.md)

- [Уничтожение объектов окон](../mfc/destroying-window-objects.md)

- [Отсоединение CWnd от HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

- [Работа с объектами окон](../mfc/working-with-window-objects.md)

- [Контексты устройств](../mfc/device-contexts.md): объекты, которые делают независимых графических устройств Windows

- [Графические объекты](../mfc/graphic-objects.md): перья, кисти, шрифты, растровые изображения, палитр, регионах

## <a name="see-also"></a>См. также

[Windows](../mfc/windows.md)

