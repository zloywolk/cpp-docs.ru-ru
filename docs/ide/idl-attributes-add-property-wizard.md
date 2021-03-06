---
title: Атрибуты IDL, мастер добавления свойства | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.prop.idlattributes
dev_langs:
- C++
ms.assetid: 356ed666-79d0-4bd9-a5e7-cda679cbadbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7da654321dfae520f458374654a21a9e8ebb98f5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706658"
---
# <a name="idl-attributes-add-property-wizard"></a>Атрибуты IDL, мастер добавления свойства
Используйте эту страницу мастера добавления свойства, чтобы указать все параметры IDL для этого свойства.  
  
- **id**

   Задает числовой идентификатор, который определяет это свойство. Этот параметр недоступен для свойств настраиваемых интерфейсов. См. описание [id](/windows/desktop/Midl/id) в *справочнике по MIDL*.  
  
- **helpcontext**

   Задает идентификатор контекста, позволяющий пользователю просматривать в файле справки информацию об этом свойстве. См. описание [helpcontext](/windows/desktop/Midl/helpcontext) в *справочнике по MIDL*.  
  
- **helpstring**

   Определяет строку символов, используемую для описания элемента, к которому оно применяется. По умолчанию имеет значение "property *имя свойства*". См. описание [helpstring](/windows/desktop/Midl/helpstring) в *справочнике по MIDL*.  
  
## <a name="other-options"></a>Другие параметры  

Не все параметры доступны для всех типов свойств.  
  
|Параметр|Описание:|  
|------------|-----------------|  
|**bindable**|Указывает, что свойство поддерживает привязку данных. См. описание [bindable](/windows/desktop/Midl/bindable) в *справочнике по MIDL*. Для стандартной реализации свойства этот параметр задан по умолчанию и недоступен для изменения.|  
|**defaultbind**|Указывает, что это единственное привязываемое свойство представляет объект наилучшим образом. См. описание [defaultbind](/windows/desktop/Midl/defaultbind) в *справочнике по MIDL*.|  
|**displaybind**|Указывает, что это свойство должно отображаться пользователю как связываемое. См. описание [displaybind](/windows/desktop/Midl/displaybind) в *справочнике по MIDL*.|  
|**immediatebind**|Указывает, что база данных будет немедленно оповещаться обо всех изменениях этого свойства для объекта с привязкой к данным. См. описание [immediatebind](/windows/desktop/Midl/immediatebind) в *справочнике по MIDL*.|  
|**defaultcollelem**|Указывает, что свойство является функцией метода доступа для элемента в коллекции по умолчанию. См. описание [defaultcollelem](/windows/desktop/Midl/defaultcollelem) в *справочнике по MIDL*.|  
|**nonbrowsable**|Помечает член интерфейса или disp-интерфейса, который не должен отображаться в обозревателе свойств. См. описание [nonbrowsable](/windows/desktop/Midl/nonbrowsable) в *справочнике по MIDL*.|  
|**requestedit**|Указывает, что свойство поддерживает уведомление **OnRequestEdit**. См. описание [requestedit](/windows/desktop/Midl/requestedit) в *справочнике по MIDL*. Для стандартной реализации свойства этот параметр задан по умолчанию и недоступен для изменения.|  
|**source**|Указывает, что член свойства является источником событий. См. описание [source](/windows/desktop/Midl/source) в *справочнике по MIDL*.|  
|**hidden**|Указывает, что свойство существует, но не должно отображаться в пользовательском браузере. См. описание [hidden](/windows/desktop/Midl/hidden) в *справочнике по MIDL*.|  
|**restricted**|Указывает, что свойство не может вызываться произвольным образом. См. описание [restricted](/windows/desktop/Midl/restricted) в *справочнике по MIDL*.|  
|`local`|Указывает компилятору MIDL, что свойство не является удаленным. См. описание [local](/windows/desktop/Midl/local) в *справочнике по MIDL*.|  
  
## <a name="see-also"></a>См. также  
 [Добавление свойства](../ide/adding-a-property-visual-cpp.md)   
 [Мастер добавления свойств, страница "Имена"](../ide/names-add-property-wizard.md)   
 [Реализация интерфейса](../ide/implementing-an-interface-visual-cpp.md)   
 [Свойства хранения](../ide/stock-properties.md)