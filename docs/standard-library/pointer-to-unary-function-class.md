---
title: Класс pointer_to_unary_function | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::pointer_to_unary
dev_langs:
- C++
helpviewer_keywords:
- pointer_to_unary_function function
- pointer_to_unary_function class
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9543ed9bec188ab810bbfd3e0ac52a764fc2fdd
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110403"
---
# <a name="pointertounaryfunction-class"></a>Класс pointer_to_unary_function

Преобразует указатель на унарную функцию в адаптируемую унарную функцию.

## <a name="syntax"></a>Синтаксис

```cpp
template <class Arg, class Result>
class pointer_to_unary_function
    : public unary_function<Arg, Result>
{
public:
    explicit pointer_to_unary_function(Result(*pfunc)(Arg));
    Result operator()(Arg left) const;
};
```

### <a name="parameters"></a>Параметры

*pfunc*<br/>
Бинарная функция для преобразования.

*left*<br/>
Объект, для которого вызывается функция *\*pfunc*.

## <a name="return-value"></a>Возвращаемое значение

Класс шаблона сохраняет копию `pfunc`. Он определяет свою функцию-член `operator()` как возвращающую ( \* **pfunc**)(_ *Left*).

## <a name="remarks"></a>Примечания

Указатель на унарную функцию является объектом функции и может передаваться в любой алгоритм стандартной библиотеки C++, ожидающий унарную функцию в качестве параметра, но не может настраиваться. Для использования его с адаптером, например привязка к нему значения или использование его с negator, он должен передаваться с вложенными типами `argument_type` и `result_type` , делает такую возможных. Преобразование посредством `pointer_to_unary_function` позволяет адаптерам функций работать с указателями бинарных функций.

## <a name="example"></a>Пример

Конструктор `pointer_to_unary_function` редко используется напрямую. См. раздел по вспомогательной функции [ptr_fun](../standard-library/functional-functions.md#ptr_fun) с примером того, как объявлять и использовать предикат адаптера `pointer_to_unary_function`.

## <a name="requirements"></a>Требования

**Заголовок:** \<functional>

**Пространство имен:** std

## <a name="see-also"></a>См. также

[Справочник по стандартной библиотеке C++](../standard-library/cpp-standard-library-reference.md)<br/>
