# Procurement System

A full-stack procurement and inventory management platform with Amazon Seller Central integration. Manage products, purchase orders, inventory movements, and supplier relationships while syncing data with Amazon's Selling Partner API.

## Key Features

- **Inventory Management**: Track stock levels, movements, and inventory adjustments
- **Product Management**: Manage SKUs, ASINs, pricing, and product metadata
- **Purchase Orders**: Create and manage POs with multiple items and suppliers
- **Supplier Management**: Maintain supplier contacts, addresses, and communication details
- **Amazon Integration**: Sync orders, inventory, and product data with Amazon SP-API
- **CSV Import/Export**: Bulk import products, inventory movements, and POs from CSV
- **User Authentication**: JWT-based auth with role-based access (admin/user)
- **Real-time Updates**: Celery task queue for async data syncing and imports

## Tech Stack

**Backend:**
- FastAPI (Python web framework)
- SQLAlchemy (ORM)
- SQLite (development database)
- Celery (async task queue)
- Amazon SP-API SDK
- JWT/OAuth2 authentication

**Frontend:**
- React 18 + TypeScript
- Vite (build tool)
- Tailwind CSS (styling)
- React Router (navigation)

## Setup

### Backend

1. Navigate to the backend directory:
   ```bash
   cd proco
   ```

2. Create and activate a virtual environment:
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Configure environment variables in `.env`:
   ```
   DATABASE_URL=sqlite:///./test.db
   SECRET_KEY=your-secret-key
   AMAZON_CLIENT_ID=your-client-id
   AMAZON_CLIENT_SECRET=your-client-secret
   AMAZON_REFRESH_TOKEN=your-refresh-token
   AWS_ACCESS_KEY=your-aws-key
   AWS_SECRET_KEY=your-aws-secret
   ```

5. Initialize the database:
   ```bash
   python scripts/init_db.py
   python scripts/seed_data.py
   ```

6. Start the API server:
   ```bash
   uvicorn app.main:app --reload --port 8000
   ```

API docs available at `http://localhost:8000/docs`

### Frontend

1. Navigate to the frontend directory:
   ```bash
   cd procurement-frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the development server:
   ```bash
   npm run dev
   ```

Frontend available at `http://localhost:5173`

## Usage

1. **Login** with default credentials (set up during seeding):
   - Username: `admin` / Password: `admin123`
   - Username: `user` / Password: `user123`

2. **Dashboard**: View inventory overview and key metrics

3. **Products**: Add/edit products with SKU, ASIN, pricing, and stock levels

4. **Purchase Orders**: Create POs from suppliers and track items

5. **Inventory**: Monitor stock movements and adjust quantities

6. **Amazon Integration**: Configure Amazon credentials and sync orders/inventory

7. **Import/Export**: Use CSV templates to bulk import/export data

## Project Structure

```
proco/                          # Backend API
├── app/
│   ├── api/v1/                # API endpoints
│   ├── integrations/          # Amazon SP-API and CSV import
│   ├── models/                # Database models
│   ├── schemas/               # Request/response schemas
│   ├── tasks/                 # Celery background tasks
│   └── core/                  # Configuration and security
├── scripts/                   # Database initialization and seeding
└── requirements.txt

procurement-frontend/          # React Frontend
├── src/
│   ├── pages/                # Page components
│   ├── components/           # Reusable UI components
│   ├── services/             # API client services
│   ├── layouts/              # Layout components
│   └── lib/                  # Utilities
└── package.json
```

## License

Proprietary