---
title: Класс CD2DEllipse | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse::CD2DEllipse
dev_langs:
- C++
helpviewer_keywords:
- CD2DEllipse [MFC], CD2DEllipse
ms.assetid: e9f02f54-acf2-427e-b349-db50cd9a77df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6acec41bcae08f5585eb521dc90ff12d082fd5ad
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418688"
---
# <a name="cd2dellipse-class"></a>Класс CD2DEllipse

Программа-оболочка для `D2D1_ELLIPSE`.

## <a name="syntax"></a>Синтаксис

```
class CD2DEllipse : public D2D1_ELLIPSE;
```

## <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Описание|
|----------|-----------------|
|[CD2DEllipse::CD2DEllipse](#cd2dellipse)|Перегружен. Создает `CD2DEllipse` объекта из `D2D1_ELLIPSE` объекта.|

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`D2D1_ELLIPSE`

`CD2DEllipse`

## <a name="requirements"></a>Требования

**Заголовок:** afxrendertarget.h

##  <a name="cd2dellipse"></a>  CD2DEllipse::CD2DEllipse

Создает объект CD2DEllipse из CD2DRectF объект.

```
CD2DEllipse(const CD2DRectF& rect);
CD2DEllipse(const D2D1_ELLIPSE& ellipse);
  CD2DEllipse(const D2D1_ELLIPSE* ellipse);


CD2DEllipse(
    const CD2DPointF& ptCenter,
    const CD2DSizeF& sizeRadius);
```

### <a name="parameters"></a>Параметры

*Rect*<br/>
исходный прямоугольник

*эллипс*<br/>
эллипс источника

*ptCenter*<br/>
Центральной точки эллипса.

*sizeRadius*<br/>
Радиус по оси X и Y-радиус эллипса.

## <a name="see-also"></a>См. также

[Классы](../../mfc/reference/mfc-classes.md)
