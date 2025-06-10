![](https://user-images.githubusercontent.com/970858/63474771-d6734700-c469-11e9-83bb-9429da563909.png)

# LAB-Agile-APIs-MongoDB

## Introduction

This set of exercises is designed to help you learn how to work with **MongoDB** using **MongoDB Compass** as a visual environment. Throughout the exercises, you will get familiar with importing collections, creating relationships, and executing complex queries using aggregations and lookups. The goal is for you to develop practical skills for managing a MongoDB database and performing advanced analysis on Pokémon data.

## Requirements

- [Learn how to fork this repo](https://guides.github.com/activities/forking/)
- Clone this repo into your `code/labs` folder
- write the answers to the queries in the readme or upload them as pnj in a repository folder

## Exercise 1: Import the Collections

**Instructions**: 
- Import the provided collections.
- Use `mongoimport` or any preferred method to import the collections into your MongoDB database.

## Exercise 2: Add Your Two Favorite Pokémon

**Instructions**:
- Use the existing structure in the collection to add your two Pokémon.
  
```json
{
  "pokemon_id": 150,
  "name": "Mewtwo",
  "types": [ObjectId("some_type_id")],
  "abilities": [ObjectId("some_ability_id")],
  "base_stats": {
    "hp": 106,
    "attack": 110,
    "defense": 90,
    "speed": 130,
    "special_attack": 154,
    "special_defense": 90
  },
  "evolution": null
}
```
  
- Ensure that at least one of your Pokémon has an evolution (it can be a record in the `evolution` field).
# con ADD DATA. Pokemon sin Evolution
{
  "pokemon_id": 23,
  "name": "Antonio",
  "types": [{"$oid": "6716157b16572cf5a1b13900"}],
  "abilities": [{"$oid": "6716141d16572cf5a1b138d0"}],
  "base_stats": {
    "hp": 100,
    "attack": 100,
    "defense": 100,
    "speed": 100,
    "special_attack": 100,
    "special_defense": 100
  },
  "evolution": null
}
 // Pokemon con evolution
 {
  "pokemon_id": 24,
  "name": "Chikorita",
  "types": [{"$oid":"6716157b16572cf5a1b13903"}], 
  "abilities": [{"$oid":"6716141d16572cf5a1b138de"}], 
  "base_stats": {
    "hp": 45,
    "attack": 49,
    "defense": 65,
    "speed": 45,
    "special_attack": 49,
    "special_defense": 65
  },
  "evolution": {
    "next_evolution": 153,
    "level_requirement": 16,
    "other_requirements": null
  }
}
## Exercise 3: Create the `pokemon_moves` Collection

The `pokemon_moves` collection is necessary to establish a **many-to-many** relationship between Pokémon and the moves they can learn. Each Pokémon can learn several moves, and each move can be learned by multiple Pokémon.

**Instructions**:
- Create the `pokemon_moves` collection with the appropriate structure.
- Add some moves to at least 6 Pokémon using this collection.

// Crear la colección (se crea automáticamente al insertar el primer documento)
db.pokemon_moves.insertMany([
  // Bulbasaur
  {
    "pokemon_id": 1,
    "move_id": 1,  // Tackle
    "learn_method": "level-up",
    "level_learned_at": 1
  },
  {
    "pokemon_id": 1,
    "move_id": 5,  // Vine Whip
    "learn_method": "level-up",
    "level_learned_at": 7
  },
  {
    "pokemon_id": 1,
    "move_id": 15, // Leaf Blade
    "learn_method": "level-up",
    "level_learned_at": 32
  },
  
  // Charmander
  {
    "pokemon_id": 4,
    "move_id": 1,  // Tackle
    "learn_method": "level-up",
    "level_learned_at": 1
  },
  {
    "pokemon_id": 4,
    "move_id": 2,  // Flamethrower
    "learn_method": "level-up",
    "level_learned_at": 16
  },
  {
    "pokemon_id": 4,
    "move_id": 7,  // Fire Blast
    "learn_method": "level-up",
    "level_learned_at": 36
  },
  
  // Squirtle
  {
    "pokemon_id": 7,
    "move_id": 1,  // Tackle
    "learn_method": "level-up",
    "level_learned_at": 1
  },
  {
    "pokemon_id": 7,
    "move_id": 3,  // Water Gun
    "learn_method": "level-up",
    "level_learned_at": 7
  },
  {
    "pokemon_id": 7,
    "move_id": 8,  // Hydro Pump
    "learn_method": "level-up",
    "level_learned_at": 36
  },
  
  // Pikachu (ejemplo adicional)
  {
    "pokemon_id": 25,
    "move_id": 4,  // Thunderbolt
    "learn_method": "level-up",
    "level_learned_at": 26
  },
  {
    "pokemon_id": 25,
    "move_id": 9,  // Thunder
    "learn_method": "level-up",
    "level_learned_at": 42
  },
  
  // Butterfree
  {
    "pokemon_id": 12,
    "move_id": 6,  // Quick Attack
    "learn_method": "level-up",
    "level_learned_at": 1
  },
  {
    "pokemon_id": 12,
    "move_id": 10, // Solar Beam
    "learn_method": "tm"
  }
]);

## Exercise 4: Add the `trainers` Collection

**Instructions**:
- Create the `trainers` collection with the appropriate structure.
```json
  {
  "_id": ObjectId(),
  "trainer_id": 1,
  "name": "Ash",
  "team": [ObjectId("pokemon_id_1"), ObjectId("pokemon_id_2"), ObjectId("pokemon_id_3"), ObjectId("pokemon_id_4"), ObjectId("pokemon_id_5"), ObjectId("pokemon_id_6")]
}
```
  
- Add at least one complete team of 6 Pokémon for a trainer.

// codigo
db.trainers.insertMany([
  {
  "_id": ObjectId(),
  "trainer_id": 1,
  "name": "Ash",
  "team": [ObjectId("67162c6716572cf5a1b139b1"), ObjectId("67162c6716572cf5a1b139b4"), ObjectId("67162c6716572cf5a1b139b5"), ObjectId("67162c6716572cf5a1b139b6"), ObjectId("67162c6716572cf5a1b139b8"), ObjectId("6716366616572cf5a1b139cf")]
},
  {
  "_id": ObjectId(),
  "trainer_id": 2,
  "name": "Bentley",
 "team": [ObjectId("6716366616572cf5a1b139d0"), ObjectId("6716366616572cf5a1b139d1"), ObjectId("6716366616572cf5a1b139d2"), ObjectId("6716366616572cf5a1b139d2"), ObjectId("6716366616572cf5a1b139d5"), ObjectId("6716366616572cf5a1b139d6")]
},
  {
  "_id": ObjectId(),
  "trainer_id": 3,
  "name": "Guaso",
  "team": [ObjectId("6716366616572cf5a1b139d7"), ObjectId("6716366616572cf5a1b139d8"), ObjectId("6716366616572cf5a1b139d9"), ObjectId("6716366616572cf5a1b139d9"), ObjectId("6847f45c512e5c7aac75ebb9"), ObjectId("6847f65f512e5c7aac75ebc1")]
}
]);

## Exercise 5:  Queries

1. **Query a Pokémon by name**: Return all the information of a specific Pokémon by its name.

db['pokemons'].find({'name':'Rattata'})
{
  _id: ObjectId('6716366616572cf5a1b139d7'),
  pokemon_id: 19,
  name: 'Rattata',
  types: [
    ObjectId('6716157b16572cf5a1b138fb')
  ],
  abilities: [
    ObjectId('6716141d16572cf5a1b138cc')
  ],
  base_stats_hp: 30,
  base_stats_attack: 56,
  base_stats_defense: 35,
  base_stats_speed: 72,
  base_stats_special_attack: 25,
  base_stats_special_defense: 35,
  evolves_to: 20,
  evolution_level: 20
}
   
2. **Get Pokémon of a specific type**: Use a **lookup** to find Pokémon that have a specific type.


db.types.aggregate([
  {
    $match:
      /**
       * query: The query in MQL.
       */
      {
        name: "Fire"
      }
  },
  {
    $lookup:
      /**
       * from: The target collection.
       * localField: The local join field.
       * foreignField: The target join field.
       * as: The name for the results.
       * pipeline: Optional pipeline to run on the foreign collection.
       * let: Optional variables to use in the pipeline field stages.
       */
      {
        from: "types",
        localField: "_id",
        foreignField: "types",
        as: "pokemon_fire"
      }
  }
]
   
3. **Get all the moves a Pokémon can learn**: Write a query that shows all the moves a Pokémon can learn, including the level at which it learns them.


4. **Average base stats of all Pokémon**: Perform an aggregation to get the average HP, attack, defense, and speed of all Pokémon.
   
5. **Count Pokémon by type**: Use a **lookup** and an aggregation to count how many Pokémon exist for each type.
   
6. **Pokémon with more than 100 speed**: Perform an aggregation to find all Pokémon whose base speed is greater than 100.

7.  **Pokémon that have evolutions** Write a query that returns all Pokémon that have evolutions and the level at which they evolve.

8. **Fastest Pokémon** Find the 5 fastest Pokémon.

9. **Pokémon by Combined Types** Get all the Pokémon that have a combination of two specific types, for example, "Fire" and "Flying".

10. **Group Pokémon by Number of Evolutions** Group Pokémon by the number of evolutions they have (0, 1, or more evolutions).

11. **Find between the `pokemons` and `abilities` collections to identify Pokémon that share at least one common ability.**

12. **Average Stats by Type** : Calculate the average base stats (HP, attack, defense, etc.) for each Pokémon type.


## Bonus

1.1: Find the Most Common Type

1.2: Find Pokémon that have more than two evolutions


