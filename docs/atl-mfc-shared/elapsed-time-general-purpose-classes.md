---
title: 'Затраченное время: Классы общего назначения | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- adding dates
- calculating dates and times
- dates, calculating intervals
- elapsed time, calculating
- elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: e5c5d3d2-ce1d-409e-875c-98848434e716
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff07c1b26649ffd591bcab9917cf45fa4c67f30a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/05/2018
ms.locfileid: "43756520"
---
# <a name="elapsed-time-general-purpose-classes"></a>Затраченное время: Классы общего назначения

Ниже показано, как вычислить разницу между двумя `CTime` объектов и получите `CTimeSpan` результат. Используйте `CTime` и `CTimeSpan` объекты для вычисления истекшего времени, следующим образом:

   [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]

После вычисления `elapsedTime`, можно использовать функции-члены `CTimeSpan` для извлечения компонентов значения затраченного времени.  

