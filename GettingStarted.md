# Getting Started

Let's break this down step-by-step:

### 1. Set Up a GitHub Repo

1. Create a new GitHub repository named `<yourusername>.github.io`. This naming convention allows GitHub to recognize it as a GitHub Pages repo associated with your profile.
2. Clone the repository to your local machine:
   ```bash
   git clone https://github.com/<yourusername>/<yourusername>.github.io.git
   ```

### 2. Set Up Jekyll

1. Navigate to the cloned repo's directory:
   ```bash
   cd <yourusername>.github.io
   ```
2. Install Jekyll:
   ```bash
   gem install bundler jekyll
   ```
3. Create a new Jekyll site:
   ```bash
   jekyll new .
   ```

### 3. Set Up Dev Containers

1. In the root directory of your cloned repo, create a `.devcontainer` folder.
2. Inside this folder, create two files: `Dockerfile` and `devcontainer.json`.
3. In the `Dockerfile`, set up the environment for Jekyll. Here's an example to get you started:
   ```Dockerfile
   FROM ruby:2.7

   # Install required packages for Jekyll
   RUN gem install bundler jekyll

   # Expose the port for Jekyll's built-in server
   EXPOSE 4000
   ```
4. In the `devcontainer.json` file, configure your dev container to use the above Dockerfile:
   ```json
   {
     "name": "Jekyll Dev Container",
     "dockerFile": "Dockerfile",
     "forwardPorts": [4000],
     "postCreateCommand": "bundle install"
   }
   ```

### 4. Customize Themes and Illustrations

1. To customize your theme, you can pick a Jekyll theme from [Jekyll Themes](https://jekyllthemes.io/) and follow the theme's documentation for setup.
2. For illustrations, you can place the PNG images in the `assets` or `images` directory and reference them in your pages or posts using Markdown or HTML.

### 5. Setting up GitHub Pages

1. Push your local changes to the GitHub repo.
2. Go to your GitHub repository's settings, scroll down to the "GitHub Pages" section, and select the `main` branch (or the appropriate branch) as the source.

### 6. Testing Locally

With the Dev Container setup, you can open your repository in VS Code, and it will prompt you to reopen in a container. Once inside, you can run the Jekyll server:

```bash
jekyll serve --host 0.0.0.0
```

This will start the Jekyll server, and you can preview your website at `http://localhost:4000`.

### 7. Deploying

Every time you push your changes to GitHub, GitHub Pages will automatically rebuild and deploy your website, making it accessible at `https://<yourusername>.github.io`.
