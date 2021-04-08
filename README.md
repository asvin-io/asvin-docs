<img src="images/logo.png" width="200"/>

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)

- [Asvin](#asvin)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [License](#license)

# asvin Platform

asvin facilitates Platform as a Service to distribute over the air firmware updates for IoT devices.

# Documentation

If you want the world to read asvin documentation in your own language, you are welcome to translate it. The documentation is already available in German and English. Therefore, you can contribute in the existing translations or add a new language if it doesn't exist.

asvin uses [Read the Docs](https://readthedocs.org/) for software documentation. It facilitates automatic building, versioning, and hosting of the documentation. The [Sphinx](https://www.sphinx-doc.org/en/master/) tool is used to build the documentation using the [theme](https://github.com/readthedocs/sphinx_rtd_theme).
The documentation is generated for each commit in the master branch. Therefore, it is advised to build locally for update, preview and design. The [section](#update-documentation) describe the procedure. You could find the latest version of [documentation](https://asvin.readthedocs.io/en/latest/index.html) online.

## Update Documentation

### Setup

1. Download and install latest version of Python from [here](https://www.python.org/downloads/)
2. Clone the repo
   ```
   git clone https://github.com/Asvin-io/asivn-docs.git
   ```
3. Install dependencies

   ```
   cd documentation/docs
   pip3 install -r requirements.txt
   ```

### Build

Make your changes and run following commands to generate html documentation.

```
cd asvin-docs/docs/locale/en
make html
```

### Preview

Open `build/html/index.html` file in a browser.

### Upload

When all the changes are according to your needs then push changes or make pull request.

Please find further information about the architecture, getting started and tutorials in our online documentation.

- [latest](https://asvin.readthedocs.io/en/latest/index.html)

Find out more about us

- [website](https://asvin.io)

# Contributing

asvin is an Open Source project. We welcome your [contribution](https://asvin.readthedocs.io/en/latest/contributing/contributing.html) in the project.

# License

The information here is made available under the Apache License, Version 2.0 (Apache-2.0), located in the [LICENSE](LICENSE) file.
