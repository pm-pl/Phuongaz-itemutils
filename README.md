EXAMPLE CONFIG

config.yml
```yaml
# This is the config for BaseItem
item: 276:0:1
name: "&aExample Item"
lore:
- "&7This is an example item"
- "&7It has two lines of lore"
enchantments:
- "sharpness:1"
- "poison:2"
```

```php

$data = yaml_parse_file("config.yml");

$item = \phuongaz\baseitem\ItemUtils::fromArray($data["item"]);

$player->getInventory()->addItem($item);

```

---

```php
$contents = $player->getInventory()->getContents();
$serialized = \phuongaz\baseitem\ItemUtils::serializeItems($contents); //string
$deserialized = \phuongaz\baseitem\ItemUtils::deserializeItems($serialized); //Item[]
```

---

config.yml
```yaml
items:
# This is the config for BaseItem
    item: 276:0:1
    name: "&aExample Item 1"
    lore:
      - "&7This is an example item"
      - "&7It has two lines of lore"
    enchantments:
      - "sharpness:1"
      - "poison:2"
    item: 276:0:1
    name: "&aExample Item 2"
    lore:
      - "&7This is an example item"
      - "&7It has two lines of lore"
    enchantments:
        - "sharpness:1"
        - "poison:2"
```

```php
$data = new \pocketmine\utils\Config("config.yml", \pocketmine\utils\Config::YAML);

$items = \phuongaz\baseitem\ItemUtils::ItemsFromArray($data->get("items")); //Item[]

foreach($items as $item){
    $player->getInventory()->addItem($item);
}
```