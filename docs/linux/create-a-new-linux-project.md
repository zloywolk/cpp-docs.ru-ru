---
title: Создание нового проекта C++ Linux в Visual Studio | Документы Майкрософт
ms.custom: ''
ms.date: 07/20/2018
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: f64f8eaf09e92df3dd776180db5904af039d6ad7
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207974"
---
# <a name="create-a-new-linux-project"></a>Создание нового проекта Linux
При написании кода на C++ в Visual Studio для Linux можно выбрать создаваемый проект: проект Visual Studio или проект CMake. В этом разделе описывается создание проекта Visual Studio. Сведения о проектах CMake см. в разделе [Настройка проекта CMake Linux](cmake-linux-project.md).

Чтобы создать новый проект Linux в Visual Studio, выполните следующие действия.

1. Выберите **Файл > Создать проект** в меню Visual Studio или нажмите клавиши **Ctrl + Shift + N**.
1. Выберите узел **Visual C++ > Кроссплатформенный > Linux**, затем выберите тип проекта, который вы хотите создать, введите имя и расположение и нажмите кнопку "ОК".

   ![Новый проект Linux](media/newproject.png)

   | Тип проекта | Описание:
   | ------------ | ---
   | **Blink (Raspberry)**           | Проект, предназначенный для устройства Raspberry Pi, с образцом кода, написанным для мерцания светодиодного индикатора
   | **Консольное приложение (Linux)** | Проект, предназначенный для любого компьютера Linux, с образцом кода, написанным для вывода текста на консоль
   | **Пустой проект (Linux)**       | Проект, предназначенный для любого компьютера Linux, без образца кода
   | **Проект Makefile (Linux)**    | Проект, предназначенный для любого компьютера Linux, который будет собран с использованием стандартной системы сборки Makefile

