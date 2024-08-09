import random
import tkinter as tk

# Define the lists of options
light_weapons = ["93R", "DAGGER", "LH1", "M11", "RECURVE BOW", "SH1900", "SR-84", "SWORD", "THROWING KNIVES", "V9S", "XP-54"]
medium_weapons = ["AKM", "CL-40", "DUAL BLADES", "FAMAS", "FCAR", "MODEL 1887", "R .357", "RIOT SHIELD"]
heavy_weapons = ["FLAMETHROWER", "KS-23", "LEWIS GUN", "M60", "MGL32", "SA1216", "SLEDGEHAMMER", "SPEAR"]

light_gadgets = ["BREACH CHARGE", "GATEWAY", "GLITCH GRENADE", "SMOKE GRENADE", "SONAR GRENADE", "STUN GUN", "THERMAL BORE", "THERMAL VISION", "TRACKING DART", "VANISHING BOMB", "FLASHBANG", "FRAG GRENADE", "GAS GRENADE", "GOO GRENADE", "PYRO GRENADE"]
medium_gadgets = ["APS TURRET", "DATA RESHAPER", "DEFIBRILLATOR", "EXPLOSIVE MINE", "GAS MINE", "GLITCH TRAP", "JUMP PAD", "ZIPLINE", "FLASHBANG", "FRAG GRENADE", "GAS GRENADE", "GOO GRENADE", "PYRO GRENADE"]
heavy_gadgets = ["ANTI-GRAVITY CUBE", "BARRICADE", "C4", "DOME SHIELD", "EXPLOSIVE MINE", "MOTION SENSOR", "PYRO MINE", "RPG-7", "FLASHBANG", "FRAG GRENADE", "GAS GRENADE", "GOO GRENADE", "PYRO GRENADE"]

# Specializations specific to each class
light_specializations = ["CLOAKING DEVICE", "EVASIVE DASH", "GRAPPLING HOOK"]
medium_specializations = ["DEMATERIALIZER", "GUARDIAN TURRET", "HEALING BEAM"]
heavy_specializations = ["CHARGE 'N' SLAM", "GOO GUN", "MESH SHIELD", "WHINCH CLAW"]

# Function to generate a random loadout
def generate_loadout():
    build = random.choice(["LIGHT", "MEDIUM", "HEAVY"])
    
    if build == "LIGHT":
        weapon = random.choice(light_weapons)
        gadgets = random.sample(light_gadgets, 3)
        specialization = random.choice(light_specializations)
    elif build == "MEDIUM":
        weapon = random.choice(medium_weapons)
        gadgets = random.sample(medium_gadgets, 3)
        specialization = random.choice(medium_specializations)
    elif build == "HEAVY":
        weapon = random.choice(heavy_weapons)
        gadgets = random.sample(heavy_gadgets, 3)
        specialization = random.choice(heavy_specializations)

    return f"Build: {build}\nWeapon: {weapon}\nGadget: {gadgets[0]}\nGadget: {gadgets[1]}\nGadget: {gadgets[2]}\nSpec: {specialization}"

# Function to update the loadout display
def update_loadout(label):
    loadout = generate_loadout()
    label.config(text=loadout)

# Create the GUI application
def show_loadout():
    # Create the main window
    root = tk.Tk()
    root.title("The Finals Random Loadout")
    root.configure(bg="red")

    # Initial loadout
    loadout = generate_loadout()

    # Display the loadout
    label = tk.Label(root, text=loadout, bg="red", fg="white", font=("Saira ExtraCondensed ExtraBold", 20))
    label.pack(padx=65, pady=20)

    # Add a "Refresh Loadout" button
    refresh_button = tk.Button(root, text="Refresh Loadout", command=lambda: update_loadout(label), font=("Saira ExtraCondensed ExtraBold", 16))
    refresh_button.pack(pady=10)

    # Start the GUI event loop
    root.mainloop()

# Run the application
if __name__ == "__main__":
    show_loadout()
