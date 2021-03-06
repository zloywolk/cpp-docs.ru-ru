---
title: 'Набор записей: Объявление класса для предопределенного запроса (ODBC) | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9161cccf9b3efd918f65ab2a703808041f3eb209
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113751"
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>Набор записей. Объявление класса для предопределенного запроса (ODBC)

Этот раздел относится к классам ODBC библиотеки MFC.  
  
В этом разделе описывается создание набора записей класса для предопределенного запроса (иногда называется хранимой процедуры, как в Microsoft SQL Server).  
  
> [!NOTE]
>  Этот раздел относится к объектам, производным от `CRecordset` в какой строке массовой выборка не был реализован. Если реализован выборка строк, процесс очень похож. Сведения о различиях между наборами записей, выборка строк и те, которые этого не сделать, см. в разделе [набор записей: получение записей (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
Некоторые систем управления базами данных (СУБД) позволяют создавать предопределенные запросы и вызывать из программ похожа на функцию. Запрос имеет имя, может принимать параметры и могут возвращать записи. В этом разделе описано, как для вызова предопределенного запроса, который возвращает записи (и, возможно, имеет параметры).  
  
Классы баз данных не поддерживают обновление предопределенных запросов. Разница между стандартным запросом моментальных снимков и динамический набор предопределенных запросов не обновляемости, а также изменения, внесенные другим пользователям (или других наборов записей в программе) отображаются в наборе записей.  
  
> [!TIP]
>  Набор записей для вызова предопределенного запроса, который не возвращает записи не обязательно. Подготовка инструкции SQL, как описано ниже, но выполните его, вызвав `CDatabase` функция-член [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).  
  
Можно создать класс одно подмножество записей для управления вызовом предопределенного запроса, но вы должны сделать некоторых операций самостоятельно. Мастера не поддерживают создание класса специально для этой цели.  
  
#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>Создание класса для вызова предопределенного запроса (хранимая процедура)  
  
1. Используйте [Мастер потребителя MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) из **Добавление класса** для создания класса набора записей для таблицы, содержащей наиболее столбцов, возвращаемых запросом. Это дает вам фору.  
  
1. Вручную добавьте поля элементов данных для всех столбцов всех таблиц, возвращаемых запросом, но, что мастер не создали для вас.  
  
     Например если запрос возвращает три столбца из двух дополнительных таблиц, добавьте к классу шесть элементами данных полей (соответствующие типы данных).  
  
1. Вручную добавьте [RFX](../../data/odbc/record-field-exchange-rfx.md) вызовы функции в [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) функцию-член класса, соответствующего типу данных каждого из них добавлен элемент поля данных.  
  
    ```cpp  
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:   
    pFX->SetFieldType( CFieldExchange::outputColumn );  
    ```  
  
    > [!NOTE]
    >  Необходимо знать типы данных и порядок столбцов, возвращаемые в результирующий набор. Порядок функции RFX вызывает в `DoFieldExchange` должен соответствовать порядку столбцов результирующего набора.  
  
1. Вручную добавьте инициализации для новых членов данных поля в конструкторе класса набора записей.  
  
     Кроме того, необходимо увеличить значение инициализации для [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) элемент данных. Мастер запишет инициализации, но она охватывает только элементами данных полей, которые он добавляет автоматически. Пример:  
  
    ```cpp  
    m_nFields += 6;  
    ```  
  
     Некоторые типы данных не должен быть инициализирован, например, `CLongBinary` или массивов байтов.  
  
1. Если запрос принимает параметры, добавление элемента данных для каждого параметра, вызов функции RFX для каждого и инициализацию для каждого параметра.  
  
1. Необходимо увеличить `m_nParams` для каждого добавленного параметра, как это делалось `m_nFields` для добавления полей на шаге 4 этой процедуры. Дополнительные сведения см. в разделе [набор записей: Параметризация набора записей (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
1. Вручную при написании строки инструкции SQL с помощью следующего вида:  
  
    ```  
    {CALL proc-name [(? [, ?]...)]}  
    ```  
  
     где **вызвать** ключевое слово ODBC, **имя процесса** — это имя запроса, известное на источнике данных и «?» — это местозаполнители для значений параметра, передаваемое набора записей во время выполнения (если таковые имеются) . В следующем примере добавляется заполнитель для одного параметра:  
  
    ```  
    CString mySQL = "{CALL Delinquent_Accts (?)}";  
    ```  
  
1. В коде, который открывает набор записей, задайте значения параметра набора записей элементов данных, а затем вызвать `Open` функция-член, передав строку SQL *lpszSQL* параметра. Либо замените строку, возвращаемую `GetDefaultSQL` функции-члена в классе.  
  
В следующих примерах показано процедура вызова предопределенного запроса, с именем `Delinquent_Accts`, который принимает один параметр — номер региона продаж. Этот запрос возвращает три столбца: `Acct_No`, `L_Name`, `Phone`. Все столбцы имеют из таблицы Customers.  
  
Следующий набор записей определяет члены данных поля для столбцов, возвращаемых запросом и параметр для продажи по району номер, запрошенный во время выполнения.  
  
```cpp  
class CDelinquents : public CRecordset  
{  
// Field/Param Data  
    LONG m_lAcct_No;  
    CString m_strL_Name;  
    CString m_strPhone;  
    LONG m_lDistParam;  
    // ...  
};  
```  
  
— Это объявление класса, как мастер записывает, за исключением `m_lDistParam` вручную добавлен член. Другие члены здесь не показаны.  
  
В следующем примере показано инициализации для элементов данных в `CDelinquents` конструктор.  
  
```cpp  
CDelinquents::CDelinquents(CDatabase* pdb)  
   : CRecordset(pdb)  
{  
    // Wizard-generated params:  
    m_lAcct_No = 0;  
    m_strL_Name = "";  
    m_strPhone = "";  
    m_nFields = 3;  
    // User-defined params:  
    m_nParams = 1;  
    m_lDistParam = 0;  
}  
```  
  
Обратите внимание, инициализации для [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) и [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). Инициализирует мастер `m_nFields`; инициализации `m_nParams`.  
  
В следующем примере показаны функции RFX в `CDelinquents::DoFieldExchange`:  
  
```cpp  
void CDelinquents::DoFieldExchange(CFieldExchange* pFX)  
{  
    pFX->SetFieldType(CFieldExchange::outputColumn);  
    RFX_Long(pFX, "Acct_No", m_lAcct_No);  
    RFX_Text(pFX, "L_Name", m_strL_Name);  
    RFX_Text(pFX, "Phone", m_strPhone);  
    pFX->SetFieldType(CFieldExchange::param);  
    RFX_Long(pFX, "Dist_No", m_lDistParam);  
}  
```  
  
Помимо того, что вызовы функций RFX для трех возвращаемых столбцов, этот код также управляет привязкой параметра, необходимо передать во время выполнения. Параметр подключается к `Dist_No` столбца (номер региона).  
  
В следующем примере показано, как настроить строку SQL и способы ее использования, чтобы открыть набор записей.  
  
```cpp  
// Construct a CDelinquents recordset object  
CDelinquents rsDel( NULL );  
CString strSQL = "{CALL Delinquent_Accts (?)}"  
// Specify a parameter value (obtained earlier from the user)  
rsDel.m_lDistParam = lDistrict;  
// Open the recordset and run the query  
if( rsDel.Open( CRecordset::snapshot, strSQL ) )  
    // Use the recordset ...  
```  
  
Этот код создает моментальный снимок, передает ему параметр, полученный ранее от пользователя и вызывает предопределенного запроса. При выполнении запроса возвращаются записи для указанного региона продаж. Каждая запись содержит столбцы для номер счета, Фамилия клиента и номер телефона клиента.  
  
> [!TIP]
>  Может потребоваться обрабатывать возвращаемое значение (выходной параметр) из хранимой процедуры. Дополнительные сведения и пример см. в разделе [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).  
  
## <a name="see-also"></a>См. также  

[Набор записей (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Набор записей. Выполнение обновления наборов записей (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)<br/>
[Набор записей. Объявление класса таблицы (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Набор записей. Объединение (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)