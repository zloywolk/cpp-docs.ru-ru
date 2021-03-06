---
title: 'TN070: Имена классов окна MFC | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.classes
dev_langs:
- C++
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 92dcc2509732472774a119dafb43174895247948
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382522"
---
# <a name="tn070-mfc-window-class-names"></a>TN070. Имена классов окна MFC

> [!NOTE]
>  Следующее техническое примечание не было обновлено, поскольку сначала оно было включено в электронную документацию. В результате некоторые процедуры и разделы могут быть устаревшими или неверными. Для получения последних сведений рекомендуется выполнить поиск интересующей темы в алфавитном указателе документации в Интернете.

MFC windows используйте имя динамически создаваемого класса, которое отражает компоненты окна. MFC создает имена классов динамически для окна фрейма, представления и всплывающие окна, созданных приложением. Диалоговые окна и элементы управления, созданные в приложении MFC имеют имя, предоставленное Windows, для класса окна в вопросе.

Можно заменить имя динамически предоставленный класс, зарегистрировав свой собственный класс окна и его использованием в переопределение [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow). Их имена классов библиотека MFC предоставляет соответствующих ни одному из двух следующих форм:

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

Шестнадцатеричных цифр, которые заменяют `%x` символов заполняются на основе данных из [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) структуры. MFC использует эту методику, чтобы несколько классов C++, требуя идентичные **WNDCLASS** структуры могут совместно использовать один зарегистрированный класс. В отличие от большинства простых приложений Win32, MFC-приложения есть только **WNDPROC**, поэтому вы можете легко обмениваться **WNDCLASS** структур для экономии времени и памяти. Можно заменить значения `%x` символов, показанный выше, следующим образом:

- **WNDCLASS.hInstance**

- **WNDCLASS.style**

- **WNDCLASS.hCursor**

- **WNDCLASS.hbrBackground**

- **WNDCLASS.hIcon**

Первая форма (`Afx:%x:%x`) используется, если **hCursor**, **hbrBackground**, и **hIcon** все **NULL**.

## <a name="see-also"></a>См. также

[Технические примечания по номеру](../mfc/technical-notes-by-number.md)<br/>
[Технические примечания по категории](../mfc/technical-notes-by-category.md)<br/>
[TN020. Соглашения об именовании и нумерации идентификаторов](../mfc/tn020-id-naming-and-numbering-conventions.md)

