## Backend Routes

> Labels: back-end, route  <br>
> Failer Response: { msg } & status()

### General Routes

Title| Description | Protected | Required middleware | Request | Success response | Errors 
 |--- |--- |--- |--- |--- |--- |--- |
POST/signup | create account & give token | No | No |{ email, username, password } | { data, msg } & status(201) | email exist? 409  wrong password? 401 invalid email? 400 
POST/signin | verify & login user | No | No |{ email, password } | { data: {email, username}, msg } & status(200) | email not exist? 409  wrong password? 401
Get/logout | delete token & logout user | No | No | {  } | { msg } & status() | 

<hr> 

### Projects Routes
Title| Description | Protected | Required middleware | Request | Success response | Errors 
 |--- |--- |--- |--- |--- |--- |--- |
GET/projects | Get all user projects | yes | checkAuth | No body | { data: {name, id}, msg } & status(200, 204) | server error? 500
POST/project | add project | yes | checkAuth |{ name } | { data: {id, name}, msg } & status(201) | server error? 500 
PUT/project/:id | edit project | yes | checkAuth | { name }, params.id | { data: {id, name}, msg } & status(200) | server error? 500 
Delete/project/:id | delete project | yes | checkAuth | params.id | { msg } & status(204) | server error? 500 
GET/project/:id | get single project | yes | checkAuth | params.id | { data: {id, name,  description, admin, members, sections}, msg } & status(204) | server error? 500 

<hr> 

### Sections Routes
Title| Description | Protected | Required middleware | Request | Success response | Errors 
 |--- |--- |--- |--- |--- |--- |--- |
GET/sections | Get all user sections | yes | checkAuth | No body | { data: {name, id}, msg } & status(200, 204) | server error? 500
POST/section | add section | yes | checkAuth |{ name } | { data: {id, name}, msg } & status(201) | server error? 500 
PUT/section/:id | edi section | yes | checkAuth | { name }, params.id | { data: {id, name}, msg } & status(200) | server error? 500 
Delete/section/:id | delete section | yes | checkAuth | params.id | { msg } & status(204) | server error? 500 

### Tasks Routes
Title| Description | Protected | Required middleware | Request | Success response | Errors 
 |--- |--- |--- |--- |--- |--- |--- |
GET/tasks | Get all tasks | yes | checkAuth | No body | { data: [tasks], msg } & status(200, 204) | server error? 500
GET/tasks/:id | Get all tasks in specfic section | yes | checkAuth | sectionId: params.id | { data: { id, name,  description, priority, endDate, status}, msg } & status(200, 204) | server error? 500
#POST/task | add section | yes | checkAuth | { name } | { data: {id, name}, msg } & status(201) | server error? 500 
#PUT/task/:id | edi section | yes | checkAuth | { name }, params.id | { data: {id, name}, msg } & status(200) | server error? 500 
#Delete/task/:id | delete section | yes | checkAuth | params.id | { msg } & status(204) | server error? 500 
