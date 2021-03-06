---
title: Макросы обработки исключений | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
dev_langs:
- C++
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2473a2a66792f1bfff18086030a8898a67339e10
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024285"
---
# <a name="exception-handling-macros"></a>Макросы для обработки исключений

Эти макросы обеспечивают поддержку обработки исключений.

|||
|-|-|
|[_ATLCATCH](#_atlcatch)|Операторы обработки ошибок, возникших в соответствующем `_ATLTRY`.|
|[_ATLCATCHALL](#_atlcatchall)|Операторы обработки ошибок, возникших в соответствующем `_ATLTRY`.|
|[_ATLTRY](#_atltry)|Помечает раздел защищенный код, где возможно может возникнуть ошибка.|

## <a name="requirements"></a>Требования:

**Заголовок:** atldef.h

##  <a name="_atlcatch"></a>  _ATLCATCH

Операторы обработки ошибок, возникших в соответствующем `_ATLTRY`.

```
_ATLCATCH(e)
```

### <a name="parameters"></a>Параметры

*e*<br/>
Чтобы перехватить исключение.

### <a name="remarks"></a>Примечания

Используется в сочетании с `_ATLTRY`. Разрешается в C++ [catch (CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md) для обработки данного типа исключения C++.

##  <a name="_atlcatchall"></a>  _ATLCATCHALL

Операторы обработки ошибок, возникших в соответствующем `_ATLTRY`.

```
_ATLCATCHALL
```

### <a name="remarks"></a>Примечания

Используется в сочетании с `_ATLTRY`. Разрешается в C++ [catch(...) ](../../cpp/try-throw-and-catch-statements-cpp.md) для обработки всех типов исключений C++.

##  <a name="_atltry"></a>  _ATLTRY

Помечает раздел защищенный код, где возможно может возникнуть ошибка.

```
_ATLTRY
```

### <a name="remarks"></a>Примечания

Используется в сочетании с [_ATLCATCH](#_atlcatch) или [_ATLCATCHALL](#_atlcatchall). Разрешается в символ C++ [попробуйте](../../cpp/try-throw-and-catch-statements-cpp.md).

## <a name="see-also"></a>См. также

[Макросы](../../atl/reference/atl-macros.md)
