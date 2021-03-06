---
title: Класс COleResizeBar | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleResizeBar
- AFXOLE/COleResizeBar
- AFXOLE/COleResizeBar::COleResizeBar
- AFXOLE/COleResizeBar::Create
dev_langs:
- C++
helpviewer_keywords:
- COleResizeBar [MFC], COleResizeBar
- COleResizeBar [MFC], Create
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf1e2b447b4cfe0e2f503d2263354f3537bbb849
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391388"
---
# <a name="coleresizebar-class"></a>Класс COleResizeBar

Тип панели элементов управления, который поддерживает изменение размера элементов OLE "на месте".

## <a name="syntax"></a>Синтаксис

```
class COleResizeBar : public CControlBar
```

## <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Описание|
|----------|-----------------|
|[COleResizeBar::COleResizeBar](#coleresizebar)|Создает объект `COleResizeBar`.|

### <a name="public-methods"></a>Открытые методы

|Имя|Описание|
|----------|-----------------|
|[COleResizeBar::Create](#create)|Создает и инициализирует дочернее окно Windows и связывает его к `COleResizeBar` объекта.|

## <a name="remarks"></a>Примечания

`COleResizeBar` объекты отображаются как [CRectTracker](../../mfc/reference/crecttracker-class.md) со штриховой границей и внешних маркеры изменения размера.

`COleResizeBar` Эти объекты объединены обычно внедренных объектов окна фрейма, производных от [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md) класса.

Дополнительные сведения см. в статье [активации](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`COleResizeBar`

## <a name="requirements"></a>Требования

**Заголовок:** afxole.h

##  <a name="coleresizebar"></a>  COleResizeBar::COleResizeBar

Создает объект `COleResizeBar`.

```
COleResizeBar();
```

### <a name="remarks"></a>Примечания

Вызовите `Create` для создания объекта панели для изменения размера.

##  <a name="create"></a>  COleResizeBar::Create

Создает дочернее окно и связывает его с `COleResizeBar` объекта.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_RESIZE_BAR);
```

### <a name="parameters"></a>Параметры

*pParentWnd*<br/>
Указатель на родительское окно полосы изменения размера.

*dwStyle*<br/>
Указывает [стиль окна](../../mfc/reference/styles-used-by-mfc.md#window-styles) атрибуты.

*nID*<br/>
Идентификатор панели изменения размера дочернего окна.

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если был создан на изменения размера панели; в противном случае 0.

## <a name="see-also"></a>См. также

[Пример MFC SUPERPAD](../../visual-cpp-samples.md)<br/>
[Класс CControlBar](../../mfc/reference/ccontrolbar-class.md)<br/>
[Диаграмма иерархии](../../mfc/hierarchy-chart.md)<br/>
[Класс COleServerDoc](../../mfc/reference/coleserverdoc-class.md)
