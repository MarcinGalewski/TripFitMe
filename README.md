# TripFitMe: Intelligent Travel Planning System

## Short Description

TripFitMe is an intelligent web system designed to automatically generate personalized, optimized travel itineraries. It leverages real-time data on flights, hotels, and attractions from external APIs to significantly minimize the time and effort required for travel planning.

## Features

* **Personalized Itinerary Generation:** Creates optimized travel plans based on user criteria (budget, preferences).
* **Automated Selection:** Intelligently selects optimal flight and hotel proposals.
* **Two-Level Optimization Algorithm:** Implements a macro-level greedy algorithm for grouping attractions into daily plans and a micro-level Traveling Salesperson Problem (TSP) solution for optimizing daily routes.
* **External API Integrations:** Connects with leading travel APIs for real-time data.
* **Comprehensive Cost Estimation:** Provides an estimated total cost for the entire trip, including flights, accommodation, and attractions.
* **PDF Export:** Generates detailed, personalized travel plans in PDF format with active links.
* **Flexible Planning Options:** Offers both a "Quick Plan" for high automation and a "Personalized Plan" for detailed user control.

## Tech Stack

* **Frontend:** React, JavaScript
* **Backend:** Python, Django, Django REST Framework
* **Database:** PostgreSQL
* **Containerization:** Docker, Docker Compose
* **Caching:** Redis
* **External APIs:** Google Maps (Directions, Places), Amadeus (Flights & Hotels), Tripadvisor (Attractions), Brevo (for email services)

## Architecture

The project is built on a client-server architecture, with the backend (Django) and frontend (React) operating within Docker containers. The system extensively utilizes cloud services through integrations with various external APIs.

## Project Status

Currently in active development.

## Author

Marcin Galewski

## License

MIT License
