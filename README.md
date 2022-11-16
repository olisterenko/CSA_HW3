### Листеренко Ольга Руслановна ###
### БПИ 217 ###
  
### Вариант 12 ###
### Задача ###
Разработать программы на языках программирования C и Ассемблер, выполняющие вычисления над числами с плавающей точкой. Разработанные программы должны принимать числа в допустимом диапазоне. Например, нужно учитывать области определения и допустимых
значений, если это связано с условием задачи.  

Разработать программу, вычисляющую с помощью степенного ряда
с точностью не хуже 0,05% значение функции tan(x) для заданного
параметра x.
    
### Тесты ###
Все программы выдают одинаковый результат и были протестированы на следующих примерах:  

#### 1 тест ####
  
##### Результат (одинаковый во всех программах) #####
  
#### 2 тест ####
  
##### Результат (одинаковый во всех программах) #####
  
#### 3 тест ####
  
##### Результат (одинаковый во всех программах) #####
  
#### 4 тест ####
  
##### Результат (одинаковый во всех программах) #####
  

#### 5 тест ####
    

##### Результат (одинаковый во всех программах) #####
    

#### 6 тест ####
  
##### Результат (одинаковый во всех программах) #####
  

#### 7 тест ####
  

##### Результат (одинаковый во всех программах) #####
  
#### 8 тест ####
  
##### Результат (одинаковый во всех программах) #####
  

### Программа на C ###
Код находится в папке Code_in_C.  
  
### Оптимизированная программа на ассембелере с комментариями ### 
Код находится в папке Assembly_modified.  
   
### Программа на ассембелере от компилятора ### 
Код находится в файле Assembly_from_C.  
Код получен путем компиляции кода на C следующим образом:  
gcc -masm=intel -fno-asynchronous-unwind-tables -fno-jump-tables -fno-stack-protector -fno-exceptions ./file_name.c -S -o ./file_name.s
  
### Информация, подтверждающая выполнение задания на 8 ###
В программе обрабатываются строки длиной до 1000 символов. Если строка в файле состоит из более, чем 1000 символов, то она обрабатывается до первой тысячи.  
Приведен код на C на оценку 8.  
Добавлены комментарии.  
Удалены из конца кода строки ниже ret, а из начала информация о файле, из которой получили код на ассемблере.  
Убраны лишние макросы, в том числе endbr64.    
Удалены cdqe и nop, добавленные компилятором для дополнения.  
Удалены промежуточные присваивания на подобии:  
<img width="151" alt="image" src="https://user-images.githubusercontent.com/57359954/200162263-9bbf45f8-cef4-4c22-a298-bba1cd8c2154.png">  
<img width="180" alt="image" src="https://user-images.githubusercontent.com/57359954/200162287-fd5b32b1-9454-4762-a81c-19b18b748944.png">  
или  
<img width="206" alt="image" src="https://user-images.githubusercontent.com/57359954/200162943-fcd441b2-3f04-4593-894f-d792313ba688.png">  
<img width="184" alt="image" src="https://user-images.githubusercontent.com/57359954/200162977-5a3a157a-adde-41ab-81ab-32c99dbe74d8.png">  
или  
<img width="204" alt="image" src="https://user-images.githubusercontent.com/57359954/200165522-b875b501-484c-48f3-afde-2f32024b0bb1.png">  
<img width="205" alt="image" src="https://user-images.githubusercontent.com/57359954/200165560-70d15e6e-c221-4955-947d-85e72592cc69.png">  
или  
<img width="229" alt="image" src="https://user-images.githubusercontent.com/57359954/200772055-505ef661-547a-4cee-b09e-61b2be62f3d8.png">  
<img width="230" alt="image" src="https://user-images.githubusercontent.com/57359954/200772189-1ac31128-dd15-45fa-8642-7b107632555c.png">    
Программа протестирована на приведенных тестах. Результаты совпадают с результатами программы на C.  
В программе использованы следующие функции с аргументами: ввод из файла (на вход имя файла), вывод в файл (на вход имя файла), генерация случайной строки(на вход n).  
Использованы локальные переменные n, i, end, start, ind_ans, flag, j, choice.  
Добавлены комментарии о передаче параметров (фактических и формальных).
Программа протестирована на приведенных тестах. Результаты совпадают с результатами программы на C.  
-4[rbp] заменен на регистр r12d в основной программе и в generate — это i. В form_ans заменен на r13d — это start. 
-12[rbp] заменен на r10d в form_ans — это ind_ans.  
-16[rbp] заменен на регистр ebx. В form_ans это i.  
-20[rbp] заменен на регистр r13d в generate — это n. В form_ans заменен на r11d — это j.  
-24[rbp] заменен на регистр r15d в form_ans — end.  
-28[rbp] заменен на регистр r13d. В основной программе это choice.  
-48[rbp] заменен на регистр r14. В основной программе это argv.  
myfile[rip] заменен на регистр r12.  
Комментарии об использовании регистров добавлены.  
Программа протестирована на приведенных тестах. Результаты совпадают с результатами программы на C.  
Необработанный файл functions.s занимает 272 строки, обработанный — 266. Начальный main.s — 154 строки, конечный — 137. В оба файла так же были добавлены пустые строки для улучшения читаемости кода. Можно говорить о заметном сокращении кода.  
Программа реализована в виде двух единиц компиляции.  
Реализовано использование файлов. В файле для чтения находится одна строка (читаются первые 1000 символов). Имена файлов являются аргументами командной строки. Первый — файл, из которого читаем, второй — в который записываем: "./program.exe input.txt output.txt". Проверяется количество аргументов, а также существование файла для чтения.  
Подготовлены файлы для тестирования. Расположены в папке Tests.  
В программу добавлен генератор случайной строки длиной от 10 до 1000 (включительно и на усмотрение пользователя). Выбор способа получения строки выполняется через консоль.  
  
Производится замер времени выполнения 3000000 формирований ответа.  
#### Результаты замеров на тестах 5, 6 и 7 ####  
##### 5 тест #####
(1000 символов)  
69 секунд необработанный ассемблер.  
64 секунд оптимизированный ассемблер.  

##### 6 тест #####
(10 символов)  
63 секунд необработанный ассемблер.  
63 секунд оптимизированный ассемблер.  

##### 7 тест #####
(345 символов)  
65 секунд необработанный ассемблер.  
63 секунд оптимизированный ассемблер.  
