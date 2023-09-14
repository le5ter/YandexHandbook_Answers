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