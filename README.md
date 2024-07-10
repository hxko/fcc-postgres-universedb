# Celestial Bodies Database

This project contains a PostgreSQL relational database for storing information about celestial bodies, including galaxies, stars, planets, moons, and black holes. This README provides an overview of the database schema and instructions for setting up and using the database.

## Database Schema

The database is named `universe` and contains the following tables:

1. **galaxy**
2. **star**
3. **planet**
4. **moon**
5. **blackhole**

### galaxy Table

The `galaxy` table stores information about galaxies.

| Column        | Type                 | Constraints          |
| ------------- | -------------------- | -------------------- |
| `galaxy_id`   | `integer`            | Primary Key          |
| `speed`       | `integer`            |                      |
| `description` | `text`               |                      |
| `name`        | `character varying`  | Unique, Not Null     |
| `rotation`    | `character varying`  |                      |

### star Table

The `star` table stores information about stars.

| Column     | Type                 | Constraints          |
| ---------- | -------------------- | -------------------- |
| `star_id`  | `integer`            | Primary Key          |
| `radius`   | `integer`            | Not Null             |
| `color`    | `character varying`  | Not Null             |
| `name`     | `character varying`  | Unique, Not Null     |
| `galaxy_id`| `integer`            | Foreign Key          |

### planet Table

The `planet` table stores information about planets.

| Column           | Type                 | Constraints          |
| ---------------- | -------------------- | -------------------- |
| `planet_id`      | `integer`            | Primary Key          |
| `name`           | `character varying`  | Unique, Not Null     |
| `amount_of_people`| `numeric`           |                      |
| `time_travel`    | `boolean`            | Default: false, Not Null |
| `star_id`        | `integer`            | Foreign Key          |

### moon Table

The `moon` table stores information about moons.

| Column       | Type                 | Constraints          |
| ------------ | -------------------- | -------------------- |
| `moon_id`    | `integer`            | Primary Key          |
| `name`       | `character varying`  | Not Null             |
| `has_water`  | `boolean`            | Not Null             |
| `planet_id`  | `integer`            | Foreign Key          |
| `name_code`  | `character varying`  | Unique, Not Null     |

### blackhole Table

The `blackhole` table stores information about black holes.

| Column         | Type                 | Constraints          |
| -------------- | -------------------- | -------------------- |
| `blackhole_id` | `integer`            | Primary Key          |
| `gravity`      | `integer`            |                      |
| `galaxy_id`    | `integer`            |                      |
| `wormhole`     | `boolean`            | Default: false, Not Null |
| `name`         | `character varying`  | Unique, Not Null     |

## Constraints and Relationships

- Each `star` belongs to a `galaxy` (`star.galaxy_id` references `galaxy.galaxy_id`).
- Each `planet` orbits a `star` (`planet.star_id` references `star.star_id`).
- Each `moon` orbits a `planet` (`moon.planet_id` references `planet.planet_id`).

## Sample Data

The database includes some initial data for each table. Here are some examples:

### galaxy

| galaxy_id | name       |
| --------- | ---------- |
| 1         | andromeda  |
| 2         | maffei1    |
| 3         | maffei2    |
| 4         | milky_way  |

### star

| star_id | name    | color   |
| ------- | ------- | ------- |
| 1       | star1   | red     |
| 2       | star2   | yellow  |
| 3       | star3   | blue    |

### planet

| planet_id | name    | star_id |
| --------- | ------- | ------- |
| 2         | earth   | 1       |
| 3         | mars    | 1       |
| 4         | neptune | 1       |

### moon

| moon_id | name   | planet_id |
| ------- | ------ | --------- |
| 1       | moon1  | 2         |
| 2       | moon2  | 2         |

### blackhole

| blackhole_id | name  |
| ------------ | ----- |
| 4            | bh1   |
| 5            | bh2   |
| 6            | bh3   |

## Setup Instructions

1. **Install PostgreSQL**: Ensure you have PostgreSQL installed on your system.

2. **Create the Database**:
    ```sh
    psql -U your_username -c "CREATE DATABASE universe;"
    ```

3. **Run the SQL Script**: Use the provided SQL script to set up the schema and initial data.
    ```sh
    psql -U your_username -d universe -f path_to_your_script.sql
    ```

## Usage

- Connect to the database using your preferred PostgreSQL client (e.g., `psql`, PgAdmin).
- Query the tables to retrieve information about celestial bodies.

## License

This project is licensed under the MIT License.
