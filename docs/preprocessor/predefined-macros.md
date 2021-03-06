---
title: Предопределенные макросы | Документация Майкрософт
ms.custom: update_every_version
ms.date: 04/30/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _ATL_VER
- __ATOM__
- __AVX__
- __AVX2__
- _CHAR_UNSIGNED
- __CLR_VER
- _CONTROL_FLOW_GUARD
- __COUNTER__
- __cplusplus
- __cplusplus_cli
- __cplusplus_winrt
- _CPPRTTI
- _CPPUNWIND
- __DATE__
- _DEBUG
- _DLL
- __FILE__
- __FUNCDNAME__
- __FUNCSIG__
- __FUNCTION__
- _INTEGRAL_MAX_BITS
- _ISO_VOLATILE
- _KERNEL_MODE
- __LINE__
- _M_AMD64
- _M_ARM
- _M_ARM_ARMV7VE
- _M_ARM_FP
- _M_ARM64
- _M_CEE
- _M_CEE_PURE
- _M_CEE_SAFE
- _M_FP_EXCEPT
- _M_FP_FAST
- _M_FP_PRECISE
- _M_FP_STRICT
- _M_IX86
- _M_IX86_FP
- _M_X64
- _MANAGED
- _MFC_VER
- _MSC_BUILD
- _MSC_EXTENSIONS
- _MSC_FULL_VER
- _MSC_VER
- _MSVC_LANG
- __MSVC_RUNTIME_CHECKS
- _MT
- _NATIVE_WCHAR_T_DEFINED
- _NO_SIZED_DEALLOCATION
- _OPENMP
- _PREFAST_
- _RESUMABLE_FUNCTIONS_SUPPORTED
- _RTC_CONVERSION_CHECKS_ENABLED
- __STDC__
- __STDC_HOSTED__
- __STDCPP_THREADS__
- __TIME__
- __TIMESTAMP__
- __VA_ARGS__
- _VC_NODEFAULTLIB
- _WCHAR_T_DEFINED
- _WIN32
- _WIN64
- _WINRT_DLL
- __func__
dev_langs:
- C++
helpviewer_keywords:
- timestamps, preprocessor macro
- cl.exe compiler, version number
- version numbers, C/C++ compiler (cl.exe)
- macros, predefined C++
- preprocessor, macros
- predefined macros
- _ATL_VER macro
- __ATOM__ macro
- __AVX__ macro
- __AVX2__ macro
- _CHAR_UNSIGNED macro
- __CLR_VER macro
- _CONTROL_FLOW_GUARD macro
- __COUNTER__ macro
- __cplusplus macro
- __cplusplus_cli macro
- __cplusplus_winrt macro
- _CPPRTTI macro
- _CPPUNWIND macro
- __DATE__ macro
- _DEBUG macro
- _DLL macro
- __FILE__ macro
- __FUNCDNAME__ macro
- __FUNCSIG__ macro
- __FUNCTION__ macro
- _INTEGRAL_MAX_BITS macro
- _ISO_VOLATILE macro
- _KERNEL_MODE macro
- __LINE__ macro
- _M_AMD64 macro
- _M_ARM macro
- _M_ARM_ARMV7VE macro
- _M_ARM_FP macro
- _M_ARM64 macro
- _M_CEE macro
- _M_CEE_PURE macro
- _M_CEE_SAFE macro
- _M_FP_EXCEPT macro
- _M_FP_FAST macro
- _M_FP_PRECISE macro
- _M_FP_STRICT macro
- _M_IX86 macro
- _M_IX86_FP macro
- _M_X64 macro
- _MANAGED macro
- _MFC_VER macro
- _MSC_BUILD macro
- _MSC_EXTENSIONS macro
- _MSC_FULL_VER macro
- _MSC_VER macro
- _MSVC_LANG macro
- __MSVC_RUNTIME_CHECKS macro
- _MT macro
- _NATIVE_WCHAR_T_DEFINED macro
- _NO_SIZED_DEALLOCATION macro
- _OPENMP macro
- _PREFAST_ macro
- _RESUMABLE_FUNCTIONS_SUPPORTED macro
- _RTC_CONVERSION_CHECKS_ENABLED macro
- __STDC__ macro
- __STDC_HOSTED__ macro
- __STDCPP_THREADS__ macro
- __TIME__ macro
- __TIMESTAMP__ macro
- __VA_ARGS__ macro
- _VC_NODEFAULTLIB macro
- _WCHAR_T_DEFINED macro
- _WIN32 macro
- _WIN64 macro
- _WINRT_DLL macro
- __func__ identifier
ms.assetid: 1cc5f70a-a225-469c-aed0-fe766238e23f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9a1472cba13f477143c9b9ace27cb2555f41406
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408431"
---
# <a name="predefined-macros"></a>Предустановленный макрос

Компилятор Visual C++ предопределяет определенные макросы препроцессора, в зависимости от языка (C или C++), целевого объекта компиляции и параметры выбранного компилятора.

Visual C++ поддерживает необходимые предварительно определенных макросов препроцессора, указанный по стандарту ANSI/ISO C99 и ISO стандартом C ++ 14. Реализация также поддерживает несколько дополнительные препроцессора макросов Microsoft. Некоторые макросы определяются только для определенной сборки сред или параметры компилятора. Если не указано, макросы определяются в записи преобразования, как если бы они были заданы как **/D** аргументов параметра компилятора. При определении, макросы разворачиваются препроцессором перед компиляцией указанные значения. Предустановленные макросы не принимают аргументы и не может быть переопределен.

## <a name="standard-predefined-identifier"></a>Стандартный предопределенный идентификатор

Компилятор поддерживает это предопределенный идентификатор, указанный по стандарту ISO C99 и ISO C ++ 11.

- **&#95;&#95;Func&#95; &#95;**  неполное и недекорируемое имя включающей функции в виде функции локальной **статический const** массив **char**.

    ```cpp
    void example(){
        printf("%s\n", __func__);
    } // prints "example"
    ```

## <a name="standard-predefined-macros"></a>Стандартный предустановленные макросы

Компилятор поддерживает эти предопределенные макросы, заданного ISO C99 и C ++ 17 стандартам ISO.

- **&#95;&#95;cplusplus** определяется как значение целочисленного литерала, при компиляции как C++ блока трансляции. В противном случае — не определено.

- **&#95;&#95;Дата&#95; &#95;**  Дата компиляции текущего файла исходного кода. Дата — строка постоянной длины литерал в формате *ммм дд гггг*. Название месяца *Mmm* совпадает со значением сокращенное название месяца в дат, созданных библиотекой времени выполнения C [asctime](../c-runtime-library/reference/asctime-wasctime.md) функции. Первый символ даты *дд* — это пространство, если значение меньше 10. Этот макрос определяется всегда.

- **&#95;&#95;ФАЙЛ&#95; &#95;**  имя текущего файла исходного кода. **&#95;&#95;ФАЙЛ&#95; &#95;**  разворачивается в символьную строку литерала. Чтобы убедиться, что отображается полный путь к файлу, используйте [/FC (полный путь из файлу исходного кода в диагностике)](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md). Этот макрос определяется всегда.

- **&#95;&#95;СТРОКИ&#95; &#95;**  определяется как integer номер строки в текущем исходном файле. Значение **&#95; &#95;строки&#95; &#95;** макрос можно изменить с помощью `#line` директива. Этот макрос определяется всегда.

- **&#95;&#95;STDC&#95; &#95;**  определены как 1 только в том случае, когда компилируется как C и если [/Za](../build/reference/za-ze-disable-language-extensions.md) указан параметр компилятора. В противном случае — не определено.

- **&#95;&#95;STDC&#95;РАЗМЕЩЕННАЯ&#95; &#95;**  определены как 1, если реализована *реализации размещенных*, поддерживающий всей необходимой библиотеки стандартных. В противном случае определяется как 0.

- **&#95;&#95;STDCPP&#95;ПОТОКОВ&#95; &#95;**  определяется как 1 только в том случае, если программа может иметь только один поток выполнения и скомпилированном как C++. В противном случае — не определено.

- **&#95;&#95;ВРЕМЯ&#95; &#95;**  время перевод предварительно обработанные записи преобразования. Время представляет собой строку символов литерал в формате *чч: мм:*, таким же, как время, возвращенное библиотекой времени выполнения C [asctime](../c-runtime-library/reference/asctime-wasctime.md) функции. Этот макрос определяется всегда.

## <a name="microsoft-specific-predefined-macros"></a>Предустановленные макросы характерные для Майкрософт

Microsoft Visual C++ поддерживает эти дополнительные предопределенные макросы.

- **&#95;&#95;ATOM&#95; &#95;**  определяется как 1, если [/favor:ATOM](../build/reference/favor-optimize-for-architecture-specifics.md) используется параметр компилятора, и компилятор должен x86 или x64. В противном случае — не определено.

- **&#95;&#95;AVX&#95; &#95;**  определяется как 1, если [/arch: AVX](../build/reference/arch-x86.md) или [/arch: avx2](../build/reference/arch-x86.md) задаются параметры компилятора и компилятор должен x86 или x64. В противном случае — не определено.

- **&#95;&#95;AVX2&#95; &#95;**  определяется как 1, если [/arch: avx2](../build/reference/arch-x86.md) используется параметр компилятора, и компилятор должен x86 или x64. В противном случае — не определено.

- **&#95;CHAR&#95;НЕПОДПИСАННЫЙ** определяется как 1, если значение по умолчанию **char** тип без знака. Это задается, если [/j (по умолчанию является тип unsigned char)](../build/reference/j-default-char-type-is-unsigned.md) используется параметр компилятора. В противном случае — не определено.

- **&#95;&#95;CLR&#95;VER** определяется как целочисленный литерал, представляющий версию среды CLR, используемой при компиляции приложения. Значение кодируется в виде `Mmmbbbbb`, где `M` является основной номер версии среды выполнения, `mm` — это дополнительный номер версии среды выполнения, и `bbbbb` — номер сборки. **&#95;&#95;CLR&#95;VER** определяется, если [/CLR](../build/reference/clr-common-language-runtime-compilation.md) используется параметр компилятора. В противном случае — не определено.

    ```cpp
    // clr_ver.cpp
    // compile with: /clr
    using namespace System;
    int main() {
       Console::WriteLine(__CLR_VER);
    }
    ```

- **&#95;Элемент УПРАВЛЕНИЯ&#95;ПОТОКА&#95;защиты** определяется как 1, если [/Guard: CF (Включение защиты потока управления)](../build/reference/guard-enable-control-flow-guard.md) используется параметр компилятора. В противном случае — не определено.

- **&#95;&#95;СЧЕТЧИК&#95; &#95;**  разворачивается для целочисленный литерал, который начинается с 0 и увеличивается на 1 каждый раз при его использовании в исходном файле или во включенных заголовках исходного файла. **&#95;&#95;СЧЕТЧИК&#95; &#95;**  запоминает свое состояние при использовании предкомпилированных заголовков. Этот макрос определяется всегда.

  В этом примере используется `__COUNTER__` назначает уникальные идентификаторы трем различным объектам одного типа. `exampleClass` Конструктор принимает целое число как параметр. В `main`, приложение объявляет три объекта типа `exampleClass`, с использованием `__COUNTER__` в качестве параметра уникального идентификатора:

    ```cpp
    // macro__COUNTER__.cpp
    // Demonstration of __COUNTER__, assigns unique identifiers to
    // different objects of the same type.
    // Compile by using: cl /EHsc /W4 macro__COUNTER__.cpp
    #include <stdio.h>

    class exampleClass {
        int m_nID;
    public:
        // initialize object with a read-only unique ID
        exampleClass(int nID) : m_nID(nID) {}
        int GetID(void) { return m_nID; }
    };

    int main()
    {
        // __COUNTER__ is initially defined as 0
        exampleClass e1(__COUNTER__);

        // On the second reference, __COUNTER__ is now defined as 1
        exampleClass e2(__COUNTER__);

        // __COUNTER__ is now defined as 2
        exampleClass e3(__COUNTER__);

        printf("e1 ID: %i\n", e1.GetID());
        printf("e2 ID: %i\n", e2.GetID());
        printf("e3 ID: %i\n", e3.GetID());

        // Output
        // ------------------------------
        // e1 ID: 0
        // e2 ID: 1
        // e3 ID: 2

        return 0;
    }
    ```

- **&#95;&#95;cplusplus&#95;cli** определяется как целочисленное литеральное значение 200406 при компиляции как C++ и [/CLR](../build/reference/clr-common-language-runtime-compilation.md) используется параметр компилятора. В противном случае — не определено. При определении  **&#95; &#95;cplusplus&#95;cli** действует на протяжении всего блока трансляции.

    ```cpp
    // cplusplus_cli.cpp
    // compile by using /clr
    #include "stdio.h"
    int main() {
       #ifdef __cplusplus_cli
          printf("%d\n", __cplusplus_cli);
       #else
          printf("not defined\n");
       #endif
    }
    ```

- **&#95;&#95;cplusplus&#95;winrt** определяется как целочисленное литеральное значение 201009 при компиляции как C++ и [/ZW (компиляция среды выполнения Windows)](../build/reference/zw-windows-runtime-compilation.md) используется параметр компилятора. В противном случае — не определено.

- **&#95;CPPRTTI** определяется как 1, если [/GR (включить сведения о типе времени выполнения)](../build/reference/gr-enable-run-time-type-information.md) используется параметр компилятора. В противном случае — не определено.

- **&#95;CPPUNWIND** определены как 1, если один или несколько из [/GX (Включить обработку исключений)](../build/reference/gx-enable-exception-handling.md), [/CLR (компиляция CLR)](../build/reference/clr-common-language-runtime-compilation.md), или [/EH (модель обработки исключений)](../build/reference/eh-exception-handling-model.md) задаются параметры компилятора. В противном случае — не определено.

- **&#95;Отладка** определяется как 1, если [/LDd](../build/reference/md-mt-ld-use-run-time-library.md), [/MDd](../build/reference/md-mt-ld-use-run-time-library.md), или [/MTd](../build/reference/md-mt-ld-use-run-time-library.md) используется параметр компилятора. В противном случае — не определено.

- **&#95;Библиотеки DLL** определяется как 1, если [/MD](../build/reference/md-mt-ld-use-run-time-library.md) или [/MDd](../build/reference/md-mt-ld-use-run-time-library.md) задать параметр компилятора (многопоточный DLL). В противном случае — не определено.

- **&#95;&#95;FUNCDNAME&#95; &#95;**  определяется как строковый литерал, содержащий [декорированное имя](../build/reference/decorated-names.md) включающей функции. Макрос определен только в пределах функции. **&#95; &#95;FUNCDNAME&#95; &#95;** макрос разворачивается не в том случае, если вы используете [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) или [/P](../build/reference/p-preprocess-to-a-file.md) параметр компилятора.

   В этом примере используется `__FUNCDNAME__`, `__FUNCSIG__`, и `__FUNCTION__` макросы для отображения сведений о функции.

   [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]

- **&#95;&#95;FUNCSIG&#95; &#95;**  определен как строковый литерал, содержащий сигнатуру включающей функции. Макрос определен только в пределах функции. **&#95; &#95;FUNCSIG&#95; &#95;** макрос разворачивается не в том случае, если вы используете [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) или [/P](../build/reference/p-preprocess-to-a-file.md) параметр компилятора. При компиляции для 64-разрядных конечных вызовах — это `__cdecl` по умолчанию. Пример использования, см. в разделе `__FUNCDNAME__` макрос.

- **&#95;&#95;ФУНКЦИЯ&#95; &#95;**  определяется как строковый литерал, содержащий внешнее имя включающей функции. Макрос определен только в пределах функции. **&#95; &#95;ФУНКЦИЯ&#95; &#95;** макрос разворачивается не в том случае, если вы используете [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) или [/P](../build/reference/p-preprocess-to-a-file.md) параметр компилятора. Пример использования, см. в разделе `__FUNCDNAME__` макрос.

- **&#95;ЦЕЛОЧИСЛЕННЫЙ&#95;MAX&#95;BITS** определяемый как целочисленное литеральное значение 64, максимальный размер (в битах) для целочисленного типа без вектора. Этот макрос определяется всегда.

   ```cpp
   // integral_max_bits.cpp
   #include <stdio.h>
   int main() {
      printf("%d\n", _INTEGRAL_MAX_BITS);
   }
   ```

- **&#95;&#95;INTELLISENSE&#95; &#95;**  определенный, как передать 1 во время компилятора IntelliSense в Интегрированной среде разработки Visual Studio. В противном случае — не определено. Этот макрос можно использовать для защиты кода компилятора IntelliSense не понимать и использовать его для переключения между сборки и компилятора IntelliSense. Дополнительные сведения см. в разделе [советы по устранению неполадок для медленная работа IntelliSense](https://blogs.msdn.microsoft.com/vcblog/2011/03/29/troubleshooting-tips-for-intellisense-slowness/).

- **&#95;ISO&#95;VOLATILE** определяется как 1, если [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) используется параметр компилятора. В противном случае — не определено.

- **&#95;ЯДРА&#95;режим** определяется как 1, если [/kernel (Создание двоичного режима ядра)](../build/reference/kernel-create-kernel-mode-binary.md) используется параметр компилятора. В противном случае — не определено.

- **&#95;M&#95;AMD64** заданы как целочисленный литерал значение 100 для компиляций, процессоров x64. В противном случае — не определено.

- **&#95;M&#95;ARM** определяется как целочисленное литеральное значение 7 для компиляций, предназначенных для процессоров ARM. В противном случае — не определено.

- **&#95;M&#95;ARM&#95;ARMV7VE** определяется как 1, если [/arch:ARMv7VE](../build/reference/arch-arm.md) параметр компилятора для компиляций, предназначенных для процессоров ARM. В противном случае — не определено.

- **&#95;M&#95;ARM&#95;FP** определяется как значение целочисленного литерала, указывающую, какие [/arch](../build/reference/arch-arm.md) был задан параметр компилятора, если целевого объекта компиляции не обрабатываются ARM. В противном случае — не определено.

  - В диапазоне 30-39, если не `/arch` был указан параметр ARM, задано значение, указывающее, по умолчанию архитектура для ARM (`VFPv3`).

  - В диапазоне 40-49, если `/arch:VFPv4` было задано.

  - См. в разделе [/arch (ARM)](../build/reference/arch-arm.md) Дополнительные сведения.

- **&#95;M&#95;ARM64** определен как 1 для компиляций, предназначенных для 64-разрядных процессоров ARM. В противном случае — не определено.

- **&#95;M&#95;CEE** определяется как 001 Если любой [/CLR (компиляция CLR)](../build/reference/clr-common-language-runtime-compilation.md) используется параметр компилятора. В противном случае — не определено.

- **&#95;M&#95;CEE&#95;ЧИСТЫЙ** устаревшими, начиная с Visual Studio 2015. Определяется как 001 Если [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md) используется параметр компилятора. В противном случае — не определено.

- **&#95;M&#95;CEE&#95;БЕЗОПАСНОМ** устаревшими, начиная с Visual Studio 2015. Определяется как 001 Если [/CLR: safe](../build/reference/clr-common-language-runtime-compilation.md) используется параметр компилятора. В противном случае — не определено.

- **&#95;M&#95;FP&#95;EXCEPT** определяется как 1, если [/fp: except](../build/reference/fp-specify-floating-point-behavior.md) или [/fp: strict](../build/reference/fp-specify-floating-point-behavior.md) используется параметр компилятора. В противном случае — не определено.

- **&#95;M&#95;FP&#95;БЫСТРЫЙ** определяется как 1, если [/fp:fast](../build/reference/fp-specify-floating-point-behavior.md) используется параметр компилятора. В противном случае — не определено.

- **&#95;M&#95;FP&#95;точные ВЫЧИСЛЕНИЯ** определяется как 1, если [/fp: точное](../build/reference/fp-specify-floating-point-behavior.md) используется параметр компилятора. В противном случае — не определено.

- **&#95;M&#95;FP&#95;STRICT** определяется как 1, если [/fp: strict](../build/reference/fp-specify-floating-point-behavior.md) используется параметр компилятора. В противном случае — не определено.

- **&#95;M&#95;IX86** заданы как целочисленный литерал значение 600 для компиляций, процессоров x86. Этот макрос не определен для x64 или целевых сред компиляции ARM.

- **&#95;M&#95;IX86&#95;FP** определяется как целочисленное литеральное значение, указывающее [/arch](../build/reference/arch-arm.md) параметра компилятора, который был установлен, или значение по умолчанию. Этот макрос определяется всегда, когда целью компиляции являются x86 процессора. В противном случае — не определено. Если определен, задается значение:

  - 0, если `/arch:IA32` параметр компилятора был установлен.

  - 1, если `/arch:SSE` параметр компилятора был установлен.

  - 2, если `/arch:SSE2`, `/arch:AVX` или `/arch:AVX2` параметр компилятора был установлен. Это значение по умолчанию, если `/arch` не указан параметр компилятора. Когда `/arch:AVX` указано, макрос **&#95; &#95;AVX&#95; &#95;** также определяется. Когда `/arch:AVX2` указано, оба **&#95; &#95;AVX&#95; &#95;** и **&#95; &#95;AVX2&#95; &#95;** также определены.

  - См. в разделе [/arch (x86)](../build/reference/arch-x86.md) Дополнительные сведения.

- **&#95;M&#95;X64** заданы как целочисленный литерал значение 100 для компиляций, процессоров x64. В противном случае — не определено.

- **&#95;УПРАВЛЯЕМЫЕ** определяется как 1, если [/CLR](../build/reference/clr-common-language-runtime-compilation.md) используется параметр компилятора. В противном случае — не определено.

- **&#95;MSC&#95;ПОСТРОЕНИЯ** определяется как целочисленный литерал, содержащий элемент номера редакции номера версии компилятора. Номер редакции — это четвертый элемент номера версии с разделителями точками. Например, 15.00.20706.01 номер версии компилятора Visual C++  **&#95;MSC&#95;ПОСТРОЕНИЯ** макрос принимает значение 1. Этот макрос определяется всегда.

- **&#95;MSC&#95;расширения** определяется как 1, если [/Ze (включить расширения языка)](../build/reference/za-ze-disable-language-extensions.md) задать параметр компилятора, который используется по умолчанию. В противном случае — не определено.

- **&#95;MSC&#95;полный&#95;VER** определяется как целочисленный литерал, кодирует основной номер, вспомогательная и создавать элементы числа номера версии компилятора. Основной номер — это первый элемент номера версии с разделителями точками, дополнительный номер — второй элемент, и номер сборки — третий элемент. Например, 15.00.20706.01 номер версии компилятора Visual C++  **&#95;MSC&#95;полный&#95;VER** макрос принимает значение 150020706. Введите `cl /?` из командной строки для просмотра номера версии компилятора. Этот макрос определяется всегда.

- **&#95;MSC&#95;VER** определяется как целочисленный литерал, кодирующий количество элементов основной и дополнительный номера версии компилятора. Основной номер — это первый элемент номера версии с разделителями точками и дополнительный номер — второй элемент. Например, если номер версии компилятора Visual C++ 17.00.51106.1  **&#95;MSC&#95;VER** макрос возвращает значение 1700. Введите `cl /?` из командной строки для просмотра номера версии компилятора. Этот макрос определяется всегда.

   |Версия Visual Studio|&AMP;#95;MSC&AMP;#95;VER|
   |-|-|
   |Visual Studio 6.0|1200|
   |Visual Studio .NET 2002 (7.0)|1300|
   |Visual Studio .NET 2003 (7.1)|1310|
   |Visual Studio 2005 (8.0)|1400|
   |Visual Studio 2008 (9.0)|1500|
   |Visual Studio 2010 (10.0)|1600|
   |Visual Studio 2012 (11.0)|1700|
   |Visual Studio 2013 (12.0)|1800|
   |Visual Studio 2015 (14.0)|1900 г.|
   |Visual Studio 2017 RTW (15.0)|1910|
   |Visual Studio 2017 версия 15.3|1911|
   |Visual Studio 2017 версии 15.5|1912|
   |Visual Studio 2017 версии 15.6|1913|
   |Visual Studio 2017 версии 15.7|1914|

   Для проверки версии компилятора или обновления в данной версии Visual Studio или после, используйте **>=** оператор (больше или равно) для сравнения  **&#95;MSC&#95;VER** от известных Версия. Если у вас есть несколько версий для сравнения в виде взаимно исключают друг друга, мы рекомендуем порядок сравнения по убыванию номера версии. Например этот код проверяет для компиляторов, выпущена в Visual Studio 2015 и более поздних версиях, компиляторы, выпущена в или после Visual Studio 2013, затем принимает действие для всех компиляторов, выпущенных до Visual Studio 2013:

   ```cpp
   #if _MSC_VER >= 1900
   // . . .
   #elif _MSC_VER >= 1800
   // . . .
   #else
   // . . .
   #endif
   ```

   Дополнительные сведения см. в разделе [версии компилятора Visual C++](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/visual-c-compiler-version/) в блоге группы Visual C++.

- **&#95;MSVC&#95;LANG** определяется как целочисленный литерал, указывающее стандарта языка C++, предназначенные для компилятора. При компиляции как C++, макрос является 201402L целочисленное литеральное значение, если [/std: c ++ 14](../build/reference/std-specify-language-standard-version.md) используется параметр компилятора или по умолчанию; ему присваивается 201703 L Если [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md) установлен параметр компилятора; а он становится равным выше, неопределенное значение, если [/std: c ++ последнюю](../build/reference/std-specify-language-standard-version.md). В противном случае макрос не определен. **&#95;MSVC&#95;LANG** макрос и [/STD (укажите стандартной версии языка)](../build/reference/std-specify-language-standard-version.md) параметры компилятора, доступные, начиная с Visual Studio 2015 с обновлением 3.

- **&#95;&#95;MSVC&#95;среды ВЫПОЛНЕНИЯ&#95;ПРОВЕРЯЕТ** определены как 1, если в одном из [/RTC](../build/reference/rtc-run-time-error-checks.md) задать параметры компилятора. В противном случае — не определено.

- **&#95;MT** определяется как 1, если [/MD или/MDd](../build/reference/md-mt-ld-use-run-time-library.md) (Многопоточная DLL) или [/MT или/MTd](../build/reference/md-mt-ld-use-run-time-library.md) указывается (многопоточный). В противном случае — не определено.

- **&#95;СОБСТВЕННЫЙ&#95;WCHAR&#95;T&#95;ОПРЕДЕЛЕННЫЕ** определяется как 1, если [/Zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) используется параметр компилятора. В противном случае — не определено.

- **&#95;OPENMP** определяется как целочисленный литерал 200203, представляющий дату спецификации OpenMP, реализуемой Visual C++, в том случае, если [/OpenMP (Включение поддержки OpenMP 2.0)](../build/reference/openmp-enable-openmp-2-0-support.md) используется параметр компилятора. В противном случае — не определено.

   ```cpp
   // _OPENMP_dir.cpp
   // compile with: /openmp
   #include <stdio.h>
   int main() {
      printf("%d\n", _OPENMP);
   }
   ```

- **&#95;PREFAST&#95;**  определяется как 1, если [/ analyze](../build/reference/analyze-code-analysis.md) используется параметр компилятора. В противном случае — не определено.

- **&#95;&#95;Метка времени&#95; &#95;**  определяется как строковый литерал, содержащий дату и время последнего изменения текущего файла исходного кода, в форме длина сокращенное, константы, возвращаемых библиотекой времени выполнения C [asctime](../c-runtime-library/reference/asctime-wasctime.md) функции, например, `Fri 19 Aug 13:32:58 2016`. Этот макрос определяется всегда.

- **&#95;VC&#95;NODEFAULTLIB** определяется как 1, если [/Zl (Omit Default Library Name)](../build/reference/zl-omit-default-library-name.md) используется параметр компилятора. В противном случае — не определено.

- **&#95;WCHAR&#95;T&#95;ОПРЕДЕЛЕННЫЕ** определяется как 1, если значение по умолчанию [/Zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) используется параметр компилятора. **&#95;WCHAR&#95;T&#95;ОПРЕДЕЛЕННЫЕ** макрос определен, но не имеет значения при `/Zc:wchar_t-` задан параметр компилятора, и **wchar_t** определяется в системном файле заголовка, включенных в ваш проект. В противном случае — не определено.

- **&#95;Win32** определяемый как 1, если целевого объекта компиляции ARM 32-разрядной, 64-разрядная ARM, x86, или x 64. В противном случае — не определено.

- **&#95;Win64** определены как 1, если 64-разрядная ARM или x64 целевого объекта компиляции. В противном случае — не определено.

- **&#95;WINRT&#95;DLL** определен как 1, если, скомпилированном как C++ и оба [/ZW (компиляция среды выполнения Windows)](../build/reference/zw-windows-runtime-compilation.md) и [/LD или /LDd](../build/reference/md-mt-ld-use-run-time-library.md) задаются параметры компилятора. В противном случае — не определено.

 Макросы препроцессора, используемые для определения версии библиотеки ATL или MFC не являются предопределенными компилятором. Эти макросы определяются в заголовках библиотеки, поэтому они не определены в директивы препроцессора, прежде чем требуемый заголовок включен.

- **&#95;ATL&#95;VER** определенные в \<atldef.h > как целочисленный литерал, кодирующий ATL номер версии.

- **&#95;MFC&#95;VER** определенные в \<afxver_.h > как целочисленный литерал, кодирующий номером версии MFC.

## <a name="see-also"></a>См. также

[Макросы (C/C++)](../preprocessor/macros-c-cpp.md)<br/>
[Операторы препроцессора](../preprocessor/preprocessor-operators.md)<br/>
[Директивы препроцессора](../preprocessor/preprocessor-directives.md)