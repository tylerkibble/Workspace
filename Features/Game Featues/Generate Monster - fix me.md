import random

class Monster:
    def __init__(self, level=1):  # Added level parameter for flexibility
        self.name = self.generate_name()
        self.hit_points = self.roll_hit_points()
        self.abilities = self.generate_abilities()
        self.armor_class = self.generate_armor_class()
        self.attack_bonus = self.generate_attack_bonus()
        self.saving_throws = self.generate_saving_throws()
        self.loot = self.generate_loot(level)

    def generate_name(self):
        prefixes = ["Dire", "Giant", "Savage", "Vicious", "Terrifying", "Mystic", "Elder", "Ancient"]
        creatures = ["Goblin", "Orc", "Troll", "Dragon", "Skeleton", "Zombie", "Beast", "Wyrm", "Faerie", "Demon", "Angel"]
        return f"{random.choice(prefixes)} {random.choice(creatures)}"

    def roll_hit_points(self):
        return random.randint(5, 50)

    def generate_abilities(self):
        abilities = {
            "Strength": random.randint(3, 18),
            "Intelligence": random.randint(3, 18),
            "Wisdom": random.randint(3, 18),
            "Dexterity": random.randint(3, 18),
            "Constitution": random.randint(3, 18),
            "Charisma": random.randint(3, 18)
        }
        return abilities

    def generate_armor_class(self):
        return random.randint(10, 20)

    def generate_attack_bonus(self):
        return random.randint(1, 5)

    def generate_saving_throws(self):
        return {
            "Death Ray or Poison": random.randint(10, 20),
            "Magic Wands": random.randint(10, 20),
            "Paralysis or Petrify": random.randint(10, 20),
            "Dragon Breath": random.randint(10, 20),
            "Spells": random.randint(10, 20)
        }

    def generate_magic_weapon(self):
        weapon_types = [
            "Great Axe", "Battle Axe", "Hand Axe", "Shortbow", "Longbow", "Light Quarrel",
            "Dagger", "Shortsword", "Longsword", "Scimitar", "Two-Handed Sword", "Warhammer", "Mace", "Pole Arm", "Spear"
        ]
        bonuses = ["+1", "+2", "+3", "+4", "+5"]
        special_enemies = ["Dragons", "Enchanted", "Lycanthropes", "Spell Users", "Undead"]
        special_abilities = [
            "Casts Light on Command", "Charm Person", "Drains Energy", "Flames on Command", "Locate Objects", "Wishes"
        ]

        weapon_type = random.choice(weapon_types)
        bonus_roll = random.randint(1, 100)
        if bonus_roll <= 40:
            bonus = "+1"
        elif bonus_roll <= 50:
            bonus = "+2"
        elif bonus_roll <= 55:
            bonus = "+3"
        elif bonus_roll <= 57:
            bonus = "+4"
        else:
            bonus = "+5"

        special_enemy_roll = random.randint(1, 6)
        special_ability_roll = random.randint(1, 20)

        if bonus_roll >= 86:
            special_ability = random.choice(special_abilities)
            if special_ability_roll > 12:
                special_ability = ""  # Ignore multiple rolls on Special Ability table
            return f"{weapon_type} +{bonus}, +{bonus} vs. {special_enemies[special_enemy_roll - 1}, {special_ability}"
        else:
            return f"{weapon_type} +{bonus}"

    def generate_potion(self):
        potion_types = [
            "Clairaudience", "Cold Resistance", "Control Animal", "Flying", "Gaseous Form",
            "Healing", "Heroism", "Invisibility", "Levitation", "Mind Reading", "Poison", "Speed", "Treasure Finding"
        ]
        return random.choice(potion_types)

    def generate_scroll(self):
        scroll_types = [
            "Cleric Spell Scroll (1 Spell)", "Magic-User Spell Scroll (1 Spell)",
            "Protection from Elementals", "Protection from Lycanthropes", "Protection from Magic",
            "Protection from Undead", "Map to Treasure Type A", "Map to Treasure Type E"
        ]
        return random.choice(scroll_types)

    def generate_loot(self, level):
        loot_types = ['copper', 'silver', 'gold', 'platinum', 'gems']
        magic_items = ['magic_weapon', 'potion', 'scroll']

        if level < 3:
            loot = [random.choice(loot_types)]
        elif level < 6:
            loot = [random.choice(loot_types), random.choice(magic_items)]
        else:
            loot = [random.choice(magic_items)]

        generated_loot = []
        for item in loot:
            if item == 'magic_weapon':
                generated_loot.append(self.generate_magic_weapon())
            elif item == 'potion':
                generated_loot.append(f"Potion of {self.generate_potion()}")
            elif item == 'scroll':
                generated_loot.append(f"Scroll of {self.generate_scroll()}")

        return generated_loot

    def display_monster(self):
        print(f"Name: {self.name}")
        print(f"Hit Points: {self.hit_points}")
        print(f"Abilities: {self.abilities}")
        print(f"Armor Class: {self.armor_class}")
        print(f"Attack Bonus: {self.attack_bonus}")
        print(f"Saving Throws: {self.saving_throws}")
        print(f"Loot: {', '.join(self.loot)}")

# Example usage
monster = Monster(level=4)
monster.display_monster()
