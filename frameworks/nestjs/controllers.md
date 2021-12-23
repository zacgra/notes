https://docs.nestjs.com/controllers

# Controllers

`DEF` Controller: receives specific requests for application

## Full Example

```ts
import {
  Controller,
  Get,
  Query,
  Post,
  Body,
  Put,
  Param,
  Delete,
} from "@nestjs/common";
import { CreateCatDto, UpdateCatDto, ListAllEntities } from "./dto";

@Controller("cats")
export class CatsController {
  @Post()
  create(@Body() createCatDto: CreateCatDto) {
    return "This action adds a new cat";
  }

  @Get()
  findAll(@Query() query: ListAllEntities) {
    return `This action returns all cats (limit: ${query.limit} items)`;
  }

  @Get(":id")
  findOne(@Param("id") id: string) {
    return `This action returns a #${id} cat`;
  }

  @Put(":id")
  update(@Param("id") id: string, @Body() updateCatDto: UpdateCatDto) {
    return `This action updates a #${id} cat`;
  }

  @Delete(":id")
  remove(@Param("id") id: string) {
    return `This action removes a #${id} cat`;
  }
}
```

## Routing

Sample Code:

```ts
import { Controller, Get } from "@nestjs/common";

@Controller("cats")
export class CatsController {
  @Get()
  findAll(): string {
    return "This action returns all cats";
  }
}
```

`@Controller` - required to define a basic controller

`('cats')` - optional argument to create a related route group prefix (ie `/cats/:id`, `/cats/name)`)

`@Get()` - creates a handler for specific HTTP endpoint request

`@Get()`
This method creates the handler at the route path, which is a concatenation of the optional prefix (`cats`) and the path specified by the decorator.

### @Get() Example #1

```ts
@Controller("cats")
export class CatsController {
  @Get()
  findAll(): string {
    return "This action returns all cats";
  }
}
```

Without any argument in `@Get()`, the path is not specified and in this case is just `/cats/`. Nestjs will map this to `GET /cats`

### @Get('profile') Example #2

```ts
@Controller("cats")
export class CatsController {
  @Get("profile")
  findAll(): string {
    return "This action returns all cats";
  }
}
```

With the argument of `"profile"`, Nestjs will map this to `GET /cats/profile`

<hr>

## Request object

Sample Code:

```ts
import { Controller, Get, Req } from "@nestjs/common";
import { Request } from "express";

@Controller("cats")
export class CatsController {
  @Get()
  findAll(@Req() request: Request): string {
    return "This action returns all cats";
  }
}
```

> import express typings with `@types/express`

A list of the provided decorators and the plain platform-specific objects they represent:
https://docs.nestjs.com/controllers#request-object

## Resources

Code Sample:

```ts
import { Controller, Get, Post } from "@nestjs/common";

@Controller("cats")
export class CatsController {
  @Post()
  create(): string {
    return "This action adds a new cat";
  }

  @Get()
  findAll(): string {
    return "This action returns all cats";
  }
}
```

Multiple methods in one controller.

## Status Code

Modify default `200` status code with `@HttpCode(...)`
Sample Code:

```ts
@Post()
@HttpCode(204)
create() {
  return 'This action adds a new cat';
}
```

Use the library-specific response (something like `create(@Res() response)`) provide conditional status codes.

> import `HttpCode` from `@nestjs/common`

## Headers, Redirection, ...

## Route parameters

```ts
@Get(':id')
findOne(@Param() params): string {
  console.log(params.id);
  return `This action returns a #${params.id} cat`;
}
```

Access router parameter with `@Param()` decorator

## Sub-Domain Routing, Scopes, ...

## Asynchonicity

Sample Code:

```ts
@Get()
async findAll(): Promise<any[]> {
  return [];
}
```

? Is promised being declared as the return type of findAll()?

## Request payloads

1. Create DTO schema
   Data Transfer Object (DTO) used to define how data is sent over network. Use classes so they are preserved in compile to JS.

```ts
export class CreateCatDto {
  name: string;
  age: number;
  breed: string;
}
```

2.  Use DTO inside of controller

```js
@Post()
async create(@Body() createCatDto: CreateCatDto) {
  return 'This action adds a new cat';
}
```

Enable DTO validation with `ValidationPipe` by setting `whitelist` to `true`.

```ts
app.useGlobalPipes(
  new ValidationPipe({
    whitelist: true,
  })
);
```
