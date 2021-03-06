---
title: / Параметр CLRUNMANAGEDCODECHECK (Добавление SuppressUnmanagedCodeSecurityAttribute) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRUNMANAGEDCODECHECK
dev_langs:
- C++
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 679adc527cc70056e1292eb7e639499bd814bca6
ms.sourcegitcommit: 7838764e09819822a105accf5d773b2e37ffa0ae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/28/2018
ms.locfileid: "47429765"
---
# <a name="clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute"></a>/ Параметр CLRUNMANAGEDCODECHECK (Добавление SuppressUnmanagedCodeSecurityAttribute)

**/ Параметр CLRUNMANAGEDCODECHECK** указывает, будет ли компоновщик применять <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> до компоновщиком `PInvoke` вызовы собственных библиотек DLL из управляемого кода.

## <a name="syntax"></a>Синтаксис

> **/ ПАРАМЕТР CLRUNMANAGEDCODECHECK**[**: НЕТ**]

## <a name="remarks"></a>Примечания

По умолчанию компоновщик применяет **SuppressUnmanagedCodeSecurityAttribute** до компоновщиком `PInvoke` вызовов. Когда **/clrunmanagedcodecheck** , **SuppressUnmanagedCodeSecurityAttribute** не применяется.

Компоновщик только добавляет атрибут к объектам, которые компилируются с **/CLR** или **/CLR: pure**. Тем не менее **/CLR: pure** параметр компилятора в Visual Studio 2015 не рекомендуется и не поддерживается в Visual Studio 2017.

Объект `PInvoke` компоновщиком создается вызов, когда компоновщик не может найти управляемый символ для удовлетворения ссылку из управляемого вызывающего объекта, но можно найти символ для удовлетворения этой ссылки. Дополнительные сведения о `PInvoke`, см. в разделе [вызов собственных функций из управляемого кода](../../dotnet/calling-native-functions-from-managed-code.md).

Обратите внимание, что при использовании <xref:System.Security.AllowPartiallyTrustedCallersAttribute> в коде, необходимо явно указать **/clrunmanagedcodecheck**. Это потенциальной уязвимости безопасности, если изображение содержит атрибуты AllowPartiallyTrustedCallers и SuppressUnmanagedCodeSecurity.

См. в разделе [правил написания безопасного кода для неуправляемого кода](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code) Дополнительные сведения о последствиях с помощью **SuppressUnmanagedCodeSecurityAttribute**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Задание данного параметра компоновщика в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [Работа со свойствами проекта](../../ide/working-with-project-properties.md).

1. Разверните узел **Свойства конфигурации**.

1. Разверните **компоновщика** узла.

1. Выберите **Дополнительно** страницу свойств.

1. Изменить **CLR неуправляемый код проверять** свойство.

### <a name="to-set-this-linker-option-programmatically"></a>Задание данного параметра компоновщика программным способом

1. См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>.

## <a name="see-also"></a>См. также

- [Настройка параметров компоновщика](../../build/reference/setting-linker-options.md)
- [Параметры компоновщика](../../build/reference/linker-options.md)
