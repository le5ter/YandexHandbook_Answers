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

### K. Файловая статистика 2.0
``` python
import json

first, second = input(), input()

result = {
    "count": 0,
    "positive_count": 0,
    "min": 0,
    "max": 0,
    "sum": 0,
    "average": 0
}

numbers = []
with open(first, 'r') as f:
    for line in f:
        numbers.extend([int(x) for x in line.split()])

result["count"] = len(numbers)
result["positive_count"] = len(list(filter(lambda x: x > 0, numbers)))
result["min"] = min(numbers)
result["max"] = max(numbers)
result["sum"] = sum(numbers)
result["average"] = round(sum(numbers) / len(numbers), 2)

with open(second, 'w') as res:
    json.dump(result, res)
```

### L. Разделяй и властвуй
``` python
from sys import stdin

files = [name.strip() for name in stdin]
data = []
with open(files[0]) as f:
    for line in f:
        data.append(line.split())
D = dict(zip([1, 2, 3], ['>', '<', '==']))
for n in range(1, len(files)):
    with open(files[n], 'w') as f:
        for line in data:
            for i in line:
                if eval('len(list(filter(lambda x: not int(x) % 2, i)))'
                        + D[n] +
                        'len(list(filter(lambda x: int(x) % 2, i)))'):
                    print(i, end=' ', file=f)
            print('\n', end='', file=f)
```

### M. Обновление данных
``` python
from sys import stdin
import json

data = [line.strip() for line in stdin]
print(data)
print({line.split(' == ')[0]: line.split(' == ')[1] for line in data[1:]})
D = {line.split(' == ')[0]: line.split(' == ')[1] for line in data[1:]}
with open(data[0], 'r', encoding="UTF-8") as f:
    records = json.load(f)
records.update(D)
if len(data) > 1:
    with open(data[0], 'w', encoding="UTF-8") as f:
        json.dump(records, f, ensure_ascii=False, indent=4, sort_keys=True)
```

### N. Слияние данных
``` python
import json

file_1, file_2 = input(), input()
with open(file_1, 'r') as f:
    data_1 = json.load(f)
with open(file_2, 'r') as f:
    data_2 = json.load(f)
data_1 = {i["name"]: {k: v for k, v in i.items() if k != "name"} for i in data_1}
for d in data_2:
    if d["name"] in data_1:
        for key in d:
            if (key not in data_1[d["name"]] or d[key] > data_1[d["name"]][key]) and key != "name":
                data_1[d["name"]][key] = d[key]
    else:
        data_1[d["name"]] = {k: v for k, v in d.items() if k != "name"}
with open(file_1, 'w') as g:
    json.dump(data_1, g, ensure_ascii=False, indent=4)
```

### O. Поставь себя на моё место
``` python
from sys import stdin
import json

answers = [i.strip() for i in stdin]
with open("scoring.json", "r") as file_in:
    data = json.load(file_in)
data = [{y["pattern"]: x["points"] // len(x["tests"]) for y in x["tests"]} for x in data]
result, counter = 0, 0
for i in data:
    for j in range(counter, len(i) + counter):
        if answers[j] in i:
            result += i[answers[j]]
        counter += 1
print(result)
```

### P. Найдётся всё 3.0
``` python
from sys import stdin

data = [line.strip() for line in stdin]
query = data[0].lower()
D = {}
for file in data[1:]:
    with open(file, "r", encoding="UTF-8") as f:
        D[file] = f.read()
        if query in ' '.join(D[file].replace('&nbsp;', ' ').lower().split()):
            print(file)
        else:
            del D[file]
if not D:
    print('404. Not Found')
```

### Q. Прятки
``` python
with open("secret.txt", 'r', encoding='UTF-8') as f:
    print(''.join([chr(ord(i) % 128) for i in f.read()]))
```

### R. Сколько вешать в байтах?
``` python
import os

size = os.path.getsize(input())
if size > 1024**3 - 1:
    size = int(size / 1024**3) + 1
    postfix = 'ГБ'
elif size > 1024**2 - 1:
    size = int(size / 1024**2) + 1
    postfix = 'МБ'
elif size > 1023:
    size = int(size / 1024) + 1
    postfix = 'КБ'
else:
    postfix = 'Б'
print(str(size) + postfix)
```

### S. Это будет наш секрет
``` python
shift = int(input())
a = "abcdefghijklmnopqrstuvwxyz"
with open("public.txt", "r", encoding="UTF-8") as file_in:
    data = file_in.read()
data_out = [a[(a.find(i.lower()) + shift) % len(a)] if i.lower() in a else i for i in data]

for i, letter in enumerate(data):
    if letter.isupper():
        data_out[i] = data_out[i].upper()

with open("private.txt", "w") as file_out:
    print(''.join(data_out), file=file_out)
```

### T. Файловая сумма
``` python
with open("numbers.num", "rb") as f:
    data = f.read()
print(sum([int.from_bytes(data[i:i + 2], "big") for i in range(0, len(data), 2)]) % 2**16)
```