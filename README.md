# Key Pharma Consulting (Atlas Authorizations)

AtlasAuth is a healthcare-focused web application built during a six-month school internship in the United States. The project was created for a small company that wanted to begin building software for healthcare workflows. I programmed the full application myself, combining my background as a pharmacist with my interest in software development.

<img src="./assets/images/atlas_auth.png" width="500">

The goal of the project is to provide a foundation for a secure healthcare portal with separate spaces for public visitors, internal staff, providers, and future API access. The app is not just a static site. It includes authentication, role-aware routing, account settings, provider record management, patient-related data models, reusable address records, user suggestions, and a Docker-based local deployment setup.

I also made a video to present this project at school which you can watch here: https://youtu.be/y_qfOvyfGs0

## What It Does

- Provides a public-facing website for Atlas Authorizations.
- Supports user registration, login, logout, password reset, password change, and email-based login codes through `django-allauth`.
- Separates users into staff and provider areas using subdomains such as `staff.atlasauth.lan` and `provider.atlasauth.lan`.
- Restricts protected areas by Django group membership, so staff and providers see different parts of the system.
- Includes staff account settings with profile details, avatar upload, and optional email two-factor login.
- Includes provider record management with create, view, update, and delete flows.
- Models healthcare-adjacent records such as providers, patients, addresses, phone numbers, and user suggestions.
- Runs locally with Docker using separate services for Django, Nginx, and MySQL.
- Uses Tailwind CSS and Flowbite for the interface.

## Why This Was Challenging

This project required more than building pages. It brought together several areas that are usually difficult for students because they cross the boundary between application code, infrastructure, security, and real-world domain needs.

Authentication was one of the largest challenges. The app uses a custom Django user model, customized allauth forms, password reset/change templates, login code confirmation, session behavior, and group-based redirects after login. These are sensitive flows where small mistakes can create confusing user experiences or security problems.

The subdomain architecture also added complexity. Instead of one simple Django URL tree, the project uses `django-hosts` so the public site, staff portal, provider portal, and API can live under different hostnames. Middleware checks the current host and verifies that the logged-in user belongs to the correct group before allowing access.

The deployment setup was another important learning area. The app is containerized with Docker Compose, with Django running behind an Nginx reverse proxy and using MySQL as the database. This made the project closer to a real service than a class exercise, because local development had to account for services, ports, environment files, database health checks, migrations, static files, and HTTPS/proxy behavior.

The healthcare context mattered too. Even at an early stage, the app needed to think in terms of staff users, providers, patients, addresses, phone numbers, account privacy, and security expectations. My pharmacy background helped me understand why healthcare software must be careful with identity, access control, and clean data modeling.

## Tech Stack

- Python and Django
- Django allauth
- Django hosts
- MySQL
- Docker Compose
- Nginx
- Tailwind CSS
- Flowbite

## Project Status

This repository represents the work completed during the internship: a functional Django foundation for a healthcare portal, with authentication, role-based sections, record models, and local infrastructure in place. It is still a development-stage project, but it demonstrates the core architecture needed to continue building a healthcare operations platform.
