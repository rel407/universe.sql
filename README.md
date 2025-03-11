# Universe Database Project

This project is a PostgreSQL database dump created as part of a FreeCodeCamp course. The database contains a collection of tables representing various celestial bodies and their attributes, including **asteroids**, **planets**, **stars**, **moons**, and **galaxies**. The data includes relevant information such as names, types, sizes, and other characteristics of each entity.

## Project Overview

The database is structured with several key tables that capture the relationships and data about celestial objects. These include:

- **Asteroids**: Information on asteroids in various galaxies, including their size, speed, and galaxy affiliation.
- **Planets**: Data on planets, such as their type (e.g., terrestrial, gas giant), whether they have confirmed life, and their associated star and galaxy.
- **Stars**: Details of stars, including their galaxy, description, and distance from Earth.
- **Moons**: Information on moons orbiting planets, including whether they are spherical and their approximate age.
- **Galaxies**: Data on various galaxies, including their type and whether they have confirmed life.

### Database Schema

The following tables are part of the schema:

1. **asteroid**:
    - `asteroid_id`: Unique ID for each asteroid
    - `name`: Name of the asteroid
    - `galaxy_id`: ID of the galaxy the asteroid belongs to
    - `diameter_in_km`: Diameter of the asteroid in kilometers
    - `speed_kmps`: Speed of the asteroid in kilometers per second

2. **galaxy**:
    - `galaxy_id`: Unique ID for each galaxy
    - `name`: Name of the galaxy
    - `galaxy_type`: Type of the galaxy (e.g., spiral, elliptical)
    - `confirmed_life`: Whether the galaxy has confirmed life
    - `diameter_in_light_years`: Diameter of the galaxy in light years

3. **moon**:
    - `moon_id`: Unique ID for each moon
    - `name`: Name of the moon
    - `planet_id`: ID of the planet the moon orbits
    - `is_spherical`: Whether the moon is spherical
    - `age_in_billions`: Age of the moon in billions of years

4. **planet**:
    - `planet_id`: Unique ID for each planet
    - `name`: Name of the planet
    - `planet_type`: Type of the planet (e.g., terrestrial, gas giant)
    - `is_spherical`: Whether the planet is spherical
    - `confirmed_life`: Whether the planet has confirmed life
    - `moon_count`: Number of moons the planet has
    - `star_id`: ID of the star the planet orbits
    - `galaxy_id`: ID of the galaxy the planet belongs to

5. **star**:
    - `star_id`: Unique ID for each star
    - `name`: Name of the star
    - `galaxy_id`: ID of the galaxy the star belongs to
    - `description`: Description of the star
    - `ly_from_earth`: Distance from Earth in light years

### Relationships

The schema includes several foreign key relationships:

- **Galaxy** is related to **Planets**, **Stars**, and **Asteroids**.
- **Planet** is related to **Moons** and **Stars**.
- **Moon** is related to **Planets**.
- **Asteroid** is related to **Galaxies**.

### Data

The database contains sample data for each of the celestial objects, including several well-known entities like:

- **Planets**: Mercury, Venus, Earth, Mars, Jupiter, Saturn, Uranus, Neptune
- **Stars**: Sun, Proxima Centauri, Kepler-22, TRAPPIST-1
- **Moons**: Moon (Earth), Io, Europa, Ganymede, Callisto
- **Asteroids**: Ceres, Vesta, Eros, Pallas, Itokawa
- **Galaxies**: Milky Way, Andromeda, Triangulum

### How to Use

1. **Set up PostgreSQL**: Install PostgreSQL on your local machine or use a cloud database service.
2. **Import the Dump**: Use the following command to restore the database from the dump:
    ```bash
    psql -U your_username -d your_database_name -f universe_dump.sql
    ```
3. **Connect to the Database**: Use any PostgreSQL client (like pgAdmin or psql) to connect to the database.
4. **Explore**: You can run SQL queries to explore the data and analyze relationships between the celestial objects.

### Example Queries

Here are some example queries you can run on the database:

1. **List all planets with their types and whether they have confirmed life:**
    ```sql
    SELECT name, planet_type, confirmed_life FROM planet;
    ```

2. **Get the names of moons for a specific planet (e.g., Earth):**
    ```sql
    SELECT name FROM moon WHERE planet_id = (SELECT planet_id FROM planet WHERE name = 'Earth');
    ```

3. **Find all asteroids in the Milky Way galaxy:**
    ```sql
    SELECT name FROM asteroid WHERE galaxy_id = (SELECT galaxy_id FROM galaxy WHERE name = 'Milky Way');
    ```

### Technologies Used

- PostgreSQL (Database)
- SQL (Queries)

### License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

Feel free to open an issue or submit a pull request if you have any questions or improvements for the project!
