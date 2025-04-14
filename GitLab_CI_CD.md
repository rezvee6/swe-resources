# 🚀 GitLab CI/CD – From Beginner to Advanced

---

## 🧰 What is GitLab CI/CD?

GitLab CI/CD is GitLab’s built-in automation for:

- Continuous Integration (CI): run tests, lint code, build artifacts.
- Continuous Deployment (CD): automate deployment of your apps.

All defined in a `.gitlab-ci.yml` file placed in the root of your repository.

---

## 🧪 Testing Workflows

<details>
<summary><strong>✅ Basic Test Pipeline</strong></summary>

```yaml
stages:
  - test

test:
  stage: test
  script:
    - npm install
    - npm run test
```

</details>

<details>
<summary><strong>🧼 Retry on Failure</strong></summary>

```yaml
test:
  script:
    - flaky-test
  retry: 2
```

</details>

<details>
<summary><strong>📊 Test Reports (JUnit Integration)</strong></summary>

```yaml
artifacts:
  reports:
    junit: report.xml
```

</details>

---

## 🚚 Deployment Workflows

<details>
<summary><strong>🚀 Basic Deploy Stage</strong></summary>

```yaml
stages:
  - deploy

deploy:
  stage: deploy
  script:
    - ./deploy.sh
```

</details>

<details>
<summary><strong>🖐️ Manual Deploy</strong></summary>

```yaml
deploy:
  stage: deploy
  script: echo "Deploying"
  when: manual
```

</details>

<details>
<summary><strong>🌐 Define Environments</strong></summary>

```yaml
deploy_prod:
  stage: deploy
  environment:
    name: production
    url: https://your-app.com
  script: ./deploy.sh
```

</details>

---

## ⚙️ Pipeline Optimization

<details>
<summary><strong>📦 Cache Dependencies</strong></summary>

```yaml
cache:
  paths:
    - node_modules/
```

</details>

<details>
<summary><strong>💾 Artifacts</strong></summary>

```yaml
artifacts:
  paths:
    - dist/
    - reports/
```

</details>

<details>
<summary><strong>🔁 Define Rules</strong></summary>

```yaml
deploy:
  script: echo "Deploy"
  rules:
    - if: '$CI_COMMIT_BRANCH == "main"'
```

</details>

<details>
<summary><strong>🔀 Matrix Jobs (Multiple Envs)</strong></summary>

```yaml
test:
  parallel:
    matrix:
      - NODE_ENV: ["dev", "prod"]
  script:
    - echo $NODE_ENV
```

</details>

---

## 🧠 Advanced CI/CD Features

<details>
<summary><strong>📂 Include Other CI Templates</strong></summary>

```yaml
include:
  - local: "ci-templates/test.yml"
  - project: "group/shared-templates"
    file: "/templates/docker.yml"
```

</details>

<details>
<summary><strong>🔐 CI/CD Variables</strong></summary>

Set these in GitLab Settings → CI/CD → Variables

```yaml
script:
  - echo "Deploying to $PROD_URL"
```

</details>

<details>
<summary><strong>🐳 Docker-in-Docker (DinD)</strong></summary>

```yaml
image: docker:latest
services:
  - docker:dind

variables:
  DOCKER_HOST: tcp://docker:2375

script:
  - docker build -t myapp .
  - docker push myapp
```

</details>

<details>
<summary><strong>👶 Dynamic Child Pipelines</strong></summary>

```yaml
trigger:
  include: deploy.yml
  strategy: depend
```

</details>

---

## 🧪 Using Services (e.g., Databases)

<details>
<summary><strong>🐘 PostgreSQL Service Example</strong></summary>

```yaml
services:
  - postgres:latest

variables:
  POSTGRES_DB: testdb

script:
  - run-tests-with-db
```

</details>
