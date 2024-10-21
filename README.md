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


## Exercise 3: Create the `pokemon_moves` Collection

The `pokemon_moves` collection is necessary to establish a **many-to-many** relationship between Pokémon and the moves they can learn. Each Pokémon can learn several moves, and each move can be learned by multiple Pokémon.

**Instructions**:
- Create the `pokemon_moves` collection with the appropriate structure.
- Add some moves to at least 6 Pokémon using this collection.

## Exercise 4: Add the `trainers` Collection

**Instructions**:
- Create the `trainers` collection with the appropriate structure.
- Add at least one complete team of 6 Pokémon for a trainer.


## Exercise 5:  Queries

1. **Query a Pokémon by name**: Return all the information of a specific Pokémon by its name.
   
2. **Get Pokémon of a specific type**: Use a **lookup** to find Pokémon that have a specific type.
   
3. **Get all the moves a Pokémon can learn**: Write a query that shows all the moves a Pokémon can learn, including the level at which it learns them.

4. **Average base stats of all Pokémon**: Perform an aggregation to get the average HP, attack, defense, and speed of all Pokémon.
   
5. **Count Pokémon by type**: Use a **lookup** and an aggregation to count how many Pokémon exist for each type.
   
6. **Pokémon with more than 100 speed**: Perform an aggregation to find all Pokémon whose base speed is greater than 100.

7.  **Pokémon that have evolutions** Write a query that returns all Pokémon that have evolutions and the level at which they evolve.

8. **Fastest Pokémon** Find the 5 fastest Pokémon.

9. **Pokémon by Combined Types** Get all the Pokémon that have a combination of two specific types, for example, "Fire" and "Flying".

10. **Group Pokémon by Number of Evolutions** Group Pokémon by the number of evolutions they have (0, 1, or more evolutions).


## Exercise 11: Find Pokémon with Common Abilities

**Objective**: Find Pokémon that share the same abilities.

**Instructions**:
- Perform a **lookup** between the `pokemons` and `abilities` collections to identify Pokémon that share at least one common ability.
- Display the name of the Pokémon and the ability they share.

---

## Exercise 12: Average Stats by Type

**Objective**: Calculate the average base stats (HP, attack, defense, etc.) for each Pokémon type.

**Instructions**:
- Perform a **lookup** between `pokemons` and `types` to get the type of each Pokémon.
- Use **group by** to calculate the average base stats by type.

---

## Exercise 13: Pokémon with More Than 3 Learned Moves

**Objective**: Find the Pokémon that can learn more than 3 moves.

**Instructions**:
- Use a **lookup** between the `pokemon_moves` and `pokemons` collections.
- Use an **aggregation** to count how many moves each Pokémon can learn and filter those with more than 3.

---

## Exercise 14: Search for Trainers with Full Teams

**Objective**: Query the trainers who have a full team of 6 Pokémon.

**Instructions**:
- Filter the documents in the `trainers` collection where the size of the `team` field is equal to 6.

---

## Exercise 15: Find the Most Common Type

**Objective**: Find the most common Pokémon type in the database.

**Instructions**:
- Use a **lookup** to get the types of the Pokémon.
- Perform an **aggregation** to count how many Pokémon have each type and sort the result to get the most common one.

---

## Exercise 16: Trainers with Legendary Pokémon Teams

**Objective**: Find trainers that have at least one legendary Pokémon on their team.

**Instructions**:
- Use a **lookup** between `trainers` and `pokemons` to find trainers that have at least one legendary Pokémon on their team.

---

## Exercise 17: Pokémon with More Than 2 Evolutions

**Objective**: Find Pokémon that have more than two evolutions.

**Instructions**:
- Use an **aggregation** to count the evolutions for each Pokémon and filter those with more than two.

---
