# Hello Docker

This is a simple .NET 8.0 application that demonstrates how to use Docker to containerize a .NET application.

## Project Structure

```
hello-docker/
├── .dockerignore
├── Dockerfile
├── appsettings.Development.json
├── appsettings.json
├── hello-docker.csproj
├── Program.cs
├── Properties/
│   └── launchSettings.json
├── bin/
│   └── Release/
│       └── net8.0/
├── obj/
│   └── Release/
│       └── net8.0/
```

## Files

- **.dockerignore**: Specifies files and directories to be ignored by Docker.
- **Dockerfile**: Contains the instructions to build the Docker image.
- **appsettings.Development.json**: Configuration settings for the development environment.
- **appsettings.json**: Configuration settings for the application.
- **hello-docker.csproj**: The project file for the .NET application.
- **Program.cs**: The main entry point of the application.
- **Properties/launchSettings.json**: Configuration settings for launching the application.

## Dockerfile

The `Dockerfile` is used to build the Docker image for the application. It consists of two stages:

1. **Build Stage**:
    - Uses the `mcr.microsoft.com/dotnet/sdk:8.0-alpine` image.
    - Sets the working directory to `/src`.
    - Copies the entire project to the container.
    - Publishes the project to the `/published` directory.

2. **Runtime Stage**:
    - Uses the `mcr.microsoft.com/dotnet/aspnet:8.0-alpine` image.
    - Sets the working directory to `/app`.
    - Copies the published files from the build stage to the runtime stage.
    - Sets the entry point to run the application using `dotnet hello-docker.dll`.

## Building and Running the Docker Container

To build and run the Docker container, follow these steps:

1. **Build the Docker Image**:
    ```sh
    docker build -t hello-docker:1.0 .
    ```

2. **Run the Docker Container**:
    ```sh
    docker run --rm -p 8080:8080 hello-docker:1.0
    ```

3. **Access the Application**:
    Open your browser and navigate to `http://localhost:8080` to see the application running.

## Application

The application is a simple web server that responds with "Hello DOCKER!" when accessed at the root URL (`/`).

## Configuration

The application uses `appsettings.json` and `appsettings.Development.json` for configuration. The `appsettings.Development.json` file is used when the application is running in the Development environment.

## License

This project is licensed under the MIT License.