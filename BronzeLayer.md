## Bronze Layer – Raw PokeAPI Tables

```mermaid
erDiagram
    bronze_pokemon {
        int id PK
        string name
        float height
        float weight
        string species_url
        stringarray types
        stringarray abilities
        stringarray moves
        objectarray stats
    }

    bronze_pokemon_species {
        int id PK
        string name
        string generation
        boolean is_legendary
        boolean is_mythical
        string evolution_chain_url
    }

    bronze_evolution_chain {
        int id PK
        json chain
    }

    bronze_type {
        int id PK
        string name
        stringarray double_damage_from
        stringarray double_damage_to
        stringarray half_damage_from
        stringarray half_damage_to
        stringarray no_damage_from
        stringarray no_damage_to
    }

    bronze_move {
        int id PK
        string name
        string type
        string damage_class
    }

    bronze_ability {
        int id PK
        string name
        string effect_short
    }

    bronze_generation {
        int id PK
        string name
        stringarray version_groups
    }
