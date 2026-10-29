#### **OVERVIEW**

---

Dental clinic management system covering patients, appointments, treatments, billing and stock, with role-based access for administrators, dentists and staff. Every record belongs to a clinic, so data isolation, permissions and an audit trail are built into the foundation. The codebase prioritizes reliability and maintainability, with strict typing, automated tests and consistent conventions across the back end and front end.

#### **STACK**

---

The application runs on Laravel, with React rendered through Inertia for the interface and TypeScript on the front end. Data is stored in PostgreSQL, and styling uses Tailwind CSS with shadcn/ui components. The versions listed are the major releases in use.

> - [x] Laravel 13
> - [x] React 19 with Inertia
> - [x] TypeScript 5
> - [x] Tailwind CSS 4
> - [x] PostgreSQL 17

#### **REQUIREMENTS**

---

The Node.js version matches the one used across Makcood projects. PostgreSQL must be running locally, with a development database and a separate test database owned by the same user.

> - [x] PHP 8.4 and Composer 2
> - [x] Node.js 24 and npm 10 or later
> - [x] PostgreSQL 17

#### **GETTING STARTED**

---

Clone the repository, install the dependencies and create the local environment file. Then add the database password, prepare the database and start the development server.

> ```bash
> git clone https://github.com/Makcood/ashasmile.git
> cd ashasmile
> ```
>
> ```bash
> composer install
> npm ci
> cp .env.example .env
> php artisan key:generate
> ```
>
> ```sql
> -- in psql
> CREATE USER ashasmile_user WITH PASSWORD 'your-dev-password';
> CREATE DATABASE ashasmile_dev OWNER ashasmile_user;
> CREATE DATABASE ashasmile_test OWNER ashasmile_user;
> ```
>
> ```bash
> # set DB_PASSWORD in .env, then:
> php artisan migrate
> composer run dev
> ```

> [!NOTE]
> The application runs on `ashasmile_dev`. Tests run on `ashasmile_test`, configured in `phpunit.xml`, so running them never touches development data.

#### **GOOD TO KNOW**

---

The project follows a few conventions that go beyond a default Laravel setup. Knowing them up front avoids data leaks between clinics and incorrect amounts.

> - Every clinic-owned table has a `clinic_id`, and queries are scoped to the signed-in user's clinic
> - Money is stored as an integer in cents, never as a decimal
> - The activity log is append-only; its cleanup command is never scheduled
> - Tests run with `php artisan test`
> - Commit messages follow Conventional Commits

#### **LICENCE**

---

Proprietary. All rights reserved.
