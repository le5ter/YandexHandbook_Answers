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