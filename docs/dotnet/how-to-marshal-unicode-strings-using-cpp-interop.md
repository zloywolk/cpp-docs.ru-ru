---
title: 'Практическое: маршалинг строк Юникода с помощью взаимодействия C++ | Документация Майкрософт'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- Unicode, marshaling strings
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 42aba2595792cca6ced3febea9890dabfb87aa14
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382249"
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>Практическое руководство. Маршалирование строк Юникода с использованием взаимодействия C++

Эта статья описывает один аспект взаимодействия Visual C++. Дополнительные сведения см. в разделе [с помощью взаимодействия C++ (неявный PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

В следующем примере кода используются [управляемые, неуправляемые](../preprocessor/managed-unmanaged.md) директивы #pragma управляемых и неуправляемых функций в одном файле, но эти функции взаимодействия таким же образом, если они определены в отдельных файлах. Файлы, содержащие только неуправляемые функции не обязательно должны быть скомпилированы с [/CLR (компиляция CLR)](../build/reference/clr-common-language-runtime-compilation.md).

В этом разделе показано, как строки в Юникоде может быть передан из управляемого в неуправляемую функцию и наоборот. Взаимодействие с другими типами строк, см. в следующих разделах:

- [Практическое руководство. Маршалинг строк ANSI с использованием взаимодействия C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [Практическое руководство. Маршалинг строк COM с помощью взаимодействия C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

## <a name="example"></a>Пример

Чтобы передать строку Юникода из управляемого в неуправляемую функцию, можно использовать функцию PtrToStringChars (объявлено в файле Vcclr.h) для доступа к памяти, где хранится управляемая строка. Так как этот адрес будет передан в неуправляемую функцию, очень важно, что память была закреплена с [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md) чтобы предотвратить перемещение строковые данные, следует цикла сборки мусора выполняются во время выполняет неуправляемой функции.

```
// MarshalUnicode1.cpp
// compile with: /clr
#include <iostream>
#include <stdio.h>
#include <vcclr.h>

using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(const wchar_t* p) {
   printf_s("(native) received '%S'\n", p);
}

#pragma managed

int main() {
   String^ s = gcnew String("test string");
   pin_ptr<const wchar_t> str = PtrToStringChars(s);

   Console::WriteLine("(managed) passing string to native func...");
   NativeTakesAString( str );
}
```

## <a name="example"></a>Пример

В следующем примере показано, маршалинг данных, необходимый для доступа к строки в Юникоде в управляемой функции, вызванных неуправляемой функции. Управляемая функция, получив собственную строку Юникода, преобразует его в строку, управляемых с помощью <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> метод.

```
// MarshalUnicode2.cpp
// compile with: /clr
#include <iostream>

using namespace std;
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedStringFunc(wchar_t* s) {
   String^ ms = Marshal::PtrToStringUni((IntPtr)s);
   Console::WriteLine("(managed) received '{0}'", ms);
}

#pragma unmanaged

void NativeProvidesAString() {
   cout << "(unmanaged) calling managed func...\n";
   ManagedStringFunc(L"test string");
}

#pragma managed

int main() {
   NativeProvidesAString();
}
```

## <a name="see-also"></a>См. также

[Использование взаимодействия языка C++ (неявный PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)