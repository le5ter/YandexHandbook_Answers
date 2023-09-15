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