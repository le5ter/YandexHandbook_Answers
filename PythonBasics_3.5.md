## 3.5 Потоковый ввод/вывод. Работа с текстовыми файлами. JSON

### A. A+B+...
``` python
from sys import stdin

print(sum(map(int, stdin.read().split())))
```

### B. Средний рост
``` python
from sys import stdin

res = 0
counter = 0

for line in stdin:
    nums = line.strip("\n").split(" ")
    res += int(nums[2]) - int(nums[1])
    counter += 1

print(round(res / counter))
```

### C. Без комментариев 2.0
``` python
from sys import stdin

for i in stdin.readlines():
    if not i.startswith('#'):
        print(i[:i.find('#')])
```

### D. Найдётся всё 2.0
``` python
from sys import stdin

lines = [i.strip() for i in stdin]
for line in lines[:-1]:
    if lines[-1].lower() in line.lower():
        print(line)
```

### E. А роза упала на лапу Азора 6.0
``` python
from sys import stdin

data = [string.strip().split() for string in stdin]
words = []

for line in data:
    words.extend(line)
    
for word in sorted(set(words)):
    if word.lower() == word.lower()[::-1]:
        print(word)
```

### F. Транслитерация 2.0
``` python
LITER = {
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

data, translit_data = '', ''
with open("cyrillic.txt", encoding="UTF-8") as file_in:
    for line in file_in:
        data += line

for i in data:
    if i.upper() in LITER:
        translit_data += LITER[i.upper()].lower().capitalize() if i == i.upper() else LITER[i.upper()].lower()
    else:
        translit_data += i

with open("transliteration.txt", "w", encoding="UTF-8") as file_out:
    print(translit_data, file=file_out)
```

### G. Файловая статистика
``` python
name = input()
numbers = []
with open(name, 'r') as f:
    for line in f:
        numbers.extend([int(x) for x in line.split()])
print(len(numbers))
print(len(list(filter(lambda x: x > 0, numbers))))
print(min(numbers))
print(max(numbers))
print(sum(numbers))
print(round(sum(numbers) / len(numbers), 2))
```

### H. Файловая разница
``` python
first, second, answer = input(), input(), input()

with open(first, 'r') as f:
    first_set = {x for x in f.read().split()}

with open(second, 'r') as f:
    second_set = {x for x in f.read().split()}

result = sorted(first_set ^ second_set)

with open(answer, 'w') as f:
    f.write('\n'.join(result))
```

### I. Файловая чистка
``` python
first, second = input(), input()
result = []

with open(first, 'r') as f:
    for line in f:
        if line.strip() != "":
            x = line.strip().replace('\t', '')
            result.append(' '.join(x.split()) + '\n')

with open(second, 'w') as f:
    f.writelines(result)
```

### J. Хвост
``` python
file_in, lines = input(), int(input())

with open(file_in, 'r') as f:
    result = [line.rstrip("\n") for line in f.readlines()]

for line in result[-lines:]:
    print(line)
```