---
title: Класс CStreamRowset | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CStreamRowset<TAccessor>
- ATL::CStreamRowset
- CStreamRowset
- ATL.CStreamRowset<TAccessor>
- ATL.CStreamRowset
- CStreamRowset::CStreamRowset
- CStreamRowset.CStreamRowset
- ATL.CStreamRowset.CStreamRowset
- ATL::CStreamRowset::CStreamRowset
- CStreamRowset
- CStreamRowset<TAccessor>::CStreamRowset
- ATL::CStreamRowset<TAccessor>::CStreamRowset
- CStreamRowset<TAccessor>.Close
- ATL.CStreamRowset<TAccessor>.Close
- CStreamRowset::Close
- CStreamRowset<TAccessor>::Close
- ATL::CStreamRowset::Close
- ATL.CStreamRowset.Close
- ATL::CStreamRowset<TAccessor>::Close
- CStreamRowset.Close
dev_langs:
- C++
helpviewer_keywords:
- CStreamRowset class
- CStreamRowset class, constructor
- Close method
ms.assetid: a106e953-a38a-464e-8ea5-28963d9e4811
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 76eb58936082c7efde7e7bc87f17e7326ecc8920
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071553"
---
# <a name="cstreamrowset-class"></a>Класс CStreamRowset

Используется в `CCommand` или `CTable` объявления.  
  
## <a name="syntax"></a>Синтаксис

```cpp
template <class TAccessor = CAccessorBase>  
class CStreamRowset  
```  
  
### <a name="parameters"></a>Параметры  

*TAccessor*<br/>
Класс, метод доступа.  

## <a name="requirements"></a>Требования  

**Заголовок:** atldbcli.h  
  
## <a name="members"></a>Участники  
  
### <a name="methods"></a>Методы  
  
|||  
|-|-|  
|[CStreamRowset](#cstreamrowset)|Конструктор. Создает и инициализирует `CStreamRowset` объекта.|  
|[Закрыть](#close)|Выпуски [ISequentialStream](/previous-versions/windows/desktop/ms718035\(v=vs.85\)) указатель на интерфейс в классе.|  
  
## <a name="remarks"></a>Примечания  

Используйте `CStreamRowset` в вашей `CCommand` или `CTable` объявление, например:  
  
[!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]  
  
или  
  
[!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]  
  
`ICommand::Execute` Возвращает `ISequentialStream` указатель, который хранится в `m_spStream`. Затем используйте `Read` метод для извлечения данных (строка Юникод) в формате XML. Пример:  
  
[!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]  
  
SQL Server 2000 выполняет форматирование XML и возвращает все столбцы и строки набора строк как одну строку XML.  
  
> [!NOTE]
>  Эта функция работает только с SQL Server 2000.  
  
## <a name="cstreamrowset"></a> CStreamRowset::CStreamRowset

Создает и инициализирует `CStreamRowset` объекта.  
  
### <a name="syntax"></a>Синтаксис  
  
```cpp
CStreamRowset();  
```  

## <a name="close"></a> CStreamRowset::Close

Выпуски [ISequentialStream](/previous-versions/windows/desktop/ms718035\(v=vs.85\)) указатель на интерфейс в классе.  
  
### <a name="syntax"></a>Синтаксис  
  
```cpp
void Close();   
```  
  
## <a name="see-also"></a>См. также  

[Шаблоны потребителей OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Ссылка на шаблоны объекта-получателя OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)