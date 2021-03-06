---
title: 'Практическое: преобразование цикла OpenMP, использующего отмену для использования среды выполнения с параллелизмом | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, cancellation
- cancellation, converting from OpenMP to the Concurrency Runtime
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3cb0d57edae11acd076a9be2bfed18ec2140bb7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373546"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-cancellation-to-use-the-concurrency-runtime"></a>Практическое руководство. Преобразование цикла OpenMP, использующего отмену для использования среды выполнения с параллелизмом

Некоторые параллельные циклы не требуют выполнения всех итераций. Например алгоритм, который выполняет поиск значения можно завершить работу, когда значение найдено. OpenMP не предоставляет механизм для выхода из параллельного цикла. Тем не менее можно использовать логическое значение или флаг, чтобы включить итерации цикла, чтобы указать, что решение найдено. Среда выполнения с параллелизмом предоставляет функциональность, позволяющую одну задачу для отмены других задач, которые еще не запущено.

В этом примере демонстрируется преобразование OpenMP [параллельных](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[для](../../parallel/openmp/reference/for-openmp.md) цикл, который не требуется для всех итераций, выполняемых с использованием механизма отмены среда выполнения с параллелизмом.

## <a name="example"></a>Пример

В этом примере используется OpenMP и среда выполнения с параллелизмом для реализации параллельную версию [std::any_of](../../standard-library/algorithm-functions.md#any_of) алгоритм. OpenMP версию этого примера использует флаг для координации всех итераций параллельного цикла, что условие было выполнено. Версии, который использует среда выполнения с параллелизмом использует [Concurrency::structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) метод общей операции при выполнении условия.

[!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]

В этом примере формируются следующие данные:

```Output
Using OpenMP...
9114046 is in the array.
Using the Concurrency Runtime...
9114046 is in the array.
```

В версии, использующей OpenMP выполните все итерации цикла, даже если этот флаг имеет значение. Кроме того Если у задачи есть дочерние задачи, флаг также пришлось бы быть доступны для этих дочерних задач для отмены связи. В среде выполнения с параллелизмом когда группа задач отменяется, среда выполнения отменяет все дерево работы, включая дочерние задачи. [Concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) алгоритм использует задачи для выполнения работы. Таким образом когда одна итерация цикла отменяет корневую задачу, отменяется все дерево вычислений. Среда выполнения не приводит к запуску новых задач, при отмене дерева работы. Однако среда выполнения позволяет задачи, которые уже запущены до конца. Таким образом, в случае использования `parallel_for_each` алгоритм, активные итерации цикла можно очистить свои ресурсы.

В этом примере обе версии Если массив содержит более одной копии значения для поиска, несколько итераций цикла можно одновременно задавать результат и отменить всю операцию. Можно использовать примитив синхронизации, например критическую секцию, если ваши проблема требует, что только одна задача выполняет работу, когда условие выполняется.

Можно также использовать обработку исключений для отмены задачи, использующие PPL. Дополнительные сведения об отмене см. в разделе [Отмена в PPL](cancellation-in-the-ppl.md).

Дополнительные сведения о `parallel_for_each` и другие параллельные алгоритмы, см. в разделе [параллельные алгоритмы](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Компиляция кода

Скопируйте код примера и вставьте его в проект Visual Studio или вставьте его в файл с именем `concrt-omp-parallel-any-of.cpp` и выполните следующую команду в окне командной строки Visual Studio.

**CL.exe/EHsc/OpenMP concrt-omp параллельного any-of.cpp**

## <a name="see-also"></a>См. также

[Переход от OpenMP к среде выполнения с параллелизмом](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Отмена в библиотеке параллельных шаблонов](cancellation-in-the-ppl.md)<br/>
[Параллельные алгоритмы](../../parallel/concrt/parallel-algorithms.md)

