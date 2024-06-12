# Instructions for a new Sukarix application

To set up your Sukarix application with Vagrant follow these steps:

## Step 1: Create a new Sukarix project

Run the following command to create a new Sukarix project using Composer:

```sh
composer create-project --stability=dev  sukarix/application
```

## Step 2: Navigate to the project directory

Once the project is created, navigate to the project directory:

```sh
cd application
```

## Step 3: Initialize vagrant

The Sukarix project includes a Vagrant setup to help streamline the development environment. Initialize Vagrant by
running:

```sh
vagrant up
```

This command will set up the Vagrant environment and automatically install PostgreSQL and Redis.

## Step 4: Access the Application

After the Vagrant setup is complete, the application will be accessible via:

```sh
http://sukarix.test
```

## Configuration Details

- **PostgreSQL** and **Redis** are installed by default in the current version of the Sukarix project.
- Ensure your local environment is configured to handle `.test` domains (you might need to adjust your hosts file if
  necessary).

### Accessing the Application

After running `vagrant up`, you can access your application at `http://sukarix.test`. If you encounter issues accessing
the site, ensure your system's hosts file includes the correct entry, typically something like:

```plaintext
192.168.50.4  sukarix.test
```
