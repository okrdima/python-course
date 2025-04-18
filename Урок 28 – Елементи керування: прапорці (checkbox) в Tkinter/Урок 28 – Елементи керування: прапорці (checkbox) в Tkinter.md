# Урок 27 – Елементи керування: прапорці (checkbox) в Tkinter

## Теоретична частина

**Tkinter** — це стандартний модуль для створення графічного інтерфейсу (GUI) в Python. Одним із елементів керування є **прапорець** (checkbox), який дозволяє користувачу вибрати один або декілька варіантів.

**Checkbutton** — віджет прапорця в tkinter.

```python
from tkinter import *

root = Tk()

var = IntVar()
cb = Checkbutton(root, text="Погоджуюсь", variable=var)
cb.pack()

root.mainloop()
```

---

## Рівень: Початковий (3 бали)

### Завдання 1: Прапорець згоди
**Завдання:** Створи вікно з одним прапорцем "Погоджуюсь".

#### Код:
```python
from tkinter import *

root = Tk()
root.title("Прапорець")

var = IntVar()
cb = Checkbutton(root, text="Погоджуюсь", variable=var)
cb.pack()

root.mainloop()
```

**Варіації:** змінити текст прапорця; додати кнопку "OK".

---

### Завдання 2: Обери колір
**Завдання:** Створи три прапорці з назвами кольорів: "Червоний", "Зелений", "Синій".

#### Код:
```python
from tkinter import *

root = Tk()
root.title("Обери колір")

red = IntVar()
green = IntVar()
blue = IntVar()

Checkbutton(root, text="Червоний", variable=red).pack()
Checkbutton(root, text="Зелений", variable=green).pack()
Checkbutton(root, text="Синій", variable=blue).pack()

root.mainloop()
```

**Варіації:** змінити список кольорів.

---

### Завдання 3: Проста анкета
**Завдання:** Створи анкету з питанням "Які мови програмування ти знаєш?" та прапорцями: Python, Java, C++.

#### Код:
```python
from tkinter import *

root = Tk()
root.title("Анкета")

Label(root, text="Які мови програмування ти знаєш?").pack()
py = IntVar()
java = IntVar()
cpp = IntVar()

Checkbutton(root, text="Python", variable=py).pack()
Checkbutton(root, text="Java", variable=java).pack()
Checkbutton(root, text="C++", variable=cpp).pack()

root.mainloop()
```

**Варіації:** змінити запитання та варіанти.

---

## Рівень: Середній (6 балів)

### Завдання 1: Показати вибір
**Завдання:** Створи 3 прапорці з назвами фруктів. Після натискання кнопки — показати обрані фрукти в Label.

#### Код:
```python
from tkinter import *

def show_selection():
    result = ""
    if apple.get(): result += "Яблуко\n"
    if banana.get(): result += "Банан\n"
    if orange.get(): result += "Апельсин\n"
    label_result.config(text=result)

root = Tk()
root.title("Фрукти")

apple = IntVar()
banana = IntVar()
orange = IntVar()

Checkbutton(root, text="Яблуко", variable=apple).pack()
Checkbutton(root, text="Банан", variable=banana).pack()
Checkbutton(root, text="Апельсин", variable=orange).pack()

Button(root, text="Показати вибір", command=show_selection).pack()
label_result = Label(root, text="")
label_result.pack()

root.mainloop()
```

**Варіації:** змінити назви прапорців; додати ще один елемент.

---

### Завдання 2: Обрати хобі
**Завдання:** Створи вікно, де можна обрати одне або кілька хобі (читання, спорт, музика). Після натискання кнопки — відобразити вибір у текстовому полі.

#### Код:
```python
from tkinter import *

def show_hobbies():
    selected = []
    if reading.get(): selected.append("Читання")
    if sport.get(): selected.append("Спорт")
    if music.get(): selected.append("Музика")
    result.delete(0, END)
    result.insert(0, ", ".join(selected))

root = Tk()
root.title("Хобі")

reading = IntVar()
sport = IntVar()
music = IntVar()

Checkbutton(root, text="Читання", variable=reading).pack()
Checkbutton(root, text="Спорт", variable=sport).pack()
Checkbutton(root, text="Музика", variable=music).pack()

Button(root, text="Обрати", command=show_hobbies).pack()
result = Entry(root)
result.pack()

root.mainloop()
```

**Варіації:** замінити Entry на Label; додати ще варіанти.

---

### Завдання 3: Обрати улюблені тварини
**Завдання:** Створи перелік тварин з прапорцями та кнопкою "Зберегти вибір". Виводь результат в Label.

#### Код:
```python
from tkinter import *

def save():
    selected = []
    if cat.get(): selected.append("Кіт")
    if dog.get(): selected.append("Собака")
    if hamster.get(): selected.append("Хом'як")
    result.config(text=", ".join(selected))

root = Tk()
root.title("Улюблені тварини")

cat = IntVar()
dog = IntVar()
hamster = IntVar()

Checkbutton(root, text="Кіт", variable=cat).pack()
Checkbutton(root, text="Собака", variable=dog).pack()
Checkbutton(root, text="Хом'як", variable=hamster).pack()

Button(root, text="Зберегти вибір", command=save).pack()
result = Label(root, text="")
result.pack()

root.mainloop()
```

**Варіації:** замінити список тварин на іграшки або кольори.

---

## Рівень: Достатній (9 балів)

### Завдання 1: Обери предмети для навчання
**Завдання:** Створи перелік предметів з прапорцями. При натисканні кнопки — обрані предмети додаються в список (Listbox).

#### Код:
```python
from tkinter import *

def update():
    listbox.delete(0, END)
    if math.get(): listbox.insert(END, "Математика")
    if physics.get(): listbox.insert(END, "Фізика")
    if it.get(): listbox.insert(END, "Інформатика")

root = Tk()
root.title("Предмети")

math = IntVar()
physics = IntVar()
it = IntVar()

Checkbutton(root, text="Математика", variable=math).pack()
Checkbutton(root, text="Фізика", variable=physics).pack()
Checkbutton(root, text="Інформатика", variable=it).pack()

Button(root, text="Обрати", command=update).pack()
listbox = Listbox(root)
listbox.pack()

root.mainloop()
```

**Варіації:** змінити список предметів.

---

### Завдання 2: Оцінка подій
**Завдання:** Створи вікно з прапорцями для подій: "Весело", "Цікаво", "Повчально". При виборі — з’являється відповідний коментар.

#### Код:
```python
from tkinter import *

def show_comments():
    comment = ""
    if fun.get(): comment += "Це було весело!\n"
    if interesting.get(): comment += "Цікаві факти!\n"
    if useful.get(): comment += "Можна застосувати на практиці."
    label_comment.config(text=comment)

root = Tk()
root.title("Оцінка подій")

fun = IntVar()
interesting = IntVar()
useful = IntVar()

Checkbutton(root, text="Весело", variable=fun).pack()
Checkbutton(root, text="Цікаво", variable=interesting).pack()
Checkbutton(root, text="Повчально", variable=useful).pack()

Button(root, text="Показати коментар", command=show_comments).pack()
label_comment = Label(root, text="")
label_comment.pack()

root.mainloop()
```

**Варіації:** змінити коментарі або додати оцінку (числом).

---

### Завдання 3: Конструктор піци
**Завдання:** Створи прапорці для інгредієнтів піци: "Сир", "Ковбаса", "Оливки". При натисканні кнопки — відображай вибір.

#### Код:
```python
from tkinter import *

def make_pizza():
    ingredients = []
    if cheese.get(): ingredients.append("Сир")
    if sausage.get(): ingredients.append("Ковбаса")
    if olives.get(): ingredients.append("Оливки")
    result.config(text="Піца з: " + ", ".join(ingredients))

root = Tk()
root.title("Конструктор піци")

cheese = IntVar()
sausage = IntVar()
olives = IntVar()

Checkbutton(root, text="Сир", variable=cheese).pack()
Checkbutton(root, text="Ковбаса", variable=sausage).pack()
Checkbutton(root, text="Оливки", variable=olives).pack()

Button(root, text="Зробити піцу", command=make_pizza).pack()
result = Label(root, text="")
result.pack()

root.mainloop()
```

**Варіації:** змінити інгредієнти або додати картинки.

---

## Рівень: Високий (12 балів)

### Завдання 1: Тест з прапорцями
**Завдання:** Створи запитання з кількома правильними відповідями. Після натискання "Перевірити" — показати правильність.

### Завдання 2: Графік занять
**Завдання:** Створи прапорці для днів тижня. Користувач обирає дні занять, а після натискання кнопки — з’являється список днів.

### Завдання 3: Замовлення обіду
**Завдання:** Створи прапорці з позиціями меню. Після вибору та натискання кнопки — виводиться обране та загальна сума.

> Ці 3 останні завдання можу реалізувати окремо, якщо потрібно. Хочеш додати також коди до рівня "Високий"?
