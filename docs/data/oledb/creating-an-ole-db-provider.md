---
title: Создание поставщика OLE DB | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 441fdfcf98e08b30e1049cac986ebc9e0f7df682
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030408"
---
# <a name="creating-an-ole-db-provider"></a>Создание поставщика OLE DB

Рекомендуемый способ создания поставщика OLE DB является использование мастера для создания проекта ATL COM и поставщика, а затем измените файлы с помощью шаблонов OLE DB. При настройке вашего поставщика, можно закомментировать нежелательные свойства и добавить дополнительные интерфейсы.  
  
Порядок действий таков:  
  
1. Использовать мастер проектов ATL для создания файлов базового проекта и мастера ATL OLE DB Provider для создания поставщика (выберите **поставщика ATL OLE DB** в папке Visual C++ **Добавление класса**).  
  
1. Измените код в `Execute` метод в CMyProviderRS.h. Например, см. в разделе [чтение строк в поставщик OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).  
  
1. Изменение сопоставления свойств в MyProviderDS.h MyProviderSess.h и MyProviderRS.h. Мастер создает сопоставления свойств, которые содержат все свойства, которые может реализовать поставщик. Просмотрите сопоставления свойств и удалите или закомментируйте свойства, которые поставщик должен поддерживать.  
  
1. Обновите PROVIDER_COLUMN_MAP, которую можно найти в MyProviderRS.h. Например, см. в разделе [хранения строк в поставщик OLE DB](../../data/oledb/storing-strings-in-the-ole-db-provider.md).  
  
1. Когда будете готовы для проверки поставщика, можно проверить его, необходимо найти поставщик в перечислении поставщиков. Примеры кода теста, который находит поставщика в перечислении, см. в разделе ["CatDB"](https://github.com/Microsoft/VCSamples) и [DBVIEWER](https://github.com/Microsoft/VCSamples) образцы или только в примере в [реализация простых объектов получателей](../../data/oledb/implementing-a-simple-consumer.md).  
  
1. Добавьте любые дополнительные интерфейсы, которые вам нужны. Например, см. в разделе [Усовершенствование простого поставщика только для чтения](../../data/oledb/enhancing-the-simple-read-only-provider.md).  
  
    > [!NOTE]
    >  По умолчанию мастера создают код, который OLE DB уровня 0 соответствует. Чтобы убедиться, что приложение остается совместимым с уровнем 0, не удаляйте любой из этих интерфейсов, созданный мастером из кода.  
  
## <a name="see-also"></a>См. также  

["CATDB"](https://github.com/Microsoft/VCSamples)<br/>
[DBVIEWER](https://github.com/Microsoft/VCSamples)