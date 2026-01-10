# AGENTS.md - Coding Guidelines for Doctor Appointment System

## Build, Lint, and Test Commands

### Development
```bash
# Start development server
npm run dev

# Build for production
npm run build

# Start production server
npm start

# Type checking
npx tsc --noEmit
```

### Code Quality
```bash
# Run ESLint on all files
npm run lint

# Run ESLint on specific file
npx eslint app/page.tsx

# Format code (when Prettier is added)
npx prettier --write .
```

### Testing (To Be Added)
```bash
# Run all tests
npm test

# Run tests in watch mode
npm run test:watch

# Run specific test file
npm test -- app/components/Button.test.tsx

# Run tests with coverage
npm run test:coverage
```

### Recommended Testing Setup
When adding tests, use:
- **Jest** + **React Testing Library** for unit/component tests
- **Playwright** or **Cypress** for E2E tests
- Test files should be colocated with components: `Component.test.tsx`

## Code Style Guidelines

### TypeScript Configuration
- **Strict mode**: Always enabled (`"strict": true` in tsconfig.json)
- **Target**: ES2017 for modern browser support
- **Module resolution**: Use bundler resolution
- **JSX**: Use `"react-jsx"` (not `"react-jsxdev"`)

### Import Organization
```typescript
// 1. React imports first
import React from 'react';

// 2. Third-party libraries
import { useState } from 'react';

// 3. Type imports
import type { Metadata } from 'next';

// 4. Local imports (relative)
import { Button } from './components/Button';

// 5. Path aliases (@/* for root)
import { api } from '@/lib/api';
```

### Component Structure
```typescript
// Function components with proper typing
interface Props {
  title: string;
  onClick: () => void;
}

export default function MyComponent({ title, onClick }: Props) {
  return (
    <div>
      <h1>{title}</h1>
      <button onClick={onClick}>Click me</button>
    </div>
  );
}
```

### Naming Conventions
- **Components**: PascalCase (`UserProfile`, `AppointmentCard`)
- **Functions/Variables**: camelCase (`handleSubmit`, `userData`)
- **Types/Interfaces**: PascalCase (`User`, `AppointmentData`)
- **Files**: kebab-case for components (`user-profile.tsx`), camelCase for utilities (`apiClient.ts`)
- **Directories**: kebab-case (`doctor-appointments`, `user-management`)

### Styling with Tailwind CSS
- Use **Tailwind utility classes** for styling
- Define **CSS custom properties** in `globals.css` for theme colors
- Follow **mobile-first responsive design**
- Use **Tailwind's dark mode** for theme switching

```css
/* globals.css */
:root {
  --background: #ffffff;
  --foreground: #171717;
}

@theme inline {
  --color-background: var(--background);
  --color-foreground: var(--foreground);
}
```

### Error Handling
```typescript
// Async operations
try {
  const data = await fetchData();
} catch (error) {
  console.error('Failed to fetch data:', error);
  // Handle error appropriately
}

// API responses
if (!response.ok) {
  throw new Error(`API request failed: ${response.status}`);
}
```

### File Organization
```
app/
├── components/     # Reusable UI components
├── lib/           # Utility functions and configurations
├── types/         # TypeScript type definitions
└── api/           # API routes and handlers
```

### Performance Considerations
- Use **React.memo** for expensive components
- Implement **lazy loading** for routes: `const Component = lazy(() => import('./Component'))`
- Optimize **images** with Next.js Image component
- Use **dynamic imports** for code splitting

### Accessibility
- Add **aria-labels** to interactive elements without visible text
- Use **semantic HTML** elements
- Ensure **keyboard navigation** works
- Test with **screen readers**

### Git Workflow
- Use **conventional commits**: `feat:`, `fix:`, `docs:`, `refactor:`
- **Branch naming**: `feature/`, `bugfix/`, `hotfix/`
- Always **pull before push**
- **Squash commits** when merging features

## Tool Configuration

### ESLint Rules
- Extends **eslint-config-next** for Next.js best practices
- Includes **core-web-vitals** rules for performance
- TypeScript rules via **eslint-config-next/typescript**

### Additional Recommended Tools
- **Prettier**: For consistent code formatting
- **Husky**: For pre-commit hooks
- **Commitlint**: For conventional commit messages

## Security Best Practices
- Never commit **secrets** or **API keys**
- Use **environment variables** for sensitive data
- Validate all **user inputs**
- Implement **proper authentication** and **authorization**

## Code Review Checklist
- [ ] TypeScript types are correct and complete
- [ ] ESLint passes without warnings
- [ ] Tests are written and passing
- [ ] Accessibility considerations included
- [ ] Performance optimizations applied where needed
- [ ] Security best practices followed
