MONSTER_XP_VALUES = {
    "less than 1": {"XP": 10, "Special Ability Bonus": 3},
    "1": {"XP": 25, "Special Ability Bonus": 12},
    "2": {"XP": 75, "Special Ability Bonus": 25},
    "3": {"XP": 145, "Special Ability Bonus": 30},
    "4": {"XP": 240, "Special Ability Bonus": 40},
    "5": {"XP": 360, "Special Ability Bonus": 45},
    "6": {"XP": 500, "Special Ability Bonus": 55},
    "7": {"XP": 670, "Special Ability Bonus": 65},
    "8": {"XP": 875, "Special Ability Bonus": 70},
    "9": {"XP": 1075, "Special Ability Bonus": 75},
    "10": {"XP": 1300, "Special Ability Bonus": 90},
    "11": {"XP": 1575, "Special Ability Bonus": 95},
    "12": {"XP": 1875, "Special Ability Bonus": 100},
    "13": {"XP": 2175, "Special Ability Bonus": 110},
    "14": {"XP": 2500, "Special Ability Bonus": 115},
    "15": {"XP": 2850, "Special Ability Bonus": 125},
    "16": {"XP": 3250, "Special Ability Bonus": 135},
    "17": {"XP": 3600, "Special Ability Bonus": 145},
    "18": {"XP": 4000, "Special Ability Bonus": 160},
    "19": {"XP": 4500, "Special Ability Bonus": 175},
    "20": {"XP": 5250, "Special Ability Bonus": 200},
    "21": {"XP": 6000, "Special Ability Bonus": 225},
    "22": {"XP": 6750, "Special Ability Bonus": 250},
    "23": {"XP": 7500, "Special Ability Bonus": 275},
    "24": {"XP": 8250, "Special Ability Bonus": 300},
    "25": {"XP": 9000, "Special Ability Bonus": 325}
}

def calculate_monster_xp(hit_dice):
    """
    Calculate the XP value for a monster based on its hit dice.
    """
    if "*" in str(hit_dice):  # Check for special ability bonus
        special_bonus = int(str(hit_dice).count("*")) * MONSTER_XP_VALUES[str(hit_dice)]["Special Ability Bonus"]
        xp_value = MONSTER_XP_VALUES[str(hit_dice)]["XP"] + special_bonus
    else:
        xp_value = MONSTER_XP_VALUES[str(hit_dice)]["XP"]
    
    if hit_dice > 25:
        xp_value += 750  # Additional XP for monsters with more than 25 hit dice
        xp_value += 25   # Additional Special Ability Bonus
    
    return xp_value