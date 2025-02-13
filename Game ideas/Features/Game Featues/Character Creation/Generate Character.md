import random

class Character:
    def __init__(self):
        self.abilities = {
            "Strength": self.roll_3d6(),
            "Intelligence": self.roll_3d6(),
            "Wisdom": self.roll_3d6(),
            "Dexterity": self.roll_3d6(),
            "Constitution": self.roll_3d6(),
            "Charisma": self.roll_3d6()
        }
        self.ability_bonuses = self.calculate_bonuses()
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

    def choose_race(self, race):
        race_restrictions = {
            "Dwarf": {"min": {"Constitution": 9}, "max": {"Charisma": 17}, "classes": ["Cleric", "Fighter", "Thief"]},
            "Elf": {"min": {"Intelligence": 9}, "max": {"Constitution": 17}, "classes": ["Cleric", "Fighter", "Magic-User", "Thief", "Fighter/Magic-User", "Magic-User/Thief"]},
            "Halfling": {"min": {"Dexterity": 9}, "max": {"Strength": 17}, "classes": ["Cleric", "Fighter", "Thief"]},
            "Human": {"min": {}, "max": {}, "classes": ["Any"]}
        }
        if self.validate_race(race, race_restrictions[race]):
            self.race = race
            print(f"Race chosen: {race}")
        else:
            print(f"{race} does not meet the ability requirements.")

    def validate_race(self, race, restrictions):
        for ability, min_value in restrictions["min"].items():
            if self.abilities[ability] < min_value:
                return False
        for ability, max_value in restrictions["max"].items():
            if self.abilities[ability] > max_value:
                return False
        return True

    def choose_class(self, character_class):
        class_requirements = {
            "Cleric": {"Prime Requisite": "Wisdom", "min": 9},
            "Fighter": {"Prime Requisite": "Strength", "min": 9},
            "Magic-User": {"Prime Requisite": "Intelligence", "min": 9},
            "Thief": {"Prime Requisite": "Dexterity", "min": 9}
        }
        if self.abilities[class_requirements[character_class]["Prime Requisite"]] >= class_requirements[character_class]["min"]:
            self.character_class = character_class
            print(f"Class chosen: {character_class}")
        else:
            print(f"{character_class} does not meet the ability requirements.")

    def calculate_hit_points(self):
        hit_die = {
            "Cleric": 6,
            "Fighter": 8,
            "Magic-User": 4,
            "Thief": 4
        }
        self.hit_points = max(1, random.randint(1, hit_die[self.character_class]) + self.ability_bonuses["Constitution"])

    def roll_gold(self):
        self.gold = sum(random.randint(1, 6) for _ in range(3)) * 10

    def purchase_equipment(self):
        equipment_list = {
            "Weapons": {
                "Dagger": 3,
                "Longsword": 15,
                "Shortbow": 25,
                "Crossbow": 30,
                "Mace": 5,
                "Spear": 2,
                "Axe": 7
            },
            "Armor": {
                "Leather": 20,
                "Chainmail": 40,
                "Plate": 50,
                "Shield": 10
            },
            "Miscellaneous": {
                "Rope": 1,
                "Torch": 1,
                "Backpack": 5,
                "Rations": 5,
                "Waterskin": 1
            }
        }
        print("Available Equipment:")
        for category, items in equipment_list.items():
            print(f"{category}:")
            for item, cost in items.items():
                print(f"  {item}: {cost} gold pieces")

        while True:
            choice = input("Enter the equipment to purchase (or 'done' to finish): ").strip()
            if choice.lower() == "done":
                break
            for category, items in equipment_list.items():
                if choice in items:
                    if self.gold >= items[choice]:
                        self.gold -= items[choice]
                        self.equipment.append(choice)
                        print(f"Purchased {choice}. Remaining gold: {self.gold}")
                    else:
                        print(f"Not enough gold to purchase {choice}.")
                    break
            else:
                print(f"{choice} is not a valid item.")

    def calculate_armor_class(self):
        base_ac = 10  # Base Armor Class for unarmored
        armor_bonus = {
            "Leather": 2,
            "Chainmail": 4,
            "Plate": 6,
            "Shield": 1
        }
        self.armor_class = base_ac + self.ability_bonuses["Dexterity"]
        for item in self.equipment:
            if item in armor_bonus:
                self.armor_class += armor_bonus[item]

    def calculate_attack_bonus(self):
        attack_bonus_table = {
            "Cleric": 1,
            "Fighter": 2,
            "Magic-User": 0,
            "Thief": 1
        }
        self.attack_bonus = attack_bonus_table[self.character_class] + self.ability_bonuses["Strength"]

    def calculate_saving_throws(self):
        saving_throw_base = {
            "Cleric": {"Death Ray or Poison": 11, "Magic Wands": 12, "Paralysis or Petrify": 14, "Dragon Breath": 16, "Spells": 15},
            "Fighter": {"Death Ray or Poison": 12, "Magic Wands": 13, "Paralysis or Petrify": 14, "Dragon Breath": 15, "Spells": 16},
            "Magic-User": {"Death Ray or Poison": 13, "Magic Wands": 14, "Paralysis or Petrify": 13, "Dragon Breath": 16, "Spells": 15},
            "Thief": {"Death Ray or Poison": 12, "Magic Wands": 13, "Paralysis or Petrify": 14, "Dragon Breath": 16, "Spells": 15}
        }
        self.saving_throws = saving_throw_base[self.character_class]
        race_saving_bonus = {
            "Dwarf": {"Death Ray or Poison": 4, "Magic Wands": 4, "Paralysis or Petrify": 4, "Dragon Breath": 3, "Spells": 4},
            "Elf": {"Paralysis or Petrify": 1, "Magic Wands": 2, "Spells": 2},
            "Halfling": {"Death Ray or Poison": 4, "Magic Wands": 4, "Paralysis or Petrify": 4, "Dragon Breath": 3, "Spells": 4},
            "Human": {}
        }
        for save, bonus in race_saving_bonus.get(self.race, {}).items():
            self.saving_throws[save] -= bonus

    def generate_character(self):
        self.choose_race(input("Choose a race (Dwarf, Elf, Halfling, Human): "))
        self.choose_class(input("Choose a class (Cleric, Fighter, Magic-User, Thief): "))
        self.calculate_hit_points()
        self.roll_gold()
        self.purchase_equipment()
        self.calculate_armor_class()
        self.calculate_attack_bonus()
        self.calculate_saving_throws()
        self.name = input("Enter character name: ")

    def display_character(self):
        print(f"\nName: {self.name}")
        print(f"Race: {self.race}")
        print(f"Class: {self.character_class}")
        print(f"Abilities: {self.abilities}")
        print(f"Ability Bonuses: {self.ability_bonuses}")
        print(f"Hit Points: {self.hit_points}")
        print(f"Gold: {self.gold}")
        print(f"Equipment: {self.equipment}")
        print(f"Armor Class: {self.armor_class}")
        print(f"Attack Bonus: {self.attack_bonus}")
        print(f"Saving Throws: {self.saving_throws}")

# Example usage
character = character()
character.generate_character()
character.display_character()
