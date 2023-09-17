## 5.3 Модель исключений Python. Try, except, else, finally. Модули

### A. Обработка ошибок
``` python
try:
    func()
except Exception as error:
    print(type(error).__name__)
else:
    print('No Exceptions')   
```

### B. Ломать — не строить
``` python
try:
    func('2', None)
except ValueError:
    print('Ура! Ошибка!')
```

### C. Ломать — не строить 2
``` python
class Broken:
    def __repr__(self):
        raise Exception


try:
    a = Broken()
    func(a)
except Exception:
    print('Ура! Ошибка!')
```

### D. Контроль параметров
``` python
def only_positive_even_sum(a, b):
    if isinstance(a, int) is False or isinstance(b, int) is False:
        raise TypeError
    if not (a > 0 and not a % 2) or not (b > 0 and not b % 2):
        raise ValueError
    return a + b
```

### E. Слияние с проверкой
``` python
def merge(a, b):
    try:
        iterator_1 = iter(a)
        iterator_2 = iter(b)
    except TypeError:
        raise StopIteration
    if not (all(isinstance(i, type(a[0])) for i in a) and all(isinstance(i, type(a[0])) for i in b)):
        raise TypeError
    if list(a) != sorted(a) or list(b) != sorted(b):
        raise ValueError
    c = list(a) + list(b)
    c.sort()
    return tuple(c)
```

### F. Корень зла 2
``` python
class InfiniteSolutionsError(Exception):
    pass


class NoSolutionsError(Exception):
    pass


def find_roots(a, b, c):
    if sum(1 for i in (a, b, c) if isinstance(i, (int, float)) is True) != 3:
        raise TypeError
    elif not a and not b and not c:
        raise InfiniteSolutionsError
    elif not a and not b and c or b ** 2 < 4 * a * c:
        raise NoSolutionsError
    elif b ** 2 == 4 * a * c:
        return -b / (2 * a), -b / (2 * a)
    elif not a:
        return -c / b
    else:
        roots = [(-b - (b ** 2 - 4 * a * c) ** 0.5) / (2 * a), (-b + (b ** 2 - 4 * a * c) ** 0.5) / (2 * a)]
        roots.sort()
        return roots[0], roots[1]
```

### G. Валидация имени
``` python
class CyrillicError(Exception):
    pass


class CapitalError(Exception):
    pass


def name_validation(name):
    if not isinstance(name, str):
        raise TypeError
    if sum(i.lower() not in 'абвгдеёжзийклмнопрстуфхцчшщьыъэюя' for i in name):
        raise CyrillicError
    if name != name.lower().capitalize():
        raise CapitalError
    return name
```

### H. Валидация имени пользователя
``` python
class BadCharacterError(Exception):
    pass


class StartsWithDigitError(Exception):
    pass


def badcharacterError(name):
    for element in name:
        if element.lower() not in 'qwertyuiopasdfghjklzxcvbnm1234567890_':
            return False
    return True


def startswithdigiterror(name):
    if name[0] in '12234567890':
        return False
    return True


def username_validation(name):
    if not isinstance(name, str):
        raise TypeError
    if not badcharacterError(name):
        raise BadCharacterError
    if not startswithdigiterror(name):
        raise StartsWithDigitError
    return name
```

### I. Валидация пользователя
``` python
class CyrillicError(Exception):
    pass


class CapitalError(Exception):
    pass


class BadCharacterError(Exception):
    pass


class StartsWithDigitError(Exception):
    pass


def badcharacterError(name):
    for element in name:
        if element.lower() not in 'qwertyuiopasdfghjklzxcvbnm1234567890_':
            return False
    return True


def startswithdigiterror(name):
    if name[0] in '12234567890':
        return False
    return True


def name_validation(name):
    if not isinstance(name, str):
        raise TypeError
    if sum(i.lower() not in 'абвгдеёжзийклмнопрстуфхцчшщьыъэюя' for i in name):
        raise CyrillicError
    if name != name.lower().capitalize():
        raise CapitalError
    return name


def username_validation(name):
    if not isinstance(name, str):
        raise TypeError
    if not badcharacterError(name):
        raise BadCharacterError
    if not startswithdigiterror(name):
        raise StartsWithDigitError
    return name


def user_validation(**kwargs):
    result1 = list(map(lambda x: x in ['last_name', 'first_name', 'username'], kwargs.keys()))
    result2 = list(map(lambda x: isinstance(x, str), kwargs.values()))
    if not all(result1) or len(result1) < 3:
        raise KeyError
    if not all(result2):
        raise TypeError
    name_validation(kwargs['last_name'])
    name_validation(kwargs['first_name'])
    username_validation(kwargs['username'])
    return kwargs
```

### J. Валидация пароля
``` python
import hashlib


class MinLengthError(Exception):
    pass


class PossibleCharError(Exception):
    pass


class NeedCharError(Exception):
    pass


def password_validation(password, min_length=8,
                        possible_chars='ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789',
                        at_least_one=str.isdigit):
    if not isinstance(password, str):
        raise TypeError
    if len(password) < min_length:
        raise MinLengthError
    if any(i not in possible_chars for i in password):
        raise PossibleCharError
    if not any(map(at_least_one, password)):
        raise NeedCharError
    return hashlib.sha256(password.encode()).hexdigest()
```