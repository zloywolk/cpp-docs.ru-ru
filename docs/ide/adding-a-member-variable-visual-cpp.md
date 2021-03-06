---
title: Добавление переменной-члена (Visual C++) | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.classes.member.variable
dev_langs:
- C++
helpviewer_keywords:
- member variables, adding
- member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dade9987358c1c160dffd0221b0421b4fab92c24
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687646"
---
# <a name="adding-a-member-variable--visual-c"></a>Добавление переменной-члена (Visual C++)
Вы можете добавить переменную-член для класса с помощью представления классов. Переменные-члены могут использоваться для [обмена данными и их проверки](../mfc/dialog-data-exchange-and-validation.md) либо могут быть универсальными. Мастер переменных-членов данных предназначен специально для получения релевантной информации и ее использования для вставки элементов в исходные файлы в нужных расположениях. Вы можете добавить переменную-член из [редактора диалоговых окон](../windows/dialog-editor.md) в [представлении ресурсов](../windows/resource-view-window.md) или из [представления классов](/visualstudio/ide/viewing-the-structure-of-code).  
  
> [!NOTE]
>  При проектировании и реализации диалогового окна может оказаться, что эффективнее использовать редактор диалоговых окон для добавления элементов управления диалоговых окон, а затем реализовать переменные-члены для элементов управления.  
  
### <a name="to-add-a-member-variable-for-a-dialog-control-in-resource-view-using-the-add-member-variable-wizard"></a>Добавление переменной-члена для элемента управления диалогового окна в представлении ресурсов с помощью мастера добавления переменной-члена  
  
1.  В представлении ресурсов разверните узел проекта и узел диалогового окна, чтобы отобразить список диалоговых окон проекта.  
  
2.  Дважды щелкните диалоговое окно, для которого хотите добавить переменную-член, чтобы открыть его в редакторе диалоговых окон.  
  
3.  В диалоговом окне, отображаемом в редакторе диалоговых окон, щелкните правой кнопкой мыши элемент управления, к которому требуется добавить переменную-член.  
  
4.  В контекстном меню выберите команду **Добавить переменную**, чтобы отобразить [Мастер добавления переменной-члена](../ide/add-member-variable-wizard.md).  
  
    > [!NOTE]
    >  Значение по умолчанию уже указано в поле **Идентификатор элемента управления**.  
  
5.  Укажите сведения в соответствующих полях мастера. Дополнительные сведения см. в разделе [Элементы управления "Диалоговое окно" и типы переменных](../ide/dialog-box-controls-and-variable-types.md).  
  
6.  Нажмите кнопку **Готово**, чтобы добавить в проект код определения и реализации, и закройте мастер.  
  
### <a name="to-add-a-member-variable-from-class-view-using-the-add-member-variable-wizard"></a>Добавление переменной-члена из представления классов с помощью мастера добавления переменной-члена  
  
1.  В [представлении классов](/visualstudio/ide/viewing-the-structure-of-code) разверните узел проекта, чтобы отобразить классы в проекте.  
  
2.  Щелкните правой кнопкой мыши класс, куда нужно добавить переменную.  
  
3.  В контекстном меню выберите **Добавить** и **Добавить переменную**, чтобы отобразить мастер добавления переменной-члена.  
  
4.  Укажите сведения в соответствующих полях мастера. Дополнительные сведения см. в разделе [Мастер добавления переменной-члена](../ide/add-member-variable-wizard.md).  
  
5.  Нажмите кнопку **Готово**, чтобы добавить в проект код определения и реализации, и закройте мастер.  
  
## <a name="see-also"></a>См. также  
 [Добавление функциональных возможностей с помощью мастеров кода](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Добавление класса](../ide/adding-a-class-visual-cpp.md)   
 [Добавление функции-члена](../ide/adding-a-member-function-visual-cpp.md)   
 [Обработчик сообщений MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Перемещение по структуре класса](../ide/navigating-the-class-structure-visual-cpp.md)