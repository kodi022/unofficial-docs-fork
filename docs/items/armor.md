# Armor
Adding armor is just as easy as tools to add into the Necesse. Additional functionality such as set bonuses are a bit more involved.

### Creating Armor
---
Armor is just an item, like many other items and tool, meaning it is created and registered similarly. Each armor type is of course its own object type, having slightly different arguments that are explained here.

This page only explains arguments/variables that are only specific to armor. Others not here such as `stringID`/`itemID`, `rarity` are described at this page:
[**Adding Items**](https://necesse-community.github.io/unofficial-docs/#/items/home)

#### Chest
---
We register a `new ChestArmorItem()` into the ItemRegistry, which this line is all that is required for our new chestplate
<!-- div:right-panel -->
<!-- tabs:start -->
#### **Java**

```java
  ItemRegistry.registerItem(stringID, 
    new ChestArmorItem(armorValue, enchantCost, rarity, bodyTextureName, armsTextureName),
    brokerValue, isObtainable);
    
  ItemRegistry.registerItem("coolchest", 
    new ChestArmorItem(8, 400, Rarity.NORMAL, "coolchestbody", "coolchestarms"),
    50, true);
```

#### **Kotlin**

```kt
  wip
```
<!-- tabs:end -->
<!-- panels:end -->

For the variables specifically related to armor and/or chestplate:
`armorValue` is the number of armor the item has you see ingame, for example the copper chestplate has 5.

`bodyTextureName` is the name of your spritesheet for the armors torso animation.  Examples [**here**](https://necesse-community.github.io/unofficial-docs/#/resources/texturing)

`armsTexturename` is the same as above, but for the arm / shoulder texture. Examples [**here**](https://necesse-community.github.io/unofficial-docs/#/resources/texturing)

#### Boots
---
Boots follow a very similar setup as the Chest armor, but only requiring one texture instead of two

<!-- div:right-panel -->
<!-- tabs:start -->
#### **Java**

```java
  ItemRegistry.registerItem(stringID, 
    new BootsArmorItem(armorValue, enchantCost, itemRarity, textureName),
    brokerValue, isObtainable)
    
  ItemRegistry.registerItem("coolboots, 
    new BootsArmorItem(6, 400, Rarity.NORMAL, "coolbootstexture"),
    50, true)
```

#### **Kotlin**

```kt
  wip
```
<!-- tabs:end -->
<!-- panels:end -->

WIP

#### Helmet
---
We explain the Helmet last because the helmet actually has two valid types to create an item. One being `new HelmetArmorItem()` following a identical creation process to boots, and the other being `new SetHelmetArmorItem()` which requires the stringID of the two other armor pieces you've created before.

<!-- div:right-panel -->
<!-- tabs:start -->
#### **Java**

```java
  ItemRegistry.registerItem(stringID, 
    new ChestArmorItem(armorValue, enchantCost, rarity, bodyTextureName, armsTextureName),
    brokerValue, isObtainable);
```

#### **Kotlin**

```kt
  wip
```
<!-- tabs:end -->
<!-- panels:end -->

WIP
