### Листеренко Ольга Руслановна ###
### БПИ 217 ###
  
### Вариант 12 ###
### Задача ###
Разработать программы на языках программирования C и Ассемблер, выполняющие вычисления над числами с плавающей точкой. Разработанные программы должны принимать числа в допустимом диапазоне. Например, нужно учитывать области определения и допустимых значений, если это связано с условием задачи.  

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
В программе ищется значение тангенса для числа, модуль которого меньше pi/2.  
Числа Бернулли и факториалы описаны до n = 20, т.к. факториалы чисел больше 20 уже не помещаются в unsigned long long. Поэтому степенной ряд вычисляется до 10 члена.  
Приведен код на C на оценку 8.  
Добавлены комментарии.  
Удалены из конца кода строки ниже ret, а из начала информация о файле, из которой получили код на ассемблере.  
Убраны лишние макросы, в том числе endbr64.    
Удалены cdqe и nop, добавленные компилятором для дополнения.  
Удалены промежуточные присваивания на подобии:  
![image](https://user-images.githubusercontent.com/57359954/203371590-a1805288-767c-47fa-8b19-54ffaa3db3ca.png)  
![image](https://user-images.githubusercontent.com/57359954/203373413-ff75e846-8ec8-4a3f-b45b-f199d4c03a00.png)  
или  
![image](https://user-images.githubusercontent.com/57359954/203594905-dd3ddd84-1327-4d5e-9b28-17e57f3284ce.png)  
![image](https://user-images.githubusercontent.com/57359954/203594996-5b6cd3a9-ce43-43eb-b11b-6626f2262eec.png)  
или  
![image](https://user-images.githubusercontent.com/57359954/203595748-b9d27f55-822a-49f4-8cdd-882b09e0abbd.png)  
![image](https://user-images.githubusercontent.com/57359954/203595818-74e132dd-2191-401e-b781-1920b93dcdae.png)  
или  
![image](https://user-images.githubusercontent.com/57359954/203599270-ba9b11d9-3b42-46f3-bb2b-980cff03ef33.png)  
![image](https://user-images.githubusercontent.com/57359954/203599385-76005cfe-1ba4-4fd4-89d0-6a5c651c7928.png)  

Программа протестирована на приведенных тестах. Результаты совпадают с результатами программы на C.  
В программе использованы следующие функции с аргументами: ввод из файла (на вход имя файла), вывод в файл (на вход имя файла, начальное значение, ответ, точный ответ, длительность вычислений), тангенс (на вход x).  
Использованы локальные переменные myfile, i, end, start, x, ans, choice.  
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
