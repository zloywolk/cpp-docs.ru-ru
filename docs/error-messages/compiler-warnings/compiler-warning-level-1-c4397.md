---
title: Предупреждение компилятора (уровень 1) C4397 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4397
dev_langs:
- C++
helpviewer_keywords:
- C4397
ms.assetid: 6346fdc2-dbbf-4fba-803a-32b0d0a707be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f5a3ccc7b55a9a4aabad5d5567f08b0a56d4ba87
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064533"
---
# <a name="compiler-warning-level-1-c4397"></a>Предупреждение компилятора (уровень 1) C4397

DefaultCharSetAttribute игнорируется

<xref:System.Runtime.InteropServices.DefaultCharSetAttribute> игнорируется компилятором Visual C++. Чтобы указать набор символов для библиотеки DLL, используйте параметр CharSet DllImport. Дополнительные сведения см. в разделе [с помощью взаимодействия C++ (неявный PInvoke)](../../dotnet/using-cpp-interop-implicit-pinvoke.md).

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C4397.

```
// C4397.cpp
// compile with: /W1 /c /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[module:DefaultCharSetAttribute(CharSet::Unicode)];   // C4397

[DllImport("kernel32", EntryPoint="CloseHandle", CharSet=CharSet::Unicode)]   // OK
extern "C" bool ImportDefault(IntPtr hObject);

public ref class MySettingVC {
public:
   void method() {
      ImportDefault(IntPtr::Zero);
   }
};

[StructLayout(LayoutKind::Explicit)]
public ref struct StructDefault1{};

public ref class ClassDefault1{};
```