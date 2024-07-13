# Project Documentation

## Table of Contents

1. [Introduction](#introduction)
2. [Installation](#installation)
    1. [Prerequisites](#prerequisites)
    2. [Setup](#setup)
3. [Usage](#usage)
    1. [Running the Application](#running-the-application)
    2. [Available Endpoints](#available-endpoints)
4. [Development](#development)
    1. [Code Structure](#code-structure)
        1. [Overview](#overview)
        2. [Detailed Breakdown](#detailed-breakdown)
        3. [Reverse Engineering](#reverse-engineering)
    2. [Contributing](#contributing)
        1. [Guidelines](#guidelines)
        2. [Setting Up Development Environment](#setting-up-development-environment)
        3. [Code Style and Best Practices](#code-style-and-best-practices)
5. [Testing](#testing)
6. [API Reference](#api-reference)
7. [Architecture](#architecture)
8. [Technology Stack](#technology-stack)
9. [Core Concepts](#core-concepts)
10. [Terminology](#terminology)
11. [File Disposition Scheme](#file-disposition-scheme)
12. [License](#license)
13. [Contact](#contact)

## Introduction

- **DMART** is a data service layer that makes it easy to build solutions with small to medium amounts of data (up to 300 million entries). It's not designed for systems with large data sets or complex data models that need transactions.

- **DMART** is a general-purpose system for managing information, also known as Data-as-a-Service (DaaS).

- **DMART** is a low-code platform for managing different types of data (structured, unstructured, and binary). It helps you manage your valuable data assets easily, allowing you to create, share, and extend data. This way, your important data can be kept as the main version and act as the single source of truth.

## Installation

Before running the application locally, there are several steps to follow for setting up the project.


- ### Prerequisites
Before installing DMART, ensure you have the following prerequisites installed:
- python >=3.11
- pip
- git 
- jq 
- redis>=7.2
- RedisJSON (rejson) >= 2.6
- RediSearch >= 2.8

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
   <br>
   <br>
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
