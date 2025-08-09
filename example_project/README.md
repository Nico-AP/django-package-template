# Example Django Project for the Package App

This example project demonstrates how to integrate the Package App into a Django site.


## Quick Start

1. Install dependencies:
```bash
cd example_project
pip install -r requirements.txt
```

2. Set up environment variables (optional)
```bash
cp .env.example .env
# Edit .env if you want to customize settings
```

3. Run the example project
```bash
python manage.py migrate
python manage.py createsuperuser  # Optional
python manage.py runserver
```
Next, open the application in your browser.

4. Use the example project to test the Package App.
```bash
python manage.py test package_app
```



## Configuration

The example works out of the box with SQLite and default settings.
