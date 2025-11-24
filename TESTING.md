# Frontend Testing Guide

This document describes the testing setup and how to run tests for the frontend application.

## Test Setup

The project uses:
- **Jest** - Test runner
- **React Testing Library** - Component testing utilities
- **@testing-library/jest-dom** - Custom Jest matchers for DOM
- **@testing-library/user-event** - User interaction simulation

## Running Tests

### Run all tests
```bash
npm test
```

### Run tests in watch mode
```bash
npm run test:watch
```

### Run tests with coverage
```bash
npm run test:coverage
```

## Test Structure

Tests are organized in `__tests__` directories alongside the code they test:

```
src/
  ├── components/
  │   ├── __tests__/
  │   │   ├── ErrorDisplay.test.tsx
  │   │   ├── EmptyState.test.tsx
  │   │   ├── LoadingState.test.tsx
  │   │   ├── pagination.test.tsx
  │   │   └── searchBar.test.tsx
  ├── utils/
  │   ├── __tests__/
  │   │   ├── apiErrorHandler.test.ts
  │   │   ├── paginationUtils.test.ts
  │   │   ├── storageUtils.test.ts
  │   │   └── urlUtils.test.ts
  └── lib/
      ├── __tests__/
      │   └── api.test.ts
```

## Test Coverage

Current test coverage includes:

### Utilities
- ✅ `urlUtils` - URL building, parsing, validation
- ✅ `storageUtils` - SessionStorage operations
- ✅ `paginationUtils` - Pagination calculations
- ✅ `apiErrorHandler` - Error handling

### Components
- ✅ `ErrorDisplay` - Error message display
- ✅ `EmptyState` - Empty state with actions
- ✅ `LoadingState` - Loading skeleton
- ✅ `Pagination` - Page navigation
- ✅ `SearchBar` - Search input with debouncing

### API
- ✅ `movieApi` - All API methods (search, favorites, add/remove)

## Writing New Tests

### Component Test Example
```typescript
import { render, screen } from '@testing-library/react';
import { MyComponent } from '../MyComponent';

describe('MyComponent', () => {
  it('should render correctly', () => {
    render(<MyComponent />);
    expect(screen.getByText('Hello')).toBeInTheDocument();
  });
});
```

### Utility Test Example
```typescript
import { myUtility } from '../myUtility';

describe('myUtility', () => {
  it('should work correctly', () => {
    const result = myUtility('input');
    expect(result).toBe('expected');
  });
});
```

## Best Practices

1. **Test behavior, not implementation** - Focus on what the component does, not how
2. **Use semantic queries** - Prefer `getByRole`, `getByLabelText` over `getByTestId`
3. **Test user interactions** - Use `userEvent` for realistic user interactions
4. **Keep tests isolated** - Each test should be independent
5. **Mock external dependencies** - Mock API calls, timers, etc.

## Configuration Files

- `jest.config.js` - Jest configuration
- `jest.setup.js` - Test setup and global mocks
- `tsconfig.test.json` - TypeScript config for tests (if needed)

