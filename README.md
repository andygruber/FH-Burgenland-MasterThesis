# LaTeX-Builder Documentation

## Overview
LaTeX-Builder is a template repository designed to streamline the process of building and releasing LaTeX documents.
You can either fork this repository or directly use the "Use this template" button on GitHub to get started.

## Usage

### **GitHub Action Workflow**

- **Building**: Automatically compiles all `*.tex` files located in the repository root.
- **Accessing Outputs**: Post-compilation, the resulting PDF files can be accessed from the build artifacts.
- **Triggers**: The workflow is activated after commits to the `main` branch, any `release/*` branches, or upon pull requests to these branches.
- **Releases**: On creating and publishing a release, the any PDF file will be appended to the release. If it is just one PDF, it will be added in the form of `<reponame>_<tagname>.pdf` (e.g., `LaTeX-builder_v0.0.1.pdf`). If there are more PDFs than one, the original name of the PDF will be appended after the `tagname` (e.g., `LaTeX-builder_v0.0.1_demo.pdf`).

#### Setup
To ensure the release workflow functions optimally, grant the necessary read/write permissions by navigating to: `Repo-Settings -> Actions -> General -> Workflow permissions`.

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

The `data/versinfo.tex` file contains version details. To incorporate it in another `.tex` file, use:
```latex
\input{data/versinfo.tex}
```
During standard builds (be it local or via GitHub Action), the output will display `DRAFT` followed by the date and time (e.g., `DRAFT 2023-03-06 13:32:10`). For release builds, the tag name will be shown (e.g., `v0.0.1`).

For a hands-on example, refer to the `demo.tex` file.

## Contributing

Your contributions play a pivotal role in enhancing the open-source community, making it a hub for learning, inspiration, and innovation. Every contribution, big or small, is deeply appreciated.

**Steps to Contribute**:
1. Fork the Project.
2. Create your Feature Branch: `git checkout -b feature/YourFeatureName`.
3. Commit your Changes: `git commit -m 'Describe your change'`.
4. Push to the Branch: `git push origin feature/YourFeatureName`.
5. Open a Pull Request.

For suggestions or enhancements, either submit a pull request or open an issue with the "enhancement" tag. If you find value in this project, kindly star it. Your support means a lot to me!