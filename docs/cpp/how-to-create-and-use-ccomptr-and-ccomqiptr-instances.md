---
title: 'Практическое: Создание и использование экземпляров CComPtr и CComQIPtr | Документация Майкрософт'
ms.custom: how-to
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b0356cfb-12cc-4ee8-b988-8311ed1ab5e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 052f915f2626e7b9eeef6a762c52943083b955b8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072151"
---
# <a name="how-to-create-and-use-ccomptr-and-ccomqiptr-instances"></a>Практическое руководство. Создание и использование экземпляров CComPtr и CComQIPtr

В классическом программировании Windows библиотеки часто реализуются как COM-объекты (или, более точно, как COM-серверы). Многие компоненты операционной системы Windows реализованы в виде COM-серверов, и большинство разработчиков предоставляют библиотеки в этой форме. Дополнительные сведения об основах COM см. [объектов модели компонентов (COM)](/windows/desktop/com/component-object-model--com--portal).

При создании COM-объекта сохраните указатель на интерфейс в интеллектуальном указателе COM, который подсчитывает ссылки с помощью вызовов `AddRef` и `Release` в деструкторе. Если вы работаете с библиотекой ATL или библиотекой MFC, используйте интеллектуальный указатель `CComPtr` . В противном случае используйте `_com_ptr_t`. Поскольку эквивалент COM для `std::unique_ptr`отсутствует, применяйте эти интеллектуальные указатели в сценариях с одним и несколькими владельцами. `CComPtr` и `ComQIPtr` поддерживают операции перемещения, имеющие ссылки rvalue.

## <a name="example"></a>Пример

В следующем примере показано, как использовать `CComPtr` для создания COM-объекта и получения указателей на его интерфейсы. Обратите внимание, что для создания объекта используется функция-член `CComPtr::CoCreateInstance` , а не функция Win32 с таким же именем.

[!code-cpp[COM_smart_pointers#01](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_1.cpp)]

`CComPtr` и родственными являются частью библиотеки ATL и определяются в \<atlcomcli.h >. `_com_ptr_t` объявляется в \<comip.h >. Компилятор создает специализации `_com_ptr_t` при создании классов-оболочек для библиотек типов.

## <a name="example"></a>Пример

Кроме того, библиотека ATL предоставляет указатель `CComQIPtr`с более простым синтаксисом запросов к COM-объекту для получения новых интерфейсов. Однако рекомендуется использовать `CComPtr` , так как он поддерживает все возможности `CComQIPtr` и семантически более совместим с необработанными указателями на интерфейс СОМ. Если запрос на интерфейс выполняется с помощью `CComPtr` , указатель на новый интерфейс помещается в выходной параметр. Если вызов завершается ошибкой, возвращается значение HRESULT, которое является стандартным шаблоном COM. В случае с `CComQIPtr`возвращаемым значением является сам указатель, и при сбое вызова внутреннее возвращаемое значение HRESULT будет недоступно. В следующих двух строках показано различие механизмов обработки ошибок `CComPtr` и `CComQIPtr` .

[!code-cpp[COM_smart_pointers#02](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_2.cpp)]

## <a name="example"></a>Пример

`CComPtr` предоставляет специализацию для IDispatch, который позволяет сохранить указатели на компоненты автоматизации COM и вызывать методы в интерфейсе с помощью позднего связывания. `CComDispatchDriver` является определением типа `CComQIPtr<IDispatch, &IIDIDispatch>`, который неявно преобразуется в `CComPtr<IDispatch>`. Таким образом, когда любое из этих трех имен появляется в коде, оно считается эквивалентным `CComPtr<IDispatch>`. В примере ниже демонстрируется получение указателя на объектную модель Microsoft Word с помощью `CComPtr<IDispatch>`.

[!code-cpp[COM_smart_pointers#03](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_3.cpp)]

## <a name="see-also"></a>См. также

[Интеллектуальные указатели](../cpp/smart-pointers-modern-cpp.md)