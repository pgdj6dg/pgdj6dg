import tkinter as tk

# List of fruits
fruits = [
    "Bari Bari no Mi", "Bara Bara no Mi", "Buddha Buddha no Mi", "Chop Chop Fruit",
    "Dark Dark Fruit", "Diamond Fruit", "Flame Flame Fruit", "Gum Gum Fruit",
    "Ice Ice Fruit", "Light Light Fruit", "Magma Magma Fruit", "Mera Mera no Mi",
    "Mochi Mochi no Mi", "Nika Nika no Mi", "Quake Quake Fruit", "Rumble Rumble Fruit",
    "Shadow Shadow Fruit", "Smoke Smoke Fruit", "Snow Snow Fruit", "Spirit Spirit Fruit",
    "String String Fruit", "Suke Suke no Mi", "Tori Tori no Mi", "Venom Venom Fruit",
    "Yami Yami no Mi", "Zushi Zushi no Mi", "Boo Fruit", "Frog Fruit", "Dough Fruit",
    "Control Fruit", "Phoenix Fruit", "Kilo Kilo Fruit", "Rumble Fruit", "Barrier Fruit",
    "Bishop Fruit", "Blizzard Fruit", "Bounty Fruit", "Fist Fruit", "Guardian Fruit",
    "Kumo Kumo no Mi", "Rao Rao no Mi", "Tama Tama no Mi", "Tonkotsu no Mi", "Yuki Yuki no Mi",
    "Horo Horo no Mi", "Gura Gura no Mi", "Ope Ope no Mi", "Hito Hito no Mi", "Mizu Mizu no Mi",
    "Bara Bara no Mi", "Hana Hana no Mi", "Suna Suna no Mi", "Yoru Yoru no Mi", "Ito Ito no Mi",
    "Mero Mero no Mi", "Baku Baku no Mi", "Mochi Mochi no Mi", "Nomi Nomi no Mi", "Raki Raki no Mi",
    "Suke Suke no Mi", "Tori Tori no Mi", "Pika Pika no Mi", "Noro Noro no Mi", "Oshi Oshi no Mi",
    "Ryu Ryu no Mi", "Ushi Ushi no Mi", "Kizuna no Mi", "Gumo Gumo no Mi", "Paw Paw no Mi",
    "Yuki Yuki no Mi", "Hito Hito no Mi"
]

# Function to "spawn" a fruit (prints to console)
def spawn_fruit(fruit_name):
    print(f"Spawned fruit: {fruit_name}")

# Create the GUI
root = tk.Tk()
root.title("Fruit Selection")
root.geometry("400x600")

# Add a label
title_label = tk.Label(root, text="Select a Fruit:", font=("Arial", 14, "bold"))
title_label.pack(pady=10)

# Create buttons for each fruit
for fruit in fruits:
    btn = tk.Button(root, text=fruit, command=lambda f=fruit: spawn_fruit(f), width=25, height=1)
    btn.pack(pady=2)

# Run the GUI loop
root.mainloop()
