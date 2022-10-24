# Setting Core MVC space of work

## 1. Instalar los paquetes necesarios (mismas versiones)
```
Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore
```
```
Microsoft.EntityFrameworkCore.Design
```
```
Microsoft.EntityFrameworkCore.SqlServer
```
```
Microsoft.EntityFrameworkCore.Tools
```
```
Microsoft.VisualStudio.Web.CodeGeneration.Design
```

## 2. Crear los dbsets de todas las clases
```
public DbSet<Class> classes { get; set; }
```

## 3. Agregar la conexión en Program.cs y appsettings.json

### **Program.cs**
Agregar using's:
```
using Microsoft.EntityFrameworkCore;
using ProyectName.Data;
```
Luego:
```
builder.Services.AddDbContext<ClassDbContext>(options => options.UseSqlServer(builder.Configuration.GetConnectionString("DefaultConnection")));
```
### **appsettings.json**
Antes:
* Crear una base desde el Explorador de objetos de SQL Server (myDB)

Agregar conexión string:
```
"ConnectionStrings": {
    "DefaultConnection": "Server=>serverNamer;DataBase=myDB;Trusted_Connection=True;MultipleActiveResultSets=true;"
  }
```

## 4. Hacer las migraciones para todas las tablas
Para cumplir esto:
* Ve a "Herramientas" > "Administrador de paquetes NuGet" > "Consola del Administrador de paquetes"

Comando para inicializar la migración:
```
add-migration InitialMigration
```
Comando para actualizar la migración:
```
update database
```

## 5. Crear controladores con la Opcion **Scafold**
? ? ? ? 

## 6. Ir al Layout y permitir el acceso en el cshtml
```
<li class="nav-item">
    <a class="nav-link text-dark" asp-area="" asp-controller="folderName" asp-action="Index">folderView</a>
</li>
```