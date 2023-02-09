# Wiremock Stub Server

This project includes the files for mocking requests using wiremock.

## How do I get set up?

This component is into a docker container. You need to generate a docker image using the command below.

```shell
docker image build --tag <my-docker-user>/usersapi-mocks .
```

Run the generated image with:

```shell
docker container run -it --rm -p 8088:8080 --name usersapi-mock <my-docker-user>/usersapi-mocks
```

Push the generated image to DockerHub:

```shell
docker image push <my-docker-user>/usersapi-mocks
```

## User Api Request examples

Create User

```shell
curl -v -X POST -H "Content-type: application/json" -d '{
"email": "john.foo@example.com",
"first_name": "John",
"last_name": "Foo",
"birthday": "1889–04–04"
}' 'localhost:8088/api/users'
```

Delete User

```shell
curl -v -X DELETE 'localhost:8088/api/users/1'
```

Find User by Id

```shell
curl -v 'localhost:8088/api/users/1'
```

Find Users

```shell
curl -v 'localhost:8088/api/users?page=1'
```

Modify User

```shell
curl -v -X PUT -H "Content-type: application/json" -d '{
"first_name": "John",
"last_name": "Foo",
"birthday": "1889–04–04"
}' 'localhost:8088/api/users/1'
```