# AI Rules

## Tech Stack Overview
- **NestJS 11** powers the HTTP server layer and modules-based application structure.
- **TypeScript** provides static typing across the entire codebase for safer refactors.
- **TypeORM** manages PostgreSQL persistence with entities, repositories, and migrations.
- **PostgreSQL** is the relational database engine targeted by the infrastructure layer.
- **JWT & Passport** handle authentication and authorization workflows.
- **class-validator / class-transformer** enforce DTO validation and request data transformation.
- **Swagger (nestjs/swagger)** auto-generates API documentation served at `/api/docs`.
- **Helmet & express-rate-limit** secure HTTP traffic with sensible defaults.
- **Winston-based LoggerService** standardizes structured logging throughout the app.
- **Jest with ts-jest** runs unit and integration test suites.

## Library Usage Guidelines
1. **HTTP & Modules**: Use NestJS controllers, providers, and decorators for all web endpoints and dependency injection needs.
2. **Data Access**: Use TypeORM entities, repositories, and migrations for every database interaction; avoid raw SQL unless absolutely necessary.
3. **Validation**: Always validate and transform inbound DTOs with `class-validator` and `class-transformer` to keep controllers thin and consistent.
4. **Auth**: Rely on `@nestjs/passport`, `passport-jwt`, and the existing JWT strategy for authentication/authorization features.
5. **Security Middleware**: Configure CORS, Helmet, and rate limiting with the provided `setupSecurity` handler—do not introduce alternate middleware stacks.
6. **Logging**: Route logging through `LoggerService` (Winston) to maintain structured logs and masking of sensitive data.
7. **Hashing & Tokens**: Use `bcrypt` via the `Password` helper for password hashing and `@nestjs/jwt` for token issuance.
8. **Documentation**: Extend the automated Swagger docs through the existing `setupSwagger` helper; avoid manual documentation generators.
9. **Testing**: Write tests with Jest and `ts-jest`, matching the existing testing patterns under the `__tests__`/`tests` directories.
10. **Linting & Formatting**: Follow Biome configurations for code style and import hygiene; do not introduce alternative linters or formatters.