---
title: Добавление класса из элемента ActiveX (Visual C++) | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], adding classes
- classes [C++], creating
ms.assetid: 729fcb37-54b8-44d5-9b4e-50bb16e0eea4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fd284236d2e9267d281061eef3915ed41f6f590
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375961"
---
# <a name="adding-a-class-from-an-activex-control-visual-c"></a>Добавление класса из элемента управления ActiveX (Visual C++)

Этот мастер используется для создания класса MFC из интерфейса в доступном элементе управления ActiveX. Вы можете добавить класс MFC для [приложения MFC](../mfc/reference/creating-an-mfc-application.md), [библиотеки DLL MFC](../mfc/reference/creating-an-mfc-dll-project.md) или [элемента управления ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md).

> [!NOTE]
>  Чтобы добавить класс из элемента управления ActiveX, вам не нужно создавать проект MFC с включенной автоматизацией.

Элемент управления ActiveX — это многоразовый программный компонент, основанный на модели COM, который поддерживает широкий набор функциональных возможностей OLE и может быть настроен под различные потребности программного обеспечения. Элементы управления ActiveX предназначены для использования в обычных контейнерах элементов управления ActiveX, а также на веб-страницах в Интернете.

### <a name="to-add-an-mfc-class-from-an-activex-control"></a>Добавление класса MFC из элемента управления ActiveX

1. В **обозревателе решений** или [представлении классов](/visualstudio/ide/viewing-the-structure-of-code) щелкните правой кнопкой мыши имя проекта, куда вы хотите добавить класс элемента управления ActiveX.

1. В контекстном меню выберите команду **Добавить**, а затем — **Добавить класс**.

1. В области "Шаблоны" диалогового окна [Добавление класса](../ide/add-class-dialog-box.md) щелкните **Класс MFC из элемента управления ActiveX**, а затем нажмите кнопку **Открыть**, чтобы отобразить [Мастер добавления классов из элемента ActiveX](../ide/add-class-from-activex-control-wizard.md).

В этом мастере можно добавить несколько интерфейсов в элементе управления ActiveX. Аналогично можно создать классы из более чем одного элемента управления ActiveX в одном сеансе мастера.

Вы можете добавлять классы из элементов управления ActiveX, зарегистрированных в системе, а также расположенных в файлах библиотеки типов (TLB, OLB, DLL, OCX или EXE) без их предварительной регистрации в системе. Дополнительные сведения о регистрации элементов управления ActiveX см. в разделе [Регистрация элементов управления OLE](../mfc/reference/registering-ole-controls.md).

Мастер создает класс MFC, производный от [CWnd](../mfc/reference/cwnd-class.md) или [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md), для каждого интерфейса, добавляемого из выбранного элемента управления ActiveX.

## <a name="see-also"></a>См. также

[Элементы ActiveX библиотеки MFC](../mfc/mfc-activex-controls.md)<br>
[Введение в модель COM и ATL](../atl/introduction-to-com-and-atl.md)