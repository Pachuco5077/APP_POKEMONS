```markdown
# SOAINT Test Práctico

Este proyecto implementa flujos de integración en IBM App Connect Enterprise (ACE) para realizar consultas a la API de Pokémons. El proyecto incluye dos servicios REST principales que permiten recuperar datos de Pokémons y contar la cantidad por un tipo de categoria específico.

---

## **Servicios Implementados**

### 1. **pokemons_retrieve**
- **Descripción**: Recupera la lista de todos los Pokémons disponibles.
- **Método**: `GET`
- **URL**:  
  ```
  http://localhost:7080/api/v1/pokemons_retrieve
  ```

#### Ejemplo de Respuesta
```json
{
    "pokemons": [
        {
            "name": "bulbasaur",
            "url": "https://pokeapi.co/api/v2/pokemon/1/"
        },
        {
            "name": "ivysaur",
            "url": "https://pokeapi.co/api/v2/pokemon/2/"
        }
    ]
}

```

---

### 2. **pokemons_retrievebytype**
- **Descripción**: Recupera la lista de Pokémons según su tipo.
- **Método**: `GET`
- **URL**:  
  ```
  http://localhost:7080/api/v1/pokemons_retrievebytype?category=type=flying
  ```

#### Parámetros de Consulta
| Parámetro   | Descripción                     | Ejemplo      |
|-------------|---------------------------------|--------------|
| `category`  | Categoría por tipo de Pokémon  | `type=flying` |

#### Ejemplo de Respuesta
```json
{
    "category": "flying",
    "pokemon_count": 149
}
```

---

## **Requisitos del Entorno**
- IBM App Connect Enterprise (ACE) v13.
- Postman (para probar los servicios).
- Puerto `7080` habilitado en el entorno local.

---

## **Uso**
1. Clonar este repositorio:
   ```bash
   git clone https://github.com/Pachuco5077/APP_POKEMONS
   ```
2. Importar el archivo de colección de Postman incluido en el proyecto:  
   - **Archivo:** `SOAINT_test_practico.postman_collection.json`.
   - Abrir Postman, ir a "Importar" y seleccionar el archivo.

3. Iniciar el flujo de integración en ACE.
4. Probar los servicios utilizando Postman con los ejemplos proporcionados.

---

## **Despliegue**
1. Generar el archivo BAR para el despliegue:
   ```bash
   mqsicreatebar -b BAR_APP_POKEAPI.bar -a Application -k PokemonLibrary
   ```
2. Desplegar el archivo BAR en el servidor de integración:
   ```bash
   mqsideploy -i localhost -p 7080 -e default -a BAR_APP_POKEAPI.bar
   ```

---

**Autor:** Vladimir  
```  
