---
title: Класс CRestrictions | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
dev_langs:
- C++
helpviewer_keywords:
- CRestrictions class
- Open method
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c66200acab5fc1be509136fc45895fdf08e40fdb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072086"
---
# <a name="crestrictions-class"></a>Класс CRestrictions

Универсальный класс, который позволяет указать ограничения для наборов строк схемы.  
  
## <a name="syntax"></a>Синтаксис

```cpp
template <class T, short nRestrictions, const GUID* pguid>  
class CRestrictions : 
   public CSchemaRowset <T, nRestrictions>  
```  
  
### <a name="parameters"></a>Параметры  

*T*<br/>
Класс, используемый для метода доступа.  
  
*nRestrictions*<br/>
Число столбцов ограничений для набора строк схемы.  
  
*pguid*<br/>
Указатель на идентификатор GUID для схемы.  

## <a name="requirements"></a>Требования  

**Заголовок:** atldbsch.h 
  
## <a name="members"></a>Участники  
  
### <a name="methods"></a>Методы  
  
|||  
|-|-|  
|[Открыть](#open)|Возвращает результирующий набор в соответствии с ограничения, предоставленное пользователем.|   

## <a name="open"></a> CRestrictions::Open

Возвращает результирующий набор в соответствии с ограничения, предоставленное пользователем.  
  
### <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCTSTR lpszParam 1 = NULL,  
   LPCTSTR lpszParam 2 = NULL,  
   LPCTSTR lpszParam 3 = NULL,  
   LPCTSTR lpszParam 4 = NULL,  
   LPCTSTR lpszParam 5 = NULL,  
   LPCTSTR lpszParam 6 = NULL,  
   LPCTSTR lpszParam 7 = NULL,  
   bool bBind = true);  
```  
  
#### <a name="parameters"></a>Параметры  

*Сеанс*<br/>
[in] Указывает существующий объект сеанса, используемый для подключения к источнику данных.  
  
*lpszParam*<br/>
[in] Задает ограничения в наборе строк схемы.  
  
*bBind*<br/>
[in] Указывает, нужно ли автоматически привязывать сопоставление столбцов. По умолчанию используется **true**, что приводит в сопоставление столбцов, автоматически привязываться. Установка *bBind* для **false** предотвращает автоматическое связывание сопоставление столбцов, можно привязать вручную. (Привязке вручную является особый интерес для пользователей OLAP).  
  
### <a name="return-value"></a>Возвращаемое значение  

Одно из стандартных значений HRESULT.  
  
### <a name="remarks"></a>Примечания  

Можно указать максимум семь ограничений в наборе строк схемы.  
  
См. в разделе [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\)) сведения об определенных ограничениях на все наборы строк схемы.  
  
## <a name="see-also"></a>См. также  

[Шаблоны потребителей OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Ссылка на шаблоны объекта-получателя OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Классы Rowset и Typedef схемы](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)