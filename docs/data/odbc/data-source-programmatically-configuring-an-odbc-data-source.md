---
title: 'Источник данных: Программная настройка источника данных ODBC | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
f1_keywords:
- SQLConfigDataSource
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources, configuring
- SQLConfigDataSource method example
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 36f8233d7d3683a885fc0f38468ad5a7b9b59c57
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030772"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>Источник данных. Программная настройка источника данных ODBC

В этом разделе объясняется, как программным образом можно настроить имена источников данных Open Database Connectivity (ODBC). Это обеспечивает гибкость для доступа к данным не заставляя пользователя напрямую использовать администратор ODBC или другие программы для указания имен источников данных.  
  
Как правило пользователь запускает администратор ODBC, чтобы создать источник данных, если система управления связанной базы данных (СУБД) поддерживает эту операцию.  
  
При создании источника данных Microsoft Access ODBC помощью администратора ODBC предлагаются два варианта: можно выбрать существующий файл .mdb или создать новый файл. Нет программного метода для создания MDB-файла из приложения ODBC библиотеки MFC. Таким образом Если приложению требуется размещать данные в источник данных Microsoft Access (MDB-файл), скорее всего требуется пустой MDB-файл, можно использовать или копировать при необходимости.  
  
Однако многие СУБД позволяют создавать источник данных программными средствами. Некоторые источники данных поддерживают спецификацию каталогов для баз данных. То есть каталог является источником данных и каждая таблица в источнике данных хранится в отдельном файле (в случае использования dBASE, каждая таблица имеет DBF-файл). Драйверы для других баз данных ODBC, например Microsoft Access и SQL Server, требуют, что некоторые определенных критериев, чтобы источник данных может быть установлено. Например при использовании драйвера ODBC для SQL Server, необходимо было установлено на компьютер с SQL Server.  
  
##  <a name="_core_sqlconfigdatasource_example"></a> Пример SQLConfigDataSource  

В следующем примере используется `::SQLConfigDataSource` функции ODBC API для создания нового источника данных Excel вызывается новый источник данных для Excel:  
  
```  
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",   
                   "DSN=New Excel Data Source\0"   
                   "Description=New Excel Data Source\0"   
                   "FileType=Excel\0"   
                   "DataDirectory=C:\\EXCELDIR\0"   
                   "MaxScanRows=20\0");  
```  
  
Обратите внимание на то, что источник данных — это каталог (C:\EXCELDIR); Этот каталог должен существовать. Драйвер Excel использует каталоги как источники данных, а файлы как отдельные таблицы (по одной таблице на XLS-файл).  
  
Дополнительные сведения о создании таблиц см. в разделе [источника данных: создание таблицы в источнике данных ODBC программным путем](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md).  
  
Ниже описываются параметры, которые должны быть переданы `::SQLConfigDataSource` функции ODBC API. Чтобы использовать `::SQLConfigDataSource`, необходимо включить файл заголовка Odbcinst.h и использовать импорта Odbcinst.lib. Кроме того Odbccp32.dll должен находиться в пути во время выполнения (или Odbcinst.dll для 16-разрядных).  
  
Можно создать имя источника данных ODBC с помощью администратора ODBC или подобной служебной программы. Тем не менее иногда желательно создать имя источника данных непосредственно из приложения, чтобы получать доступ без необходимости для пользователя запускать отдельную программу.  
  
Администратор ODBC (обычно устанавливается в панель управления) создает новый источник данных, размещая записи в реестре Windows (или, для 16-разрядных, в файле Odbc.ini). Диспетчер драйверов ODBC запрашивает этот файл для получения необходимых сведений об источнике данных. Очень важно знать, какие сведения необходимо размещать в реестре, так как вам нужно задать в нем вызов `::SQLConfigDataSource`.  
  
Хотя эти сведения можно записать непосредственно в реестр без использования `::SQLConfigDataSource`, любое приложение, которое делает это полагается на которого использует диспетчер драйверов хранит свои данные. Если в более поздней версии диспетчера драйверов ODBC реализует ведения об источниках данных по-другому, любое приложение, использующее этот способ тоже прекратится. Обычно рекомендуется использовать функцию API, если она существует. Например, пригодным для переноса с 16-разрядное в 32-разрядный код при использовании `::SQLConfigDataSource` работать, так как она всегда корректно записывает данные в файл Odbc.ini или в реестр.  
  
##  <a name="_core_sqlconfigdatasource_parameters"></a> Параметры SQLConfigDataSource  

Ниже описываются параметры `::SQLConfigDataSource` функции. Большинство сведений взяты из API-Интерфейс ODBC *справочнике программиста* поставляемое с Visual C++ версии 1.5 и более поздних версий.  
  
###  <a name="_core_function_prototype"></a> Прототип функции  
  
```  
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);  
```  
  
### <a name="remarks"></a>Примечания  
  
####  <a name="_core_parameters_and_usage"></a> Параметры и использование  

*hwndParent*<br/>
Окно, являющееся владельцем всех диалоговых, создаваемые диспетчером драйверов ODBC или конкретный драйвер ODBC для получения дополнительных сведений от пользователя о новом источнике данных. Если *lpszAttributes* параметр не предоставляет достаточно сведений, появится диалоговое окно. *HwndParent* параметр может иметь значение NULL.  
  
*lpszDriver*<br/>
Описание драйвера. Это имя, представляемое пользователям вместо имени физического драйвера (DLL).  
  
*lpszAttributes*<br/>
Список атрибутов в форме «keyname = значение». Эти строки разделяются символом null расположены еще два символа конца в конец списка. Эти атрибуты являются главным образом по умолчанию записи отдельного драйвера, которые записываются в реестре для нового источника данных. Важный параметр, не упомянутый в справочнике ODBC API для этой функции — «DSN» («имя источника данных»), который указывает имя нового источника данных. Остальные записи зависят от драйвера для нового источника данных. Часто не необходимости предоставлять все записи, так как драйвер может запросить у пользователя с помощью диалоговых окон для новых значений. (Задайте *hwndParent* значение NULL, чтобы вызвать это.) Можно явно указать значения по умолчанию. таким образом, чтобы пользователю не предлагается.  
  
###### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>Чтобы определить описание драйвера для параметра lpszDriver с помощью администратора ODBC  
  
1. Запустите администратор ODBC.  
  
1. Нажмите кнопку **Добавить**.  
  
Это дает список установленных драйверов и их описания. Используйте описание в качестве *lpszDriver* параметра. Обратите внимание на то, что можно использовать описание полностью, такие как «Файлы Excel (*.xls)», включая расширение имени файла и круглые скобки, если они существуют в описании.  
  
Кроме того, можно просмотреть реестр (или, для 16-разрядных, файл Odbcinst.ini), который содержит список всех драйверов записи и описания в разделе реестра «Драйверы ODBC» (или раздел [ODBC Drivers] файла Odbcinst.ini).  
  
Один из способов найти имена параметров и их значения для *lpszAttributes* параметр — изучить файл Odbc.ini на наличие уже настроенного источника данных (возможно, настроенного администратором ODBC).  
  
###### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>Чтобы найти имена параметров и их значения для параметра lpszAttributes  
  
1. Запустите редактор реестра Windows (или, для 16-разрядных, откройте файл Odbc.ini).  
  
1. Найти сведения об источниках данных ODBC, с помощью одного из следующих:  
  
    -   Для 32-разрядная версия, найти ключ **HKEY_CURRENT_USER\Software\ODBC\ODBC. Источники данных INI\ODBC** в левой области.  
  
         В правой части перечислены записи в формате: «pub: REG_SZ:*<data source name>*«, где *<data source name>* является источником данных, который уже был настроен с требуемыми параметрами для драйвера для использования. Выберите источник данных, которые необходимы, например, SQL Server. Элементы вслед за строкой «pub:» — это имя параметра и значение для использования в вашей *lpszAttributes* параметра.  
  
    -   Для 16-разрядных, найдите раздел в файле Odbc.ini обозначен [*\<источник данных >*].  
  
         Строки, следующие за этой строке представлены в формате «keyname = значение». Это соответствует формату записей, для использования в вашей *lpszAttributes* параметра.  
  
Можно также изучить документацию по отдельному драйверу, который вы собираетесь использовать. Полезные сведения можно найти в справке для драйвера, к которому можно получить после запуска администратора ODBC. Эти файлы справки обычно размещаются в каталоге WINDOWS\SYSTEM для Windows NT, Windows 3.1 и Windows 95.  
  
###### <a name="to-obtain-online-help-for-your-odbc-driver"></a>Чтобы получить справку в Интернете по драйверу ODBC  
  
1. Запустите администратор ODBC.  
  
1. Нажмите кнопку **Добавить**.  
  
1. Выберите имя драйвера.  
  
1. Нажмите кнопку **ОК**.  
  
Администратор ODBC отобразит сведения для создания источника данных для этого драйвера, нажмите кнопку **помочь**. Откроется файл справки для этого драйвера, который обычно содержит важные сведения по использованию данного драйвера.  
  
## <a name="see-also"></a>См. также  

[Источник данных (ODBC)](../../data/odbc/data-source-odbc.md)