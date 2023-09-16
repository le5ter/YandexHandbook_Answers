## 3.3 Списочные выражения. Модель памяти для типов языка Python

### A. Список квадратов
``` python
[x * x for x in range(a, b + 1)]
```

### B. Таблица умножения 2.0
``` python
[[a * b for a in range(1, n + 1)] for b in range(1, n + 1)]
```

### C. Длины всех слов
``` python
[len(string) for string in sentence.split(' ')]
```

### D. Множество нечетных чисел
``` python
{num for num in numbers if num % 2 == 1}
```

### E. Множество всех полных квадратов
``` python
{num for num in numbers if round(num ** 0.5) ** 2 == num}
```

### F. Буквенная статистика
``` python
{letter: text.lower().count(letter) for letter in sorted(text.lower()) if letter.isalpha()}
```

### G. Делители
``` python
{number: [i for i in range(1, number + 1) if not number % i] for number in numbers}
```

### H. Аббревиатура
``` python
''.join(word[0].upper() for word in string.split(' '))
```

### I. Преобразование в строку
``` python
' - '.join(str(number) for number in sorted(set(numbers)))
```

### J. RLE наоборот
``` python
''.join(letter * count for letter, count in rle)
```