# EcommerceReact

> A multi-role e-commerce web client built with React, TypeScript and Redux Toolkit — covering a customer storefront, an admin back office, and a shipper portal.

![React](https://img.shields.io/badge/React-18-61DAFB?logo=react&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-4.9-3178C6?logo=typescript&logoColor=white)
![Redux Toolkit](https://img.shields.io/badge/Redux_Toolkit-1.9-764ABC?logo=redux&logoColor=white)
![React Router](https://img.shields.io/badge/React_Router-6-CA4245?logo=reactrouter&logoColor=white)
![Ant Design](https://img.shields.io/badge/Ant_Design-5-0170FE?logo=antdesign&logoColor=white)
![MUI](https://img.shields.io/badge/MUI-5-007FFF?logo=mui&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3-06B6D4?logo=tailwindcss&logoColor=white)
![Axios](https://img.shields.io/badge/Axios-1.4-5A29E4?logo=axios&logoColor=white)

## Overview

EcommerceReact is the front-end web client (`webclient`) for an online store. Bootstrapped with Create React App, it is a single-page TypeScript application that talks to a REST backend over Axios and ships three distinct experiences from one codebase:

- **Storefront** — what shoppers see: browse products, view product detail, filter by category, manage a cart, sign in/up, and manage their profile, addresses and orders.
- **Admin** — a back-office dashboard for managing the catalog and operations.
- **Shipper** — a focused portal for delivery staff to view and work their assigned orders.

Global client state (cart, session) is managed with Redux Toolkit and survives reloads via `redux-persist`. The backend base URL is configured through an environment variable.

## Features

### Storefront (`/ecommerce/*`)
- Home page with product listing
- Product detail page (`product/:id`)
- Category browsing (`categoryProduct/:id`)
- Shopping cart with persisted state
- Authentication: sign in and sign up
- User area: profile information, saved delivery addresses, and order history

### Admin back office (`/admin/*`)
A dashboard-driven CRUD interface across the store's domain entities:
- Products and product categories
- Customers and customer addresses
- Employees and job titles
- Providers and payment methods
- Carts and orders
- Dedicated admin login

### Shipper portal (`/shipper/*`)
- Shipper dashboard
- Assigned orders view
- Dedicated shipper login

### Platform
- Client-side routing with React Router v6 (nested layouts for the storefront, admin and shipper areas)
- Redux Toolkit store persisted to local storage with `redux-persist`
- REST API integration via Axios against a configurable base URL
- Rich UI built with Ant Design and Material UI, styled with Tailwind CSS and SASS
- Toast/alert feedback via `react-toastify` and `sweetalert2`
- Rich text editing (`react-quill`), data tables (`react-table`), date pickers, and infinite scroll
- `socket.io-client` and `firebase` wired into the project

## Tech stack

| Area | Technology |
| --- | --- |
| Framework | React 18 + TypeScript (Create React App / `react-scripts`) |
| Routing | React Router v6 (`react-router-dom`) |
| State | Redux Toolkit, React Redux, `redux-persist` |
| UI libraries | Ant Design 5, Material UI 5 (Emotion) |
| Styling | Tailwind CSS 3, SASS, PostCSS, Autoprefixer |
| HTTP | Axios |
| Realtime | `socket.io-client` |
| Other | Firebase, `react-quill`, `react-table`, `react-toastify`, `sweetalert2`, `date-fns` / `dayjs` / `moment` |
| Tooling | Prettier, Docker |
| Testing | React Testing Library, Jest |

## Getting started

### Prerequisites
- Node.js 18+
- npm (or yarn)

### Installation

```bash
git clone https://github.com/DucMinhNe/EcommerceReact.git
cd EcommerceReact
npm install
```

### Configuration

The client reads its API base URL from an environment variable. Create a `.env` file at `src/.env` (or the project root, per Create React App conventions):

```bash
REACT_APP_BASE_URL=http://your-api-host:3000/api
```

### Available scripts

| Command | Description |
| --- | --- |
| `npm start` | Run the app in development mode at http://localhost:3000 |
| `npm run build` | Produce an optimized production build in `build/` |
| `npm test` | Run the test runner in watch mode |

### Run with Docker

A `dockerfile` is included for running the dev server in a container:

```bash
docker build -t ecommerce-react .
docker run -p 3000:3000 ecommerce-react
```

## Project structure

```
EcommerceReact/
├── public/                     # Static assets and HTML template
├── src/
│   ├── App.tsx                 # Route definitions (admin / shipper / ecommerce)
│   ├── index.tsx               # App entry, Redux Provider + PersistGate
│   ├── common/                 # Shared utilities and constants
│   │   ├── consts/             # System constants (e.g. API domain)
│   │   └── utils/              # Token helpers (auth headers, logout)
│   ├── page/
│   │   ├── Admin/              # Admin dashboard pages (CRUD modules)
│   │   ├── Shipper/            # Shipper dashboard, orders, login
│   │   └── Ecommerce/          # Storefront
│   │       ├── components/     # Header, Footer, shared UI
│   │       ├── pages/          # Home, product, cart, auth, user pages
│   │       ├── api/            # Axios API calls
│   │       ├── redux/          # Store, persist config, slices
│   │       ├── firebase/       # Firebase initialization
│   │       └── assets/         # Images and static assets
│   └── img/                    # Image assets
├── tailwind.config.js
├── tsconfig.json
├── dockerfile
└── package.json
```

## License

This project is part of a personal portfolio. All rights reserved unless stated otherwise.
