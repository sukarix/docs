# Deployment

<!-- toc -->

## Introduction

Deploying a Sukarix application involves several steps to ensure your code is properly set up on the production server.

## Sukarix Deployment Basics

1. **Upload Your Code**:
    - Transfer your application's codebase to the production server using your preferred method (e.g., FTP, SCP, or
      Git).

2. **Ensure `sukarix.sh` is in the `tools` Directory**:
    - Make sure the `sukarix.sh` script is located in the `tools` directory of your application.

3. **Run the Deployment Script**:
    - Execute the deployment script with the `-d` option:
      ```bash
      ./tools/sukarix.sh -d
      ```
    - This command performs the following actions:
        - Pulls the latest code from the Git repository.
        - Runs Composer to install dependencies.
        - Applies default permissions to the `www-data` user.
        - Runs database migrations.
        - Clears the application cache.
