import tkinter as tk

def calculate(operator):
    try:
        a = float(entry1.get())
        b = float(entry2.get())

        if operator == "+":
            result = a + b
        elif operator == "-":
            result = a - b
        elif operator == "*":
            result = a * b
        elif operator == "/":
            if b == 0:
                output.config(text="Cannot divide by zero!")
                return
            result = a / b

        output.config(text=f"Result: {result:g}")

    except ValueError:
        output.config(text="Please enter valid numbers!")

def clear():
    entry1.delete(0, tk.END)
    entry2.delete(0, tk.END)
    output.config(text="Result:")

root = tk.Tk()
root.title("Calculator App")
root.geometry("350x350")

tk.Label(root, text="Python Calculator",
         font=("Arial", 18, "bold")).pack(pady=10)

entry1 = tk.Entry(root, font=("Arial", 14))
entry1.pack(pady=5)
entry1.insert(0, "10")

entry2 = tk.Entry(root, font=("Arial", 14))
entry2.pack(pady=5)
entry2.insert(0, "5")

frame = tk.Frame(root)
frame.pack(pady=15)

for operator in ["+", "-", "*", "/"]:
    tk.Button(
        frame,
        text=operator,
        width=5,
        font=("Arial", 14),
        command=lambda op=operator: calculate(op)
    ).pack(side=tk.LEFT, padx=3)

output = tk.Label(root, text="Result:",
                  font=("Arial", 14))
output.pack(pady=10)

tk.Button(root, text="Clear",
          command=clear).pack(pady=5)

root.mainloop()