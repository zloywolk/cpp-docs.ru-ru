---
title: Класс transformer | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- transformer
- AGENTS/concurrency::transformer
- AGENTS/concurrency::transformer::transformer
- AGENTS/concurrency::transformer::accept_message
- AGENTS/concurrency::transformer::consume_message
- AGENTS/concurrency::transformer::link_target_notification
- AGENTS/concurrency::transformer::propagate_message
- AGENTS/concurrency::transformer::propagate_to_any_targets
- AGENTS/concurrency::transformer::release_message
- AGENTS/concurrency::transformer::reserve_message
- AGENTS/concurrency::transformer::resume_propagation
- AGENTS/concurrency::transformer::send_message
- AGENTS/concurrency::transformer::supports_anonymous_source
dev_langs:
- C++
helpviewer_keywords:
- transformer class
ms.assetid: eea71925-7043-4a92-bfd4-dbc0ece5d081
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 803cb474edbce6eb3d397e025ecc31bd5332cc92
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427893"
---
# <a name="transformer-class"></a>Класс transformer

Блок обмена сообщениями `transformer` — это упорядоченный блок `propagator_block` с одной целью и несколькими источниками, который может принимать сообщения одного типа и хранить неограниченное число сообщений другого типа.

## <a name="syntax"></a>Синтаксис

```
template<class _Input, class _Output>
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>,
    multi_link_registry<ISource<_Input>>>;
```

#### <a name="parameters"></a>Параметры

*_Input*<br/>
Тип полезных данных сообщений, принятых в буфер.

*_Output*<br/>
Тип полезных данных сообщения хранятся и распространенных из буфера.

## <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Описание|
|----------|-----------------|
|[transformer](#ctor)|Перегружен. Создает `transformer` блок обмена сообщениями.|
|[~ transformer деструктор](#dtor)|Уничтожает `transformer` блок обмена сообщениями.|

### <a name="protected-methods"></a>Защищенные методы

|Имя|Описание|
|----------|-----------------|
|[accept_message](#accept_message)|Принимает сообщение, предложенное это `transformer` блок обмена сообщениями, передача вызывающему объекту.|
|[consume_message](#consume_message)|Получает сообщение, было предложено `transformer` и зарезервированного целевым объектом, передавая владение вызывающему объекту.|
|[link_target_notification](#link_target_notification)|Обратный вызов, который уведомляет о том, что новый целевой объект была связана с это `transformer` блок обмена сообщениями.|
|[propagate_message](#propagate_message)|Асинхронно передает сообщение от `ISource` блока к этому `transformer` блок обмена сообщениями. Он вызывается по `propagate` метод, при вызове исходного блока.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Выполняет функцию преобразователя для входящих сообщений.|
|[release_message](#release_message)|Освобождает предыдущее резервирование сообщения. (Переопределяет [source_block::release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Резервирует сообщение, ранее предложенного этим объектом `transformer` блок обмена сообщениями. (Переопределяет [source_block::reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Возобновляет распространение после выпуска резервирования. (Переопределяет [source_block::resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Синхронно передает сообщение от `ISource` блока к этому `transformer` блок обмена сообщениями. Он вызывается по `send` метод, при вызове исходного блока.|
|[supports_anonymous_source](#supports_anonymous_source)|Переопределяет метод `supports_anonymous_source`, чтобы указать, что данный блок может принимать сообщения, предоставляемые ему несвязанным источником. (Переопределяет [ITarget::supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|

## <a name="remarks"></a>Примечания

Дополнительные сведения см. в разделе [асинхронные блоки сообщений](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`transformer`

## <a name="requirements"></a>Требования

**Заголовок:** agents.h

**Пространство имен:** concurrency

##  <a name="accept_message"></a> accept_message

Принимает сообщение, предложенное это `transformer` блок обмена сообщениями, передача вызывающему объекту.

```
virtual message<_Output>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Параметры

*_MsgId*<br/>
`runtime_object_identity` Из предложенные `message` объекта.

### <a name="return-value"></a>Возвращаемое значение

Указатель на `message` объекта, что вызывающий объект теперь принадлежит.

##  <a name="consume_message"></a> consume_message

Получает сообщение, было предложено `transformer` и зарезервированного целевым объектом, передавая владение вызывающему объекту.

```
virtual message<_Output>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Параметры

*_MsgId*<br/>
`runtime_object_identity` Из `message` объекта использованное.

### <a name="return-value"></a>Возвращаемое значение

Указатель на `message` объекта, что вызывающий объект теперь принадлежит.

### <a name="remarks"></a>Примечания

Аналогичную `accept`, но всегда предшествует вызов `reserve`.

##  <a name="link_target_notification"></a> link_target_notification

Обратный вызов, который уведомляет о том, что новый целевой объект была связана с это `transformer` блок обмена сообщениями.

```
virtual void link_target_notification(_Inout_ ITarget<_Output> *);
```

##  <a name="propagate_message"></a> propagate_message

Асинхронно передает сообщение от `ISource` блока к этому `transformer` блок обмена сообщениями. Он вызывается по `propagate` метод, при вызове исходного блока.

```
virtual message_status propagate_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>Параметры

*_PMessage*<br/>
Указатель на объект `message`.

*_PSource*<br/>
Указатель на блок источника, предлагающий сообщение.

### <a name="return-value"></a>Возвращаемое значение

Объект [message_status](concurrency-namespace-enums.md) указывает, что целевой объект решил сделать с сообщением.

##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets

Выполняет функцию преобразователя для входящих сообщений.

```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Output> *);
```

##  <a name="release_message"></a> release_message

Освобождает предыдущее резервирование сообщения.

```
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Параметры

*_MsgId*<br/>
`runtime_object_identity` Из `message` объекта освобождение.

##  <a name="reserve_message"></a> reserve_message

Резервирует сообщение, ранее предложенного этим объектом `transformer` блок обмена сообщениями.

```
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Параметры

*_MsgId*<br/>
`runtime_object_identity` Из `message` объекта резервируются.

### <a name="return-value"></a>Возвращаемое значение

`true` Если сообщение было успешно зарезервировано, `false` в противном случае.

### <a name="remarks"></a>Примечания

После `reserve` вызывается, если он возвращает `true`, либо `consume` или `release` необходимо вызвать, чтобы принять или высвободить владение сообщением.

##  <a name="resume_propagation"></a> resume_propagation

Возобновляет распространение после выпуска резервирования.

```
virtual void resume_propagation();
```

##  <a name="send_message"></a> send_message

Синхронно передает сообщение от `ISource` блока к этому `transformer` блок обмена сообщениями. Он вызывается по `send` метод, при вызове исходного блока.

```
virtual message_status send_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>Параметры

*_PMessage*<br/>
Указатель на объект `message`.

*_PSource*<br/>
Указатель на блок источника, предлагающий сообщение.

### <a name="return-value"></a>Возвращаемое значение

Объект [message_status](concurrency-namespace-enums.md) указывает, что целевой объект решил сделать с сообщением.

##  <a name="supports_anonymous_source"></a> supports_anonymous_source

Переопределяет метод `supports_anonymous_source`, чтобы указать, что данный блок может принимать сообщения, предоставляемые ему несвязанным источником.

```
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Возвращаемое значение

Значение `true`, поскольку блок не откладывает предоставляемые сообщения.

##  <a name="ctor"></a> transformer

Создает `transformer` блок обмена сообщениями.

```
transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Параметры

*_Func*<br/>
Функция, которая будет вызываться для каждого принятого сообщения.

*_PTarget*<br/>
Указатель на целевой блок для связи с преобразователем.

*_Фильтр*<br/>
Функция фильтра, который определяет, следует ли принять предлагаемые сообщения.

*_PScheduler*<br/>
`Scheduler` Объекта, в течение которого задача распространения для `transformer` запланировано блок обмена сообщениями.

*_PScheduleGroup*<br/>
`ScheduleGroup` Объекта, в течение которого задача распространения для `transformer` запланировано блок обмена сообщениями. Используемый объект `Scheduler` подразумевается группой расписаний.

### <a name="remarks"></a>Примечания

Среда выполнения использует планировщик по умолчанию, если вы не указали параметры `_PScheduler` или `_PScheduleGroup` .

Тип `_Transform_method` является функтор с сигнатурой `_Output (_Input const &)` которого вызывается этим `transformer` блок обмена сообщениями для обработки сообщения.

Тип `filter_method` является функтор с сигнатурой `bool (_Input const &)` которого вызывается этим `transformer` блок обмена сообщениями, чтобы определить ли он должен принять предложенное сообщение.

##  <a name="dtor"></a> ~ transformer

Уничтожает `transformer` блок обмена сообщениями.

```
~transformer();
```

## <a name="see-also"></a>См. также

[Пространство имен concurrency](concurrency-namespace.md)<br/>
[Класс call](call-class.md)
