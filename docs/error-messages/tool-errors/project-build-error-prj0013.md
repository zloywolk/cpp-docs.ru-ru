---
title: Ошибка построения проекта PRJ0013 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0013
dev_langs:
- C++
helpviewer_keywords:
- PRJ0013
ms.assetid: 95e7bafd-63c8-4b2d-b778-f19cdf9ba36c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7a151ca34d680a517c405e5cb6f91c18d35bedd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102649"
---
# <a name="project-build-error-prj0013"></a>Ошибка построения проекта PRJ0013

Не удалось создать канал, необходимый для запуска построения. Вероятно, ресурсы системы находятся на критически низкой отметке.

Эта ошибка указывает на нехватку системных ресурсов. Чтобы устранить эту ошибку, следует снизить использование системных ресурсов другими процессами или приложениями.

Эта ошибка также может возникать, если уровень безопасности недостаточен для создания каналов (см. в разделе [CreatePipe](https://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)).