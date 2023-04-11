# Collaborate for Impact

Collaborate for Impact is a web-based platform that connects entrepreneurs, investors, and industry experts to collaborate on innovative solutions for some of the world's most pressing problems, such as climate change, poverty, and inequality. The platform aims to facilitate the exchange of ideas, resources, and expertise to drive meaningful impact.

## Platform Architecture

Collaborate for Impact offers a range of features and functionalities, including:

-   Forums for discussion: Users can participate in forums to exchange ideas and insights on specific topics related to social and environmental impact.
-   Project management tools: Users can collaborate on projects, track progress, and assign tasks to team members.
-   Resource libraries: Users can access a range of resources, including whitepapers, case studies, and other materials related to social and environmental impact.
-   Expertise exchange: Users can connect with industry experts and mentors to gain insights and guidance on specific topics related to their projects.

## Public Routes

-   Home page
-   About page
-   Contact page
-   Sign-up page for new users
-   Sign-in page for existing users

## Authenticated Routes

-   User profile page
-   Projects page: Users can view and search for existing projects and create new ones.
-   Project detail page: Users can view details of a specific project and collaborate with other users.
-   Resource library: Users can access and share resources related to the platform's themes.
-   Expert directory: Users can search for and connect with industry experts.
-   Investor directory: Users can search for and connect with potential investors.
-   Forum: Users can ask questions, share ideas, and engage in discussions with other users.

## Administrator Routes

-   Dashboard: Administrators can view analytics, manage users and projects, and monitor platform activity.
-   User management: Administrators can manage user profiles, roles, and permissions.
-   Project management: Administrators can view and manage project information, collaborations, and resources.
-   Report generation: Administrators can generate reports on platform activity, user behavior, and project impact.

## API Structure

### Routing Structure

| API Route |Http Method  | Description |
|--|--|--|
| /api/users | GET | Get all users |
|  | POST | create a new user |
|  | PUT | update a  users |
|  | DELETE | delete users |
| /api/entrepreneurs| GET | Get all entrepreneurs|
|  | POST | create a new entrepreneurs |
|  | PUT | update entrepreneurs |
|  | DELETE | delete entrepreneurs |
| /api/experts| GET | Get all experts|
|  | POST | create a new experts|
|  | PUT | update experts|
|  | DELETE | delete experts|
| /api/projects| GET | Get all projects|
|  | POST | create a new project|
|  | PUT | update project|
|  | DELETE | delete project|

### Database Schema

#### Users

| Field | Type |
|--|--|
|id | string|
|username|string|
|email|string|
|password|string(hashed)|
|role|enum (entrepreneur, investor, expert)|

#### Entrepreneurs

| Field | Type |
|--|--|
|id | string|
|user_id| string (foreign key to Users table)|
|company_name|string|
|industry|string|
|location| string|
|description| string|
|websit| string|

#### Investors
| Field | Type |
|--|--|
|id | string|
|user_id| string (foreign key to Users table)|
|company_name|string|
|industry|string|
|location| string|
|investment_focus| string|
|websit| string|

#### Industry Experts
| Field | Type |
|--|--|
|id | string|
|user_id| string (foreign key to Users table)|
|company_name|string|
|industry|string|
|location| string|
|expertise| string|
|websit| string|

#### Projects

| Field | Type |
|--|--|
|id| string|
|name| string|
|entrepreneur_id| string (foreign key to Entrepreneurs table)|
|description| string|
|industry| string|
|location| string|
|status| string (in progress, completed, cancelled)|
|investment_required| number|
|investment_received| number|
|expertise_required| string |
|start_date| Date|
|end_date| Date|


## API Documentation

The Collaborate for Impact API provides endpoints for managing users, entrepreneurs, investors, industry experts, and projects. Here is the detailed documentation for each endpoint.

### Users

#### `GET /api/users`

Returns a list of all users in the system.

**Response**

-   `200 OK` on success

```json
[
  {
    "id": "123",
    "username": "johndoe",
    "email": "johndoe@example.com",
    "role": "entrepreneur"
  },
  {
    "id": "456",
    "username": "janedoe",
    "email": "janedoe@example.com",
    "role": "investor"
  }
]
```

#### `POST /api/users`

Creates a new user in the system.

**Request Body**

```json
{
  "username": "newuser",
  "email": "newuser@example.com",
  "password": "password",
  "role": "expert"
}
``` 

**Response**

-   `201 Created` on success

```json
{
  "id": "789",
  "username": "newuser",
  "email": "newuser@example.com",
  "role": "expert"
}
``` 

#### `PUT /api/users/:id`

Updates an existing user in the system.

**Request Parameters**

-   `id`: The ID of the user to update.

**Request Body**

```json
{
  "email": "updatedemail@example.com",
  "role": "investor"
}
``` 

**Response**

-   `200 OK` on success

```json
{
  "id": "123",
  "username": "johndoe",
  "email": "updatedemail@example.com",
  "role": "investor"
}
``` 

#### `DELETE /api/users/:id`

Deletes an existing user from the system.

**Request Parameters**

-   `id`: The ID of the user to delete.

**Response**

-   `204 No Content` on success

### Entrepreneurs

#### `GET /api/entrepreneurs`

Returns a list of all entrepreneurs in the system.

**Response**

-   `200 OK` on success

```json
[
  {
    "id": "123",
    "user_id": "789",
    "company_name": "Acme Inc.",
    "industry": "Technology",
    "location": "San Francisco, CA",
    "description": "We build innovative software solutions.",
    "website": "https://acmeinc.com"
  }
]
``` 

#### `POST /api/entrepreneurs`

Creates a new entrepreneur in the system.

**Request Body**

```json
{
  "user_id": "456",
  "company_name": "NewCo",
  "industry": "Social Impact",
  "location": "New York, NY",
  "description": "We create solutions for social and environmental challenges.",
  "website": "https://newco.com"
}
``` 

**Response**

-   `201 Created` on success

```json
{
  "id": "789",
  "user_id": "456",
  "company_name": "NewCo",
  "industry": "Social Impact",
  "location": "New York, NY",
  "description": "We create solutions for social and environmental challenges.",
  "website": "https://newco.com"
}
``` 

#### `PUT /api/entrepreneurs/:id`

Updates an existing entrepreneur in the system.

**Request Parameters**

-   `id`: The ID of the entrepreneur to update.

**Request Body**
```json
{
  "description": "We create innovative solutions for social and environmental challenges."
}
```
#### `DELETE /api/users/:id`

Deletes an existing user from the system.

**Request Parameters**

-   `id`: The ID of the entrepreneurs to delete.

**Response**

-   `204 No Content` on success

### Investors

#### `GET /api/investors`

Returns a list of all investors in the system.

**Response**
- `200 OK` on success
```json
[
  {
  "id": "123",
  "user_id": "789",
  "company_name": "ABC Investments",
  "industry": "Technology",
  "location": "New York, NY",
  "investment_focus": "Early-stage startups",
  "website": "https://abcinvestments.com"
  }
]
```

#### `POST /api/investors`
Creates a new investor in the system.

Request Body
```json

{
"user_id": "456",
"company_name": "XYZ Ventures",
"industry": "Social Impact",
"location": "San Francisco, CA",
"investment_focus": "Sustainable and socially responsible startups",
"website": "https://xyzventures.com"
}
```
**Response**

- `201 Created` on success
```json
  {
  "id": "789",
  "user_id": "456",
  "company_name": "XYZ Ventures",
  "industry": "Social Impact",
  "location": "San Francisco, CA",
  "investment_focus": "Sustainable and socially responsible startups",
  "website": "https://xyzventures.com"
  }
  ```

- `PUT /api/investors/:id`

Updates an existing investor in the system.

Request Parameters

id: The ID of the investor to update.
**Request Body**

```json
{
"investment_focus": "Early-stage and socially responsible startups"
}
```
**Response**

- `200 OK on success`

```json
{
"id": "123",
"user_id": "789",
"company_name": "ABC Investments",
"industry": "Technology",
"location": "New York, NY",
"investment_focus": "Early-stage and socially responsible startups",
"website": "https://abcinvestments.com"
}
```

- `DELETE /api/investors/:id`
Deletes an existing investor from the system.

**Request Parameters**

id: The ID of the investor to delete.
Response

`204 No Content` on success

#### Industry Experts
- `GET /api/experts`
Returns a list of all industry experts in the system.

**Response**

`200 OK` on success

```json
[
{
"id": "123",
"user_id": "789",
"industry": "Technology",
"location": "San Francisco, CA",
"expertise": "Software development",
"website": "https://example.com"
}
]
```
- `POST /api/experts`
Creates a new industry expert in the system.

**Request Body**


```json
{
"user_id": "456",
"industry": "Social Impact",
"location": "New York, NY",
"expertise": "Sustainability",
"website": "https://example.com"
}
```
**Response**

`201 Created` on success

```json
{
"id": "789",
"user_id": "456",
"industry": "Social Impact",
"location": "New York, NY",
"expertise": "Sustainability",
"website": "https://example.com"
}
```
- `PUT /api/experts/:id`
Updates an existing industry expert in the system.

**Request Parameters**

id: The ID of the industry expert to update.
Request Body

```json
{
"expertise": "Sustainability and social impact investing"
}
```
**Response**

`200 OK` on success

#### Projects

- `GET /api/projects`
Returns a list of all projects in the system.

**Response**

`200 OK` on success

```json
[
  {
  "id": "123",
  "name": "Project X",
  "entrepreneur_id": "456",
  "description": "A project to build an innovative software solution.",
  "industry": "Technology",
  "location": "San Francisco, CA",
  "status": "in progress",
  "investment_required": 100000,
  "investment_received": 50000,
  "expertise_required": "Software Engineering",
  "start_date": "2022-01-01",
  "end_date": "2022-12-31"
  }
]
```
- `POST /api/projects`
Creates a new project in the system.

**Request Body**


```json
{
  "name": "Project Y",
  "entrepreneur_id": "789",
  "description": "A project to create a sustainable energy solution.",
  "industry": "Energy",
  "location": "New York, NY",
  "status": "in progress",
  "investment_required": 500000,
  "investment_received": 0,
  "expertise_required": "Energy Engineering",
  "start_date": "2023-01-01",
  "end_date": "2023-12-31"
}
```
**Response**

`201 Created` on success

```json
{
  "id": "456",
  "name": "Project Y",
  "entrepreneur_id": "789",
  "description": "A project to create a sustainable energy solution.",
  "industry": "Energy",
  "location": "New York, NY",
  "status": "in progress",
  "investment_required": 500000,
  "investment_received": 0,
  "expertise_required": "Energy Engineering",
  "start_date": "2023-01-01",
  "end_date": "2023-12-31"
}
```
- `PUT /api/projects/:id`
Updates an existing project in the system.

**Request Parameters**

id: The ID of the project to update.
Request Body


```json
{
  "status": "completed",
  "investment_received": 500000
}
```
**Response**

`200 OK` on success

```json
{
  "id": "123",
  "name": "Project X",
  "entrepreneur_id": "456",
  "description": "A project to build an innovative software solution.",
  "industry": "Technology",
  "location": "San Francisco, CA",
  "status": "completed",
  "investment_required": 100000,
  "investment_received": 500000,
  "expertise_required": "Software Engineering",
  "start_date": "2022-01-01",
  "end_date": "2022-12-31"
}
```
- `DELETE /api/projects/:id`
Deletes an existing project from the system.

**Request Parameters**

```json
id: The ID of the project to delete.
```
**Response**

`204 No Content` on success.

#### Project Comments

- `GET /api/projects/:id/comments`

Returns a list of all comments for a project.

**Request Parameters**

id: The ID of the project to retrieve comments for.

**Response**

`200 OK` on success

```json
[
{
"id": "123",
"project_id": "456",
"comment": "This is a comment.",
"created_at": "2021-01-01T00:00:00.000Z",
"updated_at": "2021-01-01T00:00:00.000Z"
}
]
```

- `POST /api/projects/:id/comments`

Creates a new comment for a project.

**Request Parameters**

id: The ID of the project to create a comment for.

**Request Body**

```json
{
"comment": "This is a comment."
}
```
**Response**

`201 Created` on success

```json
{
"id": "789",
"project_id": "456",
"comment": "This is a comment.",
"created_at": "2021-01-01T00:00:00.000Z",
"updated_at": "2021-01-01T00:00:00.000Z"
}
```
- `PUT /api/projects/:id/comments/:id`

Updates an existing comment for a project.

**Request Parameters**

id: The ID of the project to update a comment for.

id: The ID of the comment to update.

**Request Body**

```json
{
"comment": "This is an updated comment."
}
```
**Response**

`200 OK` on success

```json
{
"id": "789",
"project_id": "456",
"comment": "This is an updated comment.",
"created_at": "2021-01-01T00:00:00.000Z",
"updated_at": "2021-01-01T00:00:00.000Z"
}
```
- `DELETE /api/projects/:id/comments/:id`

Deletes an existing comment for a project.

**Request Parameters**

id: The ID of the project to delete a comment for.

id: The ID of the comment to delete.

**Response**

`204 No Content` on success.

#### Project Investments

- `GET /api/projects/:id/investments`

Returns a list of all investments for a project.

**Request Parameters**

id: The ID of the project to retrieve investments for.

**Response**

`200 OK` on success

```json
[
{
"id": "123",
"project_id": "456",
"investor_id": "789",
"amount": 10000,
"created_at": "2021-01-01T00:00:00.000Z",
"updated_at": "2021-01-01T00:00:00.000Z"
}
]
```
- `POST /api/projects/:id/investments`

Creates a new investment for a project.

**Request Parameters**

id: The ID of the project to create an investment for.

**Request Body**

```json
{
"investor_id": "789",
"amount": 10000
}
```

**Response**

`201 Created` on success

```json
{
"id": "123",
"project_id": "456",
"investor_id": "789",
"amount": 10000,
"created_at": "2021-01-01T00:00:00.000Z",
"updated_at": "2021-01-01T00:00:00.000Z"
}
```
- `PUT /api/projects/:id/investments/:id`

Updates an existing investment for a project.

**Request Parameters**

id: The ID of the project to update an investment for.

id: The ID of the investment to update.

**Request Body**

```json
{
"amount": 20000
}
```
**Response**

`200 OK` on success

```json
{
"id": "123",

"project_id": "456",
"investor_id": "789",
"amount": 20000,
"created_at": "2021-01-01T00:00:00.000Z",
"updated_at": "2021-01-01T00:00:00.000Z"
}
```
- `DELETE /api/projects/:id/investments/:id`

Deletes an existing investment for a project.

**Request Parameters**

id: The ID of the project to delete an investment for.

id: The ID of the investment to delete.

**Response**

`204 No Content` on success.


