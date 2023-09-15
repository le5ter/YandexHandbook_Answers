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