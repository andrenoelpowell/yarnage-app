# 🧶 Yarnage App - Ravelry Alternative

Welcome to **Yarnage**, your modern alternative to Ravelry — built with containers, Kubernetes, and AWS. This project supports crafters with features like project tracking, pattern libraries, and stash management, all wrapped in a scalable, cloud-native design.

---

## 📁 Project Structure
```
app/
├── frontend/      # React app (UI)
├── backend/       # API (Node.js or Django)
├── design/        # Adobe XD files, branding assets
├── helm/          # Helm charts for Kubernetes deployment
README.md          # This file
LICENSE            # License info
```

---

## 🛠️ Project Setup & Workflow

### ✅ 1. Plan and Design (Adobe XD)
- Design key MVP screens:
  - Dashboard
  - Project Tracker
  - Yarn Stash Manager
  - Pattern Browser
- Export your `.xd` file to `app/design/`
- Link designs to GitHub Issues or Project Board cards

### ✅ 2. Initialize GitHub
- Create GitHub repo (done ✅)
- Add project folders (done ✅)
- Push local repo and sync folders (done ✅)

### ✅ 3. Build the Frontend
- Navigate to `app/frontend/`
- Scaffold a React app:
  ```bash
  npx create-react-app .
  # or use Vite for a faster setup
  ```
- Add Tailwind CSS
- Test locally and commit

### ✅ 4. Dockerize the Frontend
- Create a `Dockerfile` inside `app/frontend/`
- Build and run locally:
  ```bash
  docker build -t yarnage-frontend .
  docker run -p 3000:3000 yarnage-frontend
  ```

### ✅ 5. Set Up AWS Infrastructure
- Use `eksctl` to spin up EKS:
  ```bash
  eksctl create cluster --name yarnage-cluster --region us-east-1 --nodes 2
  ```
- Set up `kubectl`, `helm`, and IAM roles

### ✅ 6. Push Docker Images to ECR
- Authenticate Docker to ECR:
  ```bash
  aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin <your-aws-account>.dkr.ecr.us-east-1.amazonaws.com
  ```
- Push the built image:
  ```bash
  docker tag yarnage-frontend:latest <ecr-url>/yarnage-frontend:latest
  docker push <ecr-url>/yarnage-frontend:latest
  ```

### ✅ 7. Deploy with Helm
- Create Helm chart in `app/helm/`
- Set up templates for deployments, services, ingress
- Install with:
  ```bash
  helm install yarnage ./helm
  ```

### ✅ 8. Set Up CI/CD (GitHub Actions)
- Automate builds, tests, and deployments to AWS
- Example: `.github/workflows/deploy.yml`

---

## 📌 Tips
- Store secrets using AWS Secrets Manager or Kubernetes Secrets
- Use GitHub Projects to organize tasks
- Design before you code!

---

## 📄 License
MIT License. See `LICENSE` file for details.
