## Installation

1. Clone the repository:
    ```sh
    git clone <repository-url>
    cd Backend
    ```

2. Install dependencies:
    ```sh
    npm install
    ```

3. Create a `.env` file in the [Backend](http://_vscodecontentref_/14) directory and add the following environment variables:
    ```
    PORT=3000
    DB_CONNECT=<your-mongodb-connection-string>
    JWT_SECRET=<your-jwt-secret>
    ```

4. Start the server:
    ```sh
    npm start
    ```

## API Endpoints

# API Endpoints

### User Routes

- **POST /users/register**
    - Registers a new user.
    - Request body:
        ```json
        {
            "fullname": {
                "firstname": "John",
                "lastname": "Doe"
            },
            "email": "john.doe@example.com",
            "password": "password123"
        }
        ```

- **POST /users/login**
    - Logs in a user.
    - Request body:
        ```json
        {
            "email": "john.doe@example.com",
            "password": "password123"
        }
        ```

- **GET /users/profile**
    - Gets the profile of the authenticated user.
    - Requires authentication.

### Captain Routes

- **POST /captains/register**
    - Registers a new captain.
    - Request body:
        ```json
        {
            "fullname": {
                "firstname": "Jane",
                "lastname": "Doe"
            },
            "email": "jane.doe@example.com",
            "password": "password123",
            "vehicle": {
                "color": "red",
                "plate": "ABC123",
                "capacity": 4,
                "vehicleType": "car"
            }
        }
        ```
    - Response:
        ```json
        {
            "token": "jwt-token",
            "captain": {
                "_id": "captain-id",
                "fullname": {
                    "firstname": "Jane",
                    "lastname": "Doe"
                },
                "email": "jane.doe@example.com",
                "vehicle": {
                    "color": "red",
                    "plate": "ABC123",
                    "capacity": 4,
                    "vehicleType": "car"
                },
                "status": "active"
            }
        }
        ```
    - Validation:
        - `email`: Must be a valid email.
        - `fullname.firstname`: Must be at least 3 characters long.
        - `password`: Must be at least 6 characters long.
        - `vehicle.color`: Must be at least 3 characters long.
        - `vehicle.plate`: Must be at least 3 characters long.
        - `vehicle.capacity`: Must be a number.
        - `vehicle.vehicleType`: Must be one of `car`, `motorcycle`, or `auto`.

- **POST /captains/login**
    - Logs in a captain.
    - Request body:
        ```json
        {
            "email": "jane.doe@example.com",
            "password": "password123"
        }
        ```
    - Response:
        ```json
        {
            "token": "jwt-token",
            "captain": {
                "_id": "captain-id",
                "fullname": {
                    "firstname": "Jane",
                    "lastname": "Doe"
                },
                "email": "jane.doe@example.com",
                "vehicle": {
                    "color": "red",
                    "plate": "ABC123",
                    "capacity": 4,
                    "vehicleType": "car"
                },
                "status": "active"
            }
        }
        ```

- **GET /captains/profile**
    - Gets the profile of the authenticated captain.
    - Requires authentication.
    - Response:
        ```json
        {
            "captain": {
                "_id": "captain-id",
                "fullname": {
                    "firstname": "Jane",
                    "lastname": "Doe"
                },
                "email": "jane.doe@example.com",
                "vehicle": {
                    "color": "red",
                    "plate": "ABC123",
                    "capacity": 4,
                    "vehicleType": "car"
                },
                "status": "active"
            }
        }
        ```

- **GET /captains/logout**
    - Logs out the authenticated captain.
    - Requires authentication.
    - Response:
        ```json
        {
            "message": "Logged out successfully"
        }
        ```

## Middleware

- **auth.middleware.js**
    - Authenticates users using JWT tokens.

## Models

- **user.model.js**
    - Defines the user schema and methods for password hashing and token generation.

- **captain.model.js**
    - Defines the captain schema and methods for password hashing and token generation.

- **blacklistToken.model.js**
    - Defines the schema for blacklisted tokens.

## Services

- **user.service.js**
    - Contains the logic for creating users.

- **captain.service.js**
    - Contains the logic for creating captains.

## Controllers

- **user.controller.js**
    - Handles user registration, login, and profile retrieval.

- **captain.controller.js**
    - Handles captain registration.

## Database

- **db.js**
    - Connects to the MongoDB database using Mongoose.

## License

This project is licensed under the ISC License.# uber-clone
