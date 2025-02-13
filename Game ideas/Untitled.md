import random
from enum import Enum

class Race(Enum):
    DWARF = ("Dwarves", {"Cleric": {"min": 9, "max": 17}, "Fighter": {}, "Thief": {}})
    ELF = ("Elves", {"Cleric": {"min": 9, "max": 17}, "Fighter": {"min": 9, "max": 17}, "Magic-User": {"min": 9, "max": 17}, "Thief": {"min": 9, "max": 17}})
    HALFLING = ("Halflings", {"Cleric": {"min": 9, "max": 17}, "Fighter": {"min": 9, "max": 17}, "Thief": {"min": 9, "max": 17}})
    HUMAN = ("Humans", {})

class Character:
    def __init__(self):
        self.abilities = {}
        self.ability_bonuses = {}
        self.race = None
        self.character_class = None
        self.hit_points = 0
        self.experience_points = 0
        self.gold = 0
        self.equipment = []
        self.armor_class = 0
        self.attack_bonus = 0
        self.saving_throws = {}
        self.name = ""

    def roll_3d6(self):
        return sum(random.randint(1, 6) for _ in range(3))

    def generate_character(self):
        self.abilities = {
            "Strength": self.roll_3d6(),
            "Intelligence": self.roll_3d6(),
            "Wisdom": self.roll_3d6(),
            "Dexterity": self.roll_3d6(),
            "Constitution": self.roll_3d6(),
            "Charisma": self.roll_3d6()
        }
        self.ability_bonuses = self.calculate_bonuses()

        self.choose_race()
        self.choose_class()
        self.calculate_hit_points()
        self.roll_gold()
        self.purchase_equipment()
        self.calculate_armor_class()
        self.calculate_attack_bonus()
        self.calculate_saving_throws()

        self.name = input("Enter character name: ")

    def calculate_bonuses(self):
        bonus_table = {
            range(3, 4): -3,
            range(4, 6): -2,
            range(6, 9): -1,
            range(9, 13): 0,
            range(13, 16): 1,
            range(16, 18): 2,
            range(18, 19): 3
        }
        return {key: next(value for k, value in bonus_table.items() if key in k) for key in self.abilities.values()}

    def choose_race(self):
        print("\nAvailable Races:")
        for race in Race:
            print(f"{race.name.capitalize()} ({race.value[0]})")
            print(f"Description: {race.value[0]}")
            print(f"Restrictions:\n{race.value[1]}\n")
        
        selected_race_name = input("Choose a race: ").upper()
        if selected_race_name in [race.name for race in Race]:
            self.race = Race[selected_race_name]
            print(f"Race chosen: {self.race.name.capitalize()}")
        else:
            print(f"{selected_race_name} is not a recognized race.")

    def choose_class(self):
        print("Available Classes:", [class_.name for class_ in CharacterClass])
        selected_class = input("Choose a class: ").upper()
        if selected_class in [class_.name for class_ in CharacterClass]:
            self.character_class = CharacterClass[selected_class]
            print(f"Class chosen: {self.character_class.name}")
        else:
            print(f"{selected_class} is not a recognized class.")

# Assuming CharacterClass Enum and other methods are not yet defined.
# Example usage
character = Character()
character.generate_character()
print(character.__dict__)