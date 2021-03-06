---
title: __readcr4 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readcr4
dev_langs:
- C++
helpviewer_keywords:
- __readcr4 intrinsic
ms.assetid: b841a27b-fe0d-4ee9-b76b-f91d3eb061fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7089a92e87449acbafe93bec8a2190a425a843a2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411079"
---
# <a name="readcr4"></a>__readcr4

**Блок, относящийся только к системам Microsoft**

Считывает регистр CR4 и возвращает его значение.

## <a name="syntax"></a>Синтаксис

```
unsigned __int64 __readcr4(void);
```

## <a name="return-value"></a>Возвращаемое значение

Значение в регистре CR4.

## <a name="requirements"></a>Требования

|Встроенная функция|Архитектура|
|---------------|------------------|
|`__readcr4`|x86, x64|

**Файл заголовка** \<intrin.h >

## <a name="remarks"></a>Примечания

Эта встроенная функция доступна только в режиме ядра и процедура доступна только как встроенная.

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Встроенные инструкции компилятора](../intrinsics/compiler-intrinsics.md)