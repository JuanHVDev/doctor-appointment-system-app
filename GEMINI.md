# Project: Doctor Appointment System

## Project Overview

This is a web application for a doctor appointment system. It is built using the [Next.js](https://nextjs.org/) framework (version 16) with [React](https://react.dev/) (version 19) and [TypeScript](https://www.typescriptlang.org/). The project uses the App Router structure provided by Next.js.

Styling is handled by [Tailwind CSS](https://tailwindcss.com/), and the project is set up with basic linting using [ESLint](https://eslint.org/).

## Building and Running

### Prerequisites
- [Node.js](https://nodejs.org/) (version 20 or later recommended)
- [npm](https://www.npmjs.com/) (usually comes with Node.js)

### Installation
To install the project dependencies, run the following command in the root directory:
```bash
npm install
```

### Development
To run the application in development mode, use:
```bash
npm run dev
```
This will start the development server, typically on [http://localhost:3000](http://localhost:3000).

### Production
To build the application for production, use:
```bash
npm run build
```
After the build is complete, you can start the production server with:
```bash
npm run start
```

### Linting
To run the linter and check for code quality issues, use:
```bash
npm run lint
```

## Development Conventions

### File Structure
The project follows the standard Next.js App Router directory structure:
- `app/`: Contains the main application pages and layouts.
- `public/`: For static assets like images.
- `next.config.ts`: Next.js configuration.
- `tsconfig.json`: TypeScript configuration.

### Styling
- [Tailwind CSS](https://tailwindcss.com/) is used for styling.
- Global styles and font imports are located in `app/globals.css`.
- The primary fonts are `Geist Sans` and `Geist Mono`.

### Coding Style
- The project uses ESLint with the `eslint-config-next` configuration for code quality and style enforcement. It's recommended to integrate an ESLint plugin into your code editor to get real-time feedback.

### Preferencias de Código Adicionales
- Mantener el proyecto con dependecias al minimo
- Usar idioma español