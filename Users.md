FORMAT: 1A

# Users

Users is a service for creating and updating users, getting profile info and dragon info

## Group User

User-related endpoints

## User [/users/{user_id}]

+ Parameters
  + user_id: 1 (required, number) - ID of the user

### View a users profile [GET]

+ Response 200 (application/json)

        {
          'id': 1,
          'username': 'Johnny',
          'email': 'John@gmail.com',
          'confirmed': true,
          'registationDate': 2017-10-26T16:51:59.000Z,
          'avatar': 'http://avatars.com/1.jpg',
          'backgroundPicture': 'http://hotbgpics.com/12.png',
          'country': 'USA',
          'dateOfBirth': 1982-01-01T00:00:00.000Z,
          'bio': 'a short bio',
          'premium': false,
          'role': 'user',
          'silver': 1220,
          'sapphires': 100,
          'items': {
            'ingredients': [],
            'items': []
          },
          dragons: []
        }

### Update user profile

Takes a object with fields to update, ignores restricted fields

+ Response 200 (application/json)
  
  Returns full user object with updated fields

## Create user [/users/create]

### Create a new user [POST]

+ Request (application/json)

  + Body

        {
          'username': 'Jason',
          'email': 'ja@gmail.com',
          'password': '123'
        }

  + Schema

        {
          'type': 'object',
          'properties': {
            'username': {
              'type': 'string',
              'minLength': 3,
              'maxLength': 30
            },
            'email': {
              'type': 'string'
            },
            'password': {
              'type': 'string',
              'minLength': 3
            }
          }
        }

+ Response 201 (application/json)
Responds with newly created user data

+ Response 409 (application/json)
Email is already taken

+ Response 400 (application/json)
Missing or wrong data
