## 3.1 Строки, кортежи, списки

### A. Азбука
``` python
for i in range(int(input())):
    if (word := input())[0] not in 'абв':
        print('NO')
        break
else:
    print('YES')
```

### B. Кручу-верчу
``` python
for letter in input():
    print(letter)
```

### C. Кручу-верчу
``` python
length = int(input())
for i in range(int(input())):
    line = input()
    if len(line) > length:
        print(line[:length - 3].ljust(length, "."))
    else:
        print(line)
```

### D. Очистка данных
``` python
while (words := input()) != '':
    if words[-3:] == '@@@':
        pass
    elif words[:2] == '##':
        print(words[2:])
    else:
        print(words)
```

### E. А роза упала на лапу Азора 4.0
``` python
word = input()
if word == word[::-1]:
    print('YES')
else:
    print('NO')
```

### F. Зайка — 6
``` python
count = 0
for i in range(int(input())):
    words = input()
    count += words.count('зайка')

print(count)
```

### G. А и Б сидели на трубе
``` python
a, b = input().split()
print(int(a) + int(b))
```

### H. Зайка — 7
``` python
for i in range(int(input())):
    words = input()
    if words.find('зайка') != -1:
        print(words.find('зайка') + 1)
    else:
        print('Заек нет =(')
```

### I. Без комментариев
``` python
while (st := input()):
    if st.startswith('#'):
        pass
    elif st.find('#') != -1:
        print(st[:st.find('#')])
    else:
        print(st)
```

### J. Частотный анализ на минималках
``` python
dict = {}
s = input()

while s != 'ФИНИШ':
    s = s.lower()
    for x in s:
        if x.isalpha():
            dict[x] = dict.get(x, 0) + 1
    s = input()
print(max(sorted(dict), key=lambda x: dict[x]))
```