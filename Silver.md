## Silver Layer – Cleaned & Structured Tables

```mermaid
erDiagram
    silver_pokemon {
        int pokemon_id PK
        string name
        float height
        float weight
        int species_id FK
    }

    silver_pokemon_species {
        int species_id PK
        string name
        int generation_id FK
        boolean is_legendary
        boolean is_mythical
        int evolution_chain_id FK
    }

    silver_evolution_chain {
        int evolution_chain_id PK
        string evolution_stage_1
        string evolution_stage_2
        string evolution_stage_3
    }

    silver_type {
        int type_id PK
        string name
    }

    silver_pokemon_type {
        int pokemon_id FK
        int type_id FK
    }

    silver_stat {
        int stat_id PK
        string stat_name
    }

    silver_pokemon_stat {
        int pokemon_id FK
        int stat_id FK
        int base_stat
    }

    silver_ability {
        int ability_id PK
        string name
        string effect_short
    }

    silver_pokemon_ability {
        int pokemon_id FK
        int ability_id FK
    }

    silver_move {
        int move_id PK
        string name
        int type_id FK
        string damage_class
    }

    silver_pokemon_move {
        int pokemon_id FK
        int move_id FK
    }

    silver_generation {
        int generation_id PK
        string generation_name
    }

    silver_type_effectiveness {
        int attacking_type_id FK
        int defending_type_id FK
        float effectiveness
    }
