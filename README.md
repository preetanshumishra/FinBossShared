# FinBossShared

Shared business logic, services, and types for FinBoss applications (Web and Mobile).

This npm package contains reusable code that can be imported by both FinBossWeb and FinBossMobile to maintain a single source of truth for business logic and avoid code duplication.

## What's Included

### Services
- **authService** - Authentication (login, register, profile, password, preferences)
- **transactionService** - Transaction CRUD, summaries, trends, and forecasts
- **budgetService** - Budget management (CRUD and status tracking)
- **categoryService** - Category operations (list, create, update, delete)
- **analyticsService** - Budget vs actual spending analysis
- **api** - Axios HTTP client with request/response interceptors for token management

### State Management
- **authStore** - Zustand store for authentication state (user, tokens, loading, errors)

### Types
Complete TypeScript interfaces for all domain models:
- Authentication (User, Login/Register requests, Auth responses)
- Transactions (Transaction, TransactionRequest, TransactionSummary)
- Budgets (Budget, BudgetRequest, BudgetStatus)
- Categories (Category)
- API responses (ApiResponse, ApiError)

### Utilities
- **exportUtils** - Export functionality for data (JSON, CSV)

## Installation

```bash
npm install @preetanshu/finboss-shared
```

## Usage Example

```typescript
import {
  useAuthStore,
  authService,
  transactionService,
  type User,
  type Transaction,
} from '@preetanshu/finboss-shared';

// Use auth store in React components
const { login, user, logout } = useAuthStore();

// Use services for API calls
const transactions = await transactionService.getAll();
const summary = await transactionService.getSummary();
```

## Development

### Build
```bash
npm run build
```

### Local Testing
Install locally in other projects:
```bash
npm install file:../FinBossShared
```

## Publishing to npm

This package is published to GitHub npm registry (`@preetanshu/finboss-shared`).

### First Time Setup
1. Create personal access token on GitHub with `read:packages` and `write:packages` scopes
2. Create `.npmrc` in home directory:
```
@preetanshu:registry=https://npm.pkg.github.com
//npm.pkg.github.com/:_authToken=YOUR_GITHUB_TOKEN
```

### Publish New Version
```bash
npm version patch   # or minor/major
npm publish
```

## License

MIT
