## 3.4 Встроенные возможности по работе с коллекциями

### A. Автоматизация списка
``` python
print(''.join(f'{k}. {v}\n' for k, v in list(enumerate(input().split(' '), 1))))
```

### B. Сборы на прогулку
``` python
s1 = input().split(', ')
s2 = input().split(', ')

print(''.join(f'{k} - {v}\n' for (k, v) in list(zip(s1, s2))))
```

### C. Рациональная считалочка
``` python
from itertools import count

nums = [float(x) for x in input().split(' ')]

for value in count(nums[0], nums[2]):
    if value <= nums[1]:
        print("%.2f" % value)
    else:
        break
```

### D. Словарная ёлка
``` python
from itertools import accumulate

for s in accumulate(input().split(' '), lambda x, nxt: f'{x} {nxt}'):
    print(s)
```

### E. Список покупок
``` python
from itertools import chain

s1, s2, s3 = input().split(', '), input().split(', '), input().split(', ')

for i, k in enumerate(sorted(list(chain(s1, s2, s3))), 1):
    print(f'{i}. {k}')
```

### F. Колода карт
``` python
from itertools import product

l1 = ['2', '3', '4', '5', '6', '7', '8', '9', '10', 'валет', 'дама', 'король', 'туз']
l2 = ['пик', 'треф', 'бубен', 'червей']

to_delete = input()
l2.remove(to_delete)

print(''.join(f'{k} {v}\n' for (k, v) in list(product(l1, l2))))
```

### G. Игровая сетка
``` python
from itertools import combinations

names = [input() for i in range(int(input()))]

for (k, v) in list(combinations(names, 2)):
    print(f'{k} - {v}')
```

### H. Меню питания 2.0
``` python
porridge = [input() for i in range(int(input()))]
n = int(input())

for i in range(n):
    print(porridge[i % len(porridge)])
```

### I. Таблица умножения 3.0
``` python
from itertools import product

n = int(input())
nums = [i for i in range(1, n + 1)]

for index, i in enumerate(product(nums, nums), 1):
    print(i[0] * i[1], end=' ')
    if index % n == 0:
        print()
```

### J. Мы делили апельсин 2.0
``` python
from itertools import product

n = int(input())
test = []

print("А Б В")
for i in product(range(1, n - 1), repeat=3):
    if sum(i) == n:
        print(*i)
```