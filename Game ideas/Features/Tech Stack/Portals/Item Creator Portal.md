### Item Creator Features: Detailed Breakdown

#### Core Objective

The item creator will enable dungeon masters to generate, customize, and manage items for their campaigns. It will create a predefined item list based on event types and allow for the addition of unique items, handling various rarities and properties.

#### Features and Functionalities

1. **Predefined Item List Generation**
    
    - **Event Type Integration**: Automatically generate a list of items relevant to the current event type.
    - **Loot Generation**: Provide options for generating loot with different rarities (basic, uncommon, rare, epic, legendary, mythic).
2. **Custom Item Creation**
    
    - **Predefined Fields**: Allow dungeon masters to fill out specific fields to define an item.
        - **Name**: The name of the item.
        - **Type**: The category (weapon, armor, potion, etc.).
        - **Description**: A brief description of the item.
        - **Properties**: Specific attributes (damage, defense, special abilities, etc.).
        - **Effects**: Any magical or special effects the item has.
            - **Magical Effects**: Positive enhancements, such as increased strength or fire damage.
            - **Cursed Effects**: Negative effects, like health drain or attracting enemies.
            - **Elemental Effects**: Damage or protection related to elements (fire, ice, lightning, etc.).
            - **Utility Effects**: Non-combat abilities like invisibility, teleportation, or unlocking mechanisms.
            - **Healing Effects**: Restore health, cure ailments, or grant temporary invulnerability.
            - **Summoning Effects**: Call forth creatures or allies to aid the wielder.
        - **Paragraph Input**: Option for dungeon masters to write a detailed paragraph describing the item, which the system will then process into structured data.
3. **Item Variations**
    
    - **Multiple Versions**: Create different versions of each item based on its properties:
        - **Basic**: Standard version with no special properties.
        - **Magical Effect**: Item with additional magical abilities.
        - **Cursed**: Item with negative effects.
        - **Enhanced**: Improved version with superior attributes.
    - **Rarity Tiers**: Classify items into different rarities:
        - **Basic**
        - **Uncommon**
        - **Rare**
        - **Epic**
        - **Legendary**
        - **Mythic**
    - **Properties by Tier**: Define the base power and the number of effects based on the item's tier.
4. **Item Assignment**
    
    - **Monster/NPC Assignment**: Assign items to specific monsters or NPCs as drops or rewards.
    - **Unassigned Items**: If an item is left unassigned, the AI module should create a suitable creature or NPC to thematically fit with the event type and the item dropped.
5. **Creature/NPC Creator Integration**
    
    - **Thematic Creatures/NPCs**: Generate creatures or NPCs that align with the event type and carry the unassigned items.
    - **Custom Attributes**: Allow for customization of generated creatures/NPCs to fit the dungeon master’s vision.
        - **Name**: Name of the creature/NPC.
        - **Type**: Classification (beast, humanoid, undead, etc.).
        - **Description**: Brief background or lore.
        - **Attributes**: Strength, agility, intelligence, etc.
        - **Abilities**: Special skills or powers.
        - **Behavior**: Aggressive, neutral, friendly, etc.
        - **Loot**: Items carried or dropped by the creature/NPC.