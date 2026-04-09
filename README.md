# Procurement System

A full-stack procurement and inventory management platform with Amazon SP-API integration. Manage products, purchase orders, suppliers, and inventory with CSV import/export capabilities and real-time Amazon synchronization.

## Features

- **Product & Inventory Management** — Track SKUs, pricing, costs, and inventory levels with movement history
- **Purchase Order System** — Create, track, and manage POs with supplier integration
- **Supplier Management** — Centralized supplier database with contact and payment information
- **Amazon Integration** — Sync orders, inventory, and product data directly from Amazon SP-API
- **CSV Import/Export** — Bulk import products and inventory from CSV files
- **User Authentication** — JWT-based authentication with role-based access control (admin/user)
- **Task Scheduling** — Celery-based background jobs for automated syncs and imports
- **REST API** — Comprehensive API with auto-generated Swagger docs

## Tech Stack

**Backend:**
- FastAPI (REST API framework)
- SQLAlchemy (ORM)
- SQLite/PostgreSQL (database)
- Celery (task queue)
- Pydantic (data validation)
- python-jose (JWT authentication)
- sp-api-python (Amazon SP-API client)
- pandas (CSV processing)

**Frontend:**
- React 18 + TypeScript
- Vite (build tool)
- TailwindCSS (styling)
- Axios (HTTP client)

## Setup

### Backend

```bash
cd proco
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Create a `.env` file with required variables:
```
DATABASE_URL=sqlite:///./test.db
SECRET_KEY=your-secret-key-here
AMAZON_REFRESH_TOKEN=your-token
AMAZON_CLIENT_ID=your-client-id
AMAZON_CLIENT_SECRET=your-client-secret
AWS_ACCESS_KEY=your-access-key
AWS_SECRET_KEY=your-secret-key
```

Initialize the database:
```bash
python scripts/init_db.py
python scripts/seed_data.py
```

Start the API:
```bash
uvicorn app.main:app --reload
```

### Frontend

```bash
cd procurement-frontend
npm install
npm run dev
```

The frontend will be available at `http://localhost:5173`

## Usage

1. **Login** — Use credentials from seed data (admin/admin123 or user/user123)
2. **Import Products** — Use Import/Export page to upload product CSV files
3. **Manage Inventory** — Track inventory levels and movements on the Inventory page
4. **Amazon Sync** — Configure Amazon integration and sync orders/inventory
5. **Purchase Orders** — Create and manage purchase orders with suppliers

## API Documentation

Once running, visit `http://localhost:8000/docs` for interactive Swagger documentation.

## Project Structure

```
proco/                          # Backend API
├── app/
│   ├── api/v1/                 # API routes
│   ├── models/                 # Database models
│   ├── schemas/                # Request/response schemas
│   ├── core/                   # Config, security, database
│   ├── integrations/           # External API integrations
│   └── tasks/                  # Celery background tasks
├── scripts/                    # Initialization and utilities
└── requirements.txt

procurement-frontend/           # React UI
├── src/
│   ├── pages/                  # Route pages
│   ├── components/             # Reusable UI components
│   ├── services/               # API service clients
│   └── lib/                    # Utilities and helpers
└── package.json
```