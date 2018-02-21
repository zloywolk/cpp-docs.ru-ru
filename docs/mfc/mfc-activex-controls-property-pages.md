---
title: "Элементов управления MFC ActiveX: Страницы свойств | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dde35df301c34a6c3a29c48d5ad145681b64a72e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-property-pages"></a>Элементы управления ActiveX в MFC. Страницы свойств
Страницы свойств позволяют пользователю элемента управления ActiveX для просмотра и изменения свойств элемента управления ActiveX. Эти свойства осуществляется путем вызова диалогового окна свойств элемента управления, которое содержит один или несколько страниц свойств, предоставляющих настраиваемый графический интерфейс для просмотра и редактирования свойств элемента управления.  
  
 Страницы свойств элемента управления ActiveX отображаются двумя способами:  
  
-   При команда свойства элемента управления (**OLEIVERB_PROPERTIES**) — вызывается, элемент управления открывает диалоговое окно свойства модального, содержащий страницы свойств элемента управления.  
  
-   Контейнер может отображать свой собственный немодальное диалоговое окно, показаны страницы свойств выбранного элемента управления.  
  
 Диалоговое окно свойств (как показано на следующем рисунке) состоит из области для отображения на текущей вкладки, вкладки для переключения между страницы свойств, а коллекция кнопок, общие задачи, например закрывающая диалоговое окно страницы свойств, Отменить все изменения, внесенные либо немедленно, применяя любые изменения в элемент управления ActiveX.  
  
 ![Диалоговое окно свойств Circ3](../mfc/media/vc373i1.gif "vc373i1")  
Диалоговое окно «Свойства»  
  
 В этой статье описываются разделы, связанные с помощью страниц свойств в элементе управления ActiveX. Сюда входит следующее.  
  
-   [Реализация по умолчанию страницу свойств для элемента управления ActiveX](#_core_implementing_the_default_property_page)  
  
-   [Добавление элементов управления на странице свойств](#_core_adding_controls_to_a_property_page)  
  
-   [Настройка DoDataExchange-функция](#_core_customizing_the_dodataexchange_function)  
  
 Дополнительные сведения об использовании страницы свойств в элементе управления ActiveX см. в следующих статьях:  
  
-   [Элементы ActiveX в MFC. Добавление дополнительной страницы пользовательских свойств](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
-   [Элементы ActiveX в MFC. Использование стандартных страниц свойств](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
 Сведения об использовании страницы свойств в приложении MFC, отличные от элемента управления ActiveX см. в разделе [свойств](../mfc/property-sheets-mfc.md).  
  
##  <a name="_core_implementing_the_default_property_page"></a>Реализация по умолчанию страницы свойств  
 При использовании мастера элементов управления ActiveX для создания проекта элемента управления, мастер элементов управления ActiveX предоставляет класс страницы свойств по умолчанию для элемента управления, производного от [COlePropertyPage класса](../mfc/reference/colepropertypage-class.md). Изначально эта страница свойств является пустым, но к нему можно добавить любой управления диалогового окна или набор элементов. Поскольку мастера элементов управления ActiveX создает класс страницы только одно свойство по умолчанию, классы страницу дополнительных свойств (который также является производным от `COlePropertyPage`) должен быть создан с помощью представления классов. Дополнительные сведения об этой процедуре см. в разделе [элементы управления MFC ActiveX: добавление другой настраиваемой свойства страницы](../mfc/mfc-activex-controls-adding-another-custom-property-page.md).  
  
 Реализация свойства страницы (в данном случае это значение по умолчанию) имеет три этапа:  
  
#### <a name="to-implement-a-property-page"></a>Для реализации страницы свойств  
  
1.  Добавить `COlePropertyPage`-производного класса в проект элемента управления. Если проект был создан с помощью мастера элементов управления ActiveX (как в данном случае), класса страницы свойств по умолчанию уже существует.  
  
2.  Использование редактора диалоговых окон для добавления всех элементов управления в шаблоне страницы свойств.  
  
3.  Настройка `DoDataExchange` функция `COlePropertyPage`-производный класс для обмена значений между элементом управления страницы свойств и элемент управления ActiveX.  
  
 Например целей, в следующих процедурах использовать простой элемент управления (с именем «Образец»). Образец был создан с помощью мастера элементов управления ActiveX и содержит только стандартное свойство заголовка.  
  
##  <a name="_core_adding_controls_to_a_property_page"></a>Добавление элементов управления на странице свойств  
  
#### <a name="to-add-controls-to-a-property-page"></a>Для добавления элементов управления страницы свойств  
  
1.  Откройте проект элемента управления откройте представление ресурсов.  
  
2.  Дважды щелкните **диалоговое окно** значок каталога.  
  
3.  Откройте **IDD_PROPPAGE_SAMPLE** диалоговое окно.  
  
     Мастер элементов управления ActiveX добавляет имя проекта в конец идентификатор диалогового окна, в этом случае образец.  
  
4.  Перетаскивание выбранного элемента управления из области элементов в область диалогового окна.  
  
5.  В этом примере текст метки элемента управления «заголовок:» и поле ввода с **IDC_CAPTION** достаточны идентификатор.  
  
6.  Нажмите кнопку **Сохранить** на панели инструментов, чтобы сохранить изменения.  
  
 Теперь, когда пользовательский интерфейс был изменен, необходимо связать со свойством заголовок поля ввода. Это делается в следующем разделе, изменив `CSamplePropPage::DoDataExchange` функции.  
  
##  <a name="_core_customizing_the_dodataexchange_function"></a>Настройка DoDataExchange-функция  
 На странице свойств [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) функция позволяет связывать значения свойств страницы с фактическими значениями свойств в элементе управления. Для установления связи, необходимо сопоставить поля страницы соответствующее свойство их соответствующим свойствам элемента управления.  
  
 Эти сопоставления реализуются с помощью страницы свойств **DDP_** функции. **DDP_** функции работают как **DDX_** функций, используемых в стандартных диалоговых окон MFC, за одним исключением. Помимо ссылку на переменную-член **DDP_** функции принимают имя свойства элемента управления. Ниже приведен типичный запись в `DoDataExchange` функции для страницы свойств.  
  
 [!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]  
  
 Эта функция связывает страницу свойств `m_caption` переменную-член с заголовком с помощью `DDP_TEXT` функции.  
  
 После вставки элемента управления свойства страницы, необходимо установить связь между управления страницы свойств, `IDC_CAPTION`, и свойство фактического элемента управления, заголовок, с помощью **DDP_Text** работать так, как описано выше.  
  
 [Страницы свойств](../mfc/reference/property-pages-mfc.md) доступны для других типов элементов управления диалогового окна, например флажков, переключателей и полей со списком. В следующей таблице перечислены весь набор свойств **DDP_** функции и их цели:  
  
### <a name="property-page-functions"></a>Функции страницы свойств  
  
|Имя функции|Эта функция используется для связывания|  
|-------------------|-------------------------------|  
|`DDP_CBIndex`|Индекс выбранной строки в поле со списком со свойством элемента управления.|  
|`DDP_CBString`|Выбранной строки в поле со списком со свойством элемента управления. Можно начать с того же буквы как значение свойства выбранной строки, но требуется его полностью совпадают.|  
|`DDP_CBStringExact`|Выбранной строки в поле со списком со свойством элемента управления. Выбранные строки и значения свойства строки должны точно совпадать.|  
|`DDP_Check`|Флажок со свойством элемента управления.|  
|`DDP_LBIndex`|Индекс выбранной строки в поле со списком со свойством элемента управления.|  
|`DDP_LBString`|Строка, выбранного в поле со списком со свойством элемента управления. Можно начать с того же буквы как значение свойства выбранной строки, но требуется его полностью совпадают.|  
|`DDP_LBStringExact`|Строка, выбранного в поле со списком со свойством элемента управления. Выбранные строки и значения свойства строки должны точно совпадать.|  
|`DDP_Radio`|Переключатель со свойством элемента управления.|  
|**DDP_Text**|Текст со свойством элемента управления.|  
  
## <a name="see-also"></a>См. также  
 [Элементы управления ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Класс COlePropertyPage](../mfc/reference/colepropertypage-class.md)