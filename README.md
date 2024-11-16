  
# Строки в С++ 

### Внимание, анекдот!

> — Вводите все через массивы char, никаких string.
> 
> — Почему?
> 
> — Потому что string — это для счастливых людей, а мы в МГТУ.



Текстовые строки в С++ могут быть реализованы в одном из двух видов:
<div align="center">
<img src="https://github.com/user-attachments/assets/f060f13c-de09-4393-bc5c-1ae00a717187" width="350px">
</div>

* __первый__ предполагает, что мы студенты МГТУ и строка определяется как символьный массив, который завершается нулевым символом ( '\0')
* __второй__ является частью библиотеки классов => не встроенный тип <=> херня, переделывай

-----
  
### Чтение наших строк с клавиатуры

----
<div>
<table align="center">
  <tr>
    <td>
     <table>
        <tr>
            <th>$${\color{red}ЗАПРЕЩАЮ}$$❌</th>
            <th>$${\color{green}РАЗРЕШАЮ}$$✔️</th>
        </tr>
        <tr>
            <td>
          
```cpp
#include <iostream>
          
int main()
{
char str[80];
          
std::cin >> str;
          
std::cout << str;
          
return 0;
}
```
</td>
     <td>
          
```cpp
#include <iostream>
          
int main()
{
char str[80];
          
std::cin.getline(str, 80);
          
std::cout << str;
          
return 0;
}
```
</td>
        </tr>
      </table>
 </td>
<td style="padding-left: 20px;">
    <img src="https://github.com/user-attachments/assets/22411220-6d0c-4a36-8592-dac9f2a3af45" width="250px">
</td>
</tr> </table>
</div>

Почему так? В варианте слева программа формально корректна, __НО__ оператор `>>` прекращает считывание строки, как только встречает символ `пробела`,`табуляции`, `новой строки`

А во втором примере `cin.getline()` позволяет считывать строки, включая пробелы. Если формально описывать ее функционал, то она извлекает данные из входного потока до строкового разделителя, который не записывается в получившийся массив данных.

----

### Функции для работы с текстовыми строками  
-----

| Функция | Заголовок | Описание | Пример использования |
| ----------- | ----------- | ----------- | ----------- |
| `strcpy(s1,s2)`    | `<cstring>`   | Копирование строки s2 в строку s1  | [взглянуть](https://github.com/Ms1black/cstring-lecture/blob/strcpy/example.cpp) 🔞|
| `strcat(s1,s2)`    | `<cstring>`   | Строка s2 присоединяется к строке s1  | [взглянуть](https://github.com/Ms1black/cstring-lecture/blob/strcat/example.cpp) 🔞|
| `strcmp(s1,s2)`    | `<cstring>`   | Сравнение строк s1 и s2: если строки равны, возвращается значение 0  | [взглянуть](https://github.com/Ms1black/cstring-lecture/blob/strcmp/example.cpp) 🔞|
| `strchr(s1,ch)`    | `<cstring>`   | Указатель на первую позицию символа ch в строке s  | [взглянуть](https://github.com/Ms1black/cstring-lecture/blob/strchr/example.cpp) 🔞|
| `strlen(s)`    | `<cstring>`   | Возвращает длину строки, указанной аргументом s  | [взглянуть](https://github.com/Ms1black/cstring-lecture/blob/strlen/example.cpp) 🔞|
| `atoi(s)`    | `<cstdlib>`   | Преобразование состоящей из цифр строки s в целое число типа int  | [взглянуть](https://github.com/Ms1black/cstring-lecture/blob/atoi/example.cpp) 🔞|
| `atol(s)`    | `<cstdlib>`   | Преобразование состоящей из цифр строки s в целое число типа long  | [взглянуть](https://github.com/Ms1black/cstring-lecture/blob/atol/example.cpp) 🔞|
| `atof(s)`    | `<cstdlib>`   | Преобразование состоящей из цифр строки s в целое число типа double | [взглянуть](https://github.com/Ms1black/cstring-lecture/blob/atof/example.cpp) 🔞|
| `tolower(ch)`    | `<cctype>`   | Преобразование буквенного символа ch к строчному формату  | [взглянуть](https://github.com/Ms1black/cstring-lecture/blob/tolower/example.cpp) 🔞|
| `toupper(ch)`    | `<cctype>`   | Преобразование буквенного символа ch к прописному формату  | [взглянуть](https://github.com/Ms1black/cstring-lecture/blob/toupper/example.cpp) 🔞|

-----

###  Попробуем задачу щелкнуть  *~~либо она решается, либо я начинаю истерить~~*


-----

<div align="center" width="300">
  
![изображение](https://github.com/user-attachments/assets/211fa716-39f7-426d-a405-d5975106aa52)

</div>

 <img src="https://github.com/user-attachments/assets/b437fde5-e0a0-4de6-b168-290dc5ceb5e9" width="250px">


##### Какие данные?
>###### на вход получаем "пример в строке", а вывести должны сумму
>>__Пример:__ 
>>
>>Вводим в консоль `1+2+3=`
>>
>>Выводим: `6`

##### В чем прикол задачи?
>###### прикол в том, что вводим мы символы, а их надо преобразовать в int и выполнить указанное арифметическое действие.

**Советую к прочтению:**

- [Про языковой стандарт (setlocale)](https://learn.microsoft.com/ru-ru/cpp/c-runtime-library/reference/setlocale-wsetlocale?view=msvc-170)