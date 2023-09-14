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
