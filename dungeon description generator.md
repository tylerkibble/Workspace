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

# Your existing new_dungeon_words list
new_dungeon_words = [
    "abyssal", "arcane", "barren", "bewitched", "brimming", "cavernous", "desolate", "ebony", "fabled", "ghastly",
    "hallowed", "icy", "jagged", "kaleidoscope", "luminous", "maledictive", "netherworld", "opulent", "parched", "quiescent",
    "radiant", "scintillating", "thunderous", "ubiquitous", "vibrant", "wrought", "xenophobic", "yonder", "zephyr"
]

# Define a new list of descriptive words for a different theme
new_theme_words = [
    "celestial", "serene", "luminous", "ethereal", "tranquil", "whimsical", "enchanted",
    "mystical", "harmonious", "bucolic", "idyllic", "sylvan", "dreamlike", "verdant", "sunlit", "soothing", "melodic",
    "radiant", "pastoral", "blissful", "seraphic", "azure", "glistening", "enchanting", "surreal", "iridescent",
    "jubilant", "serendipitous", "cosmic", "starry", "astral", "glittering", "joyful", "ephemeral", "halcyon",
    "sublime", "beauteous", "peaceful", "triumphant", "cascading", "hushed", "scenic", "breezy", "whispering",
    "nostalgic", "crystalline", "ethereal", "heavenly", "silken", "golden", "resplendent", "wondrous", "glimmering",
    "tranquil", "lucid", "enigmatic", "harmonious", "mythic", "soothing", "embellished", "illuminated", "enchanted",
    "mythical", "captivating", "innocent", "illusionary", "reflective", "utopian", "melancholic", "illustrious",
    "grand", "celestial", "elegant", "divine", "sacred", "heavenly", "lyrical", "radiant", "tender",
    "enigmatic", "drifting", "palatial", "tranquil", "mellifluous", "soothing", "resonant", "sublime",
    "splendid", "fragrant", "opulent", "picturesque", "delicate", "serene", "blissful", "calm", "timeless",
    "enveloping", "whimsical", "luminous", "glowing", "celestial", "captivating", "majestic", "enchanted",
    "dreamy", "ethereal", "mystical", "serene", "tranquil", "lucid", "harmonious", "radiant", "sublime",
    "divine", "sacred", "heavenly", "seraphic", "soothing", "tranquil", "melodic", "blissful", "joyful",
    "serendipitous", "heavenly", "bucolic", "idyllic", "sylvan", "dreamlike", "verdant", "sunlit", "luminous",
    "ethereal", "whimsical", "enchanted"
]

# Function to check for overlaps
def check_overlap(word, existing_list):
    return word.lower() not in [word.lower() for word in existing_list]

# Filter new_dungeon_words to remove duplicates from dungeon_words
filtered_new_dungeon_words = [word for word in new_dungeon_words if check_overlap(word, dungeon_words)]

# Filter new_theme_words to remove duplicates from dungeon_words
filtered_new_theme_words = [word for word in new_theme_words if check_overlap(word, dungeon_words)]

# Expanded lists for more variety
base_descriptions = [
    "a sprawling labyrinth", "an endless maze", "a treacherous network of tunnels",
    "a vast underground fortress", "a mysterious subterranean city", "a deadly dungeon filled with traps",
    "a forgotten crypt", "a labyrinth of ice and frost", "a sunless abyss", "a cavernous lair of dragons", "a twisted warren of ancient battles", "a shadowy realm of lost souls", "a haunted castle of forgotten kings", "a mystical forest of enchanted creatures", "a desolate island of time", "a hidden valley of secrets", "a perilous chasm", "a forsaken tower of dark magic", "a submerged cave of wonders", "a spectral shipwreck", "a cursed swamp of nightmares", "a whispering graveyard of the old", "a fiery volcano of legends", "a ghostly manor of illusions", "a stormy sea of adventures", "a crystalline palace of dreams", "a sacred grove of mysteries", "a frozen desert of whispers", "a phantom village of echoes", "a mythical garden of serenity", "a thunderous mountain of storms", "a cosmic tomb of stars", "a spectral cathedral of spirits", "a dreamlike forest of tranquility", "a shadowed keep of shadows", "a labyrinthine city of the ancients", "a spectral ocean of tales", "a haunted jungle of ghosts", "a forgotten continent of myths", "a celestial pyramid of gods", "a sunken temple of the past", "a mirror dimension of reflections", "a twilight forest of the unknown", "a veiled kingdom of secrets", "a shimmering lake of the unseen", "a cryptic maze of puzzles", "a timeless desert of sandstorms", "a boundless sky of freedom", "a starlit sea of the night", "a hidden land of the forgotten", "a silent castle of the wind", "a whispering cave of the unseen", "a shadowy realm of the hidden", "a spectral island of the lost", "a dreamlike forest of the ethereal", "a thunderous mountain of the wild", "a forgotten city of the ancients", "a spectral sea of the deep", "a haunted castle of the old", "a twilight desert of the silent", "a boundless sky of the infinite", "a shadowy forest of the unseen", "a spectral ocean of the forgotten", "a dreamlike city of the ethereal", "a thunderous cave of the wild", "a hidden land of the ancient", "a veiled sea of the hidden", "a spectral desert of the lost", "a shadowy realm of the unseen", "a boundless forest of the endless", "a silent castle of the wind", "a whispering sea of the unseen", "a dreamlike desert of the tranquil", "a thunderous cave of the wild", "a forgotten island of the old", "a spectral forest of the ethereal", "a twilight desert of the silent", "a boundless ocean of the infinite", "a shadowy cave of the unseen", "a spectral island of the lost", "a haunted forest of the forgotten", "a dreamlike sea of the serene", "a thunderous desert of the wild", "a hidden castle of the ancient", "a veiled forest of the unseen", "a spectral island of the lost", "a shadowy sea of the hidden", "a boundless cave of the endless", "a silent desert of the silent", "a whispering island of the unseen", "a dreamlike cave of the tranquil", "a thunderous forest of the wild", "a forgotten sea of the old", "a spectral desert of the lost", "a twilight castle of the silent", "a boundless forest of the infinite", "a shadowy cave of the unseen", "a spectral island of the forgotten", "a haunted desert of the ancient", "a dreamlike ocean of the serene", "a thunderous cave of the wild", "a hidden forest of the unseen", "a veiled sea of the lost", "a spectral castle of the silent", "a shadowy desert of the hidden", "a boundless island of the endless", "a silent cave of the unseen", "a dreamlike desert of the tranquil", "a thunderous island of the wild", "a forgotten castle of the old", "a spectral forest of the lost", "a twilight desert of the silent", "a boundless cave of the infinite", "a shadowy forest of the unseen", "a spectral island of the forgotten", "a haunted ocean of the ancient", "a dreamlike castle of the serene", "a thunderous desert of the wild", "a hidden island of the unseen", "a veiled forest of the lost", "a spectral cave of the silent", "a shadowy sea of the hidden", "a boundless desert of the endless", "a silent island of the unseen", "a dreamlike cave of the tranquil", "a thunderous forest of the wild", "a forgotten desert of the old", "a spectral island of the lost", "a twilight castle of the silent", "a boundless forest of the infinite", "a shadowy cave of the unseen", "a spectral desert of the forgotten", "a haunted island of the ancient", "a dreamlike ocean of the serene", "a thunderous cave of the wild", "a hidden forest of the unseen", "a veiled island of the lost", "a spectral castle of the silent", "a shadowy desert of the hidden", "a boundless cave of the endless", "a silent island of the unseen", "a dreamlike ocean of the tranquil", "a thunderous island of the wild", "a forgotten castle of the old", "a spectral forest of the lost", "a twilight desert of the silent", "a boundless cave of the infinite", "a shadowy island of the unseen", "a spectral ocean of the forgotten", "a haunted forest of the ancient", "a dreamlike castle of the serene", "a thunderous desert of the wild", "a hidden island of the unseen", "a veiled forest of the lost", "a spectral cave of the silent", "a shadowy ocean of the hidden", "a boundless desert of the endless", "a silent island of the unseen", "a dreamlike cave of the tranquil", "a thunderous forest of the wild", "a forgotten castle of the old", "a spectral island of the lost", "a twilight desert of the silent", "a boundless cave of the infinite", "a shadowy forest of the unseen", "a spectral ocean of the forgotten", "a haunted island of the ancient", "a dreamlike ocean of the serene", "a thunderous cave of the wild", "a hidden forest of the unseen", "a veiled island of the lost", "a spectral castle of the silent", "a shadowy desert of the hidden", "a boundless cave of the endless", "a silent island of the unseen", "a dreamlike ocean of the tranquil", "a thunderous forest of the wild", "a forgotten castle of the old", "a spectral island of the lost", "a twilight desert of the silent", "a boundless cave of the infinite", "a shadowy forest of the unseen", "a spectral ocean of the forgotten", "a haunted island of the ancient", "a dreamlike castle of the serene", "a thunderous desert of the wild", "a hidden forest of the unseen", "a veiled island of the lost", "a spectral cave of the silent", "a shadowy ocean of the hidden", "a boundless desert of the endless", "a silent island of the unseen", "a dreamlike cave of the tranquil", "a thunderous island of the wild", "a forgotten castle of the old", "a spectral forest of the lost", "a twilight desert of the silent", "a boundless cave of the infinite", "a shadowy forest of the unseen", "a spectral island of the forgotten", "a haunted ocean of the ancient", "a dreamlike castle of the serene", "a thunderous desert of the wild", "a hidden island of the unseen", "a veiled forest of the lost", "a spectral cave of the silent", "a shadowy ocean of the hidden", "a boundless desert of the endless", "a silent island of the unseen", "a dreamlike cave of the tranquil", "a thunderous forest of the wild", "a forgotten castle of the old", "a spectral island of the lost", "a twilight desert of the silent", "a boundless cave of the infinite", "a shadowy forest of the unseen", "a spectral ocean of the forgotten", "a haunted island of the ancient", "a dreamlike ocean of the serene", "a thunderous cave of the wild", "a hidden forest of the unseen", "a veiled island of the lost", "a spectral castle of the silent", "a shadowy desert of the hidden", "a boundless cave of the endless", "a silent island of the unseen", "a dreamlike ocean of the tranquil", "a thunderous forest of the wild", "a forgotten castle of the old", "a spectral island of the lost", "a twilight desert of the silent", "a boundless cave of the infinite", "a shadowy forest of the unseen", "a spectral ocean of the forgotten", "a haunted island of the ancient", "a dreamlike castle of the serene", "a thunderous desert of the wild", "a hidden forest of the unseen", "a veiled island of the lost", "a spectral cave of the silent", "a shadowy ocean of the hidden", "a boundless desert of the endless", "a silent island of the unseen", "a dreamlike cave of the tranquil", "a thunderous forest of the wild", "a forgotten castle of the old", "a spectral island of the lost", "a twilight desert of the silent", "a boundless cave of the infinite", "a shadowy forest of the unseen", "a spectral ocean of the forgotten", "a haunted island of the ancient", "a dreamlike ocean of the serene", "a thunderous cave of the wild", "a hidden forest of the unseen", "a veiled island of the lost", "a spectral castle of the silent", "a shadowy desert of the hidden", "a boundless cave of the endless", "a silent island of the unseen", "a dreamlike ocean of the tranquil", "a thunderous forest of the wild", "a forgotten castle of the old", "a spectral island of the lost", "a twilight desert of the silent", "a boundless cave of the infinite", "a shadowy forest of the unseen", "a spectral ocean of the forgotten", "a haunted island of the ancient", "a dreamlike castle of the serene", "a thunderous desert of the wild", "a hidden forest of the unseen", "a veiled island of the lost", "a spectral cave of the silent", "a shadowy ocean of the hidden", "a boundless desert of the endless", "a silent island of the unseen", "a dreamlike cave of the tranquil"
]
adjectives = [
    "dark", "musty", "cold", "treacherous", "ancient", "mysterious", "labyrinthine", "sinister", "enchanted", "forgotten", "endless", "bottomless", "dreadful", "eerie", "shadowy", "whispering", "haunted", "macabre", "forlorn", "gloomy", "ominous", "cryptic", "foreboding", "enigmatic", "ghostly", "ethereal",
    "mystical", "serene", "tranquil", "luminous", "harmonious", "bucolic", "idyllic", "sylvan", "dreamlike", "verdant", "sunlit", "soothing", "melodic", "radiant", "pastoral", "blissful", "seraphic", "azure", "glistening", "enchanting", "surreal", "iridescent", "jubilant", "serendipitous", "cosmic",
    "starry", "astral", "glittering", "joyful", "ephemeral", "halcyon", "sublime", "beauteous", "peaceful", "triumphant", "cascading", "hushed", "scenic", "breezy", "nostalgic", "crystalline", "heavenly", "silken", "golden", "resplendent", "glimmering", "tranquil", "lucid",
    "mythic", "soothing", "embellished", "illuminated", "mythical", "captivating", "innocent", "illusionary", "reflective", "utopian", "melancholic", "illustrious", "grand", "celestial", "elegant", "divine", "sacred", "lyrical", "tender", "drifting", "palatial", "mellifluous", "resonant", "splendid", "fragrant", "opulent", "picturesque", "delicate", "calm", "timeless", "enveloping", "whimsical", "glowing", "captivating", "majestic", "dreamy", "mystical", "serene", "lucid", "harmonious", "sublime", "divine", "seraphic", "melodic", "blissful", "joyful",
    "serendipitous", "bucolic", "idyllic", "sylvan", "dreamlike", "ethereal", "whimsical", "enchanted", "mystical", "serene", "tranquil", "lucid", "harmonious", "radiant", "sublime", "divine", "sacred", "heavenly", "seraphic", "soothing", "tranquil", "melodic", "blissful",
    "serendipitous", "heavenly", "bucolic", "idyllic", "sylvan", "dreamlike", "verdant", "sunlit", "luminous", "ethereal", "whimsical", "enchanted", "mystical", "serene", "tranquil", "lucid", "harmonious", "radiant", "sublime", "divine", "sacred", "heavenly",
    "seraphic", "soothing", "tranquil", "melodic", "blissful", "joyful", "serendipitous", "heavenly", "bucolic", "idyllic", "sylvan", "dreamlike", "verdant", "sunlit", "luminous", "ethereal", "whimsical", "enchanted", "mystical", "serene", "tranquil", "lucid",
    "harmonious", "radiant", "sublime", "divine", "sacred", "heavenly", "seraphic", "soothing", "tranquil", "melodic", "blissful", "joyful", "serendipitous", "heavenly", "bucolic", "idyllic", "sylvan", "dreamlike", "verdant", "sunlit", "luminous", "ethereal",
    "whimsical", "enchanted", "mystical", "serene", "tranquil", "lucid", "harmonious", "radiant", "sublime", "divine", "sacred", "heavenly", "seraphic", "soothing", "tranquil", "melodic", "blissful", "joyful", "serendipitous", "heavenly", "bucolic", "idyllic",
    "sylvan", "dreamlike", "verdant", "sunlit", "luminous", "ethereal", "whimsical", "enchanted", "mystical", "serene", "tranquil", "lucid", "harmonious", "radiant", "sublime", "divine", "sacred", "heavenly", "seraphic", "soothing", "tranquil", "melodic",
    "blissful", "joyful", "serendipitous", "heavenly", "bucolic", "idyllic", "sylvan", "dreamlike", "verdant", "sunlit", "luminous", "ethereal", "whimsical", "enchanted", "mystical", "serene", "tranquil", "lucid", "harmonious", "radiant", "sublime", "divine",
    "sacred", "heavenly", "seraphic", "soothing", "tranquil", "melodic", "blissful", "joyful", "serendipitous", "heavenly", "bucolic", "idyllic", "sylvan", "dreamlike", "verdant", "sunlit", "luminous", "ethereal", "whimsical", "enchanted", "mystical", "serene",
    "tranquil", "lucid", "harmonious", "radiant", "sublime", "divine", "sacred", "heavenly", "seraphic", "soothing", "tranquil", "melodic", "blissful", "joyful", "serendipitous", "heavenly", "bucolic", "idyllic", "sylvan", "dreamlike", "verdant", "sunlit",
    "luminous", "ethereal", "whimsical", "enchanted", "mystical", "serene", "tranquil", "lucid", "harmonious", "radiant", "sublime", "divine", "sacred", "heavenly", "seraphic", "soothing", "tranquil", "melodic", "blissful", "joyful", "serendipitous", "heavenly",
    "bucolic", "idyllic", "sylvan", "dreamlike", "verdant", "sunlit", "luminous", "ethereal", "whimsical", "enchanted", "mystical", "serene", "tranquil", "lucid", "harmonious", "radiant", "sublime", "divine", "sacred", "heavenly", "seraphic", "soothing", "tranquil",
    "melodic", "blissful", "joyful", "serendipitous", "heavenly", "bucolic", "idyllic", "sylvan", "dreamlike", "verdant", "sunlit", "luminous", "ethereal", "whimsical", "enchanted", "mystical", "serene", "tranquil", "lucid", "harmonious", "radiant", "sublime", "divine",
    "sacred", "heavenly", "seraphic", "soothing", "tranquil", "melodic", "blissful", "joyful", "serendipitous", "heavenly", "bucolic", "idyllic", "sylvan", "dreamlike", "verdant", "sunlit", "luminous", "ethereal", "whimsical", "enchanted", "mystical", "serene",
    "tranquil", "lucid", "harmonious", "radiant", "sublime", "divine", "sacred", "heavenly", "seraphic", "soothing", "tranquil", "melodic", "blissful", "joyful", "serendipitous", "heavenly", "bucolic", "idyllic", "sylvan", "dreamlike", "verdant", "sunlit", "luminous",
    "ethereal", "whimsical", "enchanted", "mystical", "serene", "tranquil", "lucid", "harmonious", "radiant", "sublime", "divine", "sacred", "heavenly", "seraphic", "soothing", "tranquil", "melodic", "blissful", "joyful", "serendipitous", "heavenly", "bucolic", "idyllic",
    "sylvan", "dreamlike", "verdant", "sunlit", "luminous", "ethereal", "whimsical", "enchanted", "mystical", "serene", "tranquil", "lucid", "harmonious", "radiant", "sublime", "divine", "sacred", "heavenly", "seraphic", "soothing", "tranquil", "melodic", "blissful",
    "joyful", "serendipitous", "heavenly", "bucolic", "idyllic", "sylvan", "dreamlike", "verdant", "sunlit", "luminous", "ethereal", "whimsical", "enchanted", "mystical", "serene", "tranquil", "lucid", "harmonious", "radiant", "sublime", "divine", "sacred", "heavenly",
    "seraphic", "soothing", "tranquil", "melodic", "blissful", "joyful", "serendipitous", "heavenly", "bucolic", "idyllic", "sylvan", "dreamlike", "verdant", "sunlit", "luminous", "ethereal", "whimsical", "enchanted", "mystical", "serene", "tranquil", "lucid", "harmonious",
    "radiant", "sublime", "divine", "sacred", "heavenly", "seraphic", "soothing", "tranquil", "melodic", "goblins", "trolls", "pits", "ruins", "crypts", "caverns", "altars", "statues", "portals", "gardens", "temples", "shrines", "vaults", "dungeons", "labyrinths", "tombs", "catacombs", "mines", "caves", "towers", "castles", "fortresses", "mazes", "bridges", "rivers", "forests", "mountains", "valleys", "lakes", "islands", "oceans", "cities", "temples", "libraries", "museums", "theaters", "docks", "markets", "taverns", "inns", "shops", "stables", "barracks", "armories", "forges", "smithies", "alchemy labs", "observatories", "aquariums", "zoo", "museums", "arenas", "docks", "harbors", "airships", "cloud cities", "space stations", "asteroid fields", "nebulae", "black holes", "wormholes", "galaxies", "planets", "moons", "comets", "starships", "asteroids", "quasars", "pulsars", "neutron stars", "supernovas", "galactic cores", "voids", "dark matter", "energy fields", "quantum realms", "time rifts", "dimensional gates", "ether realms", "dreamscapes", "nightmares", "mirrors", "lighthouses", "beacons", "farms", "orchards", "villages", "hamlets", "towns", "cities", "kingdoms", "empires", "realms", "dimensions", "portals", "gateways", "halls", "mansions", "estates", "palaces", "hovels", "shacks", "cabins", "huts", "tents", "caravans", "camps", "bivouacs", "barricades", "walls", "ramparts", "turrets", "keeps", "dungeons", "prisons", "cages", "docks", "harbors", "ships", "submarines", "islands", "reefs", "atolls", "archipelagos", "seas", "oceans", "rivers", "lakes", "waterfalls", "glaciers", "icebergs", "avalanches", "blizzards", "storms", "thunderstorms", "lightning", "rainbows", "auroras", "clouds", "skies", "sunsets", "sunrises", "dawns", "twilights", "eclipses", "comets", "meteors", "shooting stars", "constellations", "galaxies", "nebulas", "black holes", "quasars", "pulsars", "supernovas", "cosmic strings", "dark matter", "voids", "wormholes", "galactic arms", "star clusters", "nebulae", "quasars", "pulsars", "neutron stars", "white dwarfs", "red giants", "blue giants", "binary stars", "asteroid belts", "comets", "meteor showers", "cosmic webs", "galactic centers", "black holes", "voids", "quantum singularities", "event horizons", "wormholes", "multiverse portals", "time anomalies", "dimensional rifts", "etheric planes", "astral realms", "dream realms", "nightmare landscapes", "mirror dimensions", "shadow realms", "fairy circles", "mystic groves", "enchantment forests", "elfin cities", "dwarf holds", "gnome villages", "halfling burrows", "goblin caves", "troll bridges", "orc fortresses", "dragon lairs", "wyvern nests", "griffin aeries", "unicorn meadows", "phoenix sanctuaries", "chimera dens", "hydra swamps", "kraken depths", "leviathan seas", "sphinx tombs", "minotaur mazes", "medusa galleries", "gorgon lairs", "harpy roosts", "griffon eyries", "pegasus stables", "centaur plains", "nymph glades", "satyr woods", "faun groves", "dryad forests", "naiad springs", "siren islands", "mermaid coves", "nereid lakes", "undine rivers", "sprite glades", "pixie hollows", "brownie hills", "leprechaun mounds", "fairy rings", "banshee moors", "ghost towns", "zombie crypts", "vampire castles", "werewolf dens", "ghoul catacombs", "mummy tombs", "lich towers", "skeleton armies", "zombie hordes", "vampire covens", "werewolf packs", "ghoul warrens", "ghost ships", "specter fleets", "wraith ruins", "poltergeist mansions", "phantom theaters", "banshee caves", "revenant halls", "doppelganger forests", "changeling villages", "vampire keeps", "lich domes", "zombie fortresses", "ghoul cities", "specter towers", "wraith crypts", "poltergeist dungeons", "banshee labyrinths", "revenant islands", "doppelganger realms", "changeling kingdoms", "vampire empires", "lich cities", "zombie realms", "ghoul dimensions", "specter worlds", "wraith galaxies", "poltergeist nebulas", "banshee voids", "revenant quasars", "doppelganger pulsars", "changeling stars", "vampire nebulas", "lich galaxies", "zombie clusters", "ghoul singularities", "specter horizons", "wraith anomalies", "poltergeist rifts", "banshee portals", "revenant realms", "doppelganger gates", "changeling dimensions", "vampire realms", "lich planes", "zombie anomalies", "ghoul horizons", "specter singularities", "wraith portals", "poltergeist gates", "banshee dimensions", "revenant planes", "doppelganger anomalies", "changeling horizons", "vampire singularities", "lich portals", "zombie gates", "ghoul dimensions", "specter planes", "wraith anomalies", "poltergeist horizons", "banshee singularities", "revenant portals", "doppelganger gates", "changeling planes", "vampire anomalies", "lich horizons", "zombie singularities", "ghoul portals", "specter dimensions", "wraith planes", "poltergeist horizons", "banshee anomalies", "revenant singularities", "doppelganger portals", "changeling gates", "vampire planes", "lich anomalies", "zombie horizons", "ghoul singularities", "specter dimensions", "wraith portals", "poltergeist planes", "banshee anomalies", "revenant singularities", "doppelganger horizons", "changeling portals", "vampire planes", "lich dimensions", "zombie anomalies", "ghoul horizons", "specter singularities", "wraith gates", "poltergeist dimensions", "banshee planes", "revenant anomalies", "doppelganger horizons", "changeling singularities", "vampire portals", "lich dimensions", "zombie planes", "ghoul anomalies", "specter horizons", "wraith singularities", "poltergeist dimensions", "banshee planes", "revenant anomalies", "doppelganger singularities", "changeling gates", "vampire planes", "lich anomalies", "zombie horizons", "ghoul dimensions", "specter planes", "wraith singularities", "poltergeist dimensions", "banshee planes", "revenant anomalies", "doppelganger horizons", "changeling singularities", "vampire portals", "lich dimensions", "zombie planes", "ghoul anomalies", "specter horizons", "wraith singularities", "poltergeist dimensions", "banshee planes", "revenant anomalies", "doppelganger horizons", "changeling singularities", "vampire portals", "lich dimensions", "zombie planes", "ghoul anomalies", "specter horizons", "wraith singularities", "poltergeist dimensions", "banshee planes", "revenant anomalies", "doppelganger horizons", "changeling singularities", "vampire portals", "lich dimensions", "zombie planes", "ghoul anomalies", "specter horizons", "wraith singularities", "poltergeist dimensions", "banshee planes", "revenant anomalies", "doppelganger horizons", "changeling singularities", "vampire portals", "lich dimensions", "zombie planes", "ghoul anomalies", "specter horizons", "wraith singularities", "poltergeist dimensions", "banshee planes", "revenant anomalies", "doppelganger horizons", "changeling singularities", "vampire portals", "lich dimensions", "zombie planes", "ghoul anomalies", "specter horizons", "wraith singularities", "poltergeist dimensions", "banshee planes", "revenant anomalies", "doppelganger horizons", "changeling singularities", "vampire portals", "lich dimensions", "zombie planes", "ghoul anomalies", "specter horizons", "wraith singularities", "poltergeist dimensions", "banshee planes", "revenant anomalies", "doppelganger horizons", "changeling singularities", "vampire portals", "lich dimensions", "zombie planes", "ghoul anomalies", "specter horizons", "wraith singularities", "poltergeist dimensions", "banshee planes", "revenant anomalies", "doppelganger horizons", "changeling singularities", "vampire portals", "lich dimensions", "zombie planes", "ghoul anomalies", "specter horizons", "wraith singularities", "poltergeist dimensions", "banshee planes", "revenant anomalies", "doppelganger horizons", "changeling singularities", "vampire portals", "lich dimensions", "zombie planes", "ghoul anomalies", "specter horizons", "wraith singularities", "poltergeist dimensions", "banshee planes", "revenant anomalies", "doppelganger horizons", "changeling singularities", "vampire portals", "lich dimensions", "zombie planes", "ghoul anomalies", "specter horizons", "wraith singularities", "poltergeist"
]
nouns = [
    "starlight", "meadow", "grove", "brook", "rainbow", "sanctuary", "harmony",
    "crescent", "paradise", "glade", "crystal", "orchard", "valley", "waterfall",
    "mirage", "radiance", "moonlight", "constellation", "galaxy", "serenity", "aura",
    "twilight", "blossom", "whisper", "gossamer", "oasis", "haven", "treetop",
    "canopy", "horizon", "petal", "sunbeam", "garden", "village", "field",
    "temple", "island", "fairy", "dewdrop", "sunset", "sanctum", "fountain",
    "cloud", "tide", "lullaby", "breeze", "wildflower", "star", "dream",
    "unicorn", "phoenix", "pearl", "butterfly", "lighthouse", "skylark", "zenith",
    "aurora", "cascade", "ether", "tranquility", "gleam", "fantasy", "charm",
    "whimsy", "enchantment", "myth", "mystery", "realm", "fauna", "flora",
    "enclave", "haven", "arch", "grove", "solstice", "eclipse", "nebula",
    "thicket", "fragrance", "meadow", "harbor", "vista", "radiance", "labyrinth",
    "nimbus", "zephyr", "mirage", "verdure", "willow", "nook", "sanctuary",
    "fable", "tapestry", "bough", "ivory", "nymph", "azure", "lilac",
    "seraph", "periwinkle", "fen", "hollow", "arbor", "glow", "melody",
    "shimmer", "frost", "fable", "flora", "rhapsody", "zenith", "whisper",
    "treasure", "wisp", "balm", "azure", "quartz", "ripple", "dawn",
    "veil", "gleam", "flurry", "haven", "refuge", "grove", "sanctum",
    "glimmer", "harmony", "solitude", "cove", "dreamscape", "arcadia", "wisp",
    "frost", "murmur", "quartz", "whisper", "sylph", "meadow", "bliss",
    "haven", "aura", "canopy", "archway", "radiance", "nimbus", "breeze",
    "skyline", "paradise", "mist", "mirage", "dawn", "twilight", "glow", "dungeon", "castle", "tower", "forest", "cave", "crypt", "temple", "fortress",
    "labyrinth", "catacomb", "mine", "ruin", "keep", "arena", "chamber", "sanctuary",
    "sanctum", "barracks", "grotto", "stronghold", "citadel", "shrine", "vault",
    "cellar", "abbey", "monastery", "tomb", "graveyard", "underworld", "realm",
    "plane", "dimension", "realm", "hideout", "den", "refuge", "outpost",
    "lair", "camp", "encampment", "throne room", "battleground", "hall", "armory",
    "workshop", "forge", "laboratory", "study", "observatory", "garden", "courtyard",
    "meadow", "clearing", "glade", "grove", "swamp", "marsh", "bog",
    "wetland", "fen", "quagmire", "wasteland", "desert", "badlands", "canyon",
    "cliff", "gorge", "ravine", "chasm", "volcano", "crater", "geyser",
    "mountain", "peak", "ridge", "summit", "valley", "glacier", "iceberg",
    "fjord", "tundra", "plain", "plateau", "savannah", "steppe", "grassland",
    "prairie", "field", "pasture", "wood", "jungle", "rainforest", "thicket",
    "copse", "bushland", "scrubland", "moor", "heath", "down", "bluff",
    "butte", "mesa", "dune", "hill", "slope", "escarpment", "ridge",
    "waterfall", "stream", "river", "brook", "creek", "pond", "lake",
    "lagoon", "bay", "cove", "inlet", "harbor", "beach", "shore",
    "coast", "strand", "sea", "ocean", "gulf", "channel", "strait",
    "archipelago", "island", "islet", "atoll", "reef", "coral", "kelp forest",
    "sandbar", "bank", "shoal", "bridge", "dam", "weir", "dock",
    "pier", "wharf", "jetty", "quay", "causeway", "path", "trail",
    "road", "highway", "route", "track", "passage", "corridor", "tunnel",
    "viaduct", "aqueduct", "culvert", "bridge", "gate", "portal", "archway",
    "vestibule", "foyer", "entryway", "hallway", "lobby", "atrium", "courtyard",
    "plaza", "square", "marketplace", "bazaar", "flea market", "fairground",
    "carnival", "festival", "exposition", "convention", "parade", "procession",
    "ceremony", "ritual", "sacrifice", "initiation", "trial", "challenge",
    "contest", "competition", "race", "battle", "war", "conflict",
    "skirmish", "duel", "bout", "match", "tournament", "crusade", "campaign",
    "quest", "mission", "journey", "expedition", "voyage", "odyssey",
    "pilgrimage", "retreat", "escape", "flee", "flight", "pursuit",
    "chase", "hunt", "search", "exploration", "adventure", "discovery",
    "rescue", "recovery", "retrieval", "liberation", "emancipation", "deliverance",
    "salvation", "redemption", "vindication", "triumph", "victory", "conquest",
    "annexation", "colonization", "occupation", "subjugation", "domination",
    "supremacy", "ascendancy", "mastery", "control", "influence", "authority",
    "power", "strength", "might", "force", "energy", "vigor",
    "vitality", "stamina", "endurance", "resilience", "fortitude", "bravery",
    "courage", "valor", "heroism", "gallantry", "chivalry", "nobility",
    "honor", "dignity", "prestige", "reputation", "renown", "fame",
    "glory", "celebrity", "notoriety", "infamy", "legend", "myth",
    "folklore", "tale", "story", "saga", "chronicle", "account",
    "record", "narrative", "epic", "lore", "tradition", "custom",
    "ritual", "ceremony", "rite", "practice", "habit", "routine",
    "procedure", "process", "method", "system", "approach", "technique",
    "strategy", "tactic", "plan", "scheme", "design", "blueprint",
    "outline", "framework", "structure", "form", "shape", "pattern",
    "model", "prototype", "archetype", "paradigm", "example", "instance",
    "case", "occurrence", "event", "incident", "episode", "happening",
    "phenomenon", "circumstance", "situation", "condition", "state",
    "stage", "phase", "period", "epoch", "era", "age",
    "eon", "generation", "century", "decade", "year", "month",
    "week", "day", "hour", "minute", "second", "moment",
    "instant", "time", "duration", "interval", "span", "gap",
    "break", "pause", "rest", "stop", "halt", "cessation",
    "termination", "conclusion", "end", "finish", "closure",
    "finale", "denouement", "resolution", "outcome", "result",
    "effect", "consequence", "impact", "influence", "repercussion",
    "reverberation", "backlash", "reaction", "response", "feedback",
    "reflection", "reflex", "mirror", "image", "likeness",
    "portrait", "representation", "depiction", "illustration",
    "sketch", "drawing", "painting", "sculpture", "statue",
    "figure", "model", "mockup", "replica", "copy", "duplicate",
    "facsimile", "imitation", "simulation", "emulation",
    "reenactment", "recreation", "reproduction", "remake",
    "revival", "renovation", "restoration", "renewal",
    "rejuvenation", "revitalization", "resurgence", "resurrection",
    "rebirth", "reawakening", "revival", "renaissance",
    "transformation", "metamorphosis", "conversion", "change",
    "alteration", "modification", "adaptation", "adjustment",
    "amendment", "revision", "update", "upgrade", "enhancement",
    "improvement", "advancement", "progress", "development",
    "evolution", "growth", "expansion", "extension",
    "enlargement", "augmentation", "multiplication",
    "proliferation", "increase", "surge", "upsurge", "spike",
    "peak", "climax", "culmination", "pinnacle", "apex",
    "zenith", "summit", "crest", "height", "top", "crown",
    "cap", "roof", "ceiling", "sky", "heaven",
    "firmament", "cosmos", "universe", "galaxy",
    "star", "planet", "moon", "sun", "comet", "asteroid",
    "meteor", "constellation", "nebula", "black hole",
    "quasar", "supernova", "singularity", "dimension",
    "parallel universe", "alternate reality", "multiverse",
    "macrocosm", "microcosm", "atom", "molecule",
    "compound", "element", "particle", "quantum",
    "wave", "field", "force", "energy", "matter",
    "antimatter", "dark matter", "substance",
    "essence", "spirit", "soul", "psyche", "mind",
    "consciousness", "awareness", "perception", "sensation",
    "feeling", "emotion", "thought", "idea"
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

def generate_dungeon_description():
    base_description = random.choice(base_descriptions)
    adjective = random.choice(adjectives)
    noun = random.choice(nouns)
    description = f"{base_description} {adjective} {noun} awaits the brave adventurer."
    
    if random.choice([True, False]):
        surprise_element = random.choice(surprise_elements)
        description += f", {surprise_element}"
    
    if random.choice([True, False]):
        description += f". It is {random.choice(environmental_details)}"
    
    if random.choice([True, False]):
        description += f". Legend says it was {random.choice(historical_twists)}"
    
    return description

# Generate and print a dungeon description
print(generate_dungeon_description())