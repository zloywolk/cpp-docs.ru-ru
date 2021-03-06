---
title: Перенаправление типов (C + +/ CLI) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- type forwarding, C++
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 806003e33e60b5146bdd722fa5248011cd4939c0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396555"
---
# <a name="type-forwarding-ccli"></a>Перенаправление типов (C++/CLI)

*Перенаправление типов* позволяет переместить тип из одной сборки (А) в другую сборку (сборку Б), таким образом, что нет необходимости в повторной компиляции клиентов, использующих сборку а

## <a name="all-platforms"></a>Все платформы

Эта возможность поддерживается не во всех средах выполнения.

## <a name="windows-runtime"></a>Среда выполнения Windows

Эта функция не поддерживается в среде выполнения Windows.

### <a name="requirements"></a>Требования

Параметр компилятора: `/ZW`

## <a name="common-language-runtime"></a>Среда CLR

В следующем примере кода показано использование перенаправления типа.

### <a name="syntax"></a>Синтаксис

```
#using "new.dll"
[assembly:TypeForwardedTo(type::typeid)];
```

### <a name="parameters"></a>Параметры

*new*<br/>
Сборка, в которую перемещается определение типа.

*type*<br/>
Тип, определение которого перемещается в другую сборку.

### <a name="remarks"></a>Примечания

После поставки компонента (сборки) и его использования клиентскими приложениями можно применить перенаправление типа, чтобы переместить тип из этого компонента (сборки) в другую сборку. После поставки обновленного компонента (и всех необходимых дополнительных сборок) клиентские приложения будут работать без повторной компиляции.

Перенаправление типа работает только для компонентов, на которые ссылаются существующие приложения. При повторной сборке приложения для всех используемых в нем типов должны иметься соответствующие ссылки на сборки.

При перенаправлении типа (типа А) из сборки необходимо добавить для него атрибут `TypeForwardedTo`, а также ссылку на сборку. Сборка, на которую осуществляется ссылка, должна содержать один из следующих элементов:

- определение типа А;

- атрибут `TypeForwardedTo` для типа А и ссылку на сборку.

Примеры типов, которые могут переадресовываться:

- классы ссылок;

- классы значений;

- перечисления

- интерфейсы

Перечисленные ниже типы переадресовывать нельзя:

- универсальные типы;

- собственные типы;

- вложенные типы (если требуется переадресовать вложенный тип, следует переадресовать включающий его тип).

Тип можно переадресовать сборке, созданной на любом языке среды CLR.

Таким образом, если файл исходного кода, используемый для создания сборки A.dll, содержит определение типа (`ref class MyClass`), которое требуется переместить в сборку B.dll, выполните следующие действия.

1. Переместите определение типа `MyClass` в файл исходного кода, используемый для создания сборки B.dll.

2. Соберите сборку B.dll.

3. Удалите определение типа `MyClass` из исходного кода, используемого для создания сборки A.dll, и замените его следующим кодом:

    ```
    #using "B.dll"
    [assembly:TypeForwardedTo(MyClass::typeid)];
    ```

4. Соберите сборку A.dll.

5. Используйте сборку A.dll без повторной компиляции клиентских приложений.

### <a name="requirements"></a>Требования

Параметр компилятора: `/clr`