# Copilot Instructions for taller13

## Project Overview
This workspace contains a multi-app Python project focused on web services with Django (REST API) and Flask (API consumer). The main goal is to model and expose two entities—Edificio and Departamento—via Django REST, and consume them from Flask.

## Architecture
- **Django Project**: Located in `taller/api/taller_13/` and `ejemplos/ejemplo2/proyectoUno/`. Contains:
  - Models for Edificio and Departamento
  - REST API endpoints for CRUD operations (token authentication required)
  - Admin interface enabled
  - Uses SQLite as the database
- **Flask App**: Located in `consumo_api/ejemplo-flask/` and `taller/flask/`. Contains:
  - Routes to list and create Edificios and Departamentos by consuming Django REST endpoints
  - Uses Python `requests` for HTTP calls
  - Renders HTML templates for forms and lists

## Developer Workflows
- **Run Django server**: `python manage.py runserver` from the Django app directory
- **Run Flask app**: `python app.py` from the Flask app directory
- **Database migrations**: Use Django's `makemigrations` and `migrate` commands
- **API authentication**: Use token-based authentication for all CRUD endpoints
- **Testing**: Tests are located in `tests.py` within Django apps

## Project-Specific Patterns
- **API URLs**: All Django REST endpoints are under `/api/`
- **Authentication**: Flask consumers must send tokens in headers for protected endpoints
- **Entity Relationships**: Departamento has a foreign key to Edificio
- **Templates**: Flask templates are in the `templates/` subdirectory of each Flask app
- **Configuration**: Credentials for API access are stored in `config.py` in Flask apps

## Integration Points
- **Django REST Framework**: Used for API serialization and viewsets
- **Flask <-> Django**: All data flows from Django to Flask via HTTP requests
- **Static files**: Django and Flask each have their own static and template directories

## Examples
- Listing Edificios from Flask:
  ```python
  r = requests.get("http://127.0.0.1:8000/api/edificios/", headers={"Authorization": "Token <token>"})
  edificios = r.json()
  ```
- Creating Departamento from Flask:
  ```python
  r = requests.post("http://127.0.0.1:8000/api/departamentos/", data={...}, headers={"Authorization": "Token <token>"})
  ```

## Key Files & Directories
- `taller/api/taller_13/administrativo/models.py` — Django models
- `taller/api/taller_13/administrativo/views.py` — Django API views
- `consumo_api/ejemplo-flask/app.py` — Flask API consumer
- `consumo_api/ejemplo-flask/templates/` — Flask HTML templates
- `config.py` — Flask API credentials

---

If any conventions or workflows are unclear, please ask for clarification or provide feedback to improve these instructions.
