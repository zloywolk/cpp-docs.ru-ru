---
title: Использование интегрированной среды разработки Visual Studio для разработки классических приложений на языке C++ | Документы Майкрософт
ms.date: 06/08/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDE [C++]
- Visual Studio IDE [C++]
ms.assetid: d985c230-8e81-49d6-92be-2db9cac8d023
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4aa276c0e9d97cd5b723499a21432290772a49a7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390309"
---
# <a name="using-the-visual-studio-ide-for-c-desktop-development"></a>Использование интегрированной среды разработки Visual Studio для разработки приложений для настольных систем на языке C++

Интегрированная среда разработки (IDE) Visual Studio предлагает ряд возможностей для управления большими и малыми проектами, написания и рефакторинга кода, а также обнаружения и исправления ошибок с помощью статического анализа и эффективных средств отладки. Этот набор статей предназначен для рассмотрения каждого шага, необходимого для управления проектами, написания, проверки, отладки кода и последующего развертывания его на другом компьютере.

## <a name="prerequisites"></a>Предварительные требования

Если вы еще не установили Visual Studio, сделайте это. Ссылки для загрузки и краткое пошаговое руководство см. в разделе [Установка поддержки С++ в Visual Studio](../build/vscpp-step-0-installation.md). Дополнительные сведения о том, как установить Visual Studio и устранить возможные неполадки, см. в разделе [Установка Visual Studio](/visualstudio/install/install-visual-studio). Обязательно выберите рабочую нагрузку **Разработка классических приложений на C++**, чтобы включить компиляторы, средства и библиотеки C++ при установке Visual Studio, так как они не устанавливаются по умолчанию.

В этих пошаговых руководствах предполагается, что вы установили Visual Studio, а также язык Visual C++ и компоненты, необходимые для разработки классических приложений Windows. Кроме того, предполагается, что вы владеете основами языка C++. Для изучения C++ доступно множество разных книг и веб-ресурсов. Среди них можно выделить страницу [начала работы](https://isocpp.org/get-started) на веб-сайте Standard C++ Foundation.

Если вы еще не установили Visual Studio, сделайте это.

**Установка Visual Studio 2017**

Visual Studio 2017 можно скачать в разделе [загрузок Visual Studio](http://www.visualstudio.com/downloads/download-visual-studio-vs.aspx). Не забудьте включить средства разработки Visual C++ при установке Visual Studio, так как они не устанавливаются по умолчанию. Дополнительные сведения об установке Visual Studio см. в разделе [Установка Visual Studio](/visualstudio/install/install-visual-studio).

**Установка Visual Studio 2015**

Установить Visual Studio 2015 можно из раздела [Скачивание более старых версий Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Запустите программу установки и щелкните **Выборочная установка**, а затем выберите компонент C++.

Как правило, рекомендуется использовать Visual Studio 2017, даже если вам нужно скомпилировать код в компиляторе Visual Studio 2015. Дополнительные сведения см. в разделе [Использование собственного многоплатформенного нацеливания в Visual Studio для сборки старых проектов](../porting/use-native-multi-targeting.md).

После завершения установки Visual Studio вы можете продолжить процедуру.

## <a name="get-started"></a>Начало работы

Чтобы приступить к использованию интегрированной среды разработки Visual Studio для создания приложений C++, изучите каждый из приведенных ниже разделов в указанном порядке. Каждый из них основан на работе, выполненной в предыдущих разделах:

- [Пошаговое руководство. Работа с проектами и решениями (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)

- [Пошаговое руководство. Сборка проекта (C++)](../ide/walkthrough-building-a-project-cpp.md)

- [Пошаговое руководство. Тестирование проекта (C++)](../ide/walkthrough-testing-a-project-cpp.md)

- [Пошаговое руководство. Отладка проекта (C++)](../ide/walkthrough-debugging-a-project-cpp.md)

- [Пошаговое руководство. Развертывание программы (C++)](../ide/walkthrough-deploying-your-program-cpp.md)

## <a name="next-steps"></a>Следующие шаги

После выполнения этих пошаговых руководствах вы сможете приступить к созданию собственных проектов. Дополнительные сведения и ресурсы по разработке Visual C++ см. в разделе [Visual C++ в Visual Studio](../visual-cpp-in-visual-studio.md).

## <a name="see-also"></a>См. также

[Начало разработки в Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio)