# Code Snippets
---
There are lots of interesting mods you can create in Necesse, but they might not be written as expected, or they might be difficult to figure out. Here you can find snippets of functional code (as of 0.21.23) and descriptions of how they work. These code snippets are chosen because they may provide insight on how to better interact with the game or how to get around common issues.

### Item Randomizer / GameEvents
#### **JAVA**
```java
    public void init() {
        Iterable<Item> gotItems = ItemRegistry.getItems();
        List<InventoryItem> itemArray = new ArrayList<InventoryItem>();
        for (Item thing : gotItems) {
            itemArray.add(new InventoryItem(thing));
        }
        
        GameEvents.addListener(MobLootTableDropsEvent.class, new GameEventListener<MobLootTableDropsEvent>() {
            public void onEvent(MobLootTableDropsEvent event) {
                int dropsNum = event.drops.size();
                event.drops.clear();
                
                List<InventoryItem> list = new ArrayList<>();
                for (int i = 0; i < dropsNum; i++) {
                    int num = (int)(Math.random() * itemArray.size());
                    list.add(itemArray.get(num));
                }
                event.drops.addAll(list);
            }
        });
    }
```
Starting off, we get every item in the game using `ItemRegistry.getItems();`, Which returns `Iterable<Item>`. We cant pick by index out of `Iterable` type, meaning `gotItems[2]` is not valid. To fix this we iterate through it and push each item into a `List` allowing us to index into it. We also convert every item to a `InventoryItem`, which makes the items something that can be dropped on the ground and picked up.

Now that we have a indexable list of `InventoryItems`, the fun begins. Here we have `GameEvents.addListener`, which what it does is tells the game to run the code inside it when a given event runs, first argument is the event's class to watch `MobLootTableDropsEvent.class`, second argument is creating the listener to watch for ran methods in that class `new GameEventListener<GeneratedCaveOresEvent>()`.

Then we write the method `public void onEvent(event)` inside, that runs when the listeners class has a method of the same name ran.
WIP

### New ore object / Cave ore generation
#### **Java**
```java
    public class SilverOre extends RockOreObject {
       public SilverOre() {
          super((RockObject)ObjectRegistry.getObject("rock"), "oremask", "silverore", Color.gray, "silveroreitem");
       }
    }
```
WIP
#### **Java**
```java
    public void init() { 
        RockOreObject newOre = (RockOreObject) ObjectRegistry.getObject(ObjectRegistry.registerObject("newore", new NewOre(), 0, false));
        GameEvents.addListener(GeneratedCaveOresEvent.class, new GameEventListener<GeneratedCaveOresEvent>() {
            public void onEvent(GeneratedCaveOresEvent event) {
                newOre.parentRock = (RockObject) ObjectRegistry.getObject(event.caveGeneration.rockObject);
                event.caveGeneration.generateOreVeins(0.17f, 4, 6, newOre.getID());
            }
        });  
    }
```
WIP
