---
title: GetProcAddress | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- GetProcAddress
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], GetProcAddress
- ordinal exports [C++]
- GetProcAddress method
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce1a287a9fa608881a39f82a2b86cfc541674218
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713733"
---
# <a name="getprocaddress"></a>GetProcAddress

Процессы, явно связанные с DLL вызов [GetProcAddress](https://msdn.microsoft.com/library/windows/desktop/ms683212) получить адрес экспортированной функции в библиотеке DLL. Для вызова функции DLL используется указатель возвращаемой. **GetProcAddress** принимает в качестве параметров дескриптор модуля DLL (возвращенный ранее функцией **LoadLibrary**, `AfxLoadLibrary`, или **GetModuleHandle**) и принимает имя требуемую функцию к вызову или порядковому номеру экспорта функция.

Поскольку вы вызываете функцию DLL посредством указателя и отсутствует проверка типов во время компиляции, убедитесь, что правильность параметров в функцию, чтобы не превысить объем памяти, выделенной в стеке и вызвать нарушение прав доступа. Один из способов обеспечения безопасности типа — просмотреть прототипы экспортированных функций и создать соответствующие определения типов для указателей функций. Пример:

```
typedef UINT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT);
...

HINSTANCE hDLL;               // Handle to DLL
LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer
DWORD dwParam1;
UINT  uParam2, uReturnVal;

hDLL = LoadLibrary("MyDLL");
if (hDLL != NULL)
{
   lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL,
                                           "DLLFunc1");
   if (!lpfnDllFunc1)
   {
      // handle the error
      FreeLibrary(hDLL);
      return SOME_ERROR_CODE;
   }
   else
   {
      // call the function
      uReturnVal = lpfnDllFunc1(dwParam1, uParam2);
   }
}
```

Способ задания функции при вызове **GetProcAddress** зависит от способа построения библиотеки DLL.

Порядковый номер экспорта может получать только в случае, если создается ссылка на библиотеку DLL создается с помощью файла определения модуля (DEF) и если порядковые номера перечислены с помощью функций в **ЭКСПОРТОВ** разделе DEF-файла библиотеки DLL. Вызов **GetProcAddress** при экспорте порядковый номер, имя функции, в отличие от немного быстрее, если библиотека DLL имеется много экспортированных функций, поскольку порядковые номера экспорта служат индексов к динамической библиотеке Экспорт таблицы. По порядковому номеру **GetProcAddress** можно найти эту функцию напрямую в отличие от сравнения указанного имени с именами функций в таблице экспорта библиотеки DLL. Тем не менее, следует вызывать **GetProcAddress** по порядковому номеру только в том случае, если у вас есть контроль над присвоением порядковых номеров экспортированным функциям в DEF-файле.

## <a name="what-do-you-want-to-do"></a>Выберите действие

- [Неявное связывание с библиотекой DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)

- [Определение подходящего метода связывания](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Дополнительные сведения

- [Функции LoadLibrary и AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)

- [FreeLibrary](https://msdn.microsoft.com/library/windows/desktop/ms683152)

- [Экспорт из библиотеки DLL с использованием DEF-файлов](../build/exporting-from-a-dll-using-def-files.md)

## <a name="see-also"></a>См. также

[DLL в Visual C++](../build/dlls-in-visual-cpp.md)