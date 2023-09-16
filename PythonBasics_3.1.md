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

### K. Найдётся всё
``` python
num = int(input())

headers = []
for i in range(num):
    headers.append(input())
request = input()

for header in headers:
    if request.lower() in header.lower():
        print(header)
```

### L. Меню питания
``` python
num = int(input())
cereal = ['Манная', 'Гречневая', 'Пшённая', 'Овсяная', 'Рисовая']

for i in range(num):
    print(cereal[i % 5])
```

### M. Массовое возведение в степень
``` python
size = int(input())
nums = []

for i in range(size):
    nums.append(int(input()))
power = int(input())

for num in nums:
    print(num ** (power))
```

### N. Массовое возведение в степень 2.0
``` python
nums, power = input().split(), int(input())

for num in nums:
    num = int(num)
    print(num ** power, end=' ')
```

### O. НОД 3.0
``` python
from math import gcd

nums = [int(x) for x in input().split()]
print(gcd(*nums))
```

### P. Анонс новости 2.0
``` python
length, size = int(input()), int(input())

headers = []
for i in range(size):
    headers.append(input())

curr_length = length
for header in headers:
    if curr_length - len(header) - 3 > 0:
        print(header)
        curr_length -= len(header)
    else:
        header = header[:curr_length - 3] + '...'
        print(header)
        break
```

### Q. А роза упала на лапу Азора 5.0
``` python
string = ''.join(input().lower().split())

if string == string[::-1]:
    print('YES')
else:
    print('NO')
```

### R. RLE
``` python
nums = input()
count = 1
for i in range(len(nums) - 1):
    if nums[i] == nums[i + 1]:
        count += 1
    else:
        print(nums[i], count)
        count = 1
print(nums[-1], count)
```

### S. Польский калькулятор
``` python
string = [x for x in input().split()]
stack = []

for x in string:
    if x in '*+-':
        b = stack.pop()
        a = stack.pop()
        stack.append(eval(f'{a} {x} {b}'))
    else:
        stack.append(x)
print(*stack)
```

### T. Польский калькулятор — 2
``` python
import math

string = [x for x in input().split()]
stack = []

for x in string:
    if x in '*+-/':
        b = stack.pop()
        a = stack.pop()
        if x == '/':
            x = '//'
        stack.append(eval(f'{a} {x} {b}'))
    elif x in '~!#':
        if x == '~':
            stack.append(f'-{stack.pop()}')
        if x == '!':
            num = stack.pop()
            stack.append(str(math.factorial(int(num))))
        if x == '#':
            stack.append((a := stack.pop()))
            stack.append(a)
    elif x == '@':
        a = stack.pop()
        b = stack.pop()
        c = stack.pop()
        stack.append(b)
        stack.append(a)
        stack.append(c)
    else:
        stack.append(x)

print(*stack)
```