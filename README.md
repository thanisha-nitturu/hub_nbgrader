# nbgrader – Manual Setup for JupyterHub Integration (Pre-Ananke Phase)

This repository contains the initial manual work done to integrate **JupyterHub** with **nbgrader** before switching to the standardized Ananke-based setup.  
It includes custom logic for user role authentication, assignment workflows, and user signup using a customized frontend.

---

## Purpose of This Setup

- Implement **role-based user access** (instructor vs student) manually using `role_authenticator.py`.
- Configure **nbgrader** with Docker-based JupyterHub.
- Create a custom user signup experience via modified HTML.
- Allow instructors to create/release assignments and students to submit via Jupyter UI.

---

## Folder Structure Overview

nbgrader/
├── Dockerfile.hub
├── Dockerfile.nbgrader
├── docker-compose.yml
├── entrypoint.sh
├── role_authenticator.py
├── start.sh
├── nbgrader_config.py
├── nbgrader_config/
│   ├── instructor_config.py
│   ├── student_config.py
│   └── nbgrader_config.py
├── custom_signup.html


---

## File Descriptions

### Docker & Hub Setup

- **`Dockerfile.hub`**  
  Docker image for running the JupyterHub server with all dependencies (Python, nbgrader, authenticator, etc.).

- **`Dockerfile.nbgrader`**  
  Image tailored for nbgrader environment — installs nbgrader, configures permissions, sets default working directories.

- **`docker-compose.yml`**  
  Orchestrates all services — JupyterHub, nbgrader notebooks, volumes for assignment data.

- **`entrypoint.sh`**  
  The main entry script for containers, responsible for initializing environment variables and launching services.

---

### Authentication & Role Management

- **`role_authenticator.py`**  
  Custom authenticator that extends JupyterHub’s base authenticator to assign roles (student/instructor) during login based on predefined logic or user lists.

---

### nbgrader Configuration

- **`nbgrader_config/nbgrader_config.py`**  
  The main configuration file for nbgrader: sets up instructor/student permissions, assignment paths, exchange directories, and course names.

---

### Custom User Interface

- **`custom_signup.html`**  
  Customized signup page for user creation with role selection fields, enhancing the standard JupyterHub UI.

---

## Status

This setup served as the **foundation** for understanding how nbgrader, JupyterHub, and role-based workflows could be integrated manually.  
It helped test early features like:
- Role-aware UI redirection
- Custom signup flow

Later, the project moved to using **Ananke**, a more complete solution that combines Moodle, nbgrader, and JupyterHub.

---

## 🙋‍♀️ Author

**Thanisha Nitturu**  
Intern @ Hitloop  
Contributed to role-based Docker environment setup, nbgrader customization, custom UI integration, and debugging JupyterHub workflows.

