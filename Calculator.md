import tkinter as tk

def press(key):
    current = result_var.get()
    if key == "=":
        try:
            result = eval(current)
            result_var.set(result)
        except Exception as e:
            result_var.set("Error")
    elif key == "C":
        result_var.set("")
    else:
        result_var.set(current + key)

root = tk.Tk()
root.title("Simple Calculator")

result_var = tk.StringVar()
result_var.set("")

entry = tk.Entry(root, textvariable=result_var, font=("Helvetica", 16), justify="right")
entry.grid(row=0, column=0, columnspan=4)

buttons = [
    "7", "8", "9", "+",
    "4", "5", "6", "-",
    "1", "2", "3", "*",
    "C", "0", "=", "/"
]

row_val = 1
col_val = 0

for button in buttons:
    tk.Button(root, text=button, font=("Helvetica", 16), width=5, height=2, command=lambda key=button: press(key)).grid(row=row_val, column=col_val)
    col_val += 1
    if col_val > 3:
        col_val = 0
        row_val += 1

root.mainloop()
