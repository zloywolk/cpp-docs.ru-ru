---
title: Указатели (C++) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarators, pointers
- declarations, pointers
- pointers [C++]
- pointers, declarations
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a39ee9c45084d03198157f427ca3edca13767e6c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024116"
---
# <a name="pointers-c"></a>Указатели (C++)

Указатели объявляются с помощью следующей последовательности.

```
[storage-class-specifiers] [cv-qualifiers] type-specifiers 
[ms-modifier] declarator ;
```

Для элемента `declarator` этой последовательности может использоваться любой допустимый декларатор указателя. Синтаксис простого декларатора указателя следующий:

```
* [cv-qualifiers] identifier [= expression]
```

1. Спецификаторы объявления:

    - Необязательный спецификатор класса хранения. Дополнительные сведения см. в разделе [спецификаторы](../cpp/specifiers.md).

    - Необязательный **const** или **volatile** ключевое слово, относящееся к типу объекта, на который нужно указывать.

    - Спецификатор типа: имя типа, представляющее тип объекта, на который нужно указывать.

2. Декларатор:

    - Необязательный модификатор, используемый в системах Microsoft. Дополнительные сведения см. в разделе [модификаторы, используемые Microsoft](../cpp/microsoft-specific-modifiers.md).

    - Оператор `*`.

    - Необязательный **const** или **volatile** ключевое слово, применение к самому указателю.

    - Идентификатор.

    - Необязательный инициализатор.

     Декларатор для указателя на функцию выглядит следующим образом:

```
(* [cv-qualifiers] identifier )( argument-list ) [cv-qualifers]
[exception specification] [= expression];
```

- Для массива указателей синтаксис следующий:

```
* identifier [ [ constant-expression ] ]
```

- Несколько деклараторов и их инициализаторы могут присутствовать вместе в одном объявлении в разделенном запятыми списке после спецификатора объявления.

Простой пример объявления указателя:

```cpp
char *pch;
```

Указывает, что предыдущего объявления `pch` указывает на объект типа **char**.

Более сложный пример:

```cpp
static unsigned int * const ptr;
```

Указывает, что предыдущего объявления `ptr` — это постоянный указатель на объект типа **без знака** **int** со статической длительностью хранения.

В следующем примере показываются объявление и инициализация нескольких указателей.

```cpp
static int *p = &i, *q = &j;
```

В приведенном выше примере указатели p и q указывают на объекты типа **int** и инициализируются с адресами i и j соответственно.  Спецификатор класса хранения **статический** относится к обоим указателям.

## <a name="example"></a>Пример

```cpp
// pointer.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   int i = 1, j = 2; // local variables on the stack
   int *p;

   // a pointer may be assigned to "point to" the value of
   // another variable using the & (address of) operator
   p = & j;

   // since j was on the stack, this address will be somewhere
   // on the stack.  Pointers are printed in hex format using
   // %p and conventionally marked with 0x.
   printf_s("0x%p\n",  p);

   // The * (indirection operator) can be read as "the value
   // pointed to by".
   // Since p is pointing to j, this should print "2"
   printf_s("0x%p %d\n",  p, *p);

   // changing j will change the result of the indirection
   // operator on p.
   j = 7;
   printf_s("0x%p %d\n",  p, *p );

   // The value of j can also be changed through the pointer
   // by making an assignment to the dereferenced pointer
   *p = 10;
   printf_s("j is %d\n", j); // j is now 10

   // allocate memory on the heap for an integer,
   // initialize to 5
   p = new int(5);

   // print the pointer and the object pointed to
   // the address will be somewhere on the heap
   printf_s("0x%p %d\n",  p, *p);

   // free the memory pointed to by p
   delete p;

   // At this point, dereferencing p with *p would trigger
   // a runtime access violation.

   // Pointer arithmetic may be done with an array declared
   // on the stack or allocated on the heap with new.
   // The increment operator takes into account the size
   // of the objects pointed to.
   p = new int[5];
   for (i = 0; i < 5; i++, p++) {
      *p = i * 10;
      printf_s("0x%p %d\n", p, *p);
   }

   // A common expression seen is dereferencing in combination
   // with increment or decrement operators, as shown here.
   // The indirection operator * takes precedence over the
   // increment operator ++.
   // These are particularly useful in manipulating char arrays.
   char s1[4] = "cat";
   char s2[4] = "dog";
   char* p1 = s1;
   char* p2 = s2;

   // the following is a string copy operation
   while (*p1++ = *p2++);

   // s2 was copied into s1, so now they are both equal to "dog"
   printf_s("%s %s", s1, s2);
}
```

```Output
0x0012FEC8
0x0012FEC8 2
0x0012FEC8 7
j is 10
0x00320850 5
0x00320850 0
0x00320854 10
0x00320858 20
0x0032085C 30
0x00320860 40
dog dog
```

## <a name="example"></a>Пример

В другом примере показывается использование указателей в структурах данных; в данном случае — в связанном списке.

```cpp
// pointer_linkedlist.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct NewNode {
   NewNode() : node(0){}
   int i;
   NewNode * node;
};

void WalkList(NewNode * ptr) {
   if (ptr != 0) {
      int i = 1;
      while (ptr->node != 0 ) {
         cout << "node " << i++ << " = " << ptr->i << endl;
         ptr = ptr->node;
      }
      cout << "node " << i++ << " = " << ptr->i << endl;
   }
}

void AddNode(NewNode ** ptr) {
   NewNode * walker = 0;
   NewNode * MyNewNode = new NewNode;
   cout << "enter a number: " << endl;
   cin >> MyNewNode->i;

   if (*ptr == 0)
      *ptr = MyNewNode;
   else  {
      walker = *ptr;
      while (walker->node != 0)
         walker = walker->node;

      walker->node = MyNewNode;
   }
}

int main() {
   char ans = ' ';
   NewNode * ptr = 0;
   do {
      cout << "a (add node)  d (display list)  q (quit)" << endl;
      cin >> ans;
      switch (ans) {
      case 'a':
         AddNode(&ptr);
         break;
      case 'd':
         WalkList(ptr);
         break;
      }
   } while (ans != 'q');
}
```

```Output
a
45
d
a
789
d
qa (add node)  d (display list)  q (quit)
enter a number:
a (add node)  d (display list)  q (quit)
node 1 = 45
a (add node)  d (display list)  q (quit)
enter a number:
a (add node)  d (display list)  q (quit)
node 1 = 45
node 2 = 789
a (add node)  d (display list)  q (quit)
```

## <a name="see-also"></a>См. также

[Оператор косвенного обращения: *](../cpp/indirection-operator-star.md)<br/>
[Оператор address-of: &](../cpp/address-of-operator-amp.md)