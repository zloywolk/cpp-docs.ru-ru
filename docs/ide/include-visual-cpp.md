---
title: '&lt;include&gt; (Visual C++) | Документы Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- include
- <include>
dev_langs:
- C++
helpviewer_keywords:
- include C++ XML tag
- <include> C++ XML tag
ms.assetid: 392a3e61-0371-4617-8362-446650876ce3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3cb07824ad5212f4174a6f19e3efa4549432455
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894458"
---
# <a name="ltincludegt-visual-c"></a>&lt;include&gt; (Visual C++)

Тег \<include> позволяет задать ссылку на комментарии в другом файле, которые описывают типы и члены вашего исходного кода. Этот способ является альтернативой размещению комментариев документации непосредственно в файле исходного кода.  Например, можно использовать \<include> для вставки стандартных комментариев, которые применяются в вашей команде или организации.

## <a name="syntax"></a>Синтаксис

```  
<include file='filename' path='tagpath' />
```  

#### <a name="parameters"></a>Параметры

`filename`  
Имя файла, содержащего документацию. Имя файла может быть дополнено с указанием пути.  Заключите имя в одинарные или двойные кавычки.  Если компилятору не удается найти `filename`, он выдает предупреждение.

`tagpath`  
Допустимое выражение XPath, которое выбирает нужный набор узлов, содержащийся в файле.

`name`  
Спецификатор имени в теге, предшествующий комментариям. `name` будет иметь идентификатор `id`.

`id`  
Идентификатор тега, который предшествует комментариям.  Заключите имя в одинарные или двойные кавычки.

## <a name="remarks"></a>Примечания

Тег \<include> использует XML-синтаксис XPath. Сведения об использовании тега \<include>. см. в документации по XPath.

Чтобы обработать и сохранить комментарии документации в файл, при компиляции необходимо использовать параметр [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md).

## <a name="example"></a>Пример

В этом примере представлено несколько файлов. Первый файл, использующий \<include>, содержит следующие комментарии документации:

```cpp
// xml_include_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_include_tag.dll

/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test"]/*' />
public ref class Test {
   void TestMethod() {
   }
};

/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test2"]/*' />
public ref class Test2 {
   void Test() {
   }
};
```  

Второй файл (xml_include_tag.doc) содержит следующие комментарии документации:

```xml
<MyDocs>

<MyMembers name="test">
<summary>
The summary for this type.
</summary>
</MyMembers>

<MyMembers name="test2">
<summary>
The summary for this other type.
</summary>
</MyMembers>

</MyDocs>
```  

## <a name="program-output"></a>Выходные данные программы

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>t2</name>
    </assembly>
    <members>
        <member name="T:Test">
            <summary>
The summary for this type.
</summary>
        </member>
        <member name="T:Test2">
            <summary>
The summary for this other type.
</summary>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a>См. также

[Документация XML](../ide/xml-documentation-visual-cpp.md)