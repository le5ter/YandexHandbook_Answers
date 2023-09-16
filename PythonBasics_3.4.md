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

### K. Числовой прямоугольник 3.0
``` python
from itertools import product

n, m = int(input()), int(input())
for i in range(n):
    line = product(range(1, m + 1), [i * m])
    print(' '.join(map(lambda x: str(sum(x)).rjust(len(str((n - 1 - i) * m + sum(x))), ' '), line)))
```

### L. Список покупок 2.0
``` python
from itertools import chain

n = int(input())
food = []

for i in range(n):
    food = chain(food, input().split(", "))

food = sorted(food)
for i, product in enumerate(food, 1):
    print(f'{i}. {product}')
```

### M. Расстановка спортсменов
``` python
from itertools import permutations

n = int(input())
names = []

for i in range(n):
    names.append(input())

names = sorted(names)
for line in permutations(names, n):
    print(*line, sep=", ")
```

### N. Спортивные гадания
``` python
from itertools import permutations

n = int(input())
names = [input() for i in range(n)]
names = sorted(names)

for line in permutations(names, 3):
    print(*line, sep=", ")
```

### O. Список покупок 3.0
``` python
from itertools import permutations

n = int(input())
products = sorted([x for i in range(n) for x in input().split(", ")])

for food in permutations(products, 3):
    print(*food)
```

### P. Расклад таков...
``` python
from itertools import permutations, product

suits_ro = ["бубен", "пик", "треф", "червей"]
suit, exception = input(), input()
best_suit = [s for s in suits_ro if s.startswith(suit[0:3])][0]
nominal = [str(x) for x in range(2, 11)]
nominal.extend(["валет", "дама", "король", "туз"])
nominal.remove(exception)
comb = permutations(product(sorted(nominal), sorted(suits_ro)), 3)
y = [', '.join(' '.join(j) for j in sorted(i)) for i in comb]
triads = [i for i in y if best_suit in i][:10]
for triad in triads:
    print(triad)
```

### Q. А есть ещё варианты?
``` python
from itertools import product, permutations

suits_ro = sorted(["бубен", "пик", "треф", "червей"])
suit, exception, situation = input(), input(), input()
best_suit = [s for s in suits_ro if s.startswith(suit[0:3])][0]
nominal = [str(x) for x in range(2, 11)]
nominal.extend(["валет", "дама", "король", "туз"])
nominal.remove(exception)
comb = permutations(product(nominal, suits_ro), 3)
y = sorted(set([', '.join(' '.join(j) for j in sorted(i)) for i in comb]))
triads = [i for i in y if best_suit in i]
for j, triad in enumerate(triads):
    if triad == situation:
        print(triads[j + 1])
        break
```

### R. Таблица истинности
``` python
from itertools import product

statement = input()
print("a b c f")
table = product([0, 1], repeat=3)

for line in table:
    res = {'a': line[0], 'b': line[1], 'c': line[2]}
    print(*line, int(eval(statement, res)))
```

### S. Таблица истинности 2
``` python
from itertools import product

statement = input()
letters = set()
for i in statement.split():
    if i not in ["and", "or", "not"]:
        letters.add(i)

let = sorted(letters)
print(*let, "F")

table = product([0, 1], repeat=len(let))

for line in table:
    res = {}
    for i in range(len(let)):
        res[let[i]] = line[i]
    print(*line, int(eval(statement, res)))
```

### T. Таблицы истинности 3
``` python
from itertools import product

OPERATORS = {
    'not': 'not',
    'and': 'and',
    'or': 'or',
    '^': '!=',
    '->': '<=',
    '~': '==',
}

PRIORITY = {
    'not': 0,
    'and': 1,
    'or': 2,
    '^': 3,
    '->': 4,
    '~': 5,
    '(': 6,
}


def postfix_expression(expression, variables):
    stack, result, lst = [], [], expression.split()
    for i in lst:
        if i in variables:
            result.append(i)
        elif i == '(':
            stack.append(i)
        elif i == ')':
            while stack[-1] != '(':
                result.append(OPERATORS[stack.pop()])
            stack.pop()
        elif i in OPERATORS.keys():
            while len(stack) and PRIORITY[i] >= PRIORITY[stack[-1]]:
                result.append(OPERATORS[stack.pop()])
            stack.append(i)
    for _ in range(len(stack)):
        result.append(OPERATORS[stack.pop()])
    return result


def result_of_expression(postfix_exp, variables):
    stack = []
    for i in range(len(postfix_exp)):
        if postfix_exp[i] in variables.keys():
            stack.append(variables[postfix_exp[i]])
        else:
            if postfix_exp[i] == 'not':
                stack.append(not stack.pop())
            else:
                var2, var1 = stack.pop(), stack.pop()
                stack.append(eval(f'{var1} {postfix_exp[i]} {var2}'))
    return int(stack.pop())


statement = input()
var_all = sorted(set([i for i in statement if i.isupper()]))
print(' '.join(var_all), 'F')
table = product([0, 1], repeat=len(var_all))
statement = statement.replace('(', '( ').replace(')', ' )')
exp = postfix_expression(statement, var_all)

for row in table:
    res = {}
    for k, v in zip(var_all, row):
        res[k] = v
    print(' '.join(str(x) for x in row), result_of_expression(exp, res))
```