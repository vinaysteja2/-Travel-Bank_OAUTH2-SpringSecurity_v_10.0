# 🔐 Travel-Bank\_OAUTH2-SpringSecurity\_v\_10.0

> ✅ **Secure Microservices Gateway using OAuth2, OpenID Connect & Spring Security with Keycloak**

This version of the **Travel Bank Microservices Suite** focuses on implementing **centralized authentication and authorization** using **OAuth 2.0 Authorization Code Grant Flow** , **OAuth 2.0 Client Grant Flow** via **Keycloak** and **Spring Security** at the **API Gateway** level.

---

## 🔐 Core Features Implemented

### 🧭 1. OAuth2 Authorization Code Grant Flow

* Uses **Authorization Code** flow (recommended when the end user is involved)
* Redirects users to **Keycloak Login Page** for secure authentication
* **Access Token** received and validated at Gateway using **JWT**

### 🛡️ 2. Integration with Keycloak (OpenID Provider)

* Keycloak is used as the **Authorization Server**
* **Client applications and end-users** are registered in Keycloak
* Utilizes **Keycloak's OpenID Connect support** to generate ID tokens and access tokens

### 🔐 3. Spring Security Integration at Gateway

* Gateway acts as **Resource Server**
* Uses **Spring Security OAuth2** to validate tokens
* Secure routing to downstream services after token validation

---

## 🧪 Demo Walkthrough

1. 👤 **User** visits the UI Client (Angular/Web/Mobile)
2. 🚪 UI redirects to Keycloak Login Page
3. 🔐 User authenticates & consents
4. 🔁 UI receives Authorization Code → exchanges it for Access Token
5. 🎫 Access Token sent to **Spring Cloud Gateway**
6. 🔍 Gateway validates token with Keycloak
7. 🛰️ If valid, Gateway routes request to downstream microservices (Accounts, Loans, Cards)

---

## 📁 Project Module Lineage

| ⭐ Version | 📁 Module          | 🧩 Description                          |
| --------- | ------------------ | --------------------------------------- |
| v1.0      | Core Microservices | Accounts, Loans, Cards                  |
| v2.0      | Dockerization      | Dockerfile & Compose setup              |
| v3.0      | Config Management  | Spring Config Client                    |
| v4.0      | Config Server      | Centralized Config Host                 |
| v5.0      | MySQL Integration  | Database Setup                          |
| v6.0      | Service Registry   | Eureka Discovery Server                 |
| v7.0      | API Gateway        | Spring Cloud Gateway                    |
| v8.0      | Resilience         | Resilience4j Patterns                   |
| v9.0      | Observability      | Logs + Metrics + Traces (Grafana Stack) |
| ✨ v10.0   | Security           | OAuth2 + OpenID Connect via Keycloak    |

---

## 📂 Key Configuration Files

### 🔐 application.yml (Gateway)

```yaml
spring:
  security:
    oauth2:
      resourceserver:
        jwt:
          issuer-uri: http://localhost:8080/realms/travel-bank
```

### 🧾 Keycloak Client Configuration

* `client_id`: easybank-callcenter-ac
* `client_secret`: \*\*\*\*\*\*\*\*\*\*
* `Redirect URI`: [http://localhost:4200/dashboard](http://localhost:4200/dashboard)
* `Web Origins`: \*
* `Flow`: Authorization Code (Standard Flow)

---

## 📌 Benefits of OAuth2 Integration

* 🔐 **Centralized security** with Keycloak
* 🧠 Follows modern **OpenID Connect standards**
* ⚙️ Easy role-based access control using Keycloak realm roles
* 🔄 Supports SSO (Single Sign-On) and identity federation

---

## 🚀 Run Order

```bash
1. docker-compose up         # 🔌 Start Keycloak, DBs, services
2. Start Gateway             # 🛡️ OAuth2-secured Spring Cloud Gateway
3. Access UI                 # 🔄 Redirects to Keycloak for login
```

🧪 Default Keycloak login: `admin / admin`

---

## 🧠 Why Security at Gateway Matters

> Protect once, route securely. Your microservices stay internal and don’t worry about auth individually.

* 📦 Token validated once
* 🚪 All microservice access controlled at the Gateway
* ✅ JWT ensures **stateless**, verifiable tokens

---

## 💬 Contribution

🤝 Fork → Create a branch → Add your feature → Open a Pull Request

We welcome enhancements in:

* RBAC integration
* Social login extensions (Google, GitHub)
* Angular client examples

---

## 📜 License

MIT License © [Vinay Steja](https://github.com/vinaysteja2)

🛠️ Built with love using **Spring Security**, **Keycloak**, and **Spring Cloud Gateway**
