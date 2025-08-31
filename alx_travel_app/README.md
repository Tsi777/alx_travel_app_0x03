alx_travel_app_0x03

A Django RESTful API for managing travel listings, bookings, reviews, and payments, enhanced with background tasks for email notifications using Celery and RabbitMQ.
Features

    User Authentication: Secure registration and login using Django’s built-in user model and JWT authentication.
    Listings: CRUD operations for travel listings (hotels, apartments, experiences).
    Bookings: Users can book listings, view their bookings, and manage (change/cancel) them.
    Reviews: Users can leave reviews and ratings for listings.
    Payments: Integration with Chapa for secure booking payments and verification.
    Background Tasks: Asynchronous email notifications for booking confirmations using Celery with RabbitMQ.
    Permissions: Fine-grained permissions for viewing, adding, changing, and deleting listings, bookings, reviews, and payments.
    Browsable API: Interactive API documentation via Swagger and Redoc.

API Endpoints

All endpoints are prefixed by /listings/ unless otherwise noted.
Resource 	Endpoint 	Methods 	Description
Listings 	/listings/ 	GET, POST 	List or create listings
Listings 	/listings/{id}/ 	GET, PUT, PATCH, DELETE 	Retrieve, update, or delete a listing
Bookings 	/bookings/ 	GET, POST 	List or create bookings
Bookings 	/bookings/{id}/ 	GET, PUT, PATCH, DELETE 	Retrieve, update, or delete a booking
Reviews 	/reviews/ 	GET, POST 	List or create reviews
Reviews 	/reviews/{id}/ 	GET, PUT, PATCH, DELETE 	Retrieve, update, or delete a review
Payments 	/bookings/{booking_id}/initiate-payment/ 	POST 	Initiate payment via Chapa
Payments 	/bookings/verify-payment/{tx_ref}/ 	GET 	Verify Chapa payment status

    Note: Authentication is required for most operations.

Setup & Installation

Clone the repository:

git clone <repo-url>
cd alx_travel_app_0x03

Create and activate a virtual environment:

python3 -m venv venv
source venv/bin/activate

Install dependencies:

pip install -r requirements.txt

Apply migrations:

python manage.py migrate

Create a superuser (admin):

python manage.py createsuperuser

Start RabbitMQ (required for Celery):

sudo systemctl start rabbitmq-server

or on macOS (Homebrew):

brew services start rabbitmq

Start Celery worker:

celery -A alx_travel_app worker --loglevel=info

Run the Django development server:

python manage.py runserver

