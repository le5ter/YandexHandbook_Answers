## 2.4 Вложенные циклы

### A. Таблица умножения
``` python
size = int(input())

for i in range(1, size + 1):
    for j in range(1, size + 1):
        if j == size:
            print(i * j)
        else:
            print(i * j, end=" ")
```

### B. Не таблица умножения
``` python
size = int(input())

for i in range(1, size + 1):
    for j in range(1, size + 1):
        print(f'{j} * {i} = {i * j}')
```

### C. Новогоднее настроение
``` python
for y in range(1, x := int(input()) + 1):
    if y in (sum(range(i)) for i in range(x)):
        print(y)
    else:
        print(y, end=' ')
```

### D. Суммарная сумма
``` python
summ = 0
for i in range(int(input())):
    summ += sum(map(int, list(input())))
print(summ)
```

### E. Зайка — 5
``` python
size = int(input())
words = []

for i in range(size):
    curr_word = ''
    while (word := input()) != 'ВСЁ':
        curr_word += word + ' '
    words.append(curr_word)
    
count = 0
for word in words:
    if word.find('зайка') != -1:
        count += 1

print(count)
```

### F. НОД 2.0
``` python
n, a = int(input()), int(input())
for i in range(n - 1):
    b = int(input())
    while b:
        a, b = b, a % b
print(a)
```

### G. На старт! Внимание! Марш!
``` python
for i in range(int(input())):
    for j in range(3 + i, 0, -1):
        print(f'До старта {j} секунд(ы)')
    print(f'Старт {i + 1}!!!')
```

### H. Максимальная сумма
``` python
name, summ = '', 0
for i in range(int(input())):
    temp_name, temp_summ = input(), sum(map(int, input()))
    if temp_summ >= summ:
        name, summ = temp_name, temp_summ
print(name)
```

### I. Большое число
``` python
number = ''
for i in range(int(input())):
    number += max(input())
print(number)
```

### J. Мы делили апельсин
``` python
for i in range(1, (n := int(input())) - 1):
    if i == 1:
        print('А Б В')
    for j in range(1, n - i):
        print(f'{i} {j} {n - i - j}')
```

### K. Простая задача 3.0
``` python
size = int(input())
nums = []

for i in range(size):
    nums.append(int(input()))


def is_prime(x):
    for j in range(2, (x // 2) + 1):
        if x % j == 0:
            return False
    return True


count = 0
for num in nums:
    if num > 1 and is_prime(num):
        count += 1

print(count)
```

### L. Числовой прямоугольник
``` python
height, width = int(input()), int(input())

num = 1
size_num = height * width

for i in range(height):
    for j in range(width):
        if j != width - 1:
            if size_num < 10:
                print(f'{num}'.center(1), end=' ')
            elif 10 <= size_num < 100:
                print(f'{num}'.rjust(2), end=' ')
            else:
                print(f'{num}'.rjust(3), end=' ')
        else:
            if size_num < 10:
                print(f'{num}'.center(1))
            elif 10 <= size_num < 100:
                print(f'{num}'.rjust(2))
            else:
                print(f'{num}'.rjust(3))
        num += 1
```

### M. Числовой прямоугольник 2.0
``` python
height, width = int(input()), int(input())

num = 1
size_num = height * width

for i in range(height):
    curr_num = num
    for j in range(width):
        if j != width - 1:
            if size_num < 10:
                print(f'{curr_num}'.center(1), end=' ')
            elif 10 <= size_num < 100:
                print(f'{curr_num}'.rjust(2), end=' ')
            else:
                print(f'{curr_num}'.rjust(3), end=' ')
            curr_num += height
        else:
            if size_num < 10:
                print(f'{curr_num}'.center(1))
            elif 10 <= size_num < 100:
                print(f'{curr_num}'.rjust(2))
            else:
                print(f'{curr_num}'.rjust(3))
    num += 1
```

### N. Числовая змейка
``` python
height, width = int(input()), int(input())

num = 1
size_num = height * width

for i in range(height):
    curr_num = num
    for j in range(width):
        if j != width - 1:
            if size_num < 10:
                print(f'{curr_num}'.center(1), end=' ')
            elif 10 <= size_num < 100:
                print(f'{curr_num}'.rjust(2), end=' ')
            else:
                print(f'{curr_num}'.rjust(3), end=' ')
            if i % 2 == 0:
                curr_num += 1
            else:
                curr_num -= 1
        else:
            if size_num < 10:
                print(f'{curr_num}'.center(1))
            elif 10 <= size_num < 100:
                print(f'{curr_num}'.rjust(2))
            else:
                print(f'{curr_num}'.rjust(3))
            num = curr_num
    num += width
```

### O. Числовая змейка 2.0
``` python
height, width = int(input()), int(input())

num = 1
size_num = height * width

for i in range(height):
    curr_num = num
    for j in range(width):
        if j != width - 1:
            if size_num < 10:
                print(f'{curr_num}'.center(1), end=' ')
            elif 10 <= size_num < 100:
                print(f'{curr_num}'.rjust(2), end=' ')
            else:
                print(f'{curr_num}'.rjust(3), end=' ')

            if j % 2 == 0:
                curr_num += 2 * height - (num + i)
            else:
                curr_num += num + i
        else:
            if size_num < 10:
                print(f'{curr_num}'.center(1))
            elif 10 <= size_num < 100:
                print(f'{curr_num}'.rjust(2))
            else:
                print(f'{curr_num}'.rjust(3))
    num += 1
```

### P. Редизайн таблицы умножения
``` python
size, width = int(input()), int(input())

for i in range(1, size + 1):
    for j in range(1, size + 1):
        space = (width - len(str(i * j))) // 2
        if len(str(i * j)) % 2 == 0 and width % 2 != 0:
            if j != size:
                print(' ' * space + f'{i * j}' + ' ' * (space + 1), end='|')
            else:
                print(' ' * space + f'{i * j}' + ' ' * (space + 1))
        else:
            if j != size:
                print(f'{i * j}'.center(width), end='|')
            else:
                print(f'{i * j}'.center(width))
    if i != size:
        print('-' * ((width + 1) * size - 1))
```

### Q. А роза упала на лапу Азора 3.0
``` python
size = int(input())

count = 0
for i in range(size):
    number = input()
    if number == number[::-1]:
        count += 1
print(count)
```

### R. Новогоднее настроение 2.0
``` python
g, lengths = '', [0]
for j in range(1, (x := int(input())) + 1):
    g += str(j) + ' '
    if j in (sum(range(i)) for i in range(j + 2)):
        lengths.append(len(g) - 1)
        g = ''
lengths.append(len(g) - 1)
d = 1
for y in range(1, x + 1):
    if y - 1 in (sum(range(i)) for i in range(y + 2)):
        print(f"{' ' * ((max(lengths) - lengths[d]) // 2)}{y}", end=' ' if y != 1 else '\n')
        d += 1
    else:
        print(y, end='\n' if y in (sum(range(i)) for i in range(y + 2)) else ' ')
```

### S. Числовой квадрат
``` python
n = int(input())

for i in range(n):
    for j in range(n):
        num = min(i + 1, n - i, j + 1, n - j)
        if j != n - 1:
            if n <= 18:
                print(f'{num}'.center(1), end=' ')
            else:
                print(f'{num}'.rjust(2), end=' ')
        else:
            if n <= 18:
                print(f'{num}'.center(1))
            else:
                print(f'{num}'.rjust(2))
```

### T. Математическая выгода
``` python
def summ_digits(num1: int) -> int:
    summ = 0
    while num1 >= 1:
        summ += num1 % 10
        num1 //= 10
    return summ


def from_ten_to_ss(number1: int, ss: int) -> int:
    res = ''
    while number1 > 0:
        res = str(number1 % ss) + res
        number1 //= ss
    return int(res)


num = int(input())
max_sum = []

for i in range(2, 11):
    number = from_ten_to_ss(num, i)
    max_sum.append((summ_digits(number), i))
max_sum.sort(reverse=True)

max_summ = 0
max_sum_index = 0
for summ, index in max_sum:
    if summ >= max_summ:
        max_summ = summ
        max_sum_index = index

print(max_sum_index)
```