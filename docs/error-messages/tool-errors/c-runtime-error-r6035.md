---
title: C R6035 ошибку во время выполнения | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6035
dev_langs:
- C++
helpviewer_keywords:
- R6035
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 081e878e6bc96edc734f84e0e4efecee607135b5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026717"
---
# <a name="c-runtime-error-r6035"></a>C R6035 ошибку во время выполнения

Microsoft исполняемой библиотеки Visual C++, ошибка R6035 - модуля в этом приложении выполняется инициализация модуля глобальный файл cookie безопасности при активном как функция, использующая этот файл.  Вызовите __security_init_cookie ранее.

[__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md) должен вызываться перед первым использованием файла cookie глобальной безопасности.

Файл cookie глобальной безопасности используется для защиты от переполнения буфера в коде, скомпилированном с [/GS (проверка безопасности буфера)](../../build/reference/gs-buffer-security-check.md) и в коде, который используется структурная обработка исключений. По сути при входе в функцию, защищенную от переполнения куки-файл помещается в стек, и при выходе значение в стеке сравнивается с глобальным cookie-файлом. Любое различие между ними указывает, что произошло переполнение буфера и приводит к немедленному завершению работы программы.

Ошибка R6035 указывает, что вызов `__security_init_cookie` было внесено после защищенную функцию. Если необходимо продолжить выполнение, так как файл cookie в стеке больше не соответствует глобальному файлу cookie, будет обнаружено ложное переполнение буфера.

Рассмотрим следующий пример DLL. Точка входа библиотеки DLL установлена в DllEntryPoint компоновщика [/Entry (символ точки входа)](../../build/reference/entry-entry-point-symbol.md) параметр. Это позволяет обойти инициализацию CRT, в которой обычно будет инициализировать файл cookie глобальной безопасности, поэтому необходимо вызвать метод непосредственно в Библиотеки `__security_init_cookie`.

```
// Wrong way to call __security_init_cookie
DllEntryPoint(...) {
   DllInitialize();
   ...
   __try {
      ...
   } __except()... {
      ...
   }
}

void DllInitialize() {
   __security_init_cookie();
}
```

В этом примере возникнет ошибка R6035, так как DllEntryPoint использует структурированной обработки исключений и поэтому использует файл cookie безопасности для обнаружения ошибок переполнения буфера. К моменту вызова DllInitialize файл cookie глобальной безопасности уже помещен в стеке.

В этом примере демонстрируется правильный способ использования:

```
// Correct way to call __security_init_cookie
DllEntryPoint(...) {
   __security_init_cookie();
   DllEntryHelper();
}

void DllEntryHelper() {
   ...
   __try {
      ...
   } __except()... {
      ...
   }
}
```

В этом случае DllEntryPoint не защищена от переполнения буфера (он содержит не буферы локальных строк и не использует структурированной обработки исключений); Поэтому он может безопасно вызывать `__security_init_cookie`. Затем вызывается вспомогательная функция, которая защищена.

> [!NOTE]
>  Сообщение об ошибке R6035 — только для созданных x86 отладки CRT и только для структурированной обработки исключений, но условие ошибки на всех платформах, а также для всех форм исключение обрабатывает, например C++ EH.

## <a name="see-also"></a>См. также

[Функции безопасности в MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/)