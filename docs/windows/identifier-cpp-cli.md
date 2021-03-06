---
title: __identifier (c + +/ CLI) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- __identifier
- __identifier_cpp
dev_langs:
- C++
helpviewer_keywords:
- __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 572767c2f85b07f201bef93578b14b731aa467e0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415022"
---
# <a name="identifier-ccli"></a>__identifier (C++/CLI)

Включает использование ключевых слов Visual C++ в качестве идентификаторов.

## <a name="all-platforms"></a>Все платформы

### <a name="syntax"></a>Синтаксис

```cpp
__identifier(
Visual_C++_keyword
)  
```

### <a name="remarks"></a>Примечания

Использование **__identifier** ключевое слово для идентификаторов, которые не являются ключевые слова, разрешено, но настоятельно не рекомендуется в рамках стиля.

## <a name="windows-runtime"></a>Среда выполнения Windows

### <a name="requirements"></a>Требования

Параметр компилятора: `/ZW`

### <a name="examples"></a>Примеры

**Пример**

В следующем примере класс с именем **шаблона** создается на языке C# и распространяемых в виде библиотеки DLL. В программе Visual C++, который использует **шаблона** класс, **__identifier** ключевое слово скрывает тот факт, **шаблона** является ключевым словом standard C++.

```cs
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /ZW
#using <identifier_template.dll>
int main() {
   __identifier(template)^ pTemplate = ref new __identifier(template)();
   pTemplate->Run();
}
```

## <a name="common-language-runtime"></a>Среда CLR

### <a name="remarks"></a>Примечания

**__Identifier** ключевое слово может использоваться с `/clr` параметр компилятора.

### <a name="requirements"></a>Требования

Параметр компилятора: `/clr`

### <a name="examples"></a>Примеры

В следующем примере класс с именем **шаблона** создается на языке C# и распространяемых в виде библиотеки DLL. В программе Visual C++, который использует **шаблона** класс, **__identifier** ключевое слово скрывает тот факт, **шаблона** является ключевым словом standard C++.

```cs
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /clr
#using <identifier_template.dll>

int main() {
   __identifier(template) ^pTemplate = gcnew __identifier(template)();
   pTemplate->Run();
}
```

## <a name="see-also"></a>См. также

[Расширения компонентов для платформ среды выполнения](../windows/component-extensions-for-runtime-platforms.md)<br/>
[Расширения компонентов для платформ среды выполнения](../windows/component-extensions-for-runtime-platforms.md)