# AI-Powered Codebase Documentation Generator

## 📌 Overview
- **Problem**: Finding nearby parking options and managing two-sided onboarding (parkers vs. landlords) is often fragmented, manual, and location-agnostic.
- **Solution built**: Developed a **Django web application** that supports **Parker/Landlord registration + PIN-based login**, **location-aware landlord discovery**, and an **admin-style dashboard** backed by **SQLite**.
- **Why it matters**: Enables faster decision-making for parkers and simpler inventory onboarding for landlords using a scalable **MVC (Django MVT)** architecture and **geospatial distance sorting**.

## 🚀 Key Features
- **Role-based onboarding**: Implemented separate **Parker** and **Landlord** sign-up flows with form validation (PIN, phone, email uniqueness).
- **Location-aware discovery**: Designed a **Haversine distance** ranking pipeline to display the **nearest landlords (top 10)** from a provided latitude/longitude (with sensible defaults).
- **Data onboarding at scale**: Implemented a Django **management command** to **bulk import landlords from CSV** using `bulk_create` for faster seeding.

## 🛠️ Tech Stack
- **Languages**: Python
- **Frameworks**: Django (MVT)
- **Tools & Libraries**: SQLite, WhiteNoise (static assets), Pillow (image upload), geopy/geographiclib (geospatial utilities)
- **Platforms**: Vercel (Python runtime), Web (HTML templates)

## 📚 Project Learnings
- **Technical concepts learned**: Django ORM modeling, request/response lifecycle, server-side rendering, session handling, distance computation (Haversine), bulk inserts.
- **Tools/technologies mastered**: Django forms + validation, SQLite-backed development workflows, Vercel deployment configuration for WSGI apps.
- **Practical skills gained**: Built a multi-entity system (Parker/Landlord), hardened input validation (PIN + phone), and shipped an end-to-end feature from data import → UI output.

## 📊 Results / Output
- **System outputs**:
  - A **ranked list of nearby landlords** (top 10) rendered in `parker_main.html`
  - A **dashboard view** listing all registered parkers and landlords
  - A repeatable **CSV import pipeline** for landlord dataset seeding
- **Metrics**:
  - **Deterministic ranking** using Haversine distance (km) for consistent nearest-neighbor ordering
  - **Batch creation** via `bulk_create` to reduce database write overhead during imports
- **Key achievements**: Delivered a working Django application with **authentication flows**, **geospatial sorting**, and **data onboarding automation**.

## 🧠 Output Learnings
- **Geospatial behavior**: Small coordinate changes can reshuffle the “nearest” list; stable ranking requires consistent coordinate precision and null handling.
- **Data quality impact**: Missing/invalid latitude/longitude values directly reduce discoverability; excluding null coordinates improves UX predictability.

## 🔍 Output Interpretation
- **Real-world meaning**: The nearest-landlord output acts like a lightweight **location-based search engine** for parking inventory.
- **Practical impact**: Reduces time-to-find parking by prioritizing proximity and improves landlord onboarding throughput via automated imports.

## ⚠️ Challenges & Solutions
- **Two-role flows and validation complexity** → Implemented separate Django `ModelForm` workflows with field-level + cross-field validation (e.g., PIN confirmation).
- **Distance sorting without GIS dependencies** → Designed a Haversine-based ranking function to avoid heavy PostGIS/GIS setup for a lightweight deployment.
- **Seeding large datasets reliably** → Implemented a CSV import management command using `bulk_create` for performance and repeatability.

## 🔮 Future Improvements
- **Scalability**: Migrate from SQLite to PostgreSQL and add indexing on `phone`, `email`, and geospatial fields.
- **Feature enhancements**: Add real authentication (Django Auth), role-based access control, booking/reservation workflow, and landlord availability/pricing.
- **Optimization opportunities**: Introduce pagination, caching for frequent searches, and optional GIS-backed queries (PostGIS) for large-scale proximity search.

## ✅ Conclusion
Developed a Django-based, location-aware parking discovery system that unifies onboarding, discovery, and admin visibility in one deployable web app.  
Implemented deterministic proximity ranking and automated data imports to improve usability and operational efficiency.
