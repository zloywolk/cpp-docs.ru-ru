---
title: -GUARD (Включение проверок защиты) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 72758e23-70ac-4616-94d7-d767477406d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71dc4a3a1f2c08d3bac2fcf5c474768f438feccd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394990"
---
# <a name="guard-enable-guard-checks"></a>/GUARD (Включить проверки защиты)

Указывает поддержку для проверок защиты потока управления в исполняемом образе.

## <a name="syntax"></a>Синтаксис

```
/GUARD:{CF|NO}
```

## <a name="remarks"></a>Примечания

Если задано /GUARD:CF, компоновщик изменяет заголовок файла DLL или EXE, чтобы указать поддержку для проверок среды выполнения защиты потока управления (CFG). Компоновщик также добавляет в заголовок требуемый целевой поток управления. По умолчанию параметр /GUARD:CF отключен. Его можно отключить явным образом, если задать /GUARD:NO. Для обеспечения эффективности/Guard: CF также требуется [/DYNAMICBASE (использование адрес места Придание случайного характера)](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) параметр компоновщика, которая включена по умолчанию.

При компиляции исходного кода с помощью [/Guard: CF](../../build/reference/guard-enable-control-flow-guard.md) параметр, компилятор анализирует поток управления путем проверки всех косвенных вызовов на наличие возможных конечных адресов. Компилятор вставляет код, чтобы убедиться, что целевой адрес инструкции косвенного вызова находится в списке известных целевых адресов во время выполнения. Операционные системы, поддерживающие CFG, останавливают программу, для которой проверка в среде выполнения CFG завершается сбоем. Это позволяет усложнить для злоумышленника процесс выполнения вредоносного кода путем повреждения данных для изменения целевого объекта вызова.

Чтобы компилятор и компоновщик смогли создавать исполняемые образы с включенной функцией CFG, необходимо задать параметр /GUARD:CF. Код, компилируемый, но не скомпонованный с помощью /GUARD:CF, снижает стоимость проверки среды выполнения, но не включает защиту CFG. При указании параметра/Guard: CF для `cl` команду, чтобы компиляцию и компоновку за один шаг, компилятор передает флаг компоновщику. Когда **защиты потока управления** свойство задается в Visual Studio, параметр/Guard: CF передается компилятора и компоновщика. Когда файлы объектов или библиотеки скомпилированы отдельно, необходимо явно указать параметр в `link` команды.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Настройка этого параметра компоновщика в Visual Studio

1. Откройте диалоговое окно **Окна свойств** проекта. Дополнительные сведения см. в разделе [Работа со свойствами проекта](../../ide/working-with-project-properties.md).

1. Разверните **свойства конфигурации**, **компоновщика**, **командной строки**.

1. В **Дополнительные параметры**, введите `/GUARD:CF`.

## <a name="see-also"></a>См. также

[/guard (включение защиты потока управления)](../../build/reference/guard-enable-control-flow-guard.md)<br/>
[Настройка параметров компоновщика](../../build/reference/setting-linker-options.md)<br/>
[Параметры компоновщика](../../build/reference/linker-options.md)