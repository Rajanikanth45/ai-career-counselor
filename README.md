# AI Career Counselor

A Laravel-based AI career counseling application that helps users find suitable career paths through aptitude tests, AI recommendations, and downloadable reports.

## Features

- Aptitude test creation and scoring
- Career path recommendation engine
- PDF generation for report export
- MongoDB support for user and career data
- Laravel Livewire frontend components
- OpenAI integration for AI-driven advice

## Requirements

- PHP ^8.2
- Composer
- Node.js 18+ and npm
- MongoDB

## Installation

1. Clone the repository

```bash
git clone https://github.com/Rajanikanth45/ai-career-counselor.git
cd ai-career-counselor
```

2. Install PHP dependencies

```bash
composer install
```

3. Install frontend dependencies

```bash
npm install
```

4. Copy environment file and generate app key

```bash
cp .env.example .env
php artisan key:generate
```

5. Configure database settings in `.env`

6. Run migrations and seeders

```bash
php artisan migrate --force
php artisan db:seed
```

7. Build frontend assets

```bash
npm run build
```

8. Start the application

```bash
php artisan serve
```

## Scripts

- `npm run dev` - start Vite development server
- `npm run build` - build frontend assets
- `php artisan test` - run application tests

## Notes

- Ensure MongoDB is running and correctly configured in `.env`
- Update the OpenAI API key in `.env` if AI features are enabled

## License

MIT
