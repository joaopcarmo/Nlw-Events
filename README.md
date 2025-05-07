# Event Management System - NLW Events

This is an event management system developed with Spring Boot. It allows for the creation, retrieval, and management of events, along with a registration system that includes referral tracking and a ranking feature.

## Overview

The system is a Java Spring Boot application that manages events and user registrations. It provides a REST API to interact with its resources.

### Main Features:

- Create and retrieve events
- Register users for events
- Referral system: users can refer others
- Generate a referral ranking
- View a specific user's position in the ranking

## Project Structure

### Main Packages:

- **controller**: REST controllers that expose the API
- **model**: Domain entities mapped to the database
- **service**: Business logic layer
- **repository**: Interfaces for database access
- **dto**: Data Transfer Objects
- **exception**: Custom exceptions

### Core Entities:

- **Event**: Represents an event with title, location, price, and dates
- **User**: Represents a user with name and email
- **Subscription**: Represents a user's registration to an event, optionally including a referrer

## API Endpoints

### Events

- `POST /events` - Registers a new event  
- `GET /events` - Lists all events  
- `GET /events/{prettyName}` - Retrieves a specific event by its formatted name

### Subscriptions

- `POST /subscription/{prettyName}` - Registers a user for an event  
- `POST /subscription/{prettyName}/{userId}` - Registers a user with a referral  
- `GET /subscription/{prettyName}/ranking` - Returns the top 3 referrers for an event  
- `GET /subscription/{prettyName}/ranking/{userId}` - Returns a specific user’s ranking position

## Configuration

CORS configuration is included to allow frontend applications to access the API, supporting GET, POST, PUT, and DELETE methods.

## Exception Handling

The system handles the following error cases:

- Event not found  
- Registration conflict (user already registered for the event)  
- Referrer not found

## Data Modeling

The system uses a relational database with the following tables:

- `tbl_event`: Stores event information  
- `tbl_user`: Stores user information  
- `tbl_subscription`: Stores registration data and relationships

## How to Run

1. Clone the repository  
2. Configure your database in the application properties  
3. Run the project using Maven: `mvn spring-boot:run`  
4. The API will be available at: `http://localhost:8080`

## Technologies Used

- Java  
- Spring Boot  
- Spring Data JPA  
- Spring Web  
- Relational database (configurable)
