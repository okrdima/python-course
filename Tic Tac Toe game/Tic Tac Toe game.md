```python
import tkinter as tk
from tkinter import messagebox

# Глобальні змінні
current_player = "X"  # Поточний гравець
board = [[None] * 3 for _ in range(3)]  # Сітка 3x3 (список кнопок)


def make_move(row: int, col: int):
    """
    Обробляє хід гравця.

    Перевіряє, чи клітинка порожня, встановлює символ гравця,
    перевіряє переможця або нічию і змінює гравця.

    :param row: Рядок натиснутої кнопки
    :param col: Стовпець натиснутої кнопки

    Посилання на Button: https://tkdocs.com/shipman/button.html
    """
    global current_player
    button = board[row][col]

    if button["text"] == "":  # Якщо кнопка порожня, дозволяємо хід
        button["text"] = current_player  # Встановлюємо X або O

        if check_winner(current_player):  # Перевіряємо, чи виграв гравець
            messagebox.showinfo("Game Over", f"{current_player} wins!")
            disable_buttons()
        elif is_draw():  # Якщо поле заповнене, оголошуємо нічию
            messagebox.showinfo("Game Over", "It's a draw!")
            disable_buttons()
        else:
            current_player = "O" if current_player == "X" else "X"  # Зміна гравця


def check_winner(player: str) -> bool:
    """
    Перевіряє, чи є переможець у грі.

    Перевіряє рядки, стовпці і діагоналі на наявність трьох однакових символів.

    :param player: Символ гравця ('X' або 'O')
    :return: True, якщо гравець виграв, інакше False
    """
    for i in range(3):
        if all(board[i][j]["text"] == player for j in range(3)) or \
           all(board[j][i]["text"] == player for j in range(3)):
            return True
    if all(board[i][i]["text"] == player for i in range(3)) or \
       all(board[i][2 - i]["text"] == player for i in range(3)):
        return True
    return False


def is_draw() -> bool:
    """
    Перевіряє, чи настала нічия (всі клітинки заповнені).

    :return: True, якщо поле заповнене і немає переможця, інакше False
    """
    return all(board[row][col]["text"] != "" for row in range(3) for col in range(3))


def disable_buttons():
    """
    Відключає всі кнопки після завершення гри.
    """
    for row in range(3):
        for col in range(3):
            board[row][col]["state"] = "disabled"


def restart_game():
    """
    Очищає поле та починає гру заново.

    Посилання на Button.config: https://tkdocs.com/shipman/button.html
    """
    global current_player
    current_player = "X"
    for row in range(3):
        for col in range(3):
            board[row][col]["text"] = ""
            board[row][col]["state"] = "normal"


# Створення головного вікна гри
root = tk.Tk()
root.title("Tic-Tac-Toe")  # https://tkdocs.com/shipman/toplevel.html

# Створення кнопок (ігрове поле 3x3)
for row in range(3):
    for col in range(3):
        button = tk.Button(root, text="", font=("Arial", 20), width=5, height=2,
                           command=lambda r=row, c=col: make_move(r, c))
        button.grid(row=row, column=col)  # https://tkdocs.com/shipman/grid.html
        board[row][col] = button  # Зберігаємо кнопку в списку

# Кнопка "Restart" для початку нової гри
restart_button = tk.Button(root, text="Restart", font=("Arial", 14), command=restart_game)
restart_button.grid(row=3, column=0, columnspan=3)

# Запуск головного циклу Tkinter
root.mainloop()  # https://tkdocs.com/shipman/mainloop.html


```
