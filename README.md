# Poros Data Service

A TypeScript REST API for Poros, an application that helps students organize job searches, manage resumes, track applications, and research target companies.

## Technology

- Node.js, Express, and TypeScript
- PostgreSQL and Supabase
- JWT authentication with bcrypt password hashing
- Multer for PDF uploads
- Anthropic and Tavily integrations through authenticated server-side routes
- GitHub Actions and deployment configurations for Vercel, Render, and Railway

## Implemented API areas

- Authentication: `/api/auth`
- Users and career targets: `/api/users`
- Resumes and tailored-resume records: `/api/resumes`
- Companies: `/api/companies`
- Applications: `/api/applications`
- Preparation checklists: `/api/checklist`
- AI resume tailoring and company research: `/api/ai`

AI provider credentials stay on the server. The mobile client never receives Anthropic, Tavily, database, JWT, or Supabase service-role secrets.

## Local setup

### 1. Install dependencies

```bash
npm install
```

### 2. Create a local environment file

Copy `.env.example` to `.env`, then replace every placeholder with credentials from services you control.

```env
PORT=3000
DATABASE_URL=postgres://user:password@localhost:5432/poros
JWT_SECRET=replace_with_a_long_random_value
SUPABASE_URL=https://your-project.supabase.co
SUPABASE_KEY=your_supabase_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_supabase_service_role_key
ANTHROPIC_API_KEY=your_anthropic_api_key
TAVILY_API_KEY=your_tavily_api_key
```

Create the database schema using `sql/poros.sql`. Never reuse the original class team's shared database or credentials.

### 3. Run and verify

```bash
npm run type-check
npm run dev
```

Open `http://localhost:3000/health` to verify the service.

## Security notes

- All user-data and AI routes require a valid JWT.
- Passwords are hashed before storage.
- Uploads are limited to PDF files.
- Secret files and uploaded documents are excluded by `.gitignore`.
- Production deployments should restrict CORS to approved origins.

## Related repositories

- [Poros mobile client](https://github.com/Jojo-Osei-Kofi/Poros-Client)
- [Project overview and usability research](https://github.com/Jojo-Osei-Kofi/Poros-Project)

## Academic context

Poros was built by a five-person Calvin University CS 262 team. See the project overview for team attribution and Jojo Osei-Kofi's documented contributions.
