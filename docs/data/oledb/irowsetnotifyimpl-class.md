---
title: Класс IRowsetNotifyImpl | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetNotifyImpl
- ATL::IRowsetNotifyImpl
- IRowsetNotifyImpl
- IRowsetNotifyImpl.OnFieldChange
- IRowsetNotifyImpl::OnFieldChange
- OnFieldChange
- IRowsetNotifyImpl::OnRowChange
- IRowsetNotifyImpl.OnRowChange
- OnRowChange
- OnRowsetChange
- IRowsetNotifyImpl::OnRowsetChange
- IRowsetNotifyImpl.OnRowsetChange
dev_langs:
- C++
helpviewer_keywords:
- IRowsetNotifyImpl class
- OnFieldChange method
- OnRowChange method
- OnRowsetChange method
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d2d63b4046774bd7e1c427639db3483536e94bc5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095349"
---
# <a name="irowsetnotifyimpl-class"></a>Класс IRowsetNotifyImpl

Реализует и регистрирует [IRowsetNotify](/previous-versions/windows/desktop/ms712959\(v=vs.85\)) на объекте-получателе (также называется «приемник»), чтобы она могла обрабатывать уведомления.  
  
## <a name="syntax"></a>Синтаксис

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify  
```  

## <a name="requirements"></a>Требования  

**Заголовок:** atldbcli.h  
  
## <a name="members"></a>Участники  
  
### <a name="methods"></a>Методы  
  
|||  
|-|-|  
|[OnFieldChange](#onfieldchange)|Уведомляет объект-получатель о любом изменении значения столбца.|  
|[OnRowChange](#onrowchange)|Уведомляет объект-получатель о первом изменении строки или о любом изменении, влияет на всю строку.|  
|[OnRowsetChange](#onrowsetchange)|Уведомляет объект-получатель о любом изменении, влияющие на весь набор строк.|  
  
## <a name="remarks"></a>Примечания  

См. в разделе [получение уведомлений](../../data/oledb/receiving-notifications.md) о реализации интерфейса точки подключения на объекте-получателе.  
  
`IRowsetNotifyImpl` предоставляет реализацию для фиктивного `IRowsetNotify`, с пустым функциями для `IRowsetNotify` методы [OnFieldChange](/previous-versions/windows/desktop/ms715961\(v=vs.85\)), [OnRowChange](/previous-versions/windows/desktop/ms722694\(v=vs.85\)), и [OnRowsetChange](/previous-versions/windows/desktop/ms722669\(v=vs.85\)). При наследовании от этого класса, при реализации `IRowsetNotify` интерфейс, можно реализовать только методы, которые требуются. Также необходимо самостоятельно обеспечить пустые реализации для других методов.  

## <a name="onfieldchange"></a> IRowsetNotifyImpl::OnFieldChange

Уведомляет объект-получатель о любом изменении значения столбца.  
  
### <a name="syntax"></a>Синтаксис  
  
```cpp
STDMETHOD(OnFieldChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ HROW /* hRow */,  
/* [in] */ DBORDINAL /* cColumns */,  
/* [size_is][in] */ DBORDINAL /* rgColumns */ [] ,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### <a name="parameters"></a>Параметры  

См. в разделе [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961\(v=vs.85\)) для описания параметров.  
  
### <a name="return-value"></a>Возвращаемое значение  

См. в разделе [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961\(v=vs.85\)) для возврата описания значений.  
  
### <a name="remarks"></a>Примечания  

Этот метод создает оболочку для [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961\(v=vs.85\)) метод. См. описание этого метода в справочнике программиста OLE DB для сведения.  

## <a name="onrowchange"></a> IRowsetNotifyImpl::OnRowChange

Уведомляет объект-получатель о первом изменении строки или о любом изменении, влияет на всю строку.  
  
### <a name="syntax"></a>Синтаксис  
  
```cpp
STDMETHOD(OnRowChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ DBCOUNTITEM /* cRows */,  
/* [size_is][in] */ const HROW /* rghRows*/ [] ,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### <a name="parameters"></a>Параметры  

См. в разделе [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694\(v=vs.85\)) для описания параметров.  
  
### <a name="return-value"></a>Возвращаемое значение  

См. в разделе [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694\(v=vs.85\)) для возврата описания значений.  
  
### <a name="remarks"></a>Примечания  

Этот метод создает оболочку для [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694\(v=vs.85\)) метод. См. описание этого метода в справочнике программиста OLE DB для сведения. 

## <a name="onrowsetchange"></a> IRowsetNotifyImpl::OnRowsetChange

Уведомляет объект-получатель о любом изменении, влияющие на весь набор строк.  
  
### <a name="syntax"></a>Синтаксис  
  
```cpp
STDMETHOD(OnRowsetChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### <a name="parameters"></a>Параметры  

См. в разделе [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669\(v=vs.85\)) для описания параметров.  
  
### <a name="return-value"></a>Возвращаемое значение  

См. в разделе [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669\(v=vs.85\)) для возврата описания значений.  
  
### <a name="remarks"></a>Примечания  

Этот метод создает оболочку для [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669\(v=vs.85\)) метод. См. описание этого метода в справочнике программиста OLE DB для сведения.
  
## <a name="see-also"></a>См. также  

[Шаблоны потребителей OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Шаблоны потребителей OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[IRowsetNotify](/previous-versions/windows/desktop/ms712959\(v=vs.85\))   
[Класс IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)