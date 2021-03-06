---
title: Предупреждение компилятора (уровень 1) C4621 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4621
dev_langs:
- C++
helpviewer_keywords:
- C4621
ms.assetid: 40931bd9-cb89-497e-86f0-cec9f016c63c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70b9273e1c3a91db37be6bee2c1c33a0a4e30b17
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090832"
---
# <a name="compiler-warning-level-1-c4621"></a>Предупреждение компилятора (уровень 1) C4621

не постфиксная форма «operator--» для типа «тип»; используется префиксная форма

Возникла не постфиксного оператора декремента, определенные для заданного типа. Компилятор использовал перегруженный префиксный оператор.

Это предупреждение можно избежать, определив постфиксный `--` оператор. Создание двух аргументных версии `--` оператор, как показано ниже:

```
// C4621.cpp
// compile with: /W1
class A
{
public:
   A(int nData) : m_nData(nData)
   {
   }

   A operator--()
   {
      m_nData -= 1;
      return *this;
   }

   // A operator--(int)
   // {
   //    A tmp = *this;
   //    m_nData -= 1;
   //    return tmp;
   // }

private:
   int m_nData;
};

int main()
{
   A a(10);
   --a;
   a--;   // C4621
}
```