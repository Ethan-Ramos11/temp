# Simple Text Adventure - CLI Challenge

**Time Limit: 45 minutes**  
**Difficulty: Beginner-Intermediate**  
**Skills: Control Flow, Functions, User Input, Game Logic**

## Challenge Overview

Create a simple text-based adventure game where players navigate through rooms, collect items, and make choices that affect the story outcome. Focus on creating an engaging interactive experience with clear game mechanics.

## Project Structure

```
text_adventure_challenge/
├── adventure_game.py       # Your main implementation
├── README.md              # This file
└── tests/
    └── test_adventure.py  # Optional unit tests
```

## Core Requirements (35 minutes)

### 1. Basic Game Structure (10 minutes)
- Welcome message and game introduction
- Player name input
- Simple game loop with user commands
- Exit/quit functionality

**Essential Commands:**
- `look` - describe current location
- `go [direction]` - move between rooms
- `inventory` - show collected items
- `help` - show available commands
- `quit` - exit game

### 2. Room System (15 minutes)
Create at least **4 connected rooms** with:
- **Name** (e.g., "Forest Clearing", "Dark Cave")
- **Description** (what the player sees)
- **Exits** (available directions: north, south, east, west)
- **Items** (objects that can be picked up)

**Example Room:**
```
=== FOREST CLEARING ===
You stand in a peaceful forest clearing. Sunlight filters through 
the tall oak trees, and you hear birds chirping nearby. There's 
a rusty key glinting in the grass.

Exits: north, east
Items: rusty key
```

### 3. Item Collection (5 minutes)
- `take [item]` - pick up items from rooms
- Items disappear from room when taken
- Store items in player inventory
- Handle invalid item names gracefully

### 4. Simple Win Condition (5 minutes)
Create a basic goal:
- Collect 3 specific items, OR
- Reach a special "treasure room", OR
- Find a hidden exit

**Win Message Example:**
```
🎉 CONGRATULATIONS! 🎉
You found the ancient treasure! You are now rich beyond your wildest dreams!
Thanks for playing!
```

## Bonus Features (10 minutes)

Choose **ONE** bonus feature if you finish early:

### Option A: Simple Combat
- Add a monster in one room
- Player needs a weapon to defeat it
- `fight` command with random outcomes

### Option B: Locked Doors
- Some exits require specific items (like a key)
- Display helpful messages when blocked
- `use [item]` command to unlock paths

### Option C: Multiple Endings
- Different outcomes based on choices or items collected
- Good ending, bad ending, secret ending
- Track player decisions

### Option D: Save/Load Game
- `save` command to write game state to file
- `load` command to restore previous game
- Simple text file format

## Technical Requirements

### Game Data Structure
Represent your game world as a simple dictionary:

```python
# Example room structure
rooms = {
    "forest": {
        "name": "Forest Clearing",
        "description": "A peaceful forest clearing with tall oak trees.",
        "exits": {"north": "cave", "east": "village"},
        "items": ["rusty key"]
    },
    "cave": {
        "name": "Dark Cave", 
        "description": "A dark, damp cave. You hear water dripping.",
        "exits": {"south": "forest"},
        "items": ["torch", "gold coin"]
    }
    # Add more rooms...
}
```

### Input Handling
- Convert input to lowercase for consistency
- Split commands into parts: `take rusty key` → `["take", "rusty", "key"]`
- Handle invalid commands with helpful error messages

### Code Organization
- Separate functions for different game actions
- Keep the main game loop simple and clean
- Use meaningful variable names

## Starter Code Template

```python
#!/usr/bin/env python3
"""
Simple Text Adventure Game
Navigate rooms, collect items, and win the game!
"""

def display_room(room_key, rooms):
    """
    Display current room information to the player.
    
    Args:
        room_key (str): Current room identifier
        rooms (dict): Game world data
    """
    # TODO: Print room name, description, exits, and items
    pass


def move_player(current_room, direction, rooms):
    """
    Move player to a new room if possible.
    
    Args:
        current_room (str): Current room key
        direction (str): Direction to move
        rooms (dict): Game world data
        
    Returns:
        str: New room key, or current room if move invalid
    """
    # TODO: Check if direction is valid and return new room
    pass


def take_item(item_name, current_room, rooms, inventory):
    """
    Add item to inventory and remove from room.
    
    Args:
        item_name (str): Name of item to take
        current_room (str): Current room key
        rooms (dict): Game world data
        inventory (list): Player's items
    """
    # TODO: Move item from room to inventory
    pass


def check_win_condition(inventory):
    """
    Check if player has won the game.
    
    Args:
        inventory (list): Player's current items
        
    Returns:
        bool: True if player has won
    """
    # TODO: Define your win condition
    pass


def main():
    """
    Main game loop.
    """
    # Game world data
    rooms = {
        "start": {
            "name": "Starting Room",
            "description": "You are in a simple room. This is where your adventure begins!",
            "exits": {"north": "forest"},
            "items": []
        },
        # TODO: Add more rooms
    }
    
    # Game state
    current_room = "start"
    inventory = []
    player_name = input("Enter your name, brave adventurer: ")
    
    print(f"\nWelcome to the Adventure, {player_name}!")
    print("Type 'help' for available commands.\n")
    
    # Main game loop
    while True:
        # TODO: Display current room
        # TODO: Get player input
        # TODO: Process commands
        # TODO: Check win condition
        pass


if __name__ == "__main__":
    main()
```

## Sample Game World

Here's a simple 4-room world to get you started:

```
    [CAVE]
      |
[VILLAGE] — [FOREST] — [TREASURE ROOM]
```

**Story:** Find the three magical items (key, torch, gem) scattered across the rooms to unlock the treasure chamber!

## Example Gameplay Session

```
Welcome to the Adventure, Alex!
Type 'help' for available commands.

=== FOREST CLEARING ===
A peaceful forest clearing with tall oak trees.
Exits: north, east, west
Items: rusty key

> take key
You picked up the rusty key.

> go north

=== DARK CAVE ===
A dark, damp cave. You hear water dripping.
Exits: south
Items: torch

> take torch
You picked up the torch.

> inventory
You are carrying: rusty key, torch

> go south
> go east

=== VILLAGE SQUARE ===
A bustling village with friendly merchants.
Exits: west
Items: magic gem

> take gem
You picked up the magic gem.

> inventory
You are carrying: rusty key, torch, magic gem

🎉 CONGRATULATIONS! 🎉
You collected all three magical items! The treasure room has appeared!
```

## Evaluation Criteria

**Functionality (60%)**
- ✅ Player can navigate between rooms
- ✅ Items can be collected and stored
- ✅ Game has a clear win condition
- ✅ Commands work as expected

**User Experience (25%)**
- ✅ Clear, descriptive room descriptions
- ✅ Helpful error messages
- ✅ Intuitive command system
- ✅ Engaging story/theme

**Code Quality (15%)**
- ✅ Clean, readable code
- ✅ Functions are well-organized
- ✅ Good variable names
- ✅ Proper input handling

## Time Management Tips

**Minutes 0-5:** Read requirements and plan your room layout  
**Minutes 5-15:** Create room data structure and basic display  
**Minutes 15-25:** Implement movement and basic commands  
**Minutes 25-35:** Add item collection and win condition  
**Minutes 35-45:** Test gameplay and add polish/bonus features

## Common Pitfalls to Avoid

1. **Over-complex story:** Keep it simple and focus on mechanics
2. **Too many rooms:** 4-6 rooms is plenty for 45 minutes
3. **Complex item interactions:** Basic take/inventory is sufficient
4. **Perfect error handling:** Cover the basics, don't over-engineer

## Success Indicators

You've successfully completed the challenge when:
- Player can move between all rooms
- Items can be collected and viewed in inventory
- Game has a clear ending with win message
- All basic commands work without crashing

**Remember: Fun gameplay beats perfect code. Focus on making it playable!**