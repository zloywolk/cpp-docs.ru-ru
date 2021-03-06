---
title: -hotpatch (создать образ с обновлениями) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /hotpatch
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- C++
helpviewer_keywords:
- hot patching
- -hotpatch compiler option [C++]
- /hotpatch compiler option [C++]
- hotpatching
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97e1b6197ea60099457db7788ad7e24b96c9fcb8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716980"
---
# <a name="hotpatch-create-hotpatchable-image"></a>/hotpatch (Создать образ с обновлениями)

Готовит образ к оперативному исправлению.

## <a name="syntax"></a>Синтаксис

```
/hotpatch
```

## <a name="remarks"></a>Примечания

Когда **/hotpatch** используется в процессе компиляции компилятор гарантирует, что первой инструкции каждой функции по крайней мере два байта, который необходим для критического обновления.

Чтобы завершить подготовку для создания образа с обновлением, после использования **/hotpatch** для компиляции, необходимо использовать [/FUNCTIONPADMIN (создать образ с обновлениями)](../../build/reference/functionpadmin-create-hotpatchable-image.md) для связывания. Компиляция и связывание изображения с помощью одного вызова cl.exe, **/hotpatch** подразумевает **/functionpadmin**.

Так как инструкции всегда по два байта или больше для архитектуры ARM и поскольку x64 компиляции всегда рассматривается так, как если **/hotpatch** была определена, нет необходимости указывать **/hotpatch** при Компиляция для этих целевых объектов; Тем не менее, по-прежнему необходимо связать с помощью **/functionpadmin** для создания образов с обновлениями для них. **/Hotpatch** компиляции x86 влияет на единственный параметр компилятора.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [Работа со свойствами проекта](../../ide/working-with-project-properties.md).

1. Выберите **C/C++** папки.

1. Выберите **командной строки** страницу свойств.

1. Добавить параметр компилятора для **Дополнительные параметры** поле.

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="guidance"></a>Руководство

Дополнительные сведения об управлении обновлениями см. в разделе «Руководство по безопасности для обновления Management» в [ http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx ](http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx).

## <a name="see-also"></a>См. также

[Параметры компилятора](../../build/reference/compiler-options.md)<br/>
[Настройка параметров компилятора](../../build/reference/setting-compiler-options.md)