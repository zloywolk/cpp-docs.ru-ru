---
title: Функции &lt;system_error&gt; | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- system_error/std::generic_category
- system_error/std::make_error_code
- system_error/std::make_error_condition
- system_error/std::system_category
ms.assetid: 57d6f15f-f0b7-4e2f-80fe-31d3c320ee33
helpviewer_keywords:
- std::generic_category
- std::make_error_code
- std::make_error_condition
- std::system_category
ms.openlocfilehash: 838a63fc43ef71561c0911cfa4c85c76cf04bc08
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959669"
---
# <a name="ltsystemerrorgt-functions"></a>Функции &lt;system_error&gt;

||||
|-|-|-|
|[generic_category](#generic_category)|[make_error_code](#make_error_code)|[make_error_condition](#make_error_condition)|
|[system_category](#system_category)|

## <a name="generic_category"></a>  generic_category

Представляет категорию общих ошибок.

```cpp
extern const error_category& generic_category();
```

### <a name="remarks"></a>Примечания

`generic_category` Объект представляет собой реализацию [error_category](../standard-library/error-category-class.md).

## <a name="make_error_code"></a>  make_error_code

Создает объект кода ошибки.

```cpp
error_code make_error_code(generic_errno _Errno);
```

### <a name="parameters"></a>Параметры

|Параметр|Описание:|
|---------------|-----------------|
|*_Errno*|Значение перечисления для хранения в объекте кода ошибки.|

### <a name="return-value"></a>Возвращаемое значение

Объект кода ошибки.

### <a name="remarks"></a>Примечания

## <a name="make_error_condition"></a>  make_error_condition

Создает объект условия ошибки.

```cpp
error_condition make_error_condition(generic_errno _Errno);
```

### <a name="parameters"></a>Параметры

|Параметр|Описание:|
|---------------|-----------------|
|*_Errno*|Значение перечисления для хранения в объекте условия ошибки.|

### <a name="return-value"></a>Возвращаемое значение

Объект условия ошибки.

### <a name="remarks"></a>Примечания

## <a name="system_category"></a>  system_category

Представляет категорию ошибок, вызванных переполнением системы низкого уровня.

```cpp
extern const error_category& system_category();
```

### <a name="remarks"></a>Примечания

`system_category` Объект представляет собой реализацию [error_category](../standard-library/error-category-class.md).

## <a name="see-also"></a>См. также

[<system_error>](../standard-library/system-error.md)<br/>
