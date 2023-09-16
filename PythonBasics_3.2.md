## 3.2 Множества, словари

### A. Символическая выжимка
``` python
print(*set(input()), sep='')
```

### B. Символическая разница
``` python
a, b = set(input()), set(input())
print(*(a & b), sep='')
```

### C. Зайка — 8
``` python
n = int(input())
res = set()

for i in range(n):
    for word in input().split():
        if word not in res:
            res.add(word)
            print(word)
```

### D. Кашееды
``` python
a, b = int(input()), int(input())

set_1 = set()
set_2 = set()

for i in range(a):
    set_1.add(input())
for i in range(b):
    set_2.add(input())

if len(set_1 & set_2) == 0:
    print('Таких нет')
else:
    print(len(set_1 & set_2))
```

### E. Кашееды — 2
``` python
a, b = int(input()), int(input())

set_1 = set()
set_2 = set()

for i in range(a + b):
    if (x := input()) in set_1:
        set_2.add(x)
    else:
        set_1.add(x)

if len(set_1 ^ set_2) == 0:
    print('Таких нет')
else:
    print(len(set_1 ^ set_2))
```

### F. Кашееды — 3
``` python
a, b = int(input()), int(input())

set_1 = set()
set_2 = set()

for i in range(a + b):
    if (x := input()) in set_1:
        set_2.add(x)
    else:
        set_1.add(x)

if len(set_1 ^ set_2) == 0:
    print('Таких нет')
else:
    print(*sorted([x for x in (set_1 ^ set_2)]), sep='\n')
```

### G. Азбука Морзе
``` python
morze = {
    'A': '.-', 'B': '-...', 'C': '-.-.',
    'D': '-..', 'E': '.', 'F': '..-.',
    'G': '--.', 'H': '....', 'I': '..',
    'J': '.---', 'K': '-.-', 'L': '.-..',
    'M': '--', 'N': '-.', 'O': '---',
    'P': '.--.', 'Q': '--.-', 'R': '.-.',
    'S': '...', 'T': '-', 'U': '..-',
    'V': '...-', 'W': '.--', 'X': '-..-',
    'Y': '-.--', 'Z': '--..',
    '0': '-----', '1': '.----', '2': '..---',
    '3': '...--', '4': '....-', '5': '.....',
    '6': '-....', '7': '--...', '8': '---..',
    '9': '----.'
}

for word in input().upper().split():
    for letter in word:
        print(morze[letter], end=' ')
    print()
```

### H. Кашееды — 4
``` python
n = int(input())
dict_1 = {}
count = 0

for i in range(n):
    a = input().split()
    dict_1[a[0]] = ''.join(x + ' ' for x in a[1:]).strip()

dict_1 = dict(sorted(dict_1.items()))
res = input()

for x in dict_1:
    if res in dict_1[x]:
        print(x)
        count += 1

if count == 0:
    print('Таких нет')
```

### I. Зайка — 9
``` python
dict_1 = {}

while (s := input()) != '':
    for x in s.split():
        if x not in dict_1:
            dict_1[x] = 1
        else:
            dict_1[x] += 1

for x in dict_1:
    print(x, dict_1[x])
```

### J. Транслитерация
``` python
liter = {
    'А': 'A', 'Б': 'B', 'В': 'V',
    'Г': 'G', 'Д': 'D', 'Е': 'E',
    'Ё': 'E', 'Ж': 'ZH', 'З': 'Z',
    'И': 'I', 'Й': 'I', 'К': 'K',
    'Л': 'L', 'М': 'M', 'Н': 'N',
    'О': 'O', 'П': 'P', 'Р': 'R',
    'С': 'S', 'Т': 'T', 'У': 'U',
    'Ф': 'F', 'Х': 'KH', 'Ц': 'TC',
    'Ч': 'CH', 'Ш': 'SH', 'Щ': 'SHCH',
    'Ы': 'Y', 'Э': 'E', 'Ю': 'IU',
    'Я': 'IA', 'Ь': '', 'Ъ': '',
}

for i in (x := input()):
    if i.upper() in liter:
        if i == i.upper():
            print(liter[i.upper()].lower().capitalize(), end='')
        else:
            print(liter[i.upper()].lower(), end='')
    else:
        print(i, end='')
```

### K. Однофамильцы
``` python
a = dict()
count = 0
for i in range(int(input())):
    s = input()
    a[s] = a.get(s, 0) + 1
for i in a:
    if a[i] > 1:
        count += a[i]
print(count)
```

### L. Однофамильцы — 2
``` python
a = dict()
for i in range(int(input())):
    s = input()
    a[s] = a.get(s, 0) + 1
s = []
for i in a.keys():
    if a[i] > 1:
        s.append(i)
s.sort()
if len(s):
    for i in s:
        print(f'{i} - {a[i]}')
else:
    print('Однофамильцев нет')
```

### M. Дайте чего-нибудь новенького!
``` python
n = int(input())
set_1 = set()
for i in range(n):
    set_1.add(input())

a = int(input())
for i in range(a):
    b = int(input())
    for j in range(b):
        s = input()
        if s in set_1:
            set_1.remove(s)

if len(set_1) != 0:
    print(*(sorted(set_1)), sep='\n')
else:
    print('Готовить нечего')
```

### N. Это будет шедевр!
``` python
ingredients, dishes = [], set()
for i in range(int(input())):
    ingredients.append(input())
for i in range(int(input())):
    dishes.add(x := input())
    for j in range(int(input())):
        if input() not in ingredients:
            dishes.discard(x)
if dishes:
    for dish in sorted(dishes):
        print(dish)
else:
    print('Готовить нечего')
```

### O. Двоичная статистика!
``` python
res = []
for x in input().split():
    num = bin(int(x))[2:]
    zeros = 0
    for digit in num:
        if digit == '0':
            zeros += 1
    units = len(num) - zeros
    res.append({
        'digits': len(num),
        'units': units,
        'zeros': zeros
    })

print(res)
```

### P. Зайка — 10
``` python
res = set()

while (s := input()) != '':
    t = [x for x in s.split()]
    if len(t) != 0:
        for i in range(len(t)):
            if t[i] == 'зайка':
                if i + 1 < len(t):
                    res.add(t[i + 1])
                if i - 1 >= 0:
                    res.add(t[i - 1])

print(*sorted(res), sep='\n')
```

### Q. Друзья друзей
``` python
dict_1 = {}

while (s := input()) != '':
    t = [x for x in s.split()]
    if t[0] not in dict_1:
        dict_1[t[0]] = set()
        dict_1[t[0]].add(t[1])
    else:
        dict_1[t[0]].add(t[1])

    if t[1] not in dict_1:
        dict_1[t[1]] = set()
        dict_1[t[1]].add(t[0])
    else:
        dict_1[t[1]].add(t[0])

dict_1 = dict(sorted(dict_1.items()))

for x in dict_1:
    res = set()
    for y in dict_1[x]:
        for z in dict_1[y]:
            if z != x and z not in dict_1[x]:
                res.add(z)

    print(f'{x}: ', end='')
    print(*sorted(res), sep=', ')
```

### R. Карта сокровищ
``` python
n = int(input())
points = {}

for i in range(n):
    a, b = map(int, input().split())
    a //= 10
    b //= 10
    if (a, b) in points.keys():
        points[(a, b)] += 1
    else:
        points[(a, b)] = 1

print(max(points.values()))
```

### S. Частная собственность
``` python
n = int(input())
children = {}

for i in range(n):
    name, toys = input().split(': ')
    toys_set = set(toys.split(', '))
    children[name] = toys_set

res_toys = set()
for k in children.keys():
    toys = children[k].copy()
    for new_k in children.keys():
        if k != new_k:
            toys.difference_update(children[new_k])
    res_toys.update(toys)

print(*sorted(list(res_toys)), sep='\n')
```

### T. Простая задача 4.0
``` python
from math import gcd

nums = [int(x) for x in input().split('; ')]
res = {}

for num in nums:
    res[num] = set()
    for num1 in nums:
        if gcd(num, num1) == 1:
            res[num].add(num1)

sorted_res = dict(sorted(res.items()))
for item in sorted_res:
    sorted_res[item] = sorted(sorted_res[item])

for item in sorted_res:
    if len(sorted_res[item]) != 0:
        print(f'{item} - ', end='')
        print(*sorted_res[item], sep=', ')
```