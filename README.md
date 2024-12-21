# AlpineVNCDocker

## Lightweight Alpine-based Docker Container with VNC and noVNC

This project provides a lightweight Docker container based on Alpine Linux, featuring a VNC server accessible on port `5900` and an HTML5-based noVNC client available on port `6900`. It uses the Fluxbox desktop environment for simplicity and efficiency, making it ideal for deploying a Linux sandbox quickly.

The base image size is approximately **182MB**.

---

## Features
- **Fluxbox**: Lightweight window manager.
- **Xvfb**: Virtual framebuffer for graphical applications.
- **x11vnc**: VNC server.
- **noVNC**: Web-based VNC client.

---

## How to Use

### 1. Build the Docker Image
Run the following command to build the image from the Dockerfile:

```bash
docker build . -t alpinevncdocker:latest
```

### 2. Run the Docker Container

#### Basic Usage
To expose the VNC service on port `5900` and noVNC on port `6900`:

```bash
docker run -d -p 5900:5900 -p 6900:6900 alpinevncdocker:latest
```

#### With VNC Password
To secure the VNC connection with a password:

```bash
docker run -d -p 5900:5900 -p 6900:6900 -e VNC_PASSWORD="your_password" alpinevncdocker:latest
```

### 3. Access the VNC Desktop

- **Using a VNC Client**:
  Connect to `localhost:5900` using any VNC viewer.

- **Using noVNC**:
  Open a web browser and navigate to `http://localhost:6900` to access the desktop through the noVNC client.

---

## Extending the Image

You can add additional packages by modifying the `Dockerfile`:

```Dockerfile
RUN apk add --no-cache <package_name>
```

After editing the Dockerfile, rebuild the Docker image:

```bash
docker build . -t alpinevncdocker:latest
```

---

## License
This project is released under the MIT License. See the LICENSE file for details.

---

## Contributions
Contributions are welcome! Feel free to submit issues or pull requests to improve this project.
