# Databases Management

### Database Configuration

For configuring database access, the framework follows the guidelines outlined by
the [Fat-Free Framework](https://fatfreeframework.com/3.8/databases). This includes setting up database connections and
handling queries efficiently.

### Cortex ORM

The framework utilizes Cortex ORM for object-relational mapping, simplifying interactions with the database. For
detailed usage and configuration instructions, refer to the [Cortex documentation](https://github.com/ikkez/f3-cortex).

### Database Migrations

Database migrations are managed using the Phinx library, which is included in the template application with
a `phinx.json` file. This file can be customised, although Phinx is the recommended tool. Comprehensive documentation
for Phinx is available [here](https://book.cakephp.org/phinx/0/en/intro.html).

### Model Class

The `Model` class provides a structured way to access data using Cortex ORM. It includes methods for pagination, data
conversion, and change detection, ensuring robust and efficient data handling.

```admonish abstract title="<u>Sukarix Convention:</u> Model timestapms"
The `Model` class follows conventions for managing timestamps:

- **created_on:** Automatically set when a record is created.
- **updated_on:** Automatically updated when a record is modified.
```
