# Урок 26 - Елементи керування: текст та кнопка в Tkinter

## Теоретична частина

[**Tkinter**](https://docs.python.org/3/library/tkinter.html) — це стандартний модуль Python для створення графічних інтерфейсів (GUI). Він дозволяє створювати вікна, кнопки, текстові поля та інші елементи керування.

Два основні елементи, які ми розглянемо в цьому уроці:
- **Label** — використовується для відображення тексту.
- **Button** — кнопка, яка виконує дію після натискання.

### Приклад коду:
```python
import tkinter as tk

def say_hello():
    label.config(text="Привіт, Tkinter!")

root = tk.Tk()
root.title("Моя перша програма")

label = tk.Label(root, text="Натисни кнопку")
label.pack()

button = tk.Button(root, text="Натисни мене", command=say_hello)
button.pack()

root.mainloop()
```
Цей код створює вікно з написом та кнопкою. При натисканні на кнопку текст змінюється.

---

## Практичні завдання

### Початковий рівень (3 бали)
**1. Створити вікно, яке містить текст "Hello, Tkinter!".**
   - Варіація: змінити розмір і колір тексту.

**2. Додати кнопку, яка змінює текст у Label.**
   - Варіація: змінити текст на випадковий з декількох варіантів.

**3. Додати ще одну кнопку, яка закриває програму.**
   - Варіація: зробити кнопку червоного кольору.

---

### Середній рівень (6 балів)
**1. Створити вікно, де кнопка змінює текст після кожного натискання.**
   - Варіація: змінювати фон вікна при натисканні.

**2. Додати поле для введення тексту та кнопку, яка змінює текст у Label на введений користувачем.**
   - Варіація: зробити кнопку активною тільки після введення тексту.

**3. Додати кнопку, яка змінює розмір тексту у Label при натисканні.**
   - Варіація: змінювати розмір довільним чином.

---

### Достатній рівень (9 балів)
**1. Створити простий лічильник натискань на кнопку.**
   - Варіація: зменшувати лічильник іншою кнопкою.

**2. Додати кілька кнопок, кожна з яких змінює текст на різний.**
   - Варіація: додати випадковий колір для кожного натискання.

**3. Реалізувати програму, де кнопка додає новий Label з випадковим текстом.**
   - Варіація: кожен новий Label матиме свій унікальний колір.

---

### Високий рівень (12 балів)
**1. Створити калькулятор, який додає два числа, введені користувачем.**
   - Варіація: розширити функціонал (віднімання, множення, ділення).

**2. Реалізувати "Світлофор": три кнопки змінюють колір Label (червоний, жовтий, зелений).**
   - Варіація: зробити автоматичне перемикання кольорів.

**3. Створити міні-гру "Вгадай число": поле введення, кнопка "Перевірити" та Label з результатом.**
   - Варіація: обмежити кількість спроб і вказувати напрямок (більше/менше).

---

``` python

import tkinter as tk
from tkinter import messagebox

# Головне вікно
root = tk.Tk()
root.title("Tkinter - Урок 26")
root.geometry("400x500")

# --- Початковий рівень (3 бали) ---
# Завдання 1: Відображення тексту
label1 = tk.Label(root, text="Привіт, Tkinter!", font=("Arial", 14))
label1.pack(pady=5)

# Завдання 2: Відображення тексту після натискання кнопки
def show_text():
    label2.config(text="Текст з'явився!")

label2 = tk.Label(root, text="", font=("Arial", 14))
label2.pack(pady=5)

button2 = tk.Button(root, text="Показати текст", command=show_text)
button2.pack(pady=5)

# Завдання 3: Кнопка змінює текст у Label
def change_label():
    label3.config(text="Текст змінено!")

label3 = tk.Label(root, text="Оригінальний текст", font=("Arial", 14))
label3.pack(pady=5)

button3 = tk.Button(root, text="Змінити текст", command=change_label)
button3.pack(pady=5)

# --- Середній рівень (6 балів) ---
# Завдання 4: Поле для введення тексту та його відображення
def display_input():
    label4.config(text=input_entry.get())

input_entry = tk.Entry(root)
input_entry.pack(pady=5)

button4 = tk.Button(root, text="Відобразити", command=display_input)
button4.pack(pady=5)

label4 = tk.Label(root, text="", font=("Arial", 14))
label4.pack(pady=5)

# Завдання 5: Лічильник натискань кнопки
counter = 0
def increment():
    global counter
    counter += 1
    label5.config(text=f"Кількість натискань: {counter}")

label5 = tk.Label(root, text="Кількість натискань: 0", font=("Arial", 14))
label5.pack(pady=5)

button5 = tk.Button(root, text="Натисни мене", command=increment)
button5.pack(pady=5)

# Завдання 6: Зміна кольору тексту
def change_color():
    label6.config(fg="blue")

label6 = tk.Label(root, text="Текст змінить колір", font=("Arial", 14))
label6.pack(pady=5)

button6 = tk.Button(root, text="Змінити колір", command=change_color)
button6.pack(pady=5)

# --- Достатній рівень (9 балів) ---
# Завдання 7: Кілька кнопок для зміни тексту
def set_text(text):
    label7.config(text=text)

label7 = tk.Label(root, text="Вибери текст", font=("Arial", 14))
label7.pack(pady=5)

button7a = tk.Button(root, text="Привіт", command=lambda: set_text("Привіт!"))
button7a.pack()

button7b = tk.Button(root, text="Python", command=lambda: set_text("Python!"))
button7b.pack()

button7c = tk.Button(root, text="Tkinter", command=lambda: set_text("Tkinter!"))
button7c.pack()

# Завдання 8: Поле для введення тексту з перевіркою
def validate_input():
    text = input8.get()
    if len(text) < 3:
        messagebox.showerror("Помилка", "Текст має бути не менше 3 символів!")
    else:
        label8.config(text=text)

input8 = tk.Entry(root)
input8.pack(pady=5)

button8 = tk.Button(root, text="Перевірити", command=validate_input)
button8.pack(pady=5)

label8 = tk.Label(root, text="", font=("Arial", 14))
label8.pack(pady=5)

# Завдання 9: Перемикач видимості тексту
def toggle_text():
    if label9.cget("text") == "":
        label9.config(text="Цей текст можна приховати")
    else:
        label9.config(text="")

label9 = tk.Label(root, text="Цей текст можна приховати", font=("Arial", 14))
label9.pack(pady=5)

button9 = tk.Button(root, text="Показати/Сховати", command=toggle_text)
button9.pack(pady=5)

# --- Високий рівень (12 балів) ---
# Завдання 10: Динамічне створення текстових елементів
def add_text():
    new_label = tk.Label(root, text="Новий текстовий елемент", font=("Arial", 12))
    new_label.pack()

button10 = tk.Button(root, text="Додати текст", command=add_text)
button10.pack(pady=5)

# Завдання 11: Поле введення з обмеженням символів
def limit_input(*args):
    text = input11.get()
    if len(text) > 10:
        input11.set(text[:10])

input11 = tk.StringVar()
input11.trace("w", limit_input)

entry11 = tk.Entry(root, textvariable=input11)
entry11.pack(pady=5)

# Завдання 12: Кнопка змінює шрифт тексту
def change_font():
    label12.config(font=("Comic Sans MS", 16, "bold"))

label12 = tk.Label(root, text="Змінюваний шрифт", font=("Arial", 14))
label12.pack(pady=5)

button12 = tk.Button(root, text="Змінити шрифт", command=change_font)
button12.pack(pady=5)


# Запуск головного циклу
root.mainloop()

```

## Висновки
Tkinter дозволяє створювати прості GUI-програми на Python. Використання елементів Label та Button допомагає реалізовувати базові функції взаємодії користувача з програмою. Наступні кроки: додати інші елементи керування (Entry, Frame, Canvas) та розширити можливості GUI.
