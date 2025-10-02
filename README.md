# 📐 Subscription Microservices

The **Subscription Microservices** project is a **.NET 8 Application** designed as a technical assessment to evaluate backend skills in microservices architecture, data management, caching, and clean code.  

This repository contains two microservices that work together:

- **App Service** – Provides subscription-related APIs and interacts with Redis cache. If Redis data is unavailable, it calls the **Package Service** APIs to retrieve subscription data.
- **Package Service** – Stores subscription data in database and Redis, and serves as the source of truth for App Service. Any data changes are synchronized with Redis automatically.

![dotnet-version](https://img.shields.io/badge/dotnet%20version-net8.0-blue)

---

## ⭐ Introduction
The system simulates a subscription management platform with caching and fallback mechanisms.  

- **App Service** first tries to serve requests from a distributed Redis cache for fast access.  
- **Package Service** is the authoritative source of subscription data and is called by App Service when cache is unavailable or outdated.  

Both services follow **Clean Architecture principles**, with isolated use cases, centralized error handling, and proper layering.

---

## 🔎 Core Features

### App Service
- Reads subscription data from **Redis cache** first.
- Falls back to **Package Service APIs** if cache is unavailable.
- Provides APIs:
  - Get subscription by user ID
  - Get all subscriptions with optional lastRowVersion
- Implements **retry and failover** for external API calls.
- Centralized **Global Exception Middleware**.
- **Swagger UI** for interactive API testing.

### Package Service
- Stores subscription data in **SQL Server / database**.
- Syncs data automatically to **Redis** on changes.
- Provides APIs for:
  - Get subscription by user ID
  - Get all subscriptions
- Health check and monitoring for Redis.
- **Swagger UI** for API exploration.

---

## Microservices in This System

- [App Service](https://github.com/Shahinmm69/AppService) – Responsible for providing subscription-related APIs and interacting with Redis cache and the Package Service.
- [Package Service](https://github.com/Shahinmm69/PackageService) – Provides core subscription data and endpoints that App Service calls when Redis is unavailable.

---

## ✅ Technical Features
- **.NET 8 Web API**  
- **CQRS** with **MediatR** for decoupled request/response handling  
- **Distributed Redis Cache** with fallback to Package Service  
- **Database + Redis synchronization** in Package Service  
- **Global Exception Middleware** for consistent error handling  
- **Swagger (OpenAPI)** for interactive API documentation  
- **Unit Tests** written with xUnit, Moq, FluentAssertions

---

## 🧑‍💻 Development and Deployment Features
- **Local Development**:
  - SQL Server LocalDB or full SQL Server
  - Redis (local Docker or remote)
  - Swagger UI for testing endpoints
- **Testing**:
  - Unit tests for all commands, queries, services, and controllers
  - 100% code coverage possible
- **Deployment Ready**:
  - Configurable `appsettings.json` (DB connection, Redis connection, Package BaseUrl)
  - HTTPS enforced
  - Containerization via Docker supported

---

## 💾 Getting Started

### Prerequisites
- [.NET 8 SDK](https://dotnet.microsoft.com/download)
- SQL Server (LocalDB or full version)
- Redis (local Docker or remote)

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/Shahinmm69/subscription-microservices.git
   cd subscription-microservices

---

## 🩷 Follow Me!

You can connect with me on the social media and communication channels listed below.

[![LinkedIn][linkedin-shield]][linkedin-url]
[![Telegram][telegram-shield]][telegram-url]
[![WhatsApp][whatsapp-shield]][whatsapp-url]
[![Gmail][gmail-shield]][gmail-url]
![GitHub followers](https://img.shields.io/github/followers/Shahinmm69)

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?logo=linkedin&color=555
[linkedin-url]: https://www.linkedin.com/in/shahin-maboudi-moghaddam

[telegram-shield]: https://img.shields.io/badge/-Telegram-black.svg?logo=telegram&color=fff
[telegram-url]: https://t.me/Shahin_graff

[whatsapp-shield]: https://img.shields.io/badge/-WhatsApp-black.svg?logo=whatsapp&color=fff
[whatsapp-url]: https://wa.me/989304199911

[gmail-shield]: https://img.shields.io/badge/-Gmail-black.svg?logo=gmail&color=fff
[gmail-url]: mailto:s.maboudi69@gmail.com
