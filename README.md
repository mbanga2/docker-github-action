## Automate Docker Deployment with GitHub Actions Task #1

In this project, we used Docker and GitHub Actions to automate the process of packaging and deploying a simple web application. The main goal of the lab was to create a workflow where any changes pushed to our GitHub repository would automatically trigger a Docker image build and upload it to Docker Hub, instead of manually building and pushing the image ourselves.

## Docker

Docker allowed us to package our HTML files and web server into a container image. We used the official nginx:alpine base image and copied our site files into the container so they would be served automatically when the container is running. To run the container locally, we used: 'docker run -d -p 8080:80 our-dockerhub-username/docker-github-action:tag'. After running the container, we were able to access the website by visiting: 'http://localhost:8080'. Using Docker ensures that the application runs the same way on any device regardless of operating system or machine setup. This avoids the common “it works on my machine” issue.

## GitHub Actions

To automate deployment, we created a workflow file inside:
.github/workflows/docker.yml

This workflow is triggered every time we push to the main branch. The workflow performs the following steps: First, it checks out the code from the repository. Second, it builds the Docker image using the Dockerfile. Third, it logs in to Docker Hub using Docker credentials stored in GitHub Secrets. Finally, it pushes the image to Docker Hub automatically. Storing our Docker Hub username and token in GitHub Secrets allows the workflow to push the image securely without exposing any passwords in the code.

## Usefulness of Docker + GitHub Actions

Automating this process eliminates the need to rebuild and push the Docker image manually every time we update our HTML. Any change we push to GitHub instantly generates and uploads a new updated Docker image to Docker Hub. This setup reflects real-world CI/CD (Continuous Integration and Continuous Deployment) practices commonly used in professional software development to make deployment faster, more consistent, and more reliable.
