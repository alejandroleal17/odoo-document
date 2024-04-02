# Engineering Portal

Internal Engineering Portal with documentation and references for Navigator Platform 

## URLs

- Main URL: https://www.documentation-odoo-troc.com/
- Basic Auth: qbEZjrBmC8jfXggJzDWq

Basic authentication is included above without protection since it is only for documentation purposes while we are in playground mode. In the future, we could enhance security measures (or release it as is without auth).

## Local development

For a smooth development experience, ensure mkdocs is installed on your system. You can install it using pip as shown below:

```sh
$ pip install -r requirements.txt
```

To verify your changes locally before committing and pushing, run the following command:

```sh
❯ mkdocs serve
INFO    -  Building documentation...
INFO    -  Cleaning site directory
INFO    -  The following pages exist in the docs directory, but are not included
           in the "nav" configuration:
             - engineering/development-guidelines.md
             - engineering/stats_pg.md
INFO    -  Documentation built in 0.23 seconds
INFO    -  [08:00:04] Watching paths for changes: 'docs', 'mkdocs.yml'
INFO    -  [08:00:04] Serving on http://127.0.0.1:8000/
INFO    -  [08:00:36] Browser connected: http://127.0.0.1:8000/
INFO    -  [08:00:44] Browser connected: http://127.0.0.1:8000/

```

This command will build the documentation and serve it locally, allowing you to review your updates in real-time.
