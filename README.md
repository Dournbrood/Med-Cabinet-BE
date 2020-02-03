# Back-End Documentation

Under Construction!

Note: Many endpoints in this API return an array of objects for ease-of-mapping in the front end. This is a convenience feature that might not always be available depending on how the data we want to send is structured. In the case that you should receive an object of objects, go ahead and use `Object.values(thingToConvert)` to convert it to an array of objects.

## Things We, The Back-End, Need To Do

- [ ] Find out -EXACTLY- what recommendations are. What they contain and belong to, etc. 
  - A recommendation is: 
     ```
        {
            strain: "?"
        }
     ```
- [ ] Find out what responses are as well. Relations and stuff.
  - A response is: 
    ```
    {
        
    }
    ```
- [ ] Get It Hosted (oh boy)
  - API is hosted at `nowhere at the moment, go away`

## Endpoints: 

### `POST` to `/api/auth/register`:

API request data shape FROM front-end: 

```
{
    username: "your-username-here",
    password: "super-secret-thing-SHHHhHHHSSh"
}
```

If successful, the API will respond with: 

```
{
    id: 1298347, //This can really be any integer, but it increments.
    username: "some-stringy-thing"   
}
```

### `POST` to `/api/auth/login`:

What the front-end should be sending to API: 

```
{
    username: "zoinks",
    password: "scoob"
}
```

What the API will respond with on login success: 

```
{
    token: "secret cow says moo", //This will be a string of garbledygook. Send this in your authentication header whenever you want to access something restricted as the front-end.
    message: "Welcome, zoinks!"
}
```

### `GET` to `/api/users`:

Don't send a body, instead send the token you got from the `login` endpoint inside your `Authentication` header.

If successful, the API will return: 

```
[
    "0": {
        "id": 1,
        "username": "moomer"
    }
    "1": {
        "id": 2,
        "username": "donkey kong"
    }
]
```

### `GET` to `/api/responses`: 

Be sure to send a valid token in the `Authentication` header. (Once that actually gets implemented...)

The API returns: 

```
[
    "0": {
        "id": 1,
        "strain": "Nuclear War Cube"
    },
    "1": {
        "id": 2,
        "strain": "Gamer Fuel"
    },
    "2": {
        "id": 3,
        "strain": "Dogg's Select"
    }
]
```