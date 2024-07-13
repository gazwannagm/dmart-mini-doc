# Project Documentation

## Table of Contents

1. [Installation](#installation)
    1. [Setup](#setup)
2. [Usage](#usage)
    1. [Running the Application](#running-the-application)
    2. [Available Endpoints](#available-endpoints)
3. [Development](#development)
    1. [Code Structure](#code-structure)
        1. [Overview](#overview)
        2. [Detailed Breakdown](#detailed-breakdown)
        3. [Reverse Engineering](#reverse-engineering)
3. [API Reference](#api-reference)
5. [File Disposition Scheme](#file-disposition-scheme)


## Installation

Before running the application locally, there are several steps to follow for setting up the project.

- ### Setup
1. ### Enable kefahi dnf from copr to download Redis modules

    ```bash
    sudo dnf copr enable kefah/RediSearch
    ```
2. ### Download necessary system packages
   ``` bash
   sudo dnf install jq redis rejson redisearch python3-pip python3
   echo 'loadmodule /usr/lib64/redis/modules/librejson.so
   loadmodule /usr/lib64/redis/modules/redisearch.so' | sudo tee -a /etc/redis/redis.conf
   ```
   Now Start Redis Service
   ```Bash
   sudo systemctl start redis
   ```
3. ### Create logs folder
    Make sure to create the logs folder in the same directory as the repository folder.
    ```bash
        mkdir logs
    ```
   Take in consederation This Folder Structure
    ```Kotlin
      root/
      ├── logs/       <--create this Directory
      |
      └── dmart/
          ├── ... (other dmart project files and directories)
    ```

4. ### Clone the repository:
    ```bash
      git clone https://github.com/edraj/dmart.git
    ```
   Navigate Into Dmart
   ```bash
      cd dmart  
   ```
5. ### Copy sample Spaces Structure
    ```Bash
        cp -a sample/spaces ../
    ```
    Folder Structure Should Look like this 
    ```Kotlin
      root/
      ├── logs/       <--create this Directory
      |
      └── dmart/
      |    ├── ... (other dmart project files and directories)
      |
      └── spaces/
    ```
6. ### Navigate to the backend directory
     ```Bash
        cd backend
     ```
7. ### Create the virtual environment 
   ```Bash
        python -m venv ~/.env
   ```
8. ### Activate the virtual environment
   ```Bash
     source ~/.env/bin/activate
    ```
9. ### Install python dependencies
   ```Bash
      pip install --user -r requirements.txt
   ```
10. ### Optionally, fine-tune your configuration
   ```Bash
        cp config.env.sample config.env
   ```

## Usage
To start using the Application Follow the Below Step: 

### Running the Application:
To run the Application We need to Create and Admin Password for authentication

1. ### Set the Admin Password
   before Running this command make sure you are inside the Following Directory:
   <br/>
   <br/>
   root/dmart/backend/
   
   ```Bash
   ./set_admin_passwd.py
   ```
2. ### Start Dmart 
   we Must be in the same directory as the above Step and run this command
   ```Bash
   ./main.py
   ```

### Available Endpoints
### Info Directory
#### GET /me
Gets the shortname of the authenticated user.

   <details>
     <summary><code>GET</code> <code><b>/me</b></code> <code>(gets the shortname of the authenticated user)</code></summary>
   
   #### Description
   This endpoint returns the shortname of the authenticated user. The user must be authenticated using a JWT token.
      
   #### Authentication
   Requires JWT authentication.

   #### Parameters
   > | Name        | Type     | Data Type | Description                   |
   > |-------------|----------|-----------|-------------------------------|
   > | shortname   | required | string    | Authenticated user's shortname|
   
   #### Responses
   > | HTTP Code | Content-Type         | Response                                                                                     |
   > |-----------|----------------------|----------------------------------------------------------------------------------------------|
   > | `200`     | `application/json`   | `{"status":"success","attributes":{"shortname":"<shortname>"}}`                              |
   > | `401`     | `application/json`   | `{"status":"error","error":{"type":"access","code":"NOT_ALLOWED","message":"Unauthorized"}}`  |
   
   #### Example cURL
   ```bash
   curl -X GET -H "Authorization: Bearer <token>" http://0.0.0.0:8282/me
   ```
 </details>


### GET /settings
Gets the settings if the user is authenticated as 'dmart'.

<details>
  <summary><code>GET</code> <code><b>/settings</b></code> <code>(gets the settings if authenticated as 'dmart')</code></summary>
  
  #### Description
  This endpoint retrieves settings data if the authenticated user's shortname is 'dmart'. Otherwise, it returns a 401 Unauthorized error.
  
  #### Authentication
  Requires JWT authentication.
  
  #### Parameters
  > | Name        | Type     | Data Type | Description                          |
  > |-------------|----------|-----------|--------------------------------------|
  > | shortname   | required | string    | Authenticated user's shortname       |
  
  #### Responses
  > | HTTP Code | Content-Type         | Response                                                                                     |
  > |-----------|----------------------|----------------------------------------------------------------------------------------------|
  > | `200`     | `application/json`   | `{"status":"success","attributes":<settings_data>}`                                            |
  > | `401`     | `application/json`   | `{"status":"error","error":{"type":"access","code":"NOT_ALLOWED","message":"Unauthorized"}}`  |
  
  #### Example cURL
  ```bash
  curl -X GET -H "Authorization: Bearer <token>" http://0.0.0.0:8282/settings
  ```
</details>

## Development

### Code Structure

#### Overview

#### Detailed Breakdown

#### Reverse Engineering

### Contributing

#### Guidelines

#### Setting Up Development Environment

#### Code Style and Best Practices

## Testing

## API Reference

## Architecture

## Technology Stack

## Core Concepts

## Terminology

## File Disposition Scheme

## License

## Contact
