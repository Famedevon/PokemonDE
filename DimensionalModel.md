## 🧬 Dimensional Model – Pokémon Data Warehouse

```mermaid
erDiagram
    fact_pokemon_stats {
        int fact_id PK
        int pokemon_id FK
        int stat_id FK
        int type_id FK
        int generation_id FK
        int evolution_chain_id FK
        boolean is_legendary
        boolean is_mythical
    }

    dim_pokemon {
        int pokemon_id PK
        string name
        float height
        float weight
    }

    dim_stat {
        int stat_id PK
        string stat_name
        int base_value
    }

    dim_type {
        int type_id PK
        string type_name
    }

    dim_generation {
        int generation_id PK
        string generation_name
    }

    dim_evolution_chain {
        int evolution_chain_id PK
        string evolution_stages
    }

    dim_ability {
        int ability_id PK
        string ability_name
    }

    dim_move {
        int move_id PK
        string move_name
        int type_id FK
        string damage_class
    }

    bridge_pokemon_type {
        int pokemon_id FK
        int type_id FK
    }

    bridge_pokemon_ability {
        int pokemon_id FK
        int ability_id FK
    }

    bridge_pokemon_move {
        int pokemon_id FK
        int move_id FK
    }

    dim_type_effectiveness {
        int attacking_type_id FK
        int defending_type_id FK
        float effectiveness
    }

    fact_pokemon_stats ||--|| dim_pokemon : "has"
    fact_pokemon_stats ||--|| dim_stat : "has"
    fact_pokemon_stats ||--|| dim_type : "has"
    fact_pokemon_stats ||--|| dim_generation : "has"
    fact_pokemon_stats ||--|| dim_evolution_chain : "has"

    bridge_pokemon_type }|--|| dim_pokemon : "links"
    bridge_pokemon_type }|--|| dim_type : "links"

    bridge_pokemon_ability }|--|| dim_pokemon : "links"
    bridge_pokemon_ability }|--|| dim_ability : "links"

    bridge_pokemon_move }|--|| dim_pokemon : "links"
    bridge_pokemon_move }|--|| dim_move : "links"

    dim_move ||--|| dim_type : "has"
    dim_type_effectiveness }|--|| dim_type : "attacking"
    dim_type_effectiveness }|--|| dim_type : "defending"
