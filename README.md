# Django Package Template

This repository provides a template for a Django application that is intended to be packaged and distributed through PyPI.


## Features

- 🔌 Ready-to-use Django app structure
- 📦 PyPI packaging configuration
- ➿ Automated GitHub Actions workflow to create PyPI release
- 🧪 Example Django project for testing
- 🔢 Semantic versioning with BumpVer
- 📝 Changelog template


## Quickstart 🚀

How to use this repository:

1. **Fork this repository** to your GitHub account.
2. **Follow the Initial Setup** instructions below.
3. **Customize included files** using the Alteration Checklist below.
4. **Test the setup** following the instructions below.


## Repository Structure 📐

The structure below highlights the most important files and omits boilerplate information.

```md
your-django-app/
├── package_app/              # main Django app
│   ├── migrations/
│   ├── static/package_app/
│   ├── templates/package_app/
│   ├── admin.py  
│   ├── apps.py               
│   ├── models.py
│   ├── tests.py
│   ├── urls.py    
│   └── views.py
├── example_project/          # Test project
│   ├── example_project/
|   |   ├── settings.py
|   |   └── urls.py
│   ├── .env.example           
│   └── manage.py
├── docs/   
├── tests/                    
├── .github/workflows/        # GitHub Actions
│   └── publish-to-pypi.yml
├── LICENSE                   # Package configuration
├── MANIFEST.in               # Package configuration
├── pyproject.toml            # Package configuration
├── CHANGELOG.md
├── requirements.txt
└── README.md
```

## Initial Setup After Forking 🧩

1. Clone your forked repository:
```bash
git clone https://github.com/<yourusername>/<your-app-name>.git
cd <your-app-name>
```

2. Create a virtual environment
```bash
python -m venv .venv
source .venv/bin/activate
```

3. Install dependencies
```bash
pip install -r requirements.txt
```


## Alteration Checklist 🔄

This is the list of critical files to update and steps to take after the initial setup:

**Django Application** (`./package_app/`)

- [ ] Change the folder name to your app name.
- [ ] Change the name of the AppConfig Class in `./package_app/apps.py`.
- [ ] Change the subfolder names of `./package_app/templates/` and `./package_app/static/`.

**Test Project** (`./example_project/`)

- [ ] Update the `PACKAGE_APP_DIR` variable in `settings.py`.
- [ ] Update the app name included in `INSTALLED_APPS` in `settings.py`.
- [ ] Update the inclusion of your app in `urls.py`. 
- [ ] Create an `.env` file based on `.env.example` (optional).

**GitHub Action Workflow** (`./github/workflows/`)

- [ ] To connect GitHub Actions with PyPI, the workflow relies on the [Trusted Publisher](https://docs.pypi.org/trusted-publishers/) publication process implemented by PyPI. You should follow their documentation to set up a "Trusted Publisher" for your PyPI project under which you will release your package.

**Package Configuration**

- [ ] `pyproject.toml`: Update the following fields:
    ```toml
    name = "example-name"
    version = "1.0.0"
    description = "This is just an example."
    authors = [{ name = "Some Name", email = "some@mail.com" }]
    license = "MIT"
    keywords = ["some", "fancy", "keywords"]

    [project.urls]
    Homepage = "https://some-url.com"
    ```
- [ ] Check PyPI name availability: Search [PyPI](https://pypi.org/) to ensure your package name is available.
- [ ] `MANIFEST.in`: Ensure all necessary files are included.

**Adjust Changelog** (`./CHANGELOG.md`)

- [ ] Adjust the changelog.

**Update License** (`./LICENSE`)

- [ ] Update the license to include your preferred license.


## Testing Your Setup ✅

1. **Test the example project:**
```bash
cd example_project
python manage.py migrate
python manage.py runserver
```

2. **Run tests:**
```bash
# cd example_project  # if your not in the folder already.
python manage.py test
```

3. **Test package installation:**
```bash
pip install -e .
python -c "import your_app_name; print('Success!')"
```


## Suggested Release Process 🆕

This repository is intended to support the following release process.

### Prerequisites

- [ ] All tests passing.
- [ ] Documentation updated.
- [ ] CHANGELOG.md updated.
- [ ] PyPI Trusted Publisher configured.

### Steps

To create a new release, follow these steps:

1. **Prepare Release**
```bash
git checkout main
git pull origin main
git merge dev  # merge your introduced changes
```

2. **Version Bump**
```bash
# Preview changes
bumpver update --patch --dry  # or --minor --major

# Apply changes
bumpver update --patch
```

This will (a) update the version numbers in the places specified in the `pyproject.toml` file and (b)create a new commit with the updated files and (c) tag the new commit.

The current setup follows the [semantic versioning strategy](https://semver.org/):
- `--patch`: Bug fixes (1.0.0 → 1.0.1)
- `--minor`: New features, backward compatible (1.0.0 → 1.1.0)  
- `--major`: Breaking changes (1.0.0 → 2.0.0)

3. **Push and Deploy**
```bash
git push origin main --tags
```
This will trigger the GitHub Action to compile the package and publish to PyPI.


4. **Sync Development Branch**
```bash
git checkout dev
git merge main
git push origin dev
```


## Next Steps 👞 

After adjusting this template:

1. **Develop your Django app** in the `package_app/` directory.
2. **Write tests** for your app.
3. **Update documentation** in the `docs/` directory.
4. **Test locally** using the example project.
5. **Create your first release** following the release process above.


## Resources 📚

- [Django App Development Best Practices](https://docs.djangoproject.com/en/stable/intro/reusable-apps/)
- [Python Packaging User Guide](https://packaging.python.org/)
- [Semantic Versioning](https://semver.org/)
- [PyPI Trusted Publishers](https://docs.pypi.org/trusted-publishers/)


## License

This template is released under the MIT License (MIT). See `LICENSE` file for details.
