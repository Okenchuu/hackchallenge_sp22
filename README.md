# Team 12 Hack Challenge SP22 
DockerHub: https://hub.docker.com/repository/docker/juliazeng23/hackchallenge <br />
External VM IP: http://34.130.167.204 <br />

## API routes

#### 1. Get all subjects (GET /api/subjects/) <HTTP STATUS CODE 200>
<pre>
Response:
{
    "subjects": [
        {
            "id": 1,
            "name": "MATH"
        }, 
        {
            "id": 2,
            "name": "ECON"
        }
    ]
}
</pre>
#### 2. Create a user (POST /api/users/) <HTTP STATUS CODE 201>
<pre>
Request:
{
    "username": "zw332",
    "name": "Zhan Wu",
    "bio": "Senior major in Math",
    "price": 10,
    "subjects": ["MATH", "ECON"],
    "isAvailable": false,
    "password": "aaaaa"
}
Response:
{
    "session_token": "ea0c90f98c6435621f1a5c19533ee15160c0c9d3",
    "session_expiration": "2022-05-07 02:51:28.784776",
    "update_token": "59ed21dc26a7ccb44fdaed4463f2f9d3a9b6c144",
    "user": {
        "id": 1,
        "username": "jwz28",
        "name": "Julia Zeng",
        "bio": "freshman in CS",
        "price": 10,
        "isAvailable": false,
        "subjects": [
            {
                "id": 1,
                "name": "MATH"
            },
            {
                "id": 2,
                "name": "CS"
            }
        ],
        "sent_transactions": [],
        "received_transactions": []
    }
}
</pre>
#### 3. Get a user by id (GET /api/users/<int:user_id>/) <HTTP STATUS CODE 200>
<pre>
Response:
{
    "id": 1,
    "username": "zw332",
    "name": "Zhan Wu",
    "bio": "Senior major in Math",
    "price": 10,
    "isAvailable": false,
    "subjects": [
        {
            "id": 1,
            "name": "MATH"
        }, 
        {
            "id": 2,
            "name": "ECON"
        }
    ],
    "sent_transactions": [],
    "received_transactions": []
}
</pre>
#### 4. Edit a user (POST /api/users/{userId}/) <HTTP STATUS CODE 201>
<pre>
Request:
{
    "username": "zw332",
    "name": "Zhan Wu",
    "bio": "Senior major in Math",
    "price": 10,
    "subjects": ["MATH", "ECON", "CHEM"],
    "isAvailable": true
}
Response:
{
    "id": 1,
    "username": "zw332",
    "name": "Zhan Wu",
    "bio": "Senior major in Math",
    "price": 10,
    "isAvailable": true,
    "subjects": [
        {
            "id": 1,
            "name": "MATH"
        }, 
        {
            "id": 2,
            "name": "ECON"
        },
        {
            "id": 3,
            "name": "CHEM"
        }
    ],
    "sent_transactions": [],
    "received_transactions": []
}
</pre>

#### 5. Get all available mentors of a subject (GET /api/subjects/<int:subject_id>/users/) <HTTP STATUS CODE 200>
<pre>
Response:
[
    {
        "id": 1,
        "username": "zw332",
        "name": "Zhan Wu",
        "bio": "Senior major in Math",
        "price": 10,
        "isAvailable": true 
    }, 
    {
        "id": 2,
        "username": "xz348",
        "name": "Xiying Zhang",
        "bio": "Junior major in CS",
        "price": 10,
        "isAvailable": true 
    }
]
</pre>

#### 6. Delete a user (DELETE /api/users/{id}/) <HTTP STATUS CODE 200>
<pre>
Response:
{
    "id": 1,
    "username": "zw332",
    "name": "Zhan Wu",
    "bio": "Senior major in Math",
    "price": 15,
    "isAvailable": true,
    "subjects": [
        {
            "id": 1,
            "name": "MATH"
        }, 
        {
            "id": 2,
            "name": "ECON"
        }
    ],
    "sent_transactions": [
        {
            "id": 1,
            "sender_id": 1,
            "sender_name": "Zhan Wu",
            "sender_username": "zw332",
            "receiver_id": 2,
            "receiver_name": "Charlotte Ding"
        },
        {
            "id": 2,
            "sender_id": 1,
            "sender_name": "Zhan Wu",
            "sender_username": "zw332",
            "receiver_id": 3,
            "receiver_name": "Julia Zeng"
        }
    ],
    "received_transactions": [
        {
            "id": 3,
            "sender_id": 3,
            "sender_name": "Julia Zeng",
            "sender_username": "jwz28",
            "receiver_id": 1,
            "receiver_name": "Zhan Wu"
        }
    ]
}
</pre>

#### 7. A user sends a request to a tutor (POST /api/transactions/) <HTTP STATUS CODE 201>
<pre>
Request:
{
    "sender_id": 1,
    "receiver_id": 2
}
Response:
{
    "id": 2,
    "sender_id": 1,
    "sender_name": "Julia Zeng",
    "sender_username": "jwz28",
    "receiver_id": 2,
    "receiver_name": "Charlotte Ding"
}
</pre>

#### 8. Login (POST /api/login/) <HTTP STATUS CODE 200>
<pre>
Request:
{
    "username": "zzzzz",
    "password": "aaaaa"
}
Response:
{
    "session_token": "935556ce055087e0ca7ea753d8909f08c55c0d2e",
    "session_expiration": "2022-05-05 00:09:45.526060",
    "update_token": "24b47f53e4d2575093589dd1fde995bd0e7af4ae"
}
</pre>

#### 9. Simple Login (POST /api/simplelogin/) <HTTP STATUS CODE 200>
<pre>
Request:
{
    "username": "zzzzz",
    "password": "aaaaa"
}
Response:
{
    "userId": 1
}
</pre>

#### 10. Update user's session (POST /api/session/) <HTTP STATUS CODE 200>
<pre>
Request: 
{
    "Headers": {
        "KEY": "Authorization",
        "VALUE": "Bearer fe3d69ad51497777fc8f1eff7302fc4118afb492"
    }
}
Response:
{
    "session_token": "935556ce055087e0ca7ea753d8909f08c55c0d2e",
    "session_expiration": "2022-05-05 00:09:45.526060",
    "update_token": "24b47f53e4d2575093589dd1fde995bd0e7af4ae"
}
</pre>

#### 11. Get secret message (GET /api/secret/) <HTTP STATUS CODE 200>
<pre>
Request:
{
    "Headers": {
        "KEY": "Authorization",
        "VALUE": "Bearer fe3d69ad51497777fc8f1eff7302fc4118afb492"
    }
}
Response:
"Hello World"
</pre>

## Database Models
There are 3 Models and 1 association table in our database.

### Model 1: User
#### Columns:
**id** (int), **username** (string), **name** (string), **bio** (string), **price** (int), **isAvailable** (boolean), **password_digest** (string), **session_token** (string), **session_expiration** (datetime), **update_token** (string)
#### Relationships:
**subjects**: A list of subjects that has a relationship with the Subject model and has an association table as the secondary key.<br />
**sent_transactions**: A list of transactions that have been sent by the user, has a relationship with the Transaction model.<br />
**received_transactions**: A list of transactions that have been received by the user, has a relationship with the Transaction model.<br />

### Model 2: Subject
#### Columns:
**id** (int), **name** (string)
#### Relationships:
**users**: A list of users that has a relationship with the User model and has an association table as the secondary key.<br />

### Model 3: Transaction
#### Columns:
**id** (int), **sender_id** (int), **receiver_id** (int)
#### Relationships:
**sender**: Sender of the transaction, has relationship with the User model and using the sender_id referring the User's id as foreign key.<br />
**receiver**: Receiver of the transaction, has relationship with the User model and using the receiver_id referring the User's id as foreign key.<br />

### Association Table: userSubject_table
#### Resolve Many-to-Many relationship between the User model and the Subject model
#### Columns and Relationships:
**user_id** (int): The user id referring the User model's id as foreign key.<br />
**subject_id** (int): The subject id referring the Subject model's id as foreign key.<br />
