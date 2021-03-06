# [OpenMP в Visual C++](openmp-in-visual-cpp.md)
# [API OpenMP C и C++](openmp-c-and-cpp-application-program-interface.md)
## [Содержание](contents.md)
## [1. Введение](1-introduction.md)
### [1.1 Область](1-1-scope.md)
### [1.2 Определение терминов](1-2-definition-of-terms.md)
### [1.3 Модель выполнения](1-3-execution-model.md)
### [1.4 Совместимость](1-4-compliance.md)
### [1.5 Ссылки на нормативные документы](1-5-normative-references.md)
### [1.6 Организация](1-6-organization.md)
## [2. Директивы](2-directives.md)
### [2.1 Формат директивы](2-1-directive-format.md)
### [2.2 Условная компиляция](2-2-conditional-compilation.md)
### [2.3 Конструкция parallel](2-3-parallel-construct.md)
### [2.4 Конструкции совместной работы](2-4-work-sharing-constructs.md)
#### [2.4.1 Конструкция for](2-4-1-for-construct.md)
#### [2.4.2 Конструкция sections](2-4-2-sections-construct.md)
#### [2.4.3 Конструкция single](2-4-3-single-construct.md)
### [2.5 Комбинированные параллельные конструкции совместной работы](2-5-combined-parallel-work-sharing-constructs.md)
#### [2.5.1 Конструкция parallel for](2-5-1-parallel-for-construct.md)
#### [2.5.2 Конструкция parallel sections](2-5-2-parallel-sections-construct.md)
### [2.6 Ведущие директивы и директивы синхронизации](2-6-master-and-synchronization-directives.md)
#### [2.6.1 Конструкция master](2-6-1-master-construct.md)
#### [2.6.2 Конструкция critical](2-6-2-critical-construct.md)
#### [2.6.3 Директива barrier](2-6-3-barrier-directive.md)
#### [2.6.4 Конструкция atomic](2-6-4-atomic-construct.md)
#### [2.6.5 Директива flush](2-6-5-flush-directive.md)
#### [2.6.6 Конструкция ordered](2-6-6-ordered-construct.md)
### [2.7 Среда данных](2-7-data-environment.md)
#### [2.7.1 Директива threadprivate](2-7-1-threadprivate-directive.md)
#### [2.7.2 Предложения атрибутов совместного использования данных](2-7-2-data-sharing-attribute-clauses.md)
##### [2.7.2.1 private](2-7-2-1-private.md)
##### [2.7.2.2 firstprivate](2-7-2-2-firstprivate.md)
##### [2.7.2.3 lastprivate](2-7-2-3-lastprivate.md)
##### [2.7.2.4 shared](2-7-2-4-shared.md)
##### [2.7.2.5 default](2-7-2-5-default.md)
##### [2.7.2.6 reduction](2-7-2-6-reduction.md)
##### [2.7.2.7 copyin](2-7-2-7-copyin.md)
##### [2.7.2.8 copyprivate](2-7-2-8-copyprivate.md)
### [2.8 Привязка директив](2-8-directive-binding.md)
### [2.9 Директива Nesting](2-9-directive-nesting.md)
## [3. Функции библиотеки среды выполнения](3-run-time-library-functions.md)
### [3.1 Функции среды выполнения](3-1-execution-environment-functions.md)
#### [3.1.1 Функция omp_set_num_threads](3-1-1-omp-set-num-threads-function.md)
#### [3.1.2 Функция omp_get_num_threads](3-1-2-omp-get-num-threads-function.md)
#### [3.1.3 Функция omp_get_max_threads](3-1-3-omp-get-max-threads-function.md)
#### [3.1.4 Функция omp_get_thread_num](3-1-4-omp-get-thread-num-function.md)
#### [3.1.5 Функция omp_get_num_procs](3-1-5-omp-get-num-procs-function.md)
#### [3.1.6 Функция omp_in_parallel](3-1-6-omp-in-parallel-function.md)
#### [3.1.7 Функция omp_set_dynamic](3-1-7-omp-set-dynamic-function.md)
#### [3.1.8 Функция omp_get_dynamic](3-1-8-omp-get-dynamic-function.md)
#### [3.1.9 Функция omp_set_nested](3-1-9-omp-set-nested-function.md)
#### [3.1.10 Функция omp_get_nested](3-1-10-omp-get-nested-function.md)
### [3.2 Функции блокировки](3-2-lock-functions.md)
#### [3.2.1 Функции omp_init_lock и omp_init_nest_lock](3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md)
#### [3.2.2 Функции omp_destroy_lock и omp_destroy_nest_lock](3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md)
#### [3.2.3 Функции omp_set_lock и omp_set_nest_lock](3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md)
#### [3.2.4 Функции omp_unset_lock и omp_unset_nest_lock](3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md)
#### [3.2.5 Функции omp_test_lock и omp_test_nest_lock](3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md)
### [3.3 Процедуры расписания](3-3-timing-routines.md)
#### [3.3.1 Функция omp_get_wtime](3-3-1-omp-get-wtime-function.md)
#### [3.3.2 Функция omp_get_wtick](3-3-2-omp-get-wtick-function.md)
## [4. Переменные среды](4-environment-variables.md)
### [4.1 OMP_SCHEDULE](4-1-omp-schedule.md)
### [4.2 OMP_NUM_THREADS](4-2-omp-num-threads.md)
### [4.3 OMP_DYNAMIC](4-3-omp-dynamic.md)
### [4.4 OMP_NESTED](4-4-omp-nested.md)
## [A. Примеры](a-examples.md)
### [A.1 Параллельное выполнение простого цикла](a-1-executing-a-simple-loop-in-parallel.md)
### [A.2 Задание условной компиляции](a-2-specifying-conditional-compilation.md)
### [A.3 Использование параллельных регионов](a-3-using-parallel-regions.md)
### [A.4 Использование предложения nowait](a-4-using-the-nowait-clause.md)
### [A.5 Использование директивы critical](a-5-using-the-critical-directive.md)
### [A.6 Использование предложения lastprivate](a-6-using-the-lastprivate-clause.md)
### [A.7 Использование предложения reduction](a-7-using-the-reduction-clause.md)
### [A.8 Указание параллельных разделов](a-8-specifying-parallel-sections.md)
### [A.9 Использование отдельных директив](a-9-using-single-directives.md)
### [A.10 Задание последовательного упорядочивания](a-10-specifying-sequential-ordering.md)
### [A.11 Задание фиксированного количества потоков](a-11-specifying-a-fixed-number-of-threads.md)
### [A.12 Использование директивы atomic](a-12-using-the-atomic-directive.md)
### [A.13 Использование директивы flush со списком](a-13-using-the-flush-directive-with-a-list.md)
### [A.14 Использование директивы flush без списка](a-14-using-the-flush-directive-without-a-list.md)
### [A.15 Определение количества используемых потоков](a-15-determining-the-number-of-threads-used.md)
### [A.16 Использование блокировок](a-16-using-locks.md)
### [A.17 Использование вкладываемых блокировок](a-17-using-nestable-locks.md)
### [A.18 Вложенные директивы for](a-18-nested-for-directives.md)
### [A.19 Примеры неправильного вложения директив совместной работы](a-19-examples-showing-incorrect-nesting-of-work-sharing-directives.md)
### [A.20 Привязка директив barrier](a-20-binding-of-barrier-directives.md)
### [A.21 Ограничение переменных с использованием предложения private](a-21-scoping-variables-with-the-private-clause.md)
### [A.22 Использование предложения default(none)](a-22-using-the-default-none-clause.md)
### [A.23 Примеры директивы ordered](a-23-examples-of-the-ordered-directive.md)
### [A.24 Примеры предложения private](a-24-example-of-the-private-clause.md)
### [A.25 Примеры предложения атрибута данных copyprivate](a-25-examples-of-the-copyprivate-data-attribute-clause.md)
### [A.26 Использование директивы threadprivate](a-26-using-the-threadprivate-directive.md)
### [A.27 Использование массивов переменной длины C99](a-27-use-of-c99-variable-length-arrays.md)
### [A.28 Использование предложения num_threads](a-28-use-of-num-threads-clause.md)
### [A.29 Использование конструкций совместной работы в конструкции critical](a-29-use-of-work-sharing-constructs-inside-a-critical-construct.md)
### [A.30 Использование повторного закрытия](a-30-use-of-reprivatization.md)
### [A.31 Потокобезопасные функции блокировки](a-31-thread-safe-lock-functions.md)
## [B. Заглушки для функций библиотеки среды выполнения](b-stubs-for-run-time-library-functions.md)
## [C. Грамматика OpenMP C и C++](c-openmp-c-and-cpp-grammar.md)
### [C.1 Нотация](c-1-notation.md)
### [C.2 Правила](c-2-rules.md)
## [D. Использование предложения schedule](d-using-the-schedule-clause.md)
## [E. Поведения, определяемые реализацией, в OpenMP C/C++](e-implementation-defined-behaviors-in-openmp-c-cpp.md)
## [F. Новые функции и разъяснения в версии 2.0](f-new-features-and-clarifications-in-version-2-0.md)
# [Ссылки](reference/toc.md)