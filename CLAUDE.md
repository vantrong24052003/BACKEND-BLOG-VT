# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Ruby on Rails 8.1.1 blog backend API application using PostgreSQL. The project is currently in initial state with core Rails structure generated.

**Tech Stack:**
- Ruby 3.2.6
- Rails 8.1.1
- PostgreSQL (pg 1.6.3)
- Puma 6.0 web server
- Solid Queue, Solid Cache, Solid Cable for production

## Development Commands

**Setup:**
```bash
./bin/setup              # Install dependencies, prepare database, start server
./bin/setup --reset      # Same as above but resets database
```

**Start Development Server:**
```bash
./bin/dev                # Start development server
bin/rails server         # Alternative
```

**Database:**
```bash
bin/rails db:prepare     # Create/migrate database as needed
bin/rails db:reset       # Drop, create, migrate, seed
bin/rails db:migrate     # Run pending migrations
bin/rails db:rollback    # Rollback last migration
bin/rails db:seed        # Load seed data
```

**Testing:**
```bash
bin/rails test                    # Run all tests
bin/rails test test/models/user_test.rb  # Run specific test
```

**Code Quality:**
```bash
bin/rubocop              # Run linting
bin/brakeman             # Security scanning
bin/bundler-audit        # Check for vulnerable dependencies
```

**Jobs:**
```bash
bin/jobs                 # Start Solid Queue background job processor
```

## Architecture

**Standard Rails MVC:**
- `app/controllers/` - Controllers
- `app/models/` - Active Record models
- `app/views/` - ERB templates
- `app/jobs/` - Background jobs (Solid Queue)
- `app/mailers/` - Action Mailer
- `config/routes.rb` - Routes

**Database:**
- Development: `Blog-VT-dev`
- Test: `Blog-VT-test`
- Production: Multi-database (primary, cache, queue, cable)
- Config: `config/database.yml`

**Code Style:**
- RuboCop Rails Omakase (default Rails 8 style)
- Config: `.rubocop.yml`

## Production

Docker + Kamal deployment. Config in `.kamal/` directory.
