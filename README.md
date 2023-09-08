# ISEC6000-assignment1-task2

# Saleor Platform Setup

This repository provides instructions for configuring the Saleor platform, which is an open-source e-commerce solution.

# Installation
To set up the Saleor platform, follow these steps:

1. Clone this repository to your local machine:
git clone https://github.com/speakas/saleor-platform.git

2. Go to the cloned repository:
cd saleor-platform/

3. Build the application:
docker compose build

4. Apply Django migrations:
docker compose run --rm api python3 manage.py migrate

5. Populate the database with sample data and create an admin user:
docker compose run --rm api python3 manage.py populatedb --createsuperuser
Note: Using the `--createsuperuser` option creates an admin account with the email admin@example.com and the password set as admin.

## Running the Application
Start the application with the following command:
docker compose up

## Docker Compose Configuration
To run the storefront alongside the API, copy the storefront docker-compose.yaml file into the saleor-platform docker-compose.yaml file and make the necessary adjustments. Set the build path to "./react-storefront".

## API Address Setup
In the docker-compose.yaml file, modify the API reference from http://localhost:8000/graphql to http://api:8000/graphql. This adjustment is crucial for proper communication between Docker containers.

## Docker Container Networking
Ensure that all Docker containers share the same network for seamless communication. Add this configuration to the networks list for each image in the docker-compose.yaml file.
