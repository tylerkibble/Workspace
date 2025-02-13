import random
# Define the dungeon_words list as a global variable
dungeon_words = [
    "dark", "musty", "cold", "treacherous", "ancient", "mysterious", "labyrinthine",
    "dark", "musty", "cold", "treacherous", "ancient", "mysterious", "labyrinthine",
    "filled with traps", "home to monsters", "guarded by skeletons", "hidden treasure",
    "secret passage", "rumored to be haunted", "echoing with distant footsteps", "shrouded in shadows",
    "dripping with moisture", "staircase leading down", "chamber filled with gold", "sealed door",
    "flickering torchlight", "ominous silence", "whispering winds", "cavernous entrance", "dangerously unstable",
    "enchanted trapdoor", "magnificent tapestry", "abandoned altar", "forgotten library", "cryptic inscription",
    "glistening with slime", "swarming with rats", "haunted by ghosts", "overgrown with vines", "ruined throne room",
    "ancient magic still lingers", "towering statues", "mystic symbols", "beneath the earth", "where time stands still",
    "unearthly chill", "miraculous healing spring", "treacherous pit", "endless corridors", "secrets kept by the ages",
    "ominous statues", "bloodstained floors", "whispers in the dark", "forgotten torture chamber",
    "ominous glyphs on the walls", "perpetual darkness", "ominous echoes", "giant spider webs",
    "enchanted crystals glowing faintly", "broken chains", "rusty iron gates", "faint echoes of laughter",
    "dusty tombs", "ominous chanting heard from afar", "strange alchemical apparatus", "torture devices",
    "slithering sounds in the shadows", "cryptic messages carved into stone", "restless spirits",
    "strange runes glowing softly", "bottomless pit", "illusionary walls", "ominous riddles",
    "mysterious fog swirling around", "echoes of ancient battles", "crumbling architecture", "subterranean river",
    "ominous mist settling in", "ethereal whispers", "broken magical artifacts", "elaborate traps",
    "moss-covered statues", "whispers of forgotten lore", "frozen corridors", "shimmering portals",
    "eerie silence broken by distant screams", "cursed relics", "forgotten sacrificial altar", "chilling drafts",
    "whispers of betrayal", "haunting melodies echoing through halls", "unseen watchers", "corrosive mists",
    "faint glimmer of lost treasures", "ominous presence felt throughout", "ancient battle scars", "lost civilization",
    "enchanted prison cells", "whispers of impending doom", "flickering illusions", "frozen time",
    "restless guardians", "ominous thrones of long-lost kings", "mysterious artifacts of power",
    "glowing crystals reflecting eerie light", "ancient crypts filled with restless souls", "cursed relics of forgotten gods",
    "echoes of long-lost incantations", "whispering corridors leading to unseen depths", "shadows that move on their own",
    "arcane symbols etched into the walls", "enchanted pools shimmering with unknown energies", "crumbling statues of forgotten heroes",
    "mysterious laughter echoing in the darkness", "ominous silence broken by distant whispers", "strange sigils pulsating with magic",
    "crimson stains marking ancient battles", "forgotten tombs of long-dead kings", "ominous runes glowing with eldritch power",
    "whispers of a forgotten prophecy", "corrosive mists eating away at ancient stone", "creaking doors leading to forbidden chambers",
    "haunting visions flickering at the edge of perception", "whispers of betrayal lingering in the air", "ancient scripts hinting at forbidden knowledge",
    "shadows that dance unnaturally", "mystical artifacts resonating with untapped power", "ominous laughter echoing from hidden alcoves", 
    "forgotten catacombs", "crumbling passageways", "lost labyrinth", "shadowy depths", "echoing chambers",
    "ancient curse lingering", "whispers of the past", "dreadful silence", "ominous mist", "sinister presence",
    "cryptic hieroglyphs", "chilling drafts", "hidden chambers", "treacherous pathways", "frozen statues",
    "lurking horrors", "enchanted artifacts", "whispers of madness", "forbidden knowledge", "dark rituals",
    "eternal darkness", "mystical resonance", "skeletal remains", "haunted corridors", "cursed idols",
    "glowing runes", "mysterious essence", "veil of illusion", "time-worn relics", "ancient guardians",
    "twisting tunnels", "shifting shadows", "malevolent aura", "veins of crystal", "impenetrable darkness",
    "restless phantoms", "echoes of suffering", "enchanted mechanisms", "faint shimmer", "forgotten sorcery",
    "distant howls", "cavernous depths", "whispers of doom", "eerie artifacts", "relics of the void",
    "frozen echoes", "shattered mirrors", "ominous glyphs", "labyrinth of despair", "tainted waters",
    "mystic resonance", "veil of shadows", "flickering specters", "eternal torment", "crimson moonlight",
    "whispers of the damned", "chamber of echoes", "mysterious keyholes", "twisted corridors", "whispers of vengeance",
    "crumbling foundations", "veins of silver", "silent watchers", "lost souls", "haunting memories",
    "gloomy atmosphere", "eldritch glow", "cursed relics", "labyrinth of illusions", "forgotten chambers",
    "echoes of eternity", "mysterious sigils", "dreadful silence", "cryptic passages", "whispers of despair",
    "twisted statues", "veins of gold", "secrets of the ancients", "dreadful silence", "lurking shadows",
    "frozen echoes", "whispers of the void", "shattered reality", "chamber of echoes", "cursed halls",
    "mystic resonance", "veil of shadows", "flickering specters", "eternal torment", "crimson moonlight",
    "whispers of the damned", "chamber of echoes", "mysterious keyholes", "twisted corridors", "whispers of vengeance",
    "crumbling foundations", "veins of silver", "silent watchers", "lost souls", "haunting memories",
    "gloomy atmosphere", "eldritch glow", "cursed relics", "labyrinth of illusions", "forgotten chambers",
    "echoes of eternity", "mysterious sigils", "dreadful silence", "cryptic passages", "whispers of despair",
    "twisted statues", "veins of gold", "secrets of the ancients", "dreadful silence", "lurking shadows",
    "frozen echoes", "whispers of the void", "shattered reality", "chamber of echoes", "cursed halls", "gloomy", "ominous", "sinister", "malevolent", "cryptic", "foreboding", "enigmatic", "ghostly", "shadowy", "whispering", "haunted", "macabre", "forlorn", "forgotten", "echoing whispers", "cryptic messages", "shadowy figures", "ancient relics", "hidden chambers", "whispers of doom", "frozen statues", "forbidden rituals", "dreadful silence", "treacherous paths", "crumbling walls", "sealed tombs", "flickering torches", "ethereal presence", "elaborate traps", "enchanted artifacts", "mystical symbols", "veins of crystal", "lurking horrors", "ominous glyphs", "restless spirits", "whispers of madness", "sinister presences", "shifting shadows", "malevolent aura", "veins of darkness", "whispers of despair", "cursed idols", "ancient guardians", "mysterious essence", "cryptic passages", "echoes of suffering", "dreadful silence", "veil of illusion", "time-worn relics", "chilling drafts", "forgotten sorcery", "distant howls", "eerie artifacts", "relics of the void", "shattered mirrors", "labyrinth of despair", "tainted waters", "flickering specters", "crimson moonlight", "whispers of the damned", "twisted corridors", "veins of silver", "silent watchers", "haunting memories", "eldritch glow", "labyrinth of illusions", "echoes of eternity", "dreadful silence", "mysterious sigils", "whispers of vengeance", "crumbling foundations", "veins of gold", "secrets of the ancients", "lurking shadows", "frozen echoes", "whispers of the void", "shattered reality", "cursed halls", "abyssal", "arcane", "barren", "bewitched", "brimming", "cavernous", "desolate", "ebony", "fabled", "ghastly",
    "hallowed", "icy", "jagged", "kaleidoscope", "luminous", "maledictive", "netherworld", "opulent", "parched", "quiescent",
    "radiant", "scintillating", "thunderous", "ubiquitous", "vibrant", "wrought", "xenophobic", "yonder", "zephyr"
]
# Expanded lists for more variety
base_descriptions = [
    "a sprawling labyrinth", "an endless maze", "a treacherous network of tunnels",
    "a vast underground fortress", "a mysterious subterranean city", "a deadly dungeon filled with traps",
    "a forgotten crypt", "a labyrinth of ice and frost", "a sunless abyss", "a cavernous lair of dragons"
]
adjectives = [
    "dark", "musty", "cold", "treacherous", "ancient", "mysterious", "labyrinthine",
    "sinister", "enchanted", "forgotten", "endless", "bottomless", "dreadful"
]
nouns = [
    "traps", "monsters", "skeletons", "treasure", "passages", "corridors", "chambers",
    "dragons", "goblins", "trolls", "pits", "ruins", "crypts"
]
surprise_elements = [
    "rumored to be haunted", "guarded by ancient magic", "filled with secrets yet undiscovered",
    "home to creatures of legend", "shrouded in eternal darkness", "where time stands still",
    "infested with vermin", "beneath a cursed mountain", "surrounded by a moat of lava"
]
environmental_details = [
    "echoing with distant footsteps", "dripping with moisture", "shrouded in shadows",
    "damp and chilly", "warm and humid", "illuminated by flickering torchlight",
    "smelling of rot and decay", "resonating with eerie silence", "crackling with electrical energy"
]
historical_twists = [
    "built by a fallen empire", "once a sacred temple", "created by a mad wizard",
    "home to a legendary hero", "constructed by dwarven craftsmen", "a place of ancient curses",
    "a prison for gods", "the birthplace of demons", "a sanctuary for the undead"
]

new_dungeon_words = [
    "abyssal", "arcane", "barren", "bewitched", "brimming", "cavernous", "desolate", "ebony", "fabled", "ghastly",
    "hallowed", "icy", "jagged", "kaleidoscope", "luminous", "maledictive", "netherworld", "opulent", "parched", "quiescent",
    "radiant", "scintillating", "thunderous", "ubiquitous", "vibrant", "wrought", "xenophobic", "yonder", "zephyr"
]

# Function to check for overlaps
def check_overlap(word, existing_list):
    return word.lower() not in [w.lower() for w in existing_list]

# Filter new_dungeon_words to remove duplicates from dungeon_words
filtered_new_dungeon_words = [word for word in new_dungeon_words if check_overlap(word, dungeon_words)]

def generate_dungeon_description():
    base_description = random.choice(base_descriptions)
    adjective = random.choice(adjectives)
    noun = random.choice(nouns)
    description = f"{base_description} of {adjective} {noun} await the brave adventurer."
    
    if random.choice([True, False]):
        surprise_element = random.choice(surprise_elements)
        description += f", {surprise_element}"
    
    if random.choice([True, False]):
        description += f" It is {random.choice(environmental_details)."
    
    if random.choice([True, False]):
        description += f" Legend says it was {random.choice(historical_twists)}"
    
    # Optionally, add some randomness from the filtered_new_dungeon_words list
    if random.choice([True, False]):
        new_word = random.choice(filtered_new_dungeon_words)
        description += f" It has a {new_word} aura."
    
    return description

# Generating and printing a dungeon description
print(generate_dungeon_description())