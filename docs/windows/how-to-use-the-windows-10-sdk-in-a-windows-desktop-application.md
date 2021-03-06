---
title: 'Практическое: использовать Windows 10 SDK в настольном приложении Windows | Документация Майкрософт'
ms.custom: get-started-article
ms.date: 07/12/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: afe678ca4ea381709b126168639df3f710867b9e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611324"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>Практическое руководство. Использование пакета SDK для Windows 10 в классическом приложении Windows

При создании классического проекта рабочего стола Windows в Visual Studio 2017 задано по умолчанию для сборки с версией пакета SDK Windows 10, установленной при установки или последнего обновления рабочей нагрузки C++ Desktop. Эта версия пакета SDK Windows совместима с Windows 7 и более поздних версий. См. в разделе [использование заголовков Windows](/windows/desktop/WinProg/using-the-windows-headers) Дополнительные сведения о предназначенных для конкретных версий Windows.

Если вы хотите более ранней версии пакета SDK, его можно открыть **проекта | Свойства** и выберите из версии пакета SDK, доступные в раскрывающемся списке версия пакета SDK для Windows.

Начиная с Visual Studio 2015 и пакета SDK для Windows 10, библиотека CRT была разделена на две части, один (ucrtbase) содержит функции, которые являются допустимыми для использования в универсальных приложениях Windows, а тот, который содержит все остальное (vcruntime140). Поскольку пакет SDK для Windows 10 содержит новые функции, например многие функции C99, для их использования необходимо выполнить следующие действия. См. статью [CRT Library Features](../c-runtime-library/crt-library-features.md) (Функции библиотеки CRT).

### <a name="to-target-the-windows-10-sdk"></a>Изменение целевой платформы для пакета SDK для Windows 10

1. Убедитесь, что установлен пакет SDK для Windows 10. Пакет SDK для Windows 10 устанавливается как часть **разработка классических приложений C++** рабочей нагрузки. Отдельная версия доступна на [загружаемые файлы и инструменты для Windows 10](https://developer.microsoft.com/windows/downloads).

2. Откройте контекстное меню узла проекта и выберите пункт **Изменить целевую платформу для версии пакета SDK**.

   ![Перенацелить пакет SDK версии](../windows/media/retargetingwindowssdk1.PNG "RetargetingWindowsSDK1")

   Откроется диалоговое окно **Просмотр действий решения** .

   ![Просмотр действий решения](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")

3. В **версии целевой платформы** раскрывающемся списке выберите версию пакета SDK для Windows 10, вы будете работать. Нажмите кнопку «ОК» для применения изменений.

   Обратите внимание, что 8.1 в данном контексте относится к версии пакета SDK Windows, которая также обратно совместима с Windows 8, Windows Server 2012, Windows 7, Windows Server 2008 и Windows Vista.

   Если этот шаг выполнен успешно, в окне вывода появится следующее сообщение.

   `Retargeting End: 1 completed, 0 failed, 0 skipped`

4. Откройте свойства проекта и в разделе **Свойства конфигурации, Общие** обратите внимание на значения из параметра **Версия целевой платформы Windows**. Изменение значения на данном этапе действует аналогично данной процедуре. См. раздел [General Property Page (Project)](../ide/general-property-page-project.md).

   ![Версия целевой платформы](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")

   Это действие приводит к изменению значений макросов проекта, содержащих пути к файлам заголовка и файлам библиотеки. Чтобы увидеть, что было изменено в **каталогов Visual C++** раздел **свойства проекта** диалоговое окно, выберите одно из свойств, например **каталоги включаемых файлов**, решили Откройте раскрывающийся список и выберите \<изменить >. Откроется диалоговое окно **Каталоги включения** .

   ![Имеющие диалоговое окно каталогов](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")

   Выберите **макросы >>** кнопку и прокрутите вниз список макросов макросы Windows SDK, чтобы увидеть все новые значения.

   ![Макросы Windows SDK](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")

5. При необходимости повторите для других проектов и перестройте решение.

### <a name="to-target-the-windows-81-sdk"></a>Изменение целевой платформы для пакета SDK для Windows 8.1

1. Откройте контекстное меню узла проекта и выберите пункт **Изменить целевую платформу для версии пакета SDK**.

2. В **версии целевой платформы** раскрывающегося списка выберите **8.1**.

## <a name="see-also"></a>См. также

[Классические приложения Windows (Visual C++)](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)