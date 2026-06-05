# Button-mwnager
import tkinter as tk
import webbrowser
import time
import os

print("=== Widget Constructor ===")
print("Commands: <win>, <button>, <geometry>")

a = input("• ")

if a == "<win>":
    color = input("Background color: ")
    window = tk.Tk()
    window.configure(bg=color)
    window.title("My widget")

elif a == "<geometry>":
    w = input("Window width: ")
    h = input("Window height: ")
    x = input("Position X (optional, press Enter for center): ")
    y = input("Position Y (optional, press Enter for center): ")
    
    if x and y:
        window.geometry(f"{w}x{h}+{x}+{y}")
    else:
        window.geometry(f"{w}x{h}")

elif a == "<button>":
    text = input("Button text: ")
    color = input("Button color: ")
    print("Commands: open_browser, open_yandex, open_github, print_hi, print_time, clear_console, custom")
    cmd = input("Command: ")

    if cmd == "open_browser":
        def action():
            webbrowser.open("https://google.com")
    elif cmd == "open_yandex":
        def action():
            webbrowser.open("https://yandex.ru")
    elif cmd == "open_github":
        def action():
            webbrowser.open("https://github.com")
    elif cmd == "print_hi":
        def action():
            print("Hello from your widget!")
    elif cmd == "print_time":
        def action():
            print(time.ctime())
    elif cmd == "clear_console":
        def action():
            os.system("cls" if os.name == "nt" else "clear")
    elif cmd == "custom":
        print("Enter your own Python code (one line):")
        user_code = input(">>> ")
        def action():
            exec(user_code)
    else:
        def action():
            print("Unknown command")

    window = tk.Tk()
    window.title("My widget")
    window.geometry("400x300")

    button = tk.Button(window, text=text, bg=color, command=action)
    button.pack(pady=50)

if 'window' in dir():
    window.mainloop()