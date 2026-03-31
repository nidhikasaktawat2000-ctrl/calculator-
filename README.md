# calculator-
A GUI-based calculator developed using Python (Tkinter) that performs basic arithmetic operations like addition, subtraction, multiplication, and division.

import tkinter as tk

def press(num):
    entry.insert(tk.END, str(num))

def clear():
    entry.delete(0, tk.END)

def calculate():
    result = eval(entry.get())
    entry.delete(0, tk.END)
    entry.insert(0, str(result))

# Window
root = tk.Tk()
root.title("Calculator")
root.geometry("300x400")
root.configure(bg="pink")

# Display
entry = tk.Entry(
    root,
    font=("Arial", 22),
    bg="black",
    fg="white",
    bd=0,
    justify="right",
    highlightthickness=0,
    insertbackground="pink"
)
entry.grid(row=0, column=0, columnspan=4, ipadx=8, ipady=20, pady=10)

# Buttons
buttons = [
    ('7','8','9','/'),
    ('4','5','6','*'),
    ('1','2','3','-'),
    ('0','.','=','+')
]

for i, row in enumerate(buttons):
    for j, val in enumerate(row):
        if val == "=":
            action = calculate
        else:
            action = lambda x=val: press(x)

        tk.Button(
            root,
            text=val,
            width=5,
            height=2,
            font=("Arial", 14),
            bg="#333",
            fg="white",
            command=action
        ).grid(row=i+1, column=j, padx=5, pady=5)

# Clear button
tk.Button(
    root,
    text="C",
    width=22,
    height=2,
    font=("Arial", 14),
    bg="red",
    fg="white",
    command=clear
).grid(row=5, column=0, columnspan=4, pady=10)

root.mainloop()


