## 2.3 Циклы

### A. Раз, два, три! Ёлочка, гори!
``` python
while (word := input()) != 'Три!':
    print('Режим ожидания...')
print('Ёлочка, гори!')
```

### B. Зайка — 3
``` python
words = ''
count = 0
while words != 'Приехали!':
    words = input()
    if 'зайка' in words:
        count += 1
print(count)
```

### C. Считалочка
``` python
a, b = int(input()), int(input())

for i in range(a, b + 1):
    print(i, end=' ')
```

### D. Считалочка 2.0
``` python
a, b = int(input()), int(input())

if a > b:
    for i in range(a, b - 1, -1):
        print(i, end=' ')
else:
    for i in range(a, b + 1):
        print(i, end=' ')
```

### E. Внимание! Акция!
``` python
res = 0
summ = float(input())
while summ != 0:
    if summ >= 500:
        res += summ * 0.9
    else:
        res += summ
    summ = float(input())
print(res)
```

### F. НОД
``` python
a, b = int(input()), int(input())
while b:
    a, b = b, a % b
print(a)
```

### G. НОК
``` python
a, b = c, d = int(input()), int(input())
while b:
    a, b = b, a % b
print(c * d // a)
```

### H. Излишняя автоматизация 2.0
``` python
line, number = input(), int(input())
for i in range(number):
    print(line)
```

### I. Факториал
``` python
a = int(input())
fact = 1
for i in range(1, a + 1):
    fact *= i
print(fact)
```

### J. Маршрут построен
``` python
direction = input()
x, y = 0, 0
while direction != 'СТОП':
    steps = int(input())
    if direction == 'СЕВЕР':
        y += steps
    elif direction == 'ЮГ':
        y -= steps
    elif direction == 'ЗАПАД':
        x -= steps
    elif direction == 'ВОСТОК':
        x += steps
    direction = input()

print(y, x, sep='\n')
```

### K. Цифровая сумма
``` python
print(sum(map(int, input())))
```

### L. Сильная цифра
``` python
print(max(map(int, input())))
```

### M. Первому игроку приготовиться 2.0
``` python
a, min_name = int(input()), input()
for i in range(a - 1):
    min_name = min(min_name, input())
print(min_name)
```

### N. Простая задача
``` python
number = int(input())

for i in range(2, int(number ** 0.5) + 1):
    if number % i == 0:
        print('NO')
        break        
else:
    if number != 1:
        print('YES')
    else:
        print('NO')
```

### O. Зайка - 4
``` python
a = int(input())
count = 0
for i in range(a):
    if 'зайка' in input():
        count += 1
print(count)
```

### P. А роза упала на лапу Азора 2.0
``` python
num = input()
if num == num[::-1]:
    print('YES')
else:
    print('NO')
```

### Q. Чётная чистота
``` python
print(''.join(i for i in input() if int(i) % 2))
```

### R. Простая задача 2.0
``` python
number = int(input())

i = 2
while number > 1:
    if number % i == 0:
        print(i, end=' ')
        number //= i
        if number > 1:
            print('*', end=' ')
    else:
        i += 1
```

### S. Игра в «Угадайку»
``` python
step = num = 512
print(num)

while (text := input()) != 'Угадал!':
    step //= 2
    if text == 'Меньше':
        num = num - step
    if text == 'Больше':
        num = num + step
    if num > 1000:
        num = 1000
    print(num)
```

### T. Хайпанём немножечко!
``` python
n = int(input())
wrong_h = -1
h_last = 0
for i in range(n):
    b = int(input())
    h = b % 256
    m = b // 256 ** 2
    r = (b // 256) % 256
    h_curr = (37 * (m + r + h_last)) % 256
    if h_curr != h or h >= 100:
        wrong_h = i
        break
    h_last = h
print(wrong_h)
```