---
title: 'Пошаговое руководство: Создание и использование собственных динамические ссылки библиотеки (C++) | Документация Майкрософт'
ms.custom: conceptual
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5175d89925ddc09fdcd552aa57d2967071e750f7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376971"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>Пошаговое руководство: Создание и использование собственных динамические ссылки библиотеки (C++)

Это пошаговое руководство показывает, как использовать Visual Studio IDE для создания собственной библиотеки динамической компоновки (DLL), написанные на языке C++, а затем использовать его из другого приложения C++. Библиотеки DLL являются одним из наиболее полезные виды компоненты Windows. Их можно использовать как способ совместного использования кода и ресурсов, для уменьшения размера приложений и для упрощения обслуживания и расширение приложений. В этом пошаговом руководстве вы создать библиотеку DLL, который реализует некоторые математические функции и создайте консольное приложение, которое использует функции из библиотеки DLL. Попутно вы познакомитесь с некоторые приемы программирования и соглашения, используемые в библиотеках DLL Windows.

В этом пошаговом руководстве рассматриваются следующие задачи:

- Создайте проект библиотеки DLL в Visual Studio.

- Добавьте библиотеку DLL экспортированных функций и переменных.

- Создание проекта консольного приложения в Visual Studio.

- Использование функций и переменных, импортированных из библиотеки DLL в консольном приложении.

- Запустите готовое приложение.

Статически скомпонованной библиотекой DLL, такие как _экспортирует_ переменные, функции и ресурсы по имени и приложение _импортирует_ эти имена, чтобы использовать эти переменные, функции и ресурсы. В отличие от статической библиотеки Windows подключается imports в приложении экспорты в библиотеке DLL во время загрузки или во время выполнения, а не подключая во время компоновки. Windows требуется передача дополнительных сведений, который не является частью стандартной модели компиляции C++ для создания этих соединений. Компилятор Visual C++ реализует некоторые Майкрософт расширений для C++, чтобы предоставить дополнительную информацию. Мы объясним эти расширения, при переходе.

В этом пошаговом руководстве создается два решения Visual Studio; один, создающий библиотеку DLL и один, который создает клиентское приложение. Библиотеки DLL использует соглашение о вызовах C, поэтому он может вызываться из приложений, созданных с помощью других языков, до тех пор, пока платформы и вызова и связывание соглашений совпадают. Приложение использует клиент _неявное связывание_, где Windows связано приложение с библиотекой DLL во время загрузки. Это позволяет приложению вызывать функции предоставляемую DLL так же, как функции в статически скомпонованной библиотекой.

В этом пошаговом руководстве не охватывает некоторые распространенные ситуации. Оно не показывает использование библиотек DLL на C++ в других языках программирования. Оно не показывает, как создать Библиотеку ресурсов. Оно также не показывает использование явного связывания для загрузки библиотеки DLL во время выполнения, а не во время загрузки. Уверяем вас, можно использовать Visual C++ для выполнения этих действий. Ссылки на дополнительные сведения о библиотеках DLL, см. в разделе [DLL в Visual C++](../build/dlls-in-visual-cpp.md). Дополнительные сведения о неявных и неявное, см. в разделе [определение связывание метода используйте](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use). Сведения о создании библиотек DLL на C++ для использования в языках программирования, использовать соглашения о языке C, см. в разделе [Экспорт функций C++ для использования в исполняемых файлах языка C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md). Сведения о способах создания библиотек DLL для использования с языками .NET, см. в разделе [вызов функций DLL из приложений Visual Basic](../build/calling-dll-functions-from-visual-basic-applications.md).

В этом пошаговом руководстве используется Visual Studio 2017, но код и большая часть инструкции применимы к более ранним версиям. Инструкции по созданию новых проектов изменен, начиная с Visual Studio 2017 версии 15.3. В этом пошаговом руководстве описывается, как создавать проекты для новых и старых версий. Искать действия, соответствующие вашей версии Visual Studio.

## <a name="prerequisites"></a>Предварительные требования

- Компьютер под управлением Microsoft Windows 7 или более поздних версий. Мы рекомендуем использовать Windows 10 для обеспечения оптимальной среды разработки.

- Копия Visual Studio 2017. Сведения о том, как загрузить и установить Visual Studio см. в разделе [установить Visual Studio 2017 г.](/visualstudio/install/install-visual-studio) Когда вы запускаете программу установки, убедитесь, что **разработка классических приложений C++** проверяется рабочей нагрузки. Не беспокойтесь, если эта рабочая нагрузка не были установлены при установке Visual Studio. Можно снова запустите установщик и установить его.

   ![Разработка классических приложений C++](media/desktop-development-with-cpp.png "разработка классических приложений C++")

- Понимание основ использования интегрированной среде разработки Visual Studio. При использовании классических приложений Windows, прежде чем вы, вероятно, справляется. Общие сведения см. в разделе [Обзор возможностей интегрированной среды разработки Visual Studio](/visualstudio/ide/visual-studio-ide).

- Понимание достаточно основ языка C++ для выполнения этой процедуры. Не беспокойтесь, мы не слишком сложным.

## <a name="create-the-dll-project"></a>Создание проекта библиотеки DLL

В этот набор задач создайте проект для библиотеки DLL, добавьте код и постройте его. Чтобы начать, запустите Visual Studio IDE и вход, если вам нужно. Инструкции по Visual Studio 2017 версии 15.3 идти первой. Инструкции для более ранних версий в будущем, поэтому сразу перейти, если вам нужно.

### <a name="to-create-a-dll-project-in-visual-studio-2017-version-153-or-later"></a>Чтобы создать проект библиотеки DLL в Visual Studio 2017 версии 15.3 или более поздней версии

1. В строке меню последовательно выберите пункты **Файл**, **Создать**, **Проект**, чтобы открыть диалоговое окно **Новый проект**.

1. В левой части **новый проект** диалогового окна разверните узел **установленные** и **Visual C++** Если требуется, а затем выберите **Windows Desktop**. В центральной области выберите **мастер создания классических приложений Windows**. Введите `MathLibrary` в **имя** поле, чтобы задать имя для проекта.

   ![Назовите проект MathLibrary](media/mathlibrary-new-project-name-153.png "MathLibrary проекту имя")

1. Выберите **ОК** кнопку, чтобы закрыть **новый проект** диалоговое окно и начать **проект приложения Windows** мастера.

1. В **проект приложения Windows** мастера **тип приложения**выберите **библиотеки динамической компоновки (.dll)**.

   ![Создать библиотеку DLL в мастере проекта для настольных систем Windows](media/mathlibrary-desktop-project-wizard-dll.png "создать библиотеку DLL в мастере проекта для настольных систем Windows")

1. Нажмите кнопку **ОК**, чтобы создать проект.

> [!NOTE]
> Чтобы устранить ошибку в Visual Studio 2017 версии 15.3 требуются дополнительные действия. Следуйте этим инструкциям, чтобы увидеть, если необходимо внести это изменение.
>
>1. В **обозревателе решений**, если он еще не выбран, выберите **MathLibrary** проект **решение «MathLibrary»**.
>
>1. В строке меню выберите **Проект**, **Свойства**.
>
>1. В левой части **страницы свойств** выберите **препроцессор** под **свойства конфигурации**, **C/C++**. Проверьте содержимое **определения препроцессора** свойство.<br/><br/>![Проверьте свойство определения препроцессора](media/mathlibrary-153bug-preprocessor-definitions-check.png "проверьте свойство определения препроцессора")<br/><br/>Если вы видите **MATHLIBRARY&#95;ЭКСПОРТОВ** в **определения препроцессора** список, не нужно ничего менять. Если вы видите **MathLibrary&#95;ЭКСПОРТОВ** вместо этого перейдите к выполните следующие действия.
>
>1. В верхней части **страницы свойств** диалоговом окне изменения **конфигурации** раскрывающийся список, чтобы **все конфигурации**.
>
>1. На панели свойств выберите элемент управления раскрывающегося списка рядом с полем редактирования для **определения препроцессора**, а затем выберите **изменить**.<br/><br/>![Изменение свойства определения препроцессора](media/mathlibrary-153bug-preprocessor-definitions-property.png "изменение свойства определения препроцессора")
>
>1. В верхней части **определения препроцессора** диалоговом окне Добавить новый символ, `MATHLIBRARY_EXPORTS`.<br/><br/>![Добавьте символ MATHLIBRARY_EXPORTS](media/mathlibrary-153bug-preprocessor-definitions-dialog.png "добавьте символ MATHLIBRARY_EXPORTS")
>
>1. Выберите **ОК** Отклонить **определения препроцессора** диалоговое окно, а затем выберите **ОК** для сохранения изменений в свойствах проекта.

### <a name="to-create-a-dll-project-in-older-versions-of-visual-studio"></a>Создание проекта библиотеки DLL в более ранних версиях Visual Studio

1. В строке меню выберите **Файл**, **Создать**, **Проект**.

1. В левой области **новый проект** диалоговое окно последовательно раскройте элементы **установленные**, **шаблоны**и выберите **Visual C++**, а затем в центре Выберите **консольное приложение Win32**. Введите `MathLibrary` в **имя** изменить поле, чтобы задать имя для проекта.

   ![Назовите проект MathLibrary](media/mathlibrary-project-name.png "MathLibrary проекту имя")

1. Выберите **ОК** кнопку, чтобы закрыть **новый проект** диалоговое окно и начать **мастер приложений Win32**.

   ![Общие сведения о мастере приложений Win32](media/mathlibrary-project-wizard-1.png "Общие сведения о мастере приложений Win32")

1. Нажмите кнопку **Далее**. На **параметры приложения** раздела **тип приложения**выберите **DLL**.

   ![Создание библиотеки DLL в мастере приложений Win32](media/mathlibrary-project-wizard-2.png "создать библиотеку DLL в мастере приложения Win32")

1. Нажмите кнопку **Готово** , чтобы создать проект.

Когда мастер завершит решения, вы увидите созданные проекта и исходные файлы в **обозревателе решений** окно в Visual Studio.

![Созданное решение в Visual Studio](media/mathlibrary-solution-explorer-153.png "созданное решение в Visual Studio")

Справа, эта библиотека DLL не очень сильно. Создайте файл заголовка, объявлять функции DLL экспортирует, а затем добавьте определения функций на библиотеку DLL, чтобы сделать его более полезным.

### <a name="to-add-a-header-file-to-the-dll"></a>Чтобы добавить файл заголовка для библиотеки DLL

1. Чтобы создать файл заголовка для функций, в строке меню, выберите **проекта**, **Добавление нового элемента**.

1. В **Добавление нового элемента** диалоговое окно, в левой области выберите **Visual C++**. В центральной области выберите **Заголовочный файл (.h)**. Укажите `MathLibrary.h` как имя файла заголовка.

   ![Добавить заголовок в диалоговом окне Add New Item](media/mathlibrary-add-new-item-header-file.png "добавить файл заголовка в диалоговом окне Добавление нового элемента")

1. Выберите **добавить** кнопку, чтобы создать пустой файл заголовка, который отображается в новом окне редактора.

   ![Пустой файл MathLibrary.h в редакторе](media/edit-empty-mathlibrary-header.png "MathLibrary.h пустой файл в редакторе")

1. Замените содержимое файла заголовка следующим кодом:

   ```cpp
   // MathLibrary.h - Contains declarations of math functions
   #pragma once

   #ifdef MATHLIBRARY_EXPORTS
   #define MATHLIBRARY_API __declspec(dllexport)
   #else
   #define MATHLIBRARY_API __declspec(dllimport)
   #endif

   // The Fibonacci recurrence relation describes a sequence F
   // where F(n) is { n = 0, a
   //               { n = 1, b
   //               { n > 1, F(n-2) + F(n-1)
   // for some initial integral values a and b.
   // If the sequence is initialized F(0) = 1, F(1) = 1,
   // then this relation produces the well-known Fibonacci
   // sequence: 1, 1, 2, 3, 5, 8, 13, 21, 34, ...

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   extern "C" MATHLIBRARY_API void fibonacci_init(
       const unsigned long long a, const unsigned long long b);

   // Produce the next value in the sequence.
   // Returns true on success and updates current value and index;
   // false on overflow, leaves current value and index unchanged.
   extern "C" MATHLIBRARY_API bool fibonacci_next();

   // Get the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned long long fibonacci_current();

   // Get the position of the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned fibonacci_index();
   ```

Этот файл заголовка объявляет некоторые функции для создания универсальной последовательности Фибоначчи, заданной двумя начальные значения. Вызов `fibonacci_init(1, 1)` создает последовательность знакомы число Фибоначчи.

Обратите внимание, что в операторах препроцессора в верхней части файла. По умолчанию шаблон нового проекта для библиотеки DLL добавляет  **<em>ИМЯ_ПРОЕКТА</em>&#95;ЭКСПОРТОВ** определенные макросы препроцессора для проекта DLL. В этом примере Visual Studio определяет **MATHLIBRARY&#95;ЭКСПОРТОВ** при построении проекта MathLibrary DLL. (Мастер в Visual Studio 2017 версии 15.3 не используется принудительное определение этого символа в верхний регистр. Если имя проекта «MathLibrary», а затем символа, определенного является MathLibrary&#95;ЭКСПОРТОВ вместо MATHLIBRARY&#95;ЭКСПОРТОВ. That's Почему существуют дополнительные шаги, чтобы добавить этот символ.)

Когда **MATHLIBRARY&#95;ЭКСПОРТОВ** макрос определен, **MATHLIBRARY&#95;API** макрос наборы `__declspec(dllexport)` модификатор в объявлении функций. Этот модификатор сообщает компилятор и компоновщик для экспорта функция или переменная из библиотеки DLL, чтобы он может использоваться другими приложениями. Когда **MATHLIBRARY&#95;ЭКСПОРТОВ** не определен, например, если файл заголовка включен клиентским приложением, **MATHLIBRARY&#95;API** применяется `__declspec(dllimport)` модификатор объявления. Этот модификатор оптимизирует импорт функции или переменной в приложении. Дополнительные сведения см. в разделе [dllexport, dllimport](../cpp/dllexport-dllimport.md).

### <a name="to-add-an-implementation-to-the-dll"></a>Чтобы добавить реализацию на библиотеку DLL

1. В окне редактора, перейдите на вкладку для **MathLibrary.cpp** если он уже открыт. В противном случае в **обозревателе решений**откройте **MathLibrary.cpp** в **исходные файлы** папке **MathLibrary** проекта.

1. В редакторе Замените содержимое файла MathLibrary.cpp следующим кодом:

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h"
   #include <utility>
   #include <limits.h>
   #include "MathLibrary.h"

   // DLL internal state variables:
   static unsigned long long previous_;  // Previous value, if any
   static unsigned long long current_;   // Current sequence value
   static unsigned index_;               // Current seq. position

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   void fibonacci_init(
       const unsigned long long a,
       const unsigned long long b)
   {
       index_ = 0;
       current_ = a;
       previous_ = b; // see special case when initialized
   }

   // Produce the next value in the sequence.
   // Returns true on success, false on overflow.
   bool fibonacci_next()
   {
       // check to see if we'd overflow result or position
       if ((ULLONG_MAX - previous_ < current_) ||
           (UINT_MAX == index_))
       {
           return false;
       }

       // Special case when index == 0, just return b value
       if (index_ > 0)
       {
           // otherwise, calculate next sequence value
           previous_ += current_;
       }
       std::swap(current_, previous_);
       ++index_;
       return true;
   }

   // Get the current value in the sequence.
   unsigned long long fibonacci_current()
   {
       return current_;
   }

   // Get the current index position in the sequence.
   unsigned fibonacci_index()
   {
       return index_;
   }
   ```

Чтобы убедиться, что все работает до сих, Скомпилируйте библиотеку динамической компоновки. Чтобы скомпилировать, выберите **построения**, **построить решение** в строке меню. Результат должен выглядеть примерно так:

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>stdafx.cpp
1>MathLibrary.cpp
1>dllmain.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.pdb (Partial PDB)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Поздравляем, вы создали библиотеку DLL с помощью Visual C++. Далее вы создадите клиентское приложение, которое использует функций, экспортируемых посредством библиотеки DLL.

## <a name="create-a-client-app-that-uses-the-dll"></a>Создание клиентского приложения, которое использует библиотеку DLL

При создании библиотеки DLL, необходимо подумать об использовании библиотеки DLL. Чтобы скомпилировать код, который вызывает функций, экспортируемых посредством библиотеки DLL, объявления должны быть включены в исходный код клиентской. Во время компоновки, если разрешаются эти вызовы функций DLL, компоновщик должен иметь *библиотека импорта*, это специальный файл библиотеки, который содержит сведения о способах поиска функции, а не фактический код для Windows. И во время выполнения, библиотеки DLL должны быть доступны клиенту, в расположении, которое можно найти операционной системы.

Чтобы использовать библиотеку DLL ли вашей владеете или сторонняя библиотека DLL, ваш проект клиентского приложения должен иметь возможность найти заголовки, которые объявляют DLL экспортирует библиотеки импорта для компоновщика и самой библиотеки DLL. Один из способов сделать это является копирование всех файлов в проекте клиента. Для сторонних библиотек DLL, которые, скорее всего, изменять, если ваш клиент находится в разработке это может быть лучший способ их использования. Тем не менее при построении библиотеки DLL, лучше избежать дублирования. При внесении копию DLL-файлы, которые находятся в стадии разработки, можно случайно изменить файл заголовка в одну копию, но не в другой, или использовать библиотеку устарели. Чтобы избежать этой проблемы, мы рекомендуем задать пути включения проекта клиента, чтобы включать файлы заголовков библиотеки DLL из проекта DLL. Кроме того можно задайте путь к библиотеке в проекте клиента для включения библиотеки импорта библиотеки DLL из проекта DLL. И наконец, скопируйте собранную библиотеку DLL из проекта DLL, в выходном каталоге сборки. Это гарантирует, что клиентское приложение использует тот же код библиотеки DLL, которые вы создаете.

### <a name="to-create-a-client-app-in-visual-studio-2017-version-153-or-later"></a>Создание клиентского приложения в Visual Studio 2017 версии 15.3 или более поздней версии

1. Чтобы создать приложение C++, которое использует библиотеку DLL, которую вы только что создали, в строке меню выберите **файл**, **New**, **проекта**.

1. В левой части **новый проект** диалоговом окне выберите **Windows Desktop** под **установленные**, **Visual C++**. В центральной области выберите **мастер создания классических приложений Windows**. Укажите имя проекта, `MathClient`в **имя** поле ввода.

   ![Назовите проект клиента](media/mathclient-new-project-name-153.png "назовите проект клиента")

1. Выберите **ОК** запустить **проект приложения Windows** мастера. В мастере выберите **ОК** создать проект клиентского приложения.

### <a name="to-create-a-client-app-in-older-versions-of-visual-studio-2017"></a>Для создания клиентского приложения в более ранних версиях Visual Studio 2017

1. Чтобы создать приложение C++, которое использует библиотеку DLL, которую вы только что создали, в строке меню выберите **файл**, **New**, **проекта**.

1. В левой части **новый проект** диалоговом окне выберите **Win32** под **установленные**, **шаблоны**, **Visual C++**. В центральной области выберите **Консольное приложение Win32**. Укажите имя проекта, `MathClient`в **имя** поле ввода.

   ![Назовите проект клиента](media/mathclient-project-name.png "назовите проект клиента")

1. Выберите **ОК** кнопку, чтобы закрыть **новый проект** диалоговое окно и начать **мастер приложений Win32**. На странице **Обзор** диалогового окна **Мастер приложений Win32** нажмите кнопку **Далее** .

1. На **параметры приложения** раздела **тип приложения**выберите **консольное приложение** если он еще не установлен.

1. Нажмите кнопку **Готово** , чтобы создать проект.

По завершении работы мастера проект минимальной консольного приложения создается автоматически. Имя основной исходный файл является совпадает с именем проекта, заданное ранее. В этом примере он называется **MathClient.cpp**. Можно выполнить его сборку, но еще не использует библиотеки DLL.

Затем для вызова функций MathLibrary в исходном коде, проект должен содержать файл MathLibrary.h. Можно скопировать этот файл заголовка в проект приложения клиента, а затем добавить его в проект в качестве существующего элемента. Это может быть хорошим выбором для сторонних библиотек. Тем не менее при работе на код для библиотеки DLL в то же время клиент, который может привести к изменения в файле один заголовок, не отражаются в другом. Чтобы избежать этой проблемы, можно изменить **Дополнительные каталоги включаемых файлов** путь проекта, чтобы указать путь к исходный заголовок.

### <a name="to-add-the-dll-header-to-your-include-path"></a>Для добавления заголовка библиотеки DLL в путь включаемых файлов

1. Откройте **страницы свойств** диалоговое окно для **MathClient** проекта.

1. В **конфигурации** раскрывающегося списка выберите **все конфигурации** если он еще не установлен.

1. В левой области выберите **Общие** под **свойства конфигурации**, **C/C++**.

1. На панели свойств выберите элемент управления раскрывающегося списка рядом с полем **Дополнительные каталоги включаемых файлов** поле ввода, а затем выберите **изменить**.

   ![Изменение свойства Дополнительные каталоги включаемых файлов](media/mathclient-additional-include-directories-property.png "изменение свойства Дополнительные каталоги включаемых файлов")

1. Дважды щелкните в верхней части **Дополнительные каталоги включаемых файлов** диалоговое окно, чтобы включить элемент управления редактированием.

1. В элементе управления, укажите путь к расположению **MathLibrary.h** файл заголовка. В этом случае можно использовать относительный путь:

   `..\..\MathLibrary\MathLibrary`

   ![Добавьте расположение заголовка в свойстве Дополнительные каталоги включаемых файлов](media/mathclient-additional-include-directories.png "добавьте расположение заголовка в свойстве Дополнительные каталоги включаемых файлов")

1. После введения путь к файлу заголовка в **Дополнительные каталоги включаемых файлов** диалоговое окно, выберите **ОК** кнопку, чтобы вернуться к **страницы свойств** диалоговом окне и затем выберите **ОК** кнопку, чтобы сохранить изменения.

Теперь можно включать **MathLibrary.h** файл и использовать функции, он объявляется в клиентском приложении. Замените содержимое файла **MathClient.cpp** с помощью следующего кода:

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
#include "stdafx.h"
#include <iostream>
#include "MathLibrary.h"

int main()
{
    // Initialize a Fibonacci relation sequence.
    fibonacci_init(1, 1);
    // Write out the sequence values until overflow.
    do {
        std::cout << fibonacci_index() << ": "
            << fibonacci_current() << std::endl;
    } while (fibonacci_next());
    // Report count of values written before overflow.
    std::cout << fibonacci_index() + 1 <<
        " Fibonacci sequence values fit in an " <<
        "unsigned 64-bit integer." << std::endl;
}
```

Этот код можно скомпилировать, но не связаны, так как компоновщик не удается найти библиотеку импорта, необходимые для создания приложения еще. Компоновщик должен иметь возможность найти файл MathLibrary.lib для связывания успешно. Необходимо добавить в файл MathLibrary.lib сборки, задав **Дополнительные зависимости** свойство. Опять же можно скопировать файл библиотеки в проекте приложения клиента, но если одновременно с библиотекой и клиентское приложение находятся в стадии разработки, который может привести к изменения в одну копию, не отражаются в другом. Чтобы избежать этой проблемы, можно изменить **Дополнительные каталоги библиотек** путь проекта, чтобы указать путь к исходной библиотеки, во время привязки.

### <a name="to-add-the-dll-import-library-to-your-project"></a>Чтобы добавить в проект DLL-библиотека импорта

1. Откройте **страницы свойств** диалоговое окно для **MathClient** проекта.

1. В **конфигурации** раскрывающегося списка выберите **все конфигурации** если он еще не установлен.

1. В левой области выберите **ввода** под **свойства конфигурации**, **компоновщика**. На панели свойств выберите элемент управления раскрывающегося списка рядом с полем **Дополнительные зависимости** поле ввода, а затем выберите **изменить**.

   ![Изменение свойства Дополнительные зависимости](media/mathclient-additional-dependencies-property.png "изменить свойство Дополнительные зависимости")

1. В **Дополнительные зависимости** диалоговом окне Добавить `MathLibrary.lib` в список в верхней части элемента управления edit.

   ![Добавить зависимости библиотеки](media/mathclient-additional-dependencies.png "добавить зависимости библиотеки")

1. Выберите **ОК** чтобы вернуться к **страницы свойств** диалоговое окно.

1. В левой области выберите **Общие** под **свойства конфигурации**, **компоновщика**. На панели свойств выберите элемент управления раскрывающегося списка рядом с полем **Дополнительные каталоги библиотек** поле ввода, а затем выберите **изменить**.

   ![Изменение свойства Дополнительные каталоги библиотек](media/mathclient-additional-library-directories-property.png "изменение свойства Дополнительные каталоги библиотек")

1. Дважды щелкните в верхней части **Дополнительные каталоги библиотек** диалоговое окно, чтобы включить элемент управления редактированием. В элементе управления, укажите путь к расположению **MathLibrary.lib** файла. Введите это значение, чтобы использовать макрос, создающий работает для отладки и выпуска:

   `..\..\MathLibrary\$(IntDir)`

   ![Добавьте каталог библиотеки](media/mathclient-additional-library-directories.png "добавьте каталог библиотеки")

1. После введения путь к файлу библиотеки в **Дополнительные каталоги библиотек** диалоговое окно, выберите **ОК** кнопку, чтобы вернуться к **страницы свойств** диалоговое окно.

Клиентское приложение теперь выполнить компиляцию и компоновку успешно, но по-прежнему не предоставляет все необходимое для запуска. Когда операционная система загружает приложение, он ищет MathLibrary библиотеки DLL. Если не удается найти библиотеку DLL в определенные системные каталоги, путь к среде или в каталог локального приложения, загрузка завершится ошибкой. Чтобы избежать этой проблемы рекомендуется скопировать DLL в каталог, содержащий исполняемый файл клиента как часть процесса построения. Чтобы скопировать библиотеку DLL, можно добавить **POST-Build Event** в проект, чтобы добавить команду, копирует библиотеку DLL в выходном каталоге сборки. Команда, указанная здесь копирует библиотеку DLL, только в том случае, если он отсутствует или был изменен и использует макросы для копирования и из правильных местоположений Debug или Retail для вашей конфигурации.

### <a name="to-copy-the-dll-in-a-post-build-event"></a>Для копирования DLL в событие после построения

1. Откройте **страницы свойств** диалоговое окно для **MathClient** проекта, если он еще не открыт.

1. В раскрывающемся окне конфигурации выберите **все конфигурации** если он еще не установлен.

1. В левой области выберите **POST-Build Event** под **свойства конфигурации**, **события построения**.

1. На панели свойств выберите элемент управления редактирования в **командной строки** поле, а затем введите следующую команду:

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![Добавьте команду после построения](media/mathclient-post-build-command-line.png "добавьте команду после сборки")

1. Выберите **ОК** кнопку, чтобы сохранить изменения в свойствах проекта.

Теперь клиентское приложение имеет все необходимое для построения и запуска. Постройте приложение, выбрав **построения**, **построить решение** в строке меню. **Вывода** окно в Visual Studio должен содержать примерно следующее:

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>stdafx.cpp
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.pdb (Partial PDB)
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Поздравляем, вы создали приложение, вызывающее функции в вашей библиотеке DLL. Теперь запустите приложение, чтобы увидеть, что она делает. В строке меню выберите **Отладка**, **Запуск без отладки**. Visual Studio открывает окно командной строки для программы для запуска в. В последней части выходных данных должен выглядеть следующим образом:

![Запуск клиентского приложения без отладки](media/mathclient-run-without-debugging.png "запустить клиентское приложение без отладки")

Нажмите любую клавишу, чтобы скрыть окно команд.

Теперь, когда вы создали библиотеку DLL и клиентским приложением, вы можете поэкспериментировать. Попробуйте установить точки останова в коде клиентского приложения и запустить приложение в отладчике. Посмотрим, что произойдет при заходе в вызов библиотеки. Добавление других функций в библиотеку или написать другого клиентского приложения, которое использует библиотеки DLL.

При развертывании приложения, необходимо также развернуть библиотеки DLL, он использует. Самый простой способ предоставления библиотеки DLL, создании или включении сторонних производителей в приложение, — они должны быть размещены в том же каталоге, что и приложение, также известный как *развертывания локальных приложений*. Дополнительные сведения о развертывании см. в разделе [развертывание в Visual C++](..\ide\deployment-in-visual-cpp.md).

## <a name="see-also"></a>См. также

[DLL в Visual C++](../build/dlls-in-visual-cpp.md)<br/>
[Развертывание классических приложений](../ide/deploying-native-desktop-applications-visual-cpp.md)<br/>
[Пошаговое руководство. Развертывание программы (C++)](../ide/walkthrough-deploying-your-program-cpp.md)<br/>
[Вызов функций библиотек DLL из приложений Visual Basic](../build/calling-dll-functions-from-visual-basic-applications.md)