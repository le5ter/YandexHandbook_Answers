## 2.1 Ввод и вывод данных. Операции с числами, строками. Форматирование

### A. Привет, Яндекс!
``` python
print('Привет, Яндекс!')
```

### B. Привет, всем!
``` python
name = input('Как Вас зовут?\n')
print(f'Привет, {name}')
```

### C. Излишняя автоматизация
``` python
str = input()
print((str + '\n') * 3)
```

### D. Сдача
``` python
summ = int(2.5 * 38)
change = int(input()) - summ
print(change)
```

### E. Магазин
``` python
price = int(input())
weight = int(input())
money = int(input())
print(money - price * weight)
```

### F. Чек
``` python
name = input()
price = int(input())
weight = int(input())
money = int(input())

total_price = price * weight
change = money - total_price

print('Чек')
print(f'{name} - {weight}кг - {price}руб/кг')
print(f'Итого: {total_price}руб')
print(f'Внесено: {money}руб')
print(f'Сдача: {change}руб')
```

### G. Делу — время, потехе — час
``` python
n = int(input())
print('Купи слона!\n' * n)
```

### H. Наказание
``` python
n = int(input())    
str = input()
print(f'Я больше никогда не буду писать "{str}"!\n' * n)
```

### I. Деловая колбаса
``` python
minutes = int(input())
children = int(input())
print(minutes // 2 * children)
```

### J. Детский сад — штаны на лямках
#### Решение: 
``` python
name = input()
number = input()

group = number[0]
bed_number = number[1]
child_id = number[2]

print(f'Группа №{group}.')
print(f'{child_id}. {name}.')
print(f'Шкафчик: {number}.')
print(f'Кроватка: {bed_number}.')
```

### K. Автоматизация игры
``` python
number = input()
first_part = number[:2]
second_part = number[2:]
print(first_part[::-1] + second_part[::-1])
```

### L. Интересное сложение
``` python
number_1 = int(input())
number_2 = int(input())
a = (number_1 // 100 + number_2 // 100) % 10
b = (number_1 // 10 % 10 + number_2 // 10 % 10) % 10
c = (number_1 % 10 + number_2 % 10) % 10
number = a * 100 + b * 10 + c
print(number)
```

### M. Дед Мороз и конфеты
``` python
count = int(input())
value = int(input())
print(value // count)
print(value % count)
```

### N. Шарики и ручки
``` python
red = int(input())
green = int(input())
blue = int(input())
print(red + blue + 1)
```

### O. В ожидании доставки
``` python
hours = int(input())
minutes = int(input())
delivery_minutes = int(input())

hours = (hours + (minutes + delivery_minutes) // 60) % 24
minutes = (delivery_minutes + minutes) % 60
print(str(hours // 10) + str(hours % 10) + ':' + str(minutes // 10) + str(minutes % 10))
```

### P. Доставка
``` python
a = int(input())
b = int(input())
c = int(input())
print((b - a) / c)
```

### Q. Ошибка кассового аппарата
``` python
first = int(input())
second = int(input(), 2)
print(first + second)
```

### R. Сдача 10
``` python
first = int(input(), 2)
second = int(input())
print(second - first)
```

### S. Украшение чека
``` python
name = input()
price = int(input())
weight = int(input())
money = int(input())

price_and_weight = f'{weight}кг * {price}руб/кг'
str_size = 35
print('Чек'.center(str_size, '='))
print('Товар:' + ' ' * (str_size - len(name) - 6) + name)
print('Цена:' + ' ' * (str_size - len(price_and_weight) - 5) + price_and_weight)
print('Итого:' + ' ' * (str_size - len(f'{weight * price}руб') - 6) + f'{weight * price}руб')
print('Внесено:' + ' ' * (str_size - len(f'{money}руб') - 8) + f'{money}руб')
print('Сдача:' + ' ' * (str_size - len(f'{money - weight * price}руб') - 6) + f'{money - weight * price}руб')
print('=' * str_size)
```

### T. Мухи отдельно, котлеты отдельно 
``` python
all_weight = int(input())
price = int(input())
price1 = int(input())
price2 = int(input())

x = (all_weight * (price - price2)) // (price1 - price2)
print(x, all_weight - x)
```