---
title: Ошибкой R6016 ошибка времени выполнения C | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6016
dev_langs:
- C++
helpviewer_keywords:
- R6016
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65f4b4529e0faf433ff9dc5c4fc2c0594a4d9ff6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076649"
---
# <a name="c-runtime-error-r6016"></a>Ошибкой R6016 ошибка времени выполнения C

недостаточно памяти для данных потока

> [!NOTE]
>  Обнаружив это сообщение об ошибке при выполнении приложения, приложения завершил работу, поскольку в нем внутренняя проблема с памятью. Существует множество возможных причин этой ошибки, но часто причиной является условием чрезвычайно нехватки памяти, ошибки в приложении или на ошибку в надстройки или расширения, используемых в приложении.
>
>  Для устранения этой ошибки попробуйте выполнить следующие действия:
>
>  -   Закройте другие запущенные приложения или перезагрузить компьютер, чтобы освободить память.
> -   Используйте **программы и компоненты** или **программы и компоненты** странице в **панели управления** восстановите или переустановите приложение.
> -   Используйте **программы и компоненты** или **программы и компоненты** странице в **панели управления** удаление, восстановите или переустановите надстроек или расширений, используемых в приложении.
> -   Проверьте **Windows Update** в **панели управления** для обновлений программного обеспечения.
> -   Проверьте наличие обновленной версии приложения. Если проблема будет повторяться, обратитесь к его поставщиком.

**Сведения для программистов**

Эта ошибка происходит потому, что программа не получила достаточный объем памяти от операционной системы для завершения [_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md) или `_beginthreadex` звонок или не был инициализирован с локального хранилища потока `_beginthread` или `_beginthreadex`.

Для создаваемого потока в библиотеке должна создаваться внутренняя база данных. Если выделяемой в операционной системе памяти недостаточно для расширения базы данных, поток не запускается, а вызывающий процесс останавливается. Это может произойти, если процесс создал слишком много потоков или если локальное хранилище потока полностью заполнено.

Корпорация Майкрософт рекомендует использование исполняемого файла, который вызывает библиотеку времени выполнения C (CRT) `_beginthreadex` для создания потока, а не Windows API `CreateThread`. `_beginthreadex` инициализирует внутреннее статическое хранилище, которое используется многими функциями CRT в локальном хранилище потока. Если поток создан с помощью функции `CreateThread`, среда CRT может завершить процесс с ошибкой R6016 в случае вызова функции CRT, для которой требуется инициализированное внутреннее статическое хранилище.