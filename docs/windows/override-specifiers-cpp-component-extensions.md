---
title: Переопределить спецификаторы (расширения компонентов C++) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- override specifiers, C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bcbc46ea12dd053c0c0cf5066173ea2a28857452
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316124"
---
# <a name="override-specifiers--c-component-extensions"></a>Спецификаторы переопределения (расширения компонентов C++)

*Спецификаторы переопределения* изменяют поведение унаследованных типов и членов унаследованных типов ведут себя в производных типах.

## <a name="all-runtimes"></a>Все среды выполнения

### <a name="remarks"></a>Примечания

Дополнительные сведения о спецификаторах переопределения см. в разделах:

- [abstract](../windows/abstract-cpp-component-extensions.md)

- [New (новый слот в vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)

- [override](../windows/override-cpp-component-extensions.md)

- [sealed](../windows/sealed-cpp-component-extensions.md)

- [Спецификаторы переопределения и компиляции в машинный код](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)

**Абстрактный** и **запечатанный** относятся также и на объявления типа, где они не действуют как спецификаторы переопределения.

Сведения о явного переопределения функции базового класса, см. в разделе [явное переопределение](../windows/explicit-overrides-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Среда выполнения Windows

(Отсутствуют комментарии для этой возможности языка, которая применяется только в среде выполнения Windows).

### <a name="requirements"></a>Требования

Параметр компилятора: `/ZW`

## <a name="common-language-runtime"></a>Среда CLR

(Отсутствуют комментарии для этой функции языка, которая применяется только в среде CLR).

### <a name="requirements"></a>Требования

Параметр компилятора: `/clr`

## <a name="see-also"></a>См. также

[Расширения компонентов для платформ среды выполнения](../windows/component-extensions-for-runtime-platforms.md)