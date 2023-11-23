# FH Burgenland Thesis Book LaTeX template

## Overview

This template is based on the original work from Dominik Thiede (https://www.linkedin.com/in/dominik-thiede/).

The GitHub Workflow for automation with Actions is based on the [LaTeX-builder](https://github.com/andygruber/LaTeX-builder) repository.

## Usage

For information on the usage of the LaTeX template see [here](USAGE.md).

### **GitHub Action Workflow**

- **Building**: Automatically compiles all `*.tex` files located in the repository root.
- **Accessing Outputs**: Post-compilation, the resulting PDF files can be accessed from the build artifacts.
- **Triggers**: The workflow is activated after commits to the `main` branch, any `release/*` branches, or upon pull requests to these branches.
- **Releases**: On creating and publishing a release, the PDF file will be appended to the release. Just one resulting PDF is allowed, it will be added in the form of `<base_name>_<tagname>.pdf` (e.g., `your_lastname, Insert final title here_v0.0.1.pdf`).

#### Setup
To ensure the release workflow functions optimally, grant the necessary read/write permissions by navigating to: `Repo-Settings -> Actions -> General -> Workflow permissions`.

#### Set the base name of the PDF

In the file `.github\workflows\compileLaTeX.yml` find the line:
```bash
            base_name='your_lastname, Insert final title here'
```
Adapt it to your needs and the resulting PDF will get the defined name.

### **Local Compilation with VS Code**

1. **Installation**:
   - Download and install [VS Code](https://code.visualstudio.com/download).
   - Ensure a LaTeX distribution is in place. For Windows:
     - Download `TinyTex` or `TinyTex-2` from [here](https://github.com/rstudio/tinytex-releases/).
     - Extract the downloaded package.
     - Add `<extracted-path>\bin\windows` to your system or user PATH variable.
   
2. **Configuration**:
   - On launching VS Code, you might be prompted to install recommended extensions, such as `LaTeX Workshop`.
   - If the PATH variable is set correctly, VS Code will automatically detect the LaTeX distribution and compile LaTeX projects.
   - **For Linux Users**: Consider using a Docker image as your LaTeX distribution. In the `LaTeX Workshop` extension settings within VS Code:
     - Enable `latex-workshop.docker.enabled`.
     - Set `latex-workshop.docker.image.latex` to `ghcr.io/xu-cheng/texlive-full`.

### **Versioning**

The `section/versinfo.tex` file contains version details. To incorporate it in another `.tex` file, use:
```latex
% package required to get current date/time
\usepackage{datetime2}
% import the required file
\input{section/versinfo.tex}
% command which actually writes the version information
\docversion
```
During local builds, the text will be set to `DRAFT` followed by the date and time (e.g., `DRAFT; 2023-03-06 13:32:10`).

Builds via GitHub Action will set the text to the git SHA1 or the Pull-Request number instead of `DRAFT`.

For release builds, the tag name will be set as text (e.g., `v0.0.1`).

## Contributing

Your contributions play a pivotal role in enhancing the open-source community, making it a hub for learning, inspiration, and innovation. Every contribution, big or small, is deeply appreciated.

**Steps to Contribute**:
1. Fork the Project.
2. Create your Feature Branch: `git checkout -b feature/YourFeatureName`.
3. Commit your Changes: `git commit -m 'Describe your change'`.
4. Push to the Branch: `git push origin feature/YourFeatureName`.
5. Open a Pull Request.

For suggestions or enhancements, either submit a pull request or open an issue with the "enhancement" tag. If you find value in this project, kindly star it. Your support means a lot to me!