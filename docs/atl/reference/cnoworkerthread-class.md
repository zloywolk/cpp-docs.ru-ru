---
title: Класс CNoWorkerThread | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread::AddHandle
- ATLUTIL/ATL::CNoWorkerThread::AddTimer
- ATLUTIL/ATL::CNoWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CNoWorkerThread::GetThreadId
- ATLUTIL/ATL::CNoWorkerThread::Initialize
- ATLUTIL/ATL::CNoWorkerThread::RemoveHandle
- ATLUTIL/ATL::CNoWorkerThread::Shutdown
dev_langs:
- C++
helpviewer_keywords:
- CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e602b3493269924e7b80b52b70b34397fcc7dd71
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753930"
---
# <a name="cnoworkerthread-class"></a>Класс CNoWorkerThread

Этот класс используется в качестве аргумента для `MonitorClass` параметр шаблона классов кэша, если вы хотите отключить обслуживания динамического кэша.

> [!IMPORTANT]
>  Этот класс и его члены не может использоваться в приложениях, выполняемых в среде выполнения Windows.

## <a name="syntax"></a>Синтаксис

```
class CNoWorkerThread
```

## <a name="members"></a>Участники

### <a name="public-methods"></a>Открытые методы

|Имя|Описание|
|----------|-----------------|
|[CNoWorkerThread::AddHandle](#addhandle)|Нефункциональные эквивалент [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).|
|[CNoWorkerThread::AddTimer](#addtimer)|Нефункциональные эквивалент [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).|
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|Нефункциональные эквивалент [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).|
|[CNoWorkerThread::GetThreadId](#getthreadid)|Нефункциональные эквивалент [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).|
|[CNoWorkerThread::Initialize](#initialize)|Нефункциональные эквивалент [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).|
|[CNoWorkerThread::RemoveHandle](#removehandle)|Нефункциональные эквивалент [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).|
|[CNoWorkerThread::Shutdown](#shutdown)|Нефункциональные эквивалент [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).|

## <a name="remarks"></a>Примечания

Этот класс предоставляет тот же открытый интерфейс, как [CWorkerThread](../../atl/reference/cworkerthread-class.md). Этот интерфейс должен предоставляться `MonitorClass` параметр шаблона классов кэша.

Методы в этом классе реализованы в бездействии. Методы, которые всегда возвращают значение HRESULT, верните значение s_ок, и методы, возвращающие идентификатор МАРКЕРА или поток всегда возвращают 0.

## <a name="requirements"></a>Требования

**Заголовок:** файлов atlutil.h

##  <a name="addhandle"></a>  CNoWorkerThread::AddHandle

Нефункциональные эквивалент [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

```
HRESULT AddHandle(HANDLE /* hObject */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */) throw();
```

### <a name="return-value"></a>Возвращаемое значение

Всегда возвращает значение S_OK.

### <a name="remarks"></a>Примечания

Реализацию, предоставляемую этим классом не выполняет никаких действий.

##  <a name="addtimer"></a>  CNoWorkerThread::AddTimer

Нефункциональные эквивалент [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).

```
HRESULT AddTimer(DWORD /* dwInterval */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */,
    HANDLE* /* phTimer */) throw();
```

### <a name="return-value"></a>Возвращаемое значение

Всегда возвращает значение S_OK.

### <a name="remarks"></a>Примечания

Реализацию, предоставляемую этим классом не выполняет никаких действий.

##  <a name="getthreadhandle"></a>  CNoWorkerThread::GetThreadHandle

Нефункциональные эквивалент [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Возвращаемое значение

Всегда возвращает значение NULL.

### <a name="remarks"></a>Примечания

Реализацию, предоставляемую этим классом не выполняет никаких действий.

##  <a name="getthreadid"></a>  CNoWorkerThread::GetThreadId

Нефункциональные эквивалент [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Возвращаемое значение

Всегда возвращает 0.

### <a name="remarks"></a>Примечания

Реализацию, предоставляемую этим классом не выполняет никаких действий.

##  <a name="initialize"></a>  CNoWorkerThread::Initialize

Нефункциональные эквивалент [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).

```
HRESULT Initialize() throw();
```

### <a name="return-value"></a>Возвращаемое значение

Всегда возвращает значение S_OK.

### <a name="remarks"></a>Примечания

Реализацию, предоставляемую этим классом не выполняет никаких действий.

##  <a name="removehandle"></a>  CNoWorkerThread::RemoveHandle

Нефункциональные эквивалент [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).

```
HRESULT RemoveHandle(HANDLE /* hObject */) throw();
```

### <a name="return-value"></a>Возвращаемое значение

Всегда возвращает значение S_OK.

### <a name="remarks"></a>Примечания

Реализацию, предоставляемую этим классом не выполняет никаких действий.

##  <a name="shutdown"></a>  CNoWorkerThread::Shutdown

Нефункциональные эквивалент [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="return-value"></a>Возвращаемое значение

Всегда возвращает значение S_OK.

### <a name="remarks"></a>Примечания

Реализацию, предоставляемую этим классом не выполняет никаких действий.
