---
title: auto_gcroot::Release | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot::release
- auto_gcroot::release
- auto_gcroot.release
- msclr.auto_gcroot.release
dev_langs:
- C++
helpviewer_keywords:
- release method
ms.assetid: 40b253f0-154e-4d79-80a4-ff13199c3ff0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f2902f7e62c8907549fe802f4f8c2e66e230d0af
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400879"
---
# <a name="autogcrootrelease"></a>auto_gcroot::release

Освобождает объект из `auto_gcroot` управления.

## <a name="syntax"></a>Синтаксис

```
_element_type release();
```

## <a name="return-value"></a>Возвращаемое значение

Выпущено объект.

## <a name="example"></a>Пример

```
// msl_auto_gcroot_release.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {
      Console::WriteLine( "ClassA constructor: " + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "ClassA destructor: " + m_s );
   }

   void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

int main()
{
   ClassA^ a;

   // create a new scope:
   {
      auto_gcroot<ClassA^> agc1 = gcnew ClassA( "first" );
      auto_gcroot<ClassA^> agc2 = gcnew ClassA( "second" );
      a = agc1.release();
   }
   // agc1 and agc2 go out of scope here

   a->PrintHello();

   Console::WriteLine( "done" );
}
```

```Output
ClassA constructor: first
ClassA constructor: second
ClassA destructor: second
Hello from first A!
done
```

## <a name="requirements"></a>Требования

**Файл заголовка** \<msclr\auto_gcroot.h >

**Пространство имен** msclr

## <a name="see-also"></a>См. также

[Члены auto_gcroot](../dotnet/auto-gcroot-members.md)<br/>
[auto_gcroot::~auto_gcroot](../dotnet/auto-gcroot-tilde-auto-gcroot.md)