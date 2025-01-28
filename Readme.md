# SOAINT Test Práctico

Este proyecto implementa flujos de integración en IBM App Connect Enterprise (ACE) para realizar consultas a la API de Pokémons. El proyecto incluye dos servicios REST principales que permiten recuperar datos de Pokémons y filtrar por tipo.

---

## **Servicios Implementados**

### 1. **pokemons_retrieve**
- **Descripción**: Recupera la lista de todos los Pokémons disponibles.
- **Método**: `GET`
- **URL**:  

http://localhost:7080/api/v1/pokemons_retrieve

bash
Copiar
Editar

#### Ejemplo de Respuesta
```json
{
"pokemons": [
  { "name": "pikachu", "type": "electric" },
  { "name": "charizard", "type": "fire" }
]
}
2. pokemons_retrievebytype
Descripción: Recupera la lista de Pokémons según su tipo.
Método: GET
URL:
bash
Copiar
Editar
http://localhost:7080/api/v1/pokemons_retrievebytype?category=type=flying
Parámetros de Consulta
Parámetro	Descripción	Ejemplo
category	Categoría por tipo de Pokémon	type=flying
Ejemplo de Respuesta
json
Copiar
Editar
{
  "category": "flying",
  "pokemon_count": 15,
  "pokemons": [
    { "name": "pidgey", "type": "flying" },
    { "name": "zubat", "type": "flying" }
  ]
}
Requisitos del Entorno
IBM App Connect Enterprise (ACE) v12 o superior.
Postman (para probar los servicios).
Puerto 7080 habilitado en el entorno local.
Uso
Clonar este repositorio:

bash
Copiar
Editar
git clone https://github.com/usuario/soaint-test-practico.git
Importar el archivo de colección de Postman incluido en el proyecto:

Archivo: SOAINT_test_practico.postman_collection.json.
Abrir Postman, ir a "Importar" y seleccionar el archivo.
Iniciar el flujo de integración en ACE.

Probar los servicios utilizando Postman con los ejemplos proporcionados.

Despliegue
Generar el archivo BAR para el despliegue:
bash
Copiar
Editar
mqsicreatebar -b deploy.bar -a Application -k SharedLibrary
Desplegar el archivo BAR en el servidor de integración:
bash
Copiar
Editar
mqsideploy -i localhost -p 7080 -e default -a deploy.bar
Contribuciones
Si deseas colaborar, sigue estos pasos:

Haz un fork del proyecto.
Crea una rama con tu funcionalidad o corrección:
bash
Copiar
Editar
git checkout -b feature/nueva-funcionalidad
Envía un pull request para revisión.
Licencia
Este proyecto está bajo la licencia MIT. Para más detalles, consulta el archivo LICENSE.

Autor: [Tu Nombre]

css
Copiar
Editar

Este `README.md` tiene toda la información básica del proyecto y es fácil de entender para cualquier desarrollador. Puedes personalizarlo según lo necesites.






