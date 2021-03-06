---
title: Универсальные интерфейсы (Visual C++) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- generic interfaces
- interfaces, generic [C++}
ms.assetid: f3da788a-ba83-4db7-9dcf-9b95a8fb9d1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2065b96875f2c441b24eb69f8ca51b06fe5717f0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444498"
---
# <a name="generic-interfaces-visual-c"></a>Универсальные интерфейсы (Visual C++)

Ограничения, которые применяются к параметрам типа на классы являются те, которые применяются к параметрам типа на интерфейсах же (см. в разделе [универсальные классы (C + +/ CLI)](../windows/generic-classes-cpp-cli.md)).

Правила, управляющие перегрузка функций для функций в универсальных классах или интерфейсах одинаковы.

Явные реализации члена интерфейса работать с типами построенный интерфейс в так же, как с помощью простой интерфейс типов (см. следующие примеры).

Дополнительные сведения об интерфейсах см. в разделе [класс интерфейса](../windows/interface-class-cpp-component-extensions.md).

## <a name="syntax"></a>Синтаксис

```cpp
[attributes] generic <class-key type-parameter-identifier[, ...]>
[type-parameter-constraints-clauses][accesibility-modifiers] interface class identifier [: base-list] {   interface-body} [declarators] ;
```

## <a name="remarks"></a>Примечания

*Атрибуты*<br/>
(Необязательно) Дополнительные описательные данные. Дополнительные сведения об атрибутах и классах атрибутов см. в разделе **атрибуты**.

*ключ класса*<br/>
**Класс** или **typename**

*Тип-параметр-идентификаторы*<br/>
Разделенный запятыми список идентификаторов.

*Тип параметра — ограничения предложения*<br/>
Имеет формат, определенный в [ограничений для параметров универсального типа (C + +/ CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)

*модификаторы доступа*<br/>
(Необязательно) Модификаторы доступа (например **открытого, закрытого**).

*identifier*<br/>
Имя интерфейса.

*базовый список*<br/>
(Необязательно) Список, содержащий один или несколько явные базовые интерфейсы, разделенные запятыми.

*теле интерфейса*<br/>
Объявления членов интерфейса.

*деклараторы*<br/>
(Необязательно) Объявления переменных, на основе этого типа.

## <a name="example"></a>Пример

Следующий пример демонстрирует объявление и создание экземпляра универсального интерфейса. В примере универсальный интерфейс `IList<ItemType>` объявлен. Затем он реализован в двух универсальных классов, `List1<ItemType>` и `List2<ItemType>`, с различными реализациями.

```cpp
// generic_interface.cpp
// compile with: /clr
using namespace System;

// An exception to be thrown by the List when
// attempting to access elements beyond the
// end of the list.
ref class ElementNotFoundException : Exception {};

// A generic List interface
generic <typename ItemType>
public interface class IList {
   ItemType MoveFirst();
   bool Add(ItemType item);
   bool AtEnd();
   ItemType Current();
   void MoveNext();
};

// A linked list implementation of IList
generic <typename ItemType>
public ref class List1 : public IList<ItemType> {
   ref class Node {
      ItemType m_item;

   public:
      ItemType get_Item() { return m_item; };
      void set_Item(ItemType value) { m_item = value; };

      Node^ next;

      Node(ItemType item) {
         m_item = item;
         next = nullptr;
      }
   };

   Node^ first;
   Node^ last;
   Node^ current;

   public:
   List1() {
      first = nullptr;
      last = first;
      current = first;
   }

   virtual ItemType MoveFirst() {
      current = first;
      if (first != nullptr)  
        return first->get_Item();
      else
         return ItemType();
   }

   virtual bool Add(ItemType item) {
      if (last != nullptr) {
         last->next = gcnew Node(item);
         last = last->next;
      }
      else {
         first = gcnew Node(item);
         last = first;
         current = first;
      }
      return true;
   }

   virtual bool AtEnd() {
      if (current == nullptr )  
        return true;
      else
        return false;
   }

   virtual ItemType Current() {
       if (current != nullptr)  
         return current->get_Item();
       else
         throw gcnew ElementNotFoundException();
   }

   virtual void MoveNext() {
      if (current != nullptr)  
       current = current->next;
      else
        throw gcnew ElementNotFoundException();
   }
};

// An array implementation of IList
generic <typename ItemType>
ref class List2 : public IList<ItemType> {
   array<ItemType>^ item_array;
   int count;
   int current;

   public:

   List2() {
      // not yet possible to declare an
      // array of a generic type parameter
      item_array = gcnew array<ItemType>(256);
      count = current = 0;
   }

   virtual ItemType MoveFirst() {
      current = 0;
      return item_array[0];
   }

   virtual bool Add(ItemType item) {
      if (count < 256)  
         item_array[count++] = item;
      else
        return false;
      return true;
   }

   virtual bool AtEnd() {
      if (current >= count)  
        return true;
      else
        return false;
   }

   virtual ItemType Current() {
      if (current < count)  
        return item_array[current];
      else
        throw gcnew ElementNotFoundException();
   }

   virtual void MoveNext() {
      if (current < count)  
         ++current;
      else
         throw gcnew ElementNotFoundException();
   }
};

// Add elements to the list and display them.
generic <typename ItemType>
void AddStringsAndDisplay(IList<ItemType>^ list, ItemType item1, ItemType item2) {
   list->Add(item1);
   list->Add(item2);
   for (list->MoveFirst(); ! list->AtEnd(); list->MoveNext())  
   Console::WriteLine(list->Current());
}

int main() {
   // Instantiate both types of list.

   List1<String^>^ list1 = gcnew List1<String^>();
   List2<String^>^ list2 = gcnew List2<String^>();

   // Use the linked list implementation of IList.
   AddStringsAndDisplay<String^>(list1, "Linked List", "List1");

   // Use the array implementation of the IList.
   AddStringsAndDisplay<String^>(list2, "Array List", "List2");
}
```

```Output
Linked List
List1
Array List
List2
```

## <a name="example"></a>Пример

В этом примере объявляется универсальный интерфейс, `IMyGenIface`и два неуниверсальных интерфейсов, `IMySpecializedInt` и `ImySpecializedString`, который specialize `IMyGenIface`. Две специализированных интерфейсов реализуются два класса `MyIntClass` и `MyStringClass`. В примере как specialize универсальных интерфейсов, создание универсальных и неуниверсальных интерфейсов и вызова явной реализации членов интерфейсов.

```cpp
// generic_interface2.cpp
// compile with: /clr
// Specializing and implementing generic interfaces.
using namespace System;

generic <class ItemType>
public interface class IMyGenIface {
   void Initialize(ItemType f);
};

public interface class IMySpecializedInt: public IMyGenIface<int> {
   void Display();
};

public interface class IMySpecializedString: public IMyGenIface<String^> {
   void Display();
};

public ref class MyIntClass: public IMySpecializedInt {
   int myField;

public:
   virtual void Initialize(int f) {
      myField = f;
   }

   virtual void Display() {
      Console::WriteLine("The integer field contains: {0}", myField);
   } 
};

public ref struct MyStringClass: IMySpecializedString { 
   String^ myField;

public:
   virtual void Initialize(String^ f) {
      myField = f;
    }

   virtual void Display() {
      Console::WriteLine("The String field contains: {0}", myField);
   }
};

int main() {
   // Instantiate the generic interface.
   IMyGenIface<int>^ myIntObj = gcnew MyIntClass();

   // Instantiate the specialized interface "IMySpecializedInt."
   IMySpecializedInt^ mySpIntObj = (IMySpecializedInt^) myIntObj;

   // Instantiate the generic interface.
   IMyGenIface<String^>^ myStringObj = gcnew MyStringClass();

   // Instantiate the specialized interface "IMySpecializedString."
   IMySpecializedString^ mySpStringObj =
            (IMySpecializedString^) myStringObj;

   // Call the explicitly implemented interface members.
   myIntObj->Initialize(1234);
   mySpIntObj->Display();

   myStringObj->Initialize("My string");
   mySpStringObj->Display();
}
```

```Output
The integer field contains: 1234
The String field contains: My string
```

## <a name="see-also"></a>См. также

[Универсальные шаблоны](../windows/generics-cpp-component-extensions.md)