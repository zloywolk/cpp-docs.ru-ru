---
title: Расположение схем сообщений | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81958eda508a3e0b4b93ac0d169f3aa3bfece2a2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434275"
---
# <a name="where-to-find-message-maps"></a>Расположение схем сообщений

При создании нового скелет приложения с помощью мастера приложений, мастер приложений записывает схему сообщений для каждого класса целевой объект команды, которые оно создает для вас. Сюда входят производного приложения, документа, представления и классы окна фрейма. Эти схемы сообщений уже есть записи, предоставленные с помощью мастера приложений для определенных сообщений и стандартных команд, а некоторые — только заполнители для обработчиков, которые будут добавлены.

Схема класса сообщений находится в. CPP-файл для класса. Работа с картами базовый цикл обработки сообщений, создаваемых мастером приложений, использовании окна «Свойства» для добавления записи для сообщения и команды, которые будут обрабатывать каждый класс. Карту обычное сообщение может выглядеть следующим образом, после добавления некоторых записей:

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

Сопоставление сообщений представляет собой коллекцию макросов. Два макроса [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) и [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map), скобок в схеме сообщений. Другие макросы, такие как `ON_COMMAND`, заполните содержимое схемы сообщений.

> [!NOTE]
>  Макросы схемы сообщений не выполняются точкой с запятой.

При использовании мастер добавления классов для создания нового класса, он предоставляет схему сообщений для класса. Кроме того можно создать схему сообщений, вручную с помощью редактора исходного кода.

## <a name="see-also"></a>См. также

[Выполнение платформой поиска по схемам сообщений](../mfc/how-the-framework-searches-message-maps.md)

