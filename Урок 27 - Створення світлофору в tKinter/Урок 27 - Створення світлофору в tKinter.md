```python
import tkinter as tk

# Create main window
window = tk.Tk()
window.title("Traffic Light Simulator")
window.geometry("300x200")

# Function to change background color
def change_color(color):
    window.configure(bg=color)

# Create buttons
red_button = tk.Button(window, text="Red", bg="red", fg="white", width=10, command=lambda: change_color("red"))
yellow_button = tk.Button(window, text="Yellow", bg="yellow", width=10, command=lambda: change_color("yellow"))
green_button = tk.Button(window, text="Green", bg="green", fg="white", width=10, command=lambda: change_color("green"))

# Place buttons
red_button.pack(pady=5)
yellow_button.pack(pady=5)
green_button.pack(pady=5)

# Start the GUI loop
window.mainloop()
```
