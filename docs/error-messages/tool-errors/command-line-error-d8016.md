---
title: Ошибка командной строки D8016 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8016
dev_langs:
- C++
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ee16542b2f0cf9842e351813ed2e0b0d22cccaa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056993"
---
# <a name="command-line-error-d8016"></a>Ошибка командной строки D8016

несовместимые параметры командной строки «параметр1» и параметр «2»

Параметры командной строки нельзя указывать вместе.

Проверьте переменные среды, например CL, параметры.

**/ CLR** подразумевает **/EHa**, и нельзя использовать другие **/EH** параметра компилятора с **/CLR**. Дополнительные сведения см. в разделе [/clr (компиляция CLR)](../../build/reference/clr-common-language-runtime-compilation.md).

D8016 может возникнуть после обновления проекта Visual C++ 6.0: мастер обновления проекта может включить **/RTC** для каждого файла исходного кода в проекте, который переопределяет **/RTC** для проекта.  Чтобы устранить проблему, измените **/RTC** задания для каждого файла исходного кода в проекте по умолчанию, означающее параметров проекта для **/RTC** вступят в силу для каждого файла.

См. в разделе [/RTC (проверки ошибок во время выполнения)](../../build/reference/rtc-run-time-error-checks.md) сведения об изменении **/RTC** значение свойства.