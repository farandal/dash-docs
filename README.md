# .*//Dash

```
     ██                        ███████                   ██████████                  ███
 ███ ██ ███                ███████████                 ████████████                  ███
   ██████                ████████                    ██████    ████                  ███
████████████           ██████                       █████      ████                  ███
   ██████             █████                        █████       ████                  ███
 ███ ██ ███          ████                          ████        ████                  ███
     ██             ████                          █████        ████                  ███
                   █████                          ████         ████                  ███
                   ████                          █████         ████ ████████████████ ███
             ██████████                          ████          ████ ████████████████ ███
             ██████████                         █████          ████                  ███
                   █████                       █████           ████                  ███
                    ████                       █████           ████                  ███
     ██              █████                    █████            ████                  ███
   ██████             █████                  █████             ████                  ███
  ████████             ██████               █████              ████                  ███
   ██████                ████████        ███████               ████                  ███
     ██                    ███████████████████                 ████                  ███
                               ████████████                    ████                  ███
                                                                                          
```

## **.*//DASH**
A Laravel / React system for rapidly building scalable, secure, and feature-rich administrative interfaces.
Dash full-stack solution at its core combines two specialized frameworks (ReactAdmin and Laravel) to provide a powerful and flexible solution for building administrative interfaces. The value of Dash system relies in the communication protocols that makes the backend and frontend to work together to simplify CRUD resources development and frontend resource forms automated generation.

## **Dash-Backend**

A robust Laravel-based API that delivers enterprise-grade features including multi-tenant architecture, granular role-based permissions, real-time WebSocket messaging, comprehensive audit trails, and domain-driven design principles.

- **Domain-driven design principles**
- **Tenancy architecture for data isolation**
- **Granular role/endpoint based permissions**
- **Out of the box real-time WebSocket messaging**
- **Comprehensive audit trails**

## **Dash-Admin**

A frontend built on top of ReactAdmin that provides rich UI components, standardized CRUD operations, advanced data management, and seamless API integration. It extends ReactAdmin's capabilities with custom components and workflows specifically designed to leverage Dash-Backend's features, implementing specialized protocols between Frontend/Backend communication. 

- **Rich UI components**
- **Standardized CRUD operations**
- **Seamless API integration**

Together, these components create a complete platform for rapidly building scalable, secure, and feature-rich administrative interfaces while maintaining clean separation of concerns and professional code organization.

---

## **DASH/Frontend**
### **CORE FEATURES**

- **Data-driven CRUD operations** through standardized REST endpoints
- **Advanced filtering, sorting and pagination**
- **Customizable data grids and forms**
- **Resource-based architecture** matching Laravel's API responses
- **Built-in authentication and authorization flows** integration (register, login, change-password, recover-password)
- **Rich UI components** for rapid admin interface development
- **Extensible theming system**

The integration between Laravel and ReactAdmin is seamless through standardized REST API endpoints and resource controllers, as evidenced in the `DashAdminBaseController` class that handles common CRUD operations, allowing an architecture for rapid development of feature-rich admin interfaces while maintaining clean separation between frontend and backend concerns.

The system leverages ReactAdmin's powerful data provider capabilities to handle complex data operations, while Laravel's backend provides the robust API foundation, authentication, and multi-tenant data isolation.

---

## **DASH/Backend**
### **CORE FEATURES**

Dash-Backend is a robust Laravel-based web dashboard API that delivers a comprehensive **Multi-Tenant architecture** with built-in data isolation.

The system features advanced user management with granular role-based permissions controlled at API method level. It includes real-time capabilities through WebSocket-enabled messaging, detailed audit trail tracking, and follows Domain-Driven Design principles with a clear separation between core business logic and application concerns. The architecture ensures scalability and maintainability while providing a solid foundation for enterprise-grade applications.

The modular structure and API-first approach make it an excellent choice for powering modern web applications that require sophisticated access control, real-time features, and multi-tenant capabilities right from the start.

The system features:

- **Advanced user management** with granular role-based permissions controlled at API method level
- **Real-time capabilities** through WebSocket-enabled messaging
- **Detailed audit trail tracking**
- **Domain-Driven Design principles** with a clear separation between core business logic and application concerns

The architecture ensures scalability and maintainability while providing a solid foundation for enterprise-grade applications.

The modular structure and API-first approach make it an excellent choice for powering modern web applications that require sophisticated access control, real-time features, and multi-tenant capabilities right from the start.

# DASH ESSENTIALS

## Creating a CRUD (Create, Read, Update, Delete) application for a simple To-Do list

The Dash Backend offers a straightforward scaffolding command designed to facilitate the creation of a simple CRUD application. This command illustrates all the essential components necessary for developing a Resource Module within the Dash framework, to quickly implement CRUD functionality, simply invoke the CreateDashModuleCommand and specify the desired Group and Module Name.


sail artisan make:dash-module {GroupName} {ResourceName} {--force}


### What is a Group?

The group is basically the path of your resource in your api, that is both represented at frontend and backend. 


/api/group/module_name


> **TD:** The feature considers nested resources, technically the framework enables it, nevertheless the scaffolding tool for tutorial purposes has only been implemented and tested for one depth level.

### What is a ResourceName?

The Resource Name is the name of your resource that is represented both, in backend and frontend urls, the Module implements the CRUD endpoints for backend and frontend. 
While the Group can have multiple Resources, a Resource wraps the CRUD operations for a specific model. 


http://dash.frontend.url/group/resource_name
http://dash.backend.url/api/group/resource_name


Read more about Dash backend url formats: Laravel - DashAdminBaseController.
Read more about Dash frontend url formats: React - ResourceTemplate. 

### What is necessary to create a CRUD application for a model?

Dash Framework, requires a Laravel's migration (the database schema for the model), a Laravel's Model, a Laravel's Controller, and a Dash Resource Frontend configuration file.
Meanwhile the Dash Laravel's Controller requires optionally a Request, a Policy, and a Filter.

### Backend File Locations for a Dash Resource

The controllers, models, routes and migrations for your application must be located within the domain folder.

- Controllers: domain/app/Http/Controllers/API/{GroupName}/{ModuleName}/*
- Models: domain/app/Models/{GroupName}/
- Routes: domain/routes/api/
- Migrations: domain/database/migrations/

### Frontend File Locations for a Dash Resource

Resource: `./apps/dash/src/resources`

The frontend application specifies its resources in the file located at `apps/dash/src/DASHResources.tsx`. Regardless of where a particular resource configuration resides within your DashAdmin project, it must be added to the DASHResources object. It's important to keep in mind two fundamental concepts in the React frontend: Dash Resource and Dash Schema.

#### Dash Resource configuration (IDashAutoAdminResourceConfig)

A Dash Resource outlines the configuration options for a dash-auto-admin resource within the Dash Admin framework. It encompasses properties that define the group, resource, and schema, along with additional attributes such as labels, icons, custom components, buttons, toolbars, layouts, and various other options. These settings allow for the customization of the resource's behavior, influencing the operation of auto-admin components, including list, edit, create, and show views, as well as the overall layout and functionality of the resource.

#### Dash Schema configuration (IDashAutoAdminAttribute[])

A Dash Resource outlines the configuration options for a dash-auto-admin resource within the Dash Admin framework. It encompasses properties that define the group, resource, and schema, along with additional attributes such as labels, icons, custom components, buttons, toolbars, layouts, and various other options. These settings allow for the customization of the resource's behavior, influencing the operation of auto-admin components, including list, edit, create, and show views, as well as the overall layout and functionality of the resource.

## Tutorial: CRUD TODO LIST

### Step 1: Create the Migration File
This file will define the schema for your "todos" table in the database.
Note: Database table names must be "Plural", while Laravel's Models "Singular"

```php
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    public function up()
    {
        Schema::create('todos', function (Blueprint $table) {
            $table->id();
            $table->string('name', 100);
            $table->boolean('active')->default(false);
            $table->timestamps();
        });
    }

    public function down()
    {
        Schema::dropIfExists('todos');
    }
};
```

### Step 2: Create the Model

```php
<?php

namespace Domain\App\Models\Example;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;
use EloquentFilter\Filterable;
use Rennokki\QueryCache\Traits\QueryCacheable;

class Todo extends Model
{
    use HasFactory, Filterable, QueryCacheable;

    protected $fillable = ['name', 'active'];

    protected $casts = [
        'active' => 'boolean'
    ];
}
```

### Step 3: Create the Controller

```php
<?php

namespace Domain\App\Http\Controllers\API\Example\Todo;

use Domain\App\Models\Example\Todo;
use Illuminate\Support\Facades\Request;
use App\Http\Controllers\API\Admin\DashAdminBaseController;

class TodoController extends DashAdminBaseController
{
    public $resource         = 'todo';
    public $requestValidator = TodoRequest::class;
    public $modelFilter      = TodoFilter::class;
    public $policy          = TodoPolicy::class;

    public function __construct()
    {
        $this->model = Todo::query();
    }
}
```

### Step 4: Define the Resource

```php
<?php
namespace Domain\App\Http\Controllers\API\Example\Todo;

use Illuminate\Http\Resources\Json\JsonResource;

class TodoResource extends JsonResource
{
    public function toArray($request)
    {
        return [
            'id'     => $this->id,
            'name'   => $this->name,
            'active' => $this->active
        ];
    }
}
```

### Step 5: Define the Policy

```php
<?php

namespace Domain\App\Http\Controllers\API\Example\Todo;

use App\Models\User;
use Domain\App\Models\Example\Todo;
use Illuminate\Auth\Access\HandlesAuthorization;

class TodoPolicy
{
    use HandlesAuthorization;
}
```

### Step 6: Define the Request Validation

```php
<?php

namespace Domain\App\Http\Controllers\API\Example\Todo;

use Illuminate\Foundation\Http\FormRequest;

class TodoRequest extends FormRequest
{
    public function rules()
    {
        return ['name' => 'required|string|max:100'];
    }

    public function validated($key = null, $default = null)
    {
        return parent::validated($key, $default);
    }
}
```

### Step 7: Create Routes

```php
<?php

use Illuminate\Support\Facades\Route;

Route::group(['middleware' => ['auth:sanctum'], 'as' => 'example.', 'prefix' => 'example'], function () {
    Route::prefix('todo')->name('todo.')->group(function () {
        $class = \Domain\App\Http\Controllers\API\Example\Todo\TodoController::class;
        Route::get('forSelect/{url?}', [$class, 'getForSelect'])->name('getForSelect');
    });
});
```

### Step 8: Create Frontend Resource Configuration

```js
import { TrashTemplate, ResourceTemplate } from "dash-admin";
import Dot from "@mui/icons-material/FiberManualRecord";
import React from "react";

const Icon = Dot as unknown as React.FC;

const TodoSchema = [
    {
        tab: 'Datos',
        attribute: 'name',
        label: 'Nombre',
        type: String,
    }
];

const TodoResource = {
    roles: ["*"],
    component: ResourceTemplate,
    customRoutes: (resourceConfig) => TrashTemplate(resourceConfig),
    model: "example/todo",
    label: "Todo",
    schema: TodoSchema,
    icon: <Icon />,
    group: "Example",
    
    menu: [
        {
            title: "List",
            redirect: "/example/todo",
        },
        {
            title: "Trash",
            redirect: "/example/trash/todo",
        },
    ],

    mainAction: {
        title: "Crear Todo",
        mode: "create",
        fn:"virtualhash",
        redirect: "inline/create",
    },

    view: true,
    create: true,
    edit: true,
  
    drawer: true,
    drawerOptions: {
        create: true,
        edit: true,
        view: true
    },
};

export default TodoResource;
```


### File Locations Summary

Dash Backend:

1. `{date}_todo_migration.php` -> `domain/database/migrations`
2. `TodoController.php` -> `domain/app/Http/Controllers/API/Example/Todo`
3. `TodoResource.php` -> `domain/app/Http/Controllers/API/Example/Todo`
4. `TodoPolicy.php` -> `domain/app/Http/Controllers/API/Example/Todo`
5. `TodoRequest.php` -> `domain/app/Http/Controllers/API/Example/Todo`
6. `todo_routes.php` -> `domain/routes/api/`
   
Dash Frontend:

7. `TodoResource.tsx` -> `./apps/dash/src/resources`

### Step 9: Add Resource to DASHResources

```js
// apps/dash/src/DASHResources.tsx
import { TodoResource } from './resources/TodoResource';

export const DASHResources = [
   TodoResource,
   // Add other resources here
];
```

By following these steps, you have all the necessary files and code for a complete TODO List CRUD application using Dash. You can now manage TODOs from the DashAdmin interface with backend support from Laravel, providing a seamless development experience while maintaining clear separations between frontend and backend. Adjust and extend the code as needed to fit additional customizations and features.