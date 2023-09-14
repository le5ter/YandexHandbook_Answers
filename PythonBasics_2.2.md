## 2.2 Условный оператор

### A. Просто здравствуй, просто как дела
``` python
print('Как Вас зовут?')
name = input()
print(f'Здравствуйте, {name}!')
print('Как дела?')
answer = input()
if answer == 'хорошо':
    print('Я за вас рада!')
elif answer == 'плохо':
    print('Всё наладится!')
```

### B. Кто быстрее?
``` python
speed1, speed2 = int(input()), int(input())

if speed1 > speed2:
    print('Петя')
else:
    print('Вася')
```

### C. Кто быстрее на этот раз?
``` python
speed1, speed2, speed3 = int(input()), int(input()), int(input())

result = max(speed1, speed2, speed3)
if result == speed1:
    print('Петя')
elif result == speed2:
    print('Вася')
else:
    print('Толя')
```

### D. Список победителей
``` python
speed1, speed2, speed3 = int(input()), int(input()), int(input())

dict_1 = {
    speed1: 'Петя',
    speed2: 'Вася',
    speed3: 'Толя'
}
lst = sorted([speed1, speed2, speed3], reverse=True)
val = 1

for item in lst:
    print(f'{val}. {dict_1[item]}')
    val += 1
```

### E. Яблоки 
``` python
petya = 6
vasya = 12
n, m = int(input()), int(input())

if petya + n > vasya + m:
    print('Петя')
else:
    print('Вася')
```

### F. Сила прокрастинации
``` python
year = int(input())

if year % 4 == 0 and year % 100 != 0 or year % 400 == 0:
    print("YES")
else:
    print("NO")
```

### G. А роза упала на лапу Азора 
``` python
number = input()
if number == number[::-1]:
    print('YES')
else:
    print('NO')
```

### H. Зайка — 1 
``` python
word = input()
if 'зайка' in word:
    print('YES')
else:
    print('NO')
```

### I. Первому игроку приготовиться 
``` python
names = input(), input(), input()
print(min(names))
```

### J. Лучшая защита — шифрование 
``` python
number = int(input())

sum1 = number % 10 + (number // 10 % 10)
sum2 = number // 100 + number // 10 % 10

if sum1 > sum2:
    print(f'{sum1}{sum2}')
else:
    print(f'{sum2}{sum1}')
```

### K. Красота спасёт мир 
``` python
number = list(map(int, input()))
first = max(number) + min(number)
if first == 2 * (sum(number) - first):
    print('YES') 
else: 
    print('NO')
```

### L. Музыкальный инструмент 
``` python
sides = int(input()), int(input()), int(input())
if 2 * max(sides) < sum(sides):
    print('YES') 
else:
    print('NO')
```

### M. Властелин Чисел: Братство общей цифры
``` python
num1, num2, num3 = input(), input(), input()

if num1[0] == num2[0] == num3[0]:
    print(num1[0])
elif num1[1] == num2[1] == num3[1]:
    print(num1[1])
```

### N. Властелин Чисел: Две Башни
``` python
num = int(input())
n1 = num // 100
n2 = num // 10 % 10
n3 = num % 10

max_n = max(n1, n2, n3)
min_n = min(n1, n2, n3)
mid = (n1 + n2 + n3) - max_n - min_n

if min_n == 0:
    print(f'{mid}{min_n} {max_n}{mid}')
else:
    print(f'{min_n}{mid} {max_n}{mid}')
```

### O. Властелин Чисел: Возвращение Цезаря 
``` python
num1, num2 = input(), input()
nums = sorted([i for i in num1] + [i for i in num2], reverse=True)

print(nums[0] + str((int(nums[1]) + int(nums[2])) % 10) + nums[3])
```

### P. Легенды велогонок возвращаются: кто быстрее?
``` python
num1, num2, num3 = int(input()), int(input()), int(input())

dict = {
    num1: 'Петя',
    num2: 'Вася',
    num3: 'Толя'
}

nums = [num1, num2, num3]
nums.sort(reverse=True)

print(dict[nums[0]].center(24))
print(dict[nums[1]].center(8))
print(' ' * 16 + dict[nums[2]].center(8))
print('II'.center(8) + 'I'.center(8) + 'III'.center(8))
```

### Q. Корень зла
``` python
a, b, c = float(input()), float(input()), float(input())

if a == 0:
    if b == 0:
        if c == 0:
            print('Infinite solutions')
        else:
            print('No solution')
    else:
        print(-c / b)
else:
    discr = b ** 2 - 4 * a * c
    if discr < 0:
        print('No solution')
    elif discr == 0:
        print(-b / (2 * a))
    else:
        x1 = (-b + discr ** 0.5) / (2 * a)
        x2 = (-b - discr ** 0.5) / (2 * a)
        if x1 > x2:
            print(f'{x2} {x1}')
        else:
            print(f'{x1} {x2}')
```

### R. Территория зла
``` python
a, b, c = int(input()), int(input()), int(input())

max_n = max(a, b, c)
min_n = min(a, b, c)
mid = a + b + c - max_n - min_n

if min_n ** 2 + mid ** 2 == max_n ** 2:
    print('100%')
elif min_n ** 2 + mid ** 2 < max_n ** 2:
    print('велика')
else:
    print('крайне мала')
```

### S. Автоматизация безопасности 
``` python
x, y = float(input()), float(input())

if x ** 2 + y ** 2 <= 100:
    if y <= 0:
        if (0.25 * (x ** 2)) + (0.5 * x) - 8.75 <= y:
            print('Опасность! Покиньте зону как можно скорее!')
        else:
            print('Зона безопасна. Продолжайте работу.')
    else:
        if x >= 0:
            if x ** 2 + y ** 2 <= 25:
                print('Опасность! Покиньте зону как можно скорее!')
            else:
                print('Зона безопасна. Продолжайте работу.')
        else:
            if y <= 5 and y <= (5 * x + 35) / 3:
                print('Опасность! Покиньте зону как можно скорее!')
            else:
                print('Зона безопасна. Продолжайте работу.')
else:
    print('Вы вышли в море и рискуете быть съеденным акулой!')
```

### T. Зайка — 2
``` python
words = [input(), input(), input()]
words.sort()

for word in words:
    if 'зайка' in word:
        print(word, len(word))
        break
```