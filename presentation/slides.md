class: center, middle, section-title

# Contract-first API development
## using the OpenAPI Specification<br/>(fka Swagger)

???
- Hi and welcome to: 
- Contract-first API development using the OpenAPI Specification formerly known as Swagger

---

class: center, middle

.left-column[
## Ian Zelikman
### @izcoder
]

.right-column[
## Dave Forgac
### @tylerdave
]

???
- I'm Dave Forgac and this is Ian Zelikman.
- We used to work together on the API team at American Greetings, but he's since moved on to a different job at IBM Watson Health.
- You can read our bios on the OSCON site if you want to know more.
- One thing I would like to point out is that we are not affiliated with the OpenAPI Initiative.
- We are simply users of and fans of the technology.

---

class: center, middle

# Prerequisites
## + Slides, Examples,<br/>Links, Feedback:
## http://BetterAPIs.com

???
- We put together a simple website for this tutorial.
- It is available at BetterAPIs.com
- If you haven't done so already, this is where you can find instructions for installing the tutorial prerequisites
- In case you're having trouble downloading the installers we have a few USB flash drives we can pass around
- We'll also have a link to a survey for you to provide feedback at the end.
- We'd really appereciate you taking the time to compmlete that so we can improve our tutorial for next time

---

class: center, padded-top2

# Verify Your Installation

???
- If you don't have the prerequisites installed yet, you should be following the directions to do so now.
- Once do, we'd like you to verify that they're working.
- You can do this by first opening TODO: directions for editor
- Then run TODO: directions for CLI test

---

class: center, middle

# Backup Plan

???
- Before we start the tutorial lessons I'm going to run through some background information.
- During this time Ian will be walking around helping people get things installed.
- If you need help, raise your hand and he'll try to get to you.
- If you're not able to get the prerequisites installed by the time we're ready to start the lessons:
- You can use the online editor to follow-along for the first half and then we can try to get things working during the break


---

class: center, middle, section-title

# Background

???
- Before we really get started I want to go over some terminology and concepts
to make sure we're all on the same page.

---
class: center, padded-top

# REST

???
- REST is a *HUGE* topic
- For our purposes you just need to know a few things

--

## ~~Standard~~

???
- It's not a standard

--

## Architectural Style

???
- It's an architctural-style

--

## Constraints

???
- For an API to be truly RESTful it needs to adhere to specific constraints:
  - Client-Server, Stateless, Cache, Interface / Uniform Contract, Layered System, Code-On-Demand

--

## REST-inspired HTTP APIs

???
- Most APIs don't fully adhere to these constraints
- But they do follow some of the patterns, most commonly
  - mapping HTTP methods to actions
  - mapping URL paths to resources or objects
- So we're really talking about REST-like or REST-inspired HTTP APIs

---
class: center, padded-top

# API Contract

???
Next is the idea of an API contract

--

## Client ↔ Provider

???
- Like a legal contract: 
  - It's an agreement between client and API provider
  - It should be negotiated
--

## Interface Specification

???
- The contract includes technical specification of how requests & responses should work

--

## SLA, ToS, Limits, Pricing, etc.

???
- It also includes other parts of agreement like SLA, rate limits, pricing tiers, etc

---
class: center, padded-top

# JSON
--

## JavaScript Object Notation
--

```
{
    "things": [
        "foo", 
        "bar"
    ], 
    "message": "Hello, World!"
}
```

???
- Just in case anyone isn't familiar...
- ~ Stands for JavaScript object notation
- It's a way to serialize object data
- ~ Will look pretty familiar if you've done much with javascript in recent years

---

class: center

# JSON Schema
--

```
{
    "title": "Example Schema",
    "type": "object",
	"properties": {
		"displayName": {
			"type": "string"
		},
		"age": {
			"description": "Age in years",
			"type": "integer",
			"minimum": 0
		}
	},
	"required": ["firstName", "lastName"]
}
```

???
- JSON schema is a standard specification for describing your data format
- It is written in JSON itself
- Used in data validation and automated testing 

---

class: center, padded-top

# YAML
--

## Serialization format
--

## (More) human-readable
--

## Subset of JSON
--

## Broad Support

???
- YAML stands for YAML aint markup language
- ~ It's a serializatin format
- ~ meant to be more readable than JSON
- ~ It's actually a subset of JSON and can be converted to JSON
- ~ It has broad language support so it's starting to be used in a lot of places

---

class: center

# YAML Example

```

```

---

class: center

# API Definitions
--

## WSDL / WADL
--

## Swagger -> OpenAPI Spec
--

## API Blueprint
--

## RAML


---

class: center, padded-top

# OpenAPI Spec
--

## Structure
--

## History
--

## Future

---

class: center, padded-top

# OpenAPI 3.0
--

## Coming Soon
--

## Tooling to Follow

???
Note that a new version is being released soon
Tooling will take some time to catch up


---

class: center, middle, section-title

# This Tutorial

---

class: center, padded-top

# Goals

## TODO: Verify goals
## An OpenAPI Spec
## Documentation
## Mock Server
## Tests
## (Very Basic) Implementation

---

class: center

## Repo Layout

```
├── lessons
│   ├── lesson01
│   │   └── example.yaml
│   ├── lesson02
│   │   ├── example.yaml
│   │   └── solution.yaml
│   ├── ...
├── notes
│   ├── prerequisites.md
│   └── references.md
├── presentation
│   ├── openapi-tutorial-slides.html
│   └── openapi-tutorial-slides.md
├── README.md
└── spec
    ├── betterapis.yaml
    └── definitions.yaml
```

---

class: lesson

# Lessons

## Instructions

- Work in `tutorial` directory
- Save `betterapis.yml`
- Run validator: `TODO: command here`
- Generate UI: `TODO: command here`

---

class: solution

# Lesson Solutions

## Done?

- Compare with contents of `solutions/lesson##`

## Stuck?

- Copy `solutions/lesson##/*` to `tutorial`


---

class: center, middle, section-title

# Tutorial

---

class: lesson

# Lesson 1.01: Setup

## Goals

- Setting up the environment.
- Looking at some Open API example specs and exercising the tools we will use.

???
- We will start every lesson with **goals**. Then some **theory** or **demo** and then and *excercise*.
  In the end we will review some **notes** about the **solution**.
- This is an introductory lesson that will help you familiarize with the **structure of the lessons**.
- We will also look at the tools we will use, and initial **taste** of the **Open API specification.**
---

class: lesson

# Lesson 1.01: Setup

## Tooling

- Swagger editor:
```
http-server swagger-editor
```
- Validator:

TODO

???
- In the environment you downloaded you will be able to run the **swagger editor** that I will now show.
- There are several examples that come with the editor. We will look at **default.yaml**.
- This is a good basic example of how a spec file will look.
- The spec is very readable and not just easily parsed by automatic tools. But we will look at every
  element in detail in later lessons.
- As you start working with the editor. You can see it does very good **validation**.
- TODO validator

---
class: lesson

# Lesson 1.01: Setup

## Exercise Instructions

- Load an example from the Swagger editor. Go through the example and see how it is displayed.

- Export the example, validate it and create a mock server for it.
  TODO: We need to figure out what we are doing for Mock server/validator
  If we do not have a mock server and an external validator, change this to be about loading an
  example as well. Maybe play around with showing off errors that the code editor can show.
---

class: center, middle, section-title

# Exercise

---

class: solution

# Solution 1.01


???
- In the exercise you had the opportunity to better familiarize yourself with Open API spec structure.
- You were able to validate and generate mock server as well as documentation for the user.
- This demonstrates a complete cycles of developing (just) a spec. We will now dive into the specifics
  of writing a spec.

---

class: lesson

# Lesson 1.02: Hello, World!

## Goals

- Building a first (basic) spec.

???
- The goal now is to take **in depth look** at Open API spec.
- We start with a very basic (and valid) spec in this lesson and each lesson we will add functionality.
- In the end you will have an example showing how to document all the main features of your API using
  OpenAPI spec.

---

class: center, middle, demo

# YAML Example


???
- Let's open the **example.yaml** file.
- This was build from examples you can find on the **Open API github** documentation.
- Swagger is build out of objects and here you can see the root object with several fields.
- The required fields are: **swagger** (must be 2.0 now), **info** (object), **paths**.
- We want to start from **more complete example**, that has more complete meta-data and hence added
  more fields than mandatory to the info, **host basepath**, **consumes**, **produces** etc.
  The fields are very self descriptive.
- consumes/produces are the mime types that are supported and they are lists.
---

class: center, middle, demo

# JSON Example


???
- When opening a json representation. The editor renders as YAML.
- You are **free** to write it using **Json or YAML**.
  The specification have example for both.

---
class: lesson

# Lesson 1.02: Hello, World!

## Exercise Instructions

- Build an API for a conference called `betterapis`
- Include metadata as shown in the example
- Paths are empty for now

???
- We will now start to build our API. It is for  conference called betterapis.
  This is just a first step and we will build it **incrementally**.
- You are free to come up with meta data as you like, only requirement that it will be valid.
- If get stuck, remember to **consult the example** in lesson directory or the Open API spec.

---

class: center, middle, section-title

# Exercise

---

class: solution

# Solution 1.02

## Notes

- This solution might be a bit different than yours in regards to the metadata.
- Valid Spec!

???
- You can see some **metadata** that is different.
- This is **valid spec** even though we do not support any functionality.
  It promotes building the spec in an incremental way.

---
class: lesson

# Lesson 1.03: Pets

## Goals

- Get familiar with defining paths.

???
- This lesson is intended to just show the **path object**.
  It is another (small)step in adding functionality to the API.
---

# Lesson 1.03: Pets

```
    /pets:
      get:
        summary: Get a list of pets
        description: Retrieve a list of pets
        responses:
          201:
            description: OK
```

???
- An example of the paths object that contains a list of **path Item object**
- Path item object is **relative to the base path** and contains a list of valid http operations
- **operation object** Is where the interesting logic happens and it holds some metadata about the
  operation (sumamry, description) and as we will see later a bit more.
- **reponse object** is how we can define the entire response body/headers etc. For now we just see
  one response code supported and description.
  Later we will expand to describe all the data returned in this response.

---
class: lesson

# Lesson 1.03: Pets

## Exercise Instructions

- Add two paths to the API: `/talks` `/speakers`.
- Both paths only support GET and only return status code 200.
- No documentation for data returned is required.

???
- These are the two main paths we will work with. We want to start with a small step to define them
  as you might sometime do with not having the documentation complete and then iterate on that.

---

class: center, middle, section-title

# Exercise

---

class: solution

# Solution 1.03

## Notes

- We defined the very basic fields and objects needed for a valid path.

???
- You saw how you can define a **path** and an **action** on it.
  Those are the main building blocks for the HTTP protocol and REST APIs.
  You can see how you can define other paths, actions and response codes.
- Now that we defined the path in the most basic way we can move forward to a more challenging
  definition of the paths.

---

class: lesson

# Lesson 1.04: Registration

## Goals

- Learn to define complex operations on the API.

---

class: lesson

# Lesson 1.04: Registration

## Paths, Actions

```
paths:
    /pets:
      post:
        summary: Add pet to DB
        description: Results in new pet information added to the DB
        parameters:
          - name: pet
            in: body
            description: Pet details
            schema:
              required: [name, status]
              properties:
                name:
                  type: string
                  description: The pet name
                  ...
```

???
- We have seen the path and operations objects in the last lesson. Now we see how to define the **request**.
- **parameters** is what is driving the operation as it is the data passed and it is an **array**
  of this object.
- The parameter has a **name** to identify it. the **in** keyword is very important as it describes where
  in the request the parameter is passed. In this case it is in the **body**. It can also be:
  **path, header, query, body, form**
- The data types that are supported are derived from json schema draft 4: integer, long, float, double, string,
  byte, binary, boolean, data, dateTime, password.
  One type that is not in the json schema is **file** and is supported as well.
- **required** field specifies for us which fields would be required to pass which are optional.
- **schema object** is based on json schema specification draft 4. Each property has a set of
  attributes such as we see here **type**, and **description** but can also but other like
  **title, pattern, minLength, maxLength** etc.

---

class: lesson

# Lesson 1.04: Registration

## Response

```
        responses:
          201:
            description: Created new pet in the database
            schema:
              required: [pet-id]
              properties:
                pet-id:
                  type: number
                  description: Unique Id for the pet in the system

```

???
- Responses is a container with the **status codes** acting as the **field pattern** and inside we have
  as you see the **response object**
- Response object will have a **description**. Optional: **schema, headers, example**

---

class: lesson

# Lesson 1.04: Registration

## Exercise Instructions

- Add actions to support speaker registration and talk submission
- You are free to define the speaker and talk objects as you like as long as you define a unique id
  in both and exercise defining more than one basic type for the object properties.

???
- You will add the POST actions in order to register the speaker and submit talk.

- Free to be creative as would like in order to define the objects.
---

class: center, middle, section-title

# Exercise

---

class: solution

# Solution 1.04

## Notes

- Additional properties: `readOnly`, `format`, `pattern`

???
- The main difference you might have seen in the solution is we are using additional properties in
  the json schema. There are more in the specification and this gives you ability for more fine
  grained documentation.

- **readOnly** specifies that it is only passed in response but won't be passed on the request.

---

class: lesson

# Lesson 1.05: The Minimalist API

## Goals

- Reusing definitions.
- Learn more in depth about action objects and request parameters.


???
- This is in my opinion where things get **interesting**.
- You will see how we can **reuse** elements of the API and not repeat.

---

class: lesson

# Lesson 1.05: The Minimalist API

## Path Parameter

```
  /pets/{pet-id}:
    parameters:
      pet-id:
        name: pet-id
        in: path
        description: Pet identifier
        type: number
        required: true
```

???
- Sometimes you want to have a parameter in the **path**.
  For example when you define the pet resource here.
- Notice how the **keyword** indicates the parameter is in the path and hence the name must match.
- Other than the name matching this is similar to parameter definition we saw earlier.

---
class: lesson

# Lesson 1.05: The Minimalist API

## Parameter Reuse

```
  /pets/{pet-id}:
    parameters:
      - $ref: '#/parameters/pet-id'

      ...

  parameters:
    pet-id:
      name: pet-id
      in: path
      description: Pet identifier
      type: number
      required: true
```

???
- This parameter might be **reused** in other parts of your API.
- Open API spec supports defining parameters in a global spec (the **root** of your document).
  This way you can reuse them in different paths.
- As you can see once we have this definition we can just reuse the parameter using json schema
  keyword **$ref** In order to define in other places.

---

class: lesson

# Lesson 1.05: The Minimalist API

## Definitions Reuse

```
  ...
      schema:
        $ref: '#/definitions/Pet'
  ...
  definitions:
    Pet:
      type: object
      required: [name, status]
      properties:
    ...
    Pets:
      type: array
      items:
        $ref: "#/definitions/Pet"
```

???

- In a similar way to what we saw where we can define and reuse parameters we can do with any
  **general object** as we see here the object reused in an **array** definition.
- This really opens new options as we can reuse it not only in action object or responses but in other
  definitions as well.
- The **schema element is indented** in order to highlight that the
  **definitions container** is in the root of the document.
- We will later (perhaps) see that definitions can be even in **separate files**.

---

class: lesson

# Lesson 1.05: The Minimalist API

## Exercise Instructions

1. Refactor your API to use `Talk` and `Speaker` objects.
   Define `Talks` and `Speakers` objects based on the previous and update the responses from
   `/speakers` and `/talks` paths.
2. Add a two new paths `/speaker/{speaker-id}` and `/talk/{talk-id}`.
   Define all the CRUD operations for them and use parameter definition outside of the action for
   path parameter.

???
- This exercise is split into two distinct sections in order to more easily implement the definitions.
  You should first implement part 1 make sure it is valid and then continue to 1.
- **Talks** and **speakers** objects should be arrays.
- If encounter issues implementing part 1 you can consult solution specifically for this part.
- In part 2 only define 2xx responses. We will cover other responses later.

---

class: center, middle, section-title

# Exercise

---
class: solution

# Solution 1.05

## Notes

- Time saving with definition. More readable.
- Example response in the solution

???
- We can right away see this would have been much more time consuming and less readable without the
  reusable definitions.
- In the **solution** you can also see an example in one of the **responses**.
  This will be helpful later.

---

class: lesson

# Lesson 1.06: Responses

## Goals

- Learn more about parameter definition via pagination
- Learn How to define reusable responses
- Default responses

???
- Even though we are calling this lesson and it will focus on responses we will start with a pagination
  example.
---

class: lesson

# Lesson 1.06: Responses

## Pagination

```
   parameters:
    - $ref: '#/parameters/page-size'
    - $ref: '#/parameters/page-number'
   ...
parameters:
  page-size:
    name: page-size
    in: query
    description: Number of items
    type: integer
    format: int32
    minimum: 1
    maximum: 100
    multipleOf: 10
    default: 10
```

???
- A very **common task** is to add pagination to actions. Almost every time we return an array.
- This illustrates a very easy addition of pagination.
- In addition to seeing some more detailed **parameter definition** (format, minimum, maximum etc..),
  What we see here is also that since **pagination** is very **common** you can just define it once
  and then **reuse** it in other endpoints.
- This way you not only save time on redefinition but **avoid mistakes** by changing your pagination
  only in one place.

---

class: lesson

# Lesson 1.06: Responses

## Response Definition

```
responses:
  ServerErrorResponse:
    description: Server error during request.
    schema:
      $ref: "#/definitions/Error"

definitions:
  Error:
    properties:
      code:
        type: integer
      message:
        type: string

```
???
- **responses** is another container at the root level where we can define for later use.
  The interesting thing here is that we can **define** the whole **response object** as we have seen before.
- Also note how we reuse the `Error` object.

---

class: lesson

# Lesson 1.06: Responses

## Default Response

```

/pets/{pet-id}/
  delete:
    responses:
      ...
      default:
        $ref: '#/responses/UnknownResponse'

responses:
  UnknownResponse:
    description: This response is not yet docuemtned by this API.
```

???
- The **responses** object on action **MUST** have at least one **successful** response and all known errors.
  This requirement by the spec actually.

- The spec is flexible though to recognize that there might be responses that are not documented and
  allows us to define a **default** response.
  Note that this is not using an http code as a field name but uses the keyword **default**

---

class: lesson

# Lesson 1.06: Responses

## Exercise Instructions

- Add pagination to the `/talks` and `/speakers` paths. Pagination should be included by at least
  two parameters: `page-size`, `page-number`.
- Add the following responses to all paths: 400, 500, default.

---

class: center, middle, section-title

# Exercise

---

class: solution

# Solution 1.06

## Notes

- Functionality complete API

???
- I wanted you to look for a minute now at your API. Functionality wise this is very much complete.
  If you have written documentation for Rest API before without a spec you must know how complicated
  and sometime not very readable they become.
  This on the other hand is both **readable** and **parsable**.
  If you look at the right hand in your swagger
  editor you can see very readable and easy to understand HTML as well.
---


class: lesson

# Lesson 1.07: Secure Your APIs

## Goals

- Learn the different security schemas supported.
- Global vs. local security via file upload definition example.

???
- 3 security schemes are supported by the Open API. We will look at all 3 of them
and implement one.
- *securityDefinition* defines globally all the security schemes for this API and can have any and all
  3 types of security objects.
---

class: lesson

# Lesson 1.07: Secure Your APIs

## Basic Auth

```
securityDefinitions:
    type: basic
```

???
- This indicates this API supports **basic authentication**.
  This is how easy it is to define it and since this is a standard nothing else is required.

---

class: lesson

# Lesson 1.07: Secure Your APIs.

## API Key

```
securityDefinitions:
  "type": "apiKey",
  "name": "api_key",
  "in": "header"
```

???
- This one is a bit more complex since we need to define the name and **method** we pass the **api_key**.

- Note this still uses the **same object** just more of the fields.

---

class: lesson

# Lesson 1.07: Secure Your APIs

## OAuth2

```
securityDefinitions:
  OauthSecurity:
    type: oauth2
    flow: accessCode
    authorizationUrl: 'https://oauth.swagger.io.com/authorization'
    tokenUrl: 'https://oauth.swagger.io/token'
    scopes:
      admin: Admin scope
      user: User scope

security:
  - OauthSecurity:
    - user
```

???

- Oauth is outside the scope of this tutorial this only to illustrate that **Oauth** security is fully
  **supported**.
- Oauth security and it defines **full* Oauth **flow** in a very simple and readable way.
  We even defined that we have two scopes we support which are the user and the admin.
- The second object is the security object and it sets in the global level the security for all
  paths but it an be overwritten.
---

class: lesson

# Lesson 1.07: Secure Your APIs

## File Upload

```
paths:
  /pets/{pet-id}/picture:
    parameters:
          - $ref: '#/parameters/pet-id'
    post:
      summary: Upload a pet picture
      description: Admin operation to upload a pet picture
      operationId: UploadPicture
      security:
        - OauthSecurity:
          - admin
      consumes:
        - multipart/form-data
      parameters:
        - name: picture
          in: formData
          type: file
```

???
 - File upload is a more unique case then other endpoints where we might want to allow only admins.
   See how it has it's own security scope.
 - Notice also that **consumes** is **overwrite** as application/json MIME type will not work for file upload.
---

class: lesson

# Lesson 1.07: Secure Your APIs

## Exercise Instructions

- Define a security scheme for your API. Use Oauth2.
- Add a new path to be able to upload speaker resume and secure it using admin role.

---

class: center, middle, section-title

# Exercise

---

class: solution

# Solution 1.07

## Notes

- Security representation in the editor
- Header in responses

???
- Notice that now we have a security box on the right hand side in the editor.
  We even have an authentication button since it completely recognized and can authenticate for us.
- If you looked at the solution for this lesson you can see an **example of header** sent back in the response
  as a file upload endpoint it would be a good practice to secure it with rate limit.

---

class: lesson

# Lesson 1.08: Document the Documentation

## Goals

- Learn additional points on spec documentation

???
 - We will learn about additional fields we haven't focused yet.
   The give us better **documentation** of the API and better **presentation** to the user.
---

class: lesson

# Lesson 1.08: Document the Documentation

## OperationId

```
  /pets:
      get:
        operationId: GetPets
```

???
- Every operation can have it's own unique id so can be parsed more easily for presentation.
- This is something that can be used by **automatic** tools that generate code.

---
## Description GFM

```
  /pets:
      get:
        description: ## Retrieve multiple pet objects.
                     For example:
                     - pet1
                     - pet2
```

???
- Summary is limited to 120 characters. In the description is really where we can document the
  operation and we build on the **tools** we use by just doing GFM and they render it for us.
- As you saw a lot of the objects support the description field.
---

class: lesson

# Lesson 1.08: Document the Documentation

## Tags

```
paths:
  /pets:
      get:
        tags:
          - pet

  ...

tags:
  name: pet
  description: Pet operations
```

???
 - tags are used in order to indicate to automatic tools of **logical groupings**
   for the APIs operations.

---

class: lesson

# Lesson 1.08: Document The Documentation

## Exercise Instructions

- Update for API with more information on the operations description, using GFM.
- Add tags and operationIds to all your operations

---

class: center, middle, section-title

# Exercise

---

class: solution

# Solution 1.08

## Notes

- Tags in the editor


???
- The editor like other tools that can do HTML representation recognizes the logical groupings (labels)
  and gives user ability to browse them more easily.

---

class: lesson

# Lesson 1.09: This is Long, Can we Split This?

## Goals

- Learn how to support not having all the API in one flat file

???
- We learned about all these techniques of having our APIs defined in a readable, and DRY way.
  But if we just have it in one long file it is not very maintainable, is it?

---

class: lesson

# Lesson 1.09: This is Long, Can we split this?

## Reference External Files

```
  /pets:
      get:
        summary: Get a list of pets
        description: Retrieve a list of pets
        operationId: GetPets
        parameters:
          - $ref: 'parameters.yaml#/page-size'
          - $ref: 'parameters.yaml#/page-number'
```

???
- This is a simple example of how we are referencing another yaml from our main one.
  You can easily extrapolate that we can do the same with other object definitions, responses etc...

---

class: lesson

# Lesson 1.09: This is Long, Can we Split This?

## parameters.yaml

```
Parameters:
  page-size:
    name: page-size
    in: query
    description: Number of items
    type: integer
    format: int32
    minimum: 1
    maximum: 100
    multipleOf: 10
    default: 10
```

???
- In this example we choose to have our parameters in a seperate file.
- The different techniques of splitting along definitions vs. paths are dependent on the specific API
  and what make sense better for implementation.
---

class: lesson

# Lesson 1.09: This is Long, Can we Split This?

## Serving External Files

???
- Show how we configure serving external files in the swagger editor.
- Make sure to point out need to force-reload if you change the files loaded externally.
---

class: lesson

# Lesson 1.09: This is Long, Can we Split This?

## Exercise Instructions

- Split your API spec.
  The proposed scheme is to have separate file for definitions, parameters and responses.
  You can consider other split strategies.

---

class: center, middle, section-title

# Exercise

---

class: solution

# Solution 1.09

---
class: center, middle, demo

# Break

---

class: center, middle, section-title

# Contract-first API development
## using the OpenAPI Specification<br/>(fka Swagger)
# Part 2

---

# Review Spec

???
Take a quick look at the overall spec at this point
Review content from any lessons we didn't complete in part 1

---

# Changes in OpenAPI 3.0

---

# Code Generation

---

# Server Code

???
Frameworks, etc

---

# Client Code

---

class: lesson

# Lesson 2.01: Automatic Code Generation

## Goals

 - Server/Client Code from Spec


???
- As you might have seen while working with it and as Dave probably mentioned the swagger-editor
  has a few more sophisticated features.

- **Other tabs** give us the ability to generate some basic code from our API spec.

- We can generate code for a lot of the frameworks such as python, golang Ruby and many more.

- This is the first time you will see the **benefit** of writing specification first as you have put a
  lot of effort into doing the proper design of your API and now a lot of the tedious work can be done
  for you by automatic tools.

- We will see how this is done with the editor but there are **other tools** out there.

---

class: center, middle, demo

# Generate Server (Flask)

???

- Switching to the swagger-editor we will see the many frameworks that the editor offers to generate
  code for us.

- This generates skeleton code for you. Flask for example is a microframework that imposes very
  little convention so the skeleton generated for you might not be how you like the structure for your Flask
  applications. What I would do in cases like that is use the generated code at first in order to
  build your specific implementation on top of it.

- I already have the server implementation in my PyCharm. Looking at the generated code, we see a
  skeleton application.
  The main code is in the **swagger_server** directory.

- There are two places that are interesting to look and those are the **default controller**.
  The controller does basic validations but in most places it just leaves a stub for the implementation.
  Still this is a lot as all the boilerplate code was already implemented, routes are defined and
  this is an actual server we can run.

- Also notice some **basic tests** were **generated** for us. Some of the tests will fail because the editor
  doesn't do detailed enough parsing of the schema to recognize which fields are required.

---

class: center, middle, demo

# Generate Client (Python)

???
- A lot of tools generate server code for you. Here with the editor we can also generate client code.

- The Flask client code is very detailed and actually produces all the code we need in order to give
  a **professional client code** to customers in order to interact with the API.
  This can be an actual **client to distribute** or just a sample of code that is run against the API.

- You can see in the README there is explanation of how to install and actually run this client code
  against the API.

---

class: lesson

# Lesson 2.01: Automatic Code Generation

## Exercise Instructions

- Generate server & client side code with your favorite option provided by the code generator.

- (bonus) Update server side code so that the `/talks` and `/speakers` paths return empty list on GET.
  Use the methods provided by the client code in order test the responses from the server.


???
 - Run the server using the instructions and test results you are seeing on the different paths.

 - Test out the client side code by pointing it to your sever and test the results you are getting.
---

class: center, middle, section-title

# Exercise

---

class: solution

# Solution 2.01


???
- We have already seen generating server and client side code during the lesson.

- In case you didn't get to the `bonus` part I will show how I updated the Flask implementation to
  return an empty list from the controller and also by following the instructions in the README
  that was generated will test the response from the server.

---

class: lesson

# Lesson 2.02: Run the API

## Goals

 - Python/Flask
 - Connexion

???
 - By using the code generator you saw how your code can be automatically generated from the spec.

 - This however can't be done while you are **developing new features**. In order to keep your
   contract up to date with the implementation we are using a layer on top of a Flask application
   called **connexion**

 - **Connexion** defines the routing for you, and validates the input and output based on the spec.
   This way you are only left with writing the implementation as you already wrote the spec so that
   all should be automatic.

 - We will look now at the implementation of the sample application you have in your VM that was
   created using this package on top of Flask.

---

class: center, middle, demo

#  Connexion Implementation

???
 - In your VM you have an implementation of the specification as it was in lesson **1.05**

 - Several thing I want to point out on the implementation. The **README** file will instruct you how to
   run the application.

 - **__main__** if you will need to change the port of the application this is where.
 - **__init__** there is some python/Flask boilerplate code that is less interesting for us, but the
   last line is where we tell connextion about **our spec**.
 - So this connects to our **controllers**. Connexion by reading the spec knows to make the direct
   routing. We do not need to define routes or validation!
 - The final part is the **models** this is where we define persistence to the DB and uses a package
   called SQLAlchemy that Python uses for persistence.
   You will need to update this part when adding some more data model in next lessons. So I would
   remember this part.

---

class: lesson

# Lesson 2.02: Run the API

## Exercise Instructions

- Run the the betterapis application using the connexion implementation TODO: instructions in VM

- Register two speakers and submit a talk for each one.
  Check the list of speakers and talks to make sure data was persisted.

???

 - This lesson is meant to get you familiarized with the connexion app.

 - Use the tool you like most to make HTTP requests. **Postman** is recommended.
   If you use PyCharm/Intelij it has a similar tool as well.

---

class: center, middle, section-title

# Exercise

---

class: lesson

# Lesson 2.03: Test with Dredd

## Goals

 - Learn how the spec connects tests and implementation

???
 - We will see an example of a framework that automatically tests based on the
   spec and validates implementation.

---

class: lesson

# Lesson 2.03: Test with Dredd

## Installation

```
npm install -g dredd
```

```
dredd --version
```

???
- This is a **language agnostic** tool that is used in order to do basic testing(validation) of your
  implementation against the documentation.
- It can be used both with Swagger and also **Apiary blueprint**. If you will be using it with blueprint
  the installation might be more complicated depends on your environment.
- Please also note that although it can be installed it is not supported on Windows machines.
  This feature is on the road map.
- As it is written in **CoffeeScript** it is installed with npm. (TODO: It is already installed on the VMs??)
---

class: lesson

# Lesson 2.03: Test with Dredd

## Usage

```
Dredd init
```

```
? Location of the API description document apiary.apib
? Command to start API backend server e.g. (bundle exec rails server)
? URL of tested API endpoint http://127.0.0.1:3000
? Programming language of hooks nodejs
? Do you want to use Apiary test inspector? Yes
? Please enter Apiary API key or leave empty for anonymous reporter
? Dredd is best served with Continuous Integration. Create CircleCI config for Dredd? No

Configuration saved to dredd.yml

Run test now, with:

  $ dredd
```

???

- The first line is the command you need to run in order to initialize the cli.
- it will create a dredd.yml file which can be customized later or kept as is.
- You will need to point to you application and if you like you can also send results to apiary.
  If you send the results over you can see more detailed information using their webui for it.
  If you want to persist the results you can create a premium account if not the results are available
  for a limited time.
---

class: lesson

# Lesson 2.03: Test with Dredd

## How Dredd works

- In request:  `x-example` or `default`

- In response: format matching

???

- In the request Dredd needs to know about which value(s) parameters that are passed.
  Everything else is already known from the API documentation. In order to do that it it will use
  either by using the extension **x-example** or the provided **default**
  **x-** is an extension field you can add to almost any object in the open api spec. It is used for
  3rd party extensions like Apiary are doing here.
  I recommend using the **x-example** as you might need to set the default to something else.

- The validation is done mainly by **examining the response** and seeing it matches the schema provided.
  That would mean that it is a good practice to document the response using a schema (as we have been
  doing).

---

class: lesson

# Lesson 2.03: Test with Dredd

## Parameter Example

```
  pet-id:
    name: pet-id
    in: path
    description: Pet identifier
    type: number
    required: true
    x-example: 42
```

???

- I wanted to show this example that you have in the lesson folder for a bit more clarity.
- You can see that we added another field **x-example** an that is how Dredd knows this is the value
  to use when running the test.

---

class: lesson

# Lesson 2.03: Test with Dredd

## Exercise Instructions

- Update all the GET actions so that they can be tested using Dredd.

- Initialize dredd and run `dredd --method GET` command in order to verify that tests are passing.
  (Use ids from data you initialized in the application in previous lesson)

???
- updating all the actions to be testable and the application itself will be too much time consuming
  for this exercise this is why we are limiting this to **only be on GET** actions.
  Make sure you specify you only want to test the GET method on all your paths.

- We encourage you to try running without the flag and see the results.

---

class: center, middle, section-title

# Exercise

---

class: solution

# Solution 2.03

## Notes

- Checking results in Apiary.

- Arrays are valid even if empty.

???

- If you chose to send results to Apiary you can see a better representation of the output you received.

- if you tested the API before making changes to the application you might have noticed that the tests
  for the endpoint that returns an array pass even if you do not return any data. Dredd will only validate
  the format is fine and the format is an array.
  This might lead to false sense of security.

- Your lesson directory also has a **dredd.yml** file which you can use going forward.
  This will also point to dredd specific spec in order to do the validation.

---

class: lesson

# Lesson 2.04: New Features

## Goals

 - Development cycle for new feature

???

- We will see a whole development cycle of adding a new feature to an existing spec with
  spec first approach.

---

class: lesson

# Lesson 2.04: New Features

## Flow

 - Update the spec

 - Run tests -> Fail

 - Update the code

 - Run tests -> Success

???
- Up to now we saw the flow where we wrote initial spec generated code out of it and validated the
  spec using some tests.

- As we know in the real world after development we still need to develop **new features**.

- This is the flow where we add a new feature to our spec. We will see that **automatically**
  Dredd will find new paths to test for and those will **fail**

- We then **update implementation** and sequentially our tests pass.

---

class: center, middle, demo

#  New Feature Demo

???

- We start by copying the **betterapi_example** to replace the spec.
  We now have a new feature where there is an ability to add a track. And get details of that
  track.
  **very similar to previous features**

- Next steps we run **dredd** and see it fails because there is no implementation for this feature.
  Notice though we **didn't need to update** anything with dredd. No new tests that we actually wrote.
  As the spec already had **x-example**

- Now we copy the implementation that is in a new controller names **reviews.py**
  And a new models object that we will copy as well.

- Once we updated the implementation, **post a new review** to generate data in the DB.
  **run the tests** and now they all should pass.

---

class: lesson

# Lesson 2.04: New Features

## Exercise Instructions

- Add a new feature to the application to support reviews.
  Besides a unique `id` the track object should reference the `talk_id` it refers to and `details`.


???
 - We want to add a feature with a **GET** and a **POST** where people submit a review of a talk.

 - Make sure you have the **tests pass** after implementing the code.
---

class: center, middle, section-title

# Exercise

---

class: solution

# Solution 2.04

---

class: lesson

# Lesson 2.05: Documentation

## Goals

 - Generating automatic documentation for clients

???
 - Even though the spec we wrote is readable we want to give **clients** something **beyond** that.
   Luckily as the spec is easily parsable there are many tools that can generate HTML for us.

---

class: lesson

# Lesson 2.05: Documentation

## Tooling

 - Connexion: HTML, Console

 - swagger-ui

 - Many others

???
- An added bonus you get from using the **connexion** layer is basic rendering to HTML and a client
  console.
  The advantage you are getting it in **one tool** instead of from multiple packages which complicates
  your stack.

- swagger-ui is another option and that is what is generated from the editor we have been using.

- There are a lot of other tools for that so you can probably find a tool that fits most for **your stack**.

---

class: center, middle, demo

#  Connexion Docs Demo

???

- localhost:8080/ui

- The UI is not the most intuitive at first as endpoints are hidden but once it is open you can
  see all the functionality is there and all the information is displayed

---

class: lesson

# Lesson 2.05: Documentation

## Exercise Instructions

- Register a new speaker and submit a talk using the connexion UI.

- Use the UI to also update and delete the talk and the speaker.

---

class: center, middle, section-title

# Exercise

---

# Advanced Connexion
- Inheritance
- Security & Authentication

---

class: center, middle, section-title

# More Resources

---

TODO: Links

---

TODO: Thank you slide