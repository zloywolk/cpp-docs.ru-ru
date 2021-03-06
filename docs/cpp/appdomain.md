---
title: AppDomain | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- appdomain_cpp
dev_langs:
- C++
helpviewer_keywords:
- appdomain __declspec keyword
- __declspec keyword [C++], appdomain
ms.assetid: 29d843cb-cb6b-4d1b-a48d-d928a877234d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8ef06751e1c9e478c7119dbffb242581f432b9e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111775"
---
# <a name="appdomain"></a>appdomain

Указывает, что каждый домен приложения в вашем управляемого приложения должен иметь собственную копию заданной глобальной переменной или статической переменной-члена. См. в разделе [домены приложений и Visual C++](../dotnet/application-domains-and-visual-cpp.md) Дополнительные сведения.

В каждом домене приложения имеется собственная копия переменной, создаваемой на уровне домена приложения. Конструктор этой переменной выполняется при загрузке сборки в домен приложения, а деструктор — при выгрузке домена приложения.

Если вам необходимо, чтобы глобальная переменная использовалась всеми доменами приложения в рамках процесса CLR, используйте модификатор `__declspec(process)`. `__declspec(process)` действует по умолчанию в разделе [/CLR](../build/reference/clr-common-language-runtime-compilation.md). **/CLR: pure** и **/CLR: safe** параметры компилятора признаны устаревшими в Visual Studio 2015 и не поддерживается в Visual Studio 2017.

`__declspec(appdomain)` допустимо только когда один из **/CLR** используется параметры компилятора. Модификатором `__declspec(appdomain)` можно пометить только глобальную переменную, статическую переменную-член или статическую локальную переменную. Применять модификатор `__declspec(appdomain)` к статическим членам управляемых типов будет ошибкой, поскольку они в любом случае имеют имеют соответствующее поведение.

С помощью `__declspec(appdomain)` похоже на использование [локальное хранилище потока (TLS)](../parallel/thread-local-storage-tls.md). Как и у доменов приложения, у потоков имеются собственные области памяти. Если используется ключевое слово `__declspec(appdomain)`, то для глобальной переменной гарантированно создается собственная область памяти в каждом домене приложения, созданном для данного приложения.

Существуют ограничения на совместное использование каждого процесса и для отдельных переменных appdomain. см. в разделе [процесс](../cpp/process.md) Дополнительные сведения.

Например, при запуске программы сначала инициализируются все переменные на уровне процесса, а затем все переменные на уровне домена приложения. Таким образом, инициализация переменных на уровне процесса не может зависеть от значений переменных на уровне домена приложения. Одновременно использовать (присваивать) переменные на уровне процесса и домена приложения не рекомендуется.

Сведения о том, как вызвать функцию в конкретном домене приложения, см. в разделе [функция call_in_appdomain](../dotnet/call-in-appdomain-function.md).

## <a name="example"></a>Пример

```cpp
// declspec_appdomain.cpp
// compile with: /clr
#include <stdio.h>
using namespace System;

class CGlobal {
public:
   CGlobal(bool bProcess) {
      Counter = 10;
      m_bProcess = bProcess;
      Console::WriteLine("__declspec({0}) CGlobal::CGlobal constructor", m_bProcess ? (String^)"process" : (String^)"appdomain");
   }

   ~CGlobal() {
      Console::WriteLine("__declspec({0}) CGlobal::~CGlobal destructor", m_bProcess ? (String^)"process" : (String^)"appdomain");
   }

   int Counter;

private:
   bool m_bProcess;
};

__declspec(process) CGlobal process_global = CGlobal(true);
__declspec(appdomain) CGlobal appdomain_global = CGlobal(false);

value class Functions {
public:
   static void change() {
      ++appdomain_global.Counter;
   }

   static void display() {
      Console::WriteLine("process_global value in appdomain '{0}': {1}",
         AppDomain::CurrentDomain->FriendlyName,
         process_global.Counter);

      Console::WriteLine("appdomain_global value in appdomain '{0}': {1}",
         AppDomain::CurrentDomain->FriendlyName,
         appdomain_global.Counter);
   }
};

int main() {
   AppDomain^ defaultDomain = AppDomain::CurrentDomain;
   AppDomain^ domain = AppDomain::CreateDomain("Domain 1");
   AppDomain^ domain2 = AppDomain::CreateDomain("Domain 2");
   CrossAppDomainDelegate^ changeDelegate = gcnew CrossAppDomainDelegate(&Functions::change);
   CrossAppDomainDelegate^ displayDelegate = gcnew CrossAppDomainDelegate(&Functions::display);

   // Print the initial values of appdomain_global in all appdomains.
   Console::WriteLine("Initial value");
   defaultDomain->DoCallBack(displayDelegate);
   domain->DoCallBack(displayDelegate);
   domain2->DoCallBack(displayDelegate);

   // Changing the value of appdomain_global in the domain and domain2
   // appdomain_global value in "default" appdomain remain unchanged
   process_global.Counter = 20;
   domain->DoCallBack(changeDelegate);
   domain2->DoCallBack(changeDelegate);
   domain2->DoCallBack(changeDelegate);

   // Print values again
   Console::WriteLine("Changed value");
   defaultDomain->DoCallBack(displayDelegate);
   domain->DoCallBack(displayDelegate);
   domain2->DoCallBack(displayDelegate);

   AppDomain::Unload(domain);
   AppDomain::Unload(domain2);
}
```

```Output
__declspec(process) CGlobal::CGlobal constructor
__declspec(appdomain) CGlobal::CGlobal constructor
Initial value
process_global value in appdomain 'declspec_appdomain.exe': 10
appdomain_global value in appdomain 'declspec_appdomain.exe': 10
__declspec(appdomain) CGlobal::CGlobal constructor
process_global value in appdomain 'Domain 1': 10
appdomain_global value in appdomain 'Domain 1': 10
__declspec(appdomain) CGlobal::CGlobal constructor
process_global value in appdomain 'Domain 2': 10
appdomain_global value in appdomain 'Domain 2': 10
Changed value
process_global value in appdomain 'declspec_appdomain.exe': 20
appdomain_global value in appdomain 'declspec_appdomain.exe': 10
process_global value in appdomain 'Domain 1': 20
appdomain_global value in appdomain 'Domain 1': 11
process_global value in appdomain 'Domain 2': 20
appdomain_global value in appdomain 'Domain 2': 12
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(process) CGlobal::~CGlobal destructor
```

## <a name="see-also"></a>См. также

[__declspec](../cpp/declspec.md)<br/>
[Ключевые слова](../cpp/keywords-cpp.md)