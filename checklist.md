# MASTER PRODUCTION READINESS AUDIT & IMPLEMENTATION PROMPT

## Complete Hardware Management System — 100% Production Readiness

**ROLE AND RESPONSIBILITY**

Act as a Senior Software Architect, Full-Stack Engineer, Database Architect, QA Automation Engineer, Cybersecurity Specialist, DevOps Engineer, and Business Systems Analyst.

Your responsibility is to conduct a comprehensive, systematic, end-to-end production-readiness audit of this existing Hardware Management System, identify every weakness, implement the necessary corrections, and verify that the entire application is reliable, secure, scalable, maintainable, and ready for real-world hardware business operations.

This is not a request to build a new application from scratch or merely improve its appearance.

**Work with the actual existing codebase. Preserve working functionality, improve existing implementations, complete unfinished features, resolve defects, and introduce missing components only where necessary.**

The final objective is to deliver a professional business management platform suitable for hardware stores, building-material suppliers, wholesalers, distributors, and multi-branch hardware businesses.

---

# PHASE 1: COMPLETE CODEBASE AUDIT

Before modifying anything, inspect the entire repository.

1. Understand the existing architecture, frameworks, dependencies, application entry points, routing, database configuration, authentication, APIs, and project structure.
2. Identify all implemented, partially implemented, missing, duplicated, broken, and unused features.
3. Inspect every page, component, modal, form, button, dropdown, table, filter, search field, navigation item, and action.
4. Inspect frontend-to-backend communication.
5. Inspect every API endpoint, controller, service, repository, middleware, and database operation.
6. Identify placeholder content, mock data, hardcoded business values, temporary workarounds, and simulated functionality.
7. Inspect database tables, relationships, indexes, constraints, migrations, and seed data.
8. Inspect package dependencies and resolve incompatible, outdated, vulnerable, or unnecessary packages where appropriate.
9. Identify console errors, server errors, failed network requests, TypeScript errors, build failures, and runtime warnings.
10. Identify performance bottlenecks, security weaknesses, data integrity risks, and architectural limitations.

Create a comprehensive audit report containing:

- Feature/module name.
- Current implementation status.
- Problems identified.
- Business impact.
- Required corrections.
- Tests required.
- Final verification status.

**Important:** Do not assume a feature works because its page exists or its button is visible.

---

# PHASE 2: COMPLETE BUSINESS FUNCTIONALITY

Audit and verify every module below.

## 2.1 Dashboard and Business Intelligence

Ensure the dashboard displays accurate, database-driven information, including:

- Total sales.
- Today's sales.
- Weekly and monthly sales.
- Total products.
- Total stock quantity.
- Low-stock products.
- Out-of-stock products.
- Inventory valuation.
- Purchase totals.
- Outstanding customer balances.
- Supplier payables.
- Expenses.
- Gross profit.
- Net profit.
- Recent transactions.
- Recent purchases.
- Sales performance charts.
- Best-selling products.
- Slow-moving products.
- Stock alerts.
- Financial summaries.
- Branch-specific performance.

Ensure dashboard figures are calculated from real transactions and respect user permissions, branch access, selected date ranges, and reporting filters.

Do not use static numbers to represent live business performance.

## 2.2 Product and Catalogue Management

Verify:

- Create, view, edit, archive, and delete products where deletion is safe.
- Unique product codes and SKUs.
- Barcode generation and scanning.
- Product categories and subcategories.
- Brands and manufacturers.
- Product descriptions and images.
- Cost price.
- Selling price.
- Wholesale price.
- Retail price.
- Minimum selling price and discount restrictions.
- Tax configuration.
- Product status.
- Reorder levels.
- Product variants.
- Units of measurement.
- Multiple packaging levels.
- Product search and filtering.
- Duplicate detection.
- Bulk import and export.
- Product price history.

Prevent invalid prices, duplicate identifiers, and inconsistent product records.

## 2.3 Inventory and Stock Control

Verify:

- Stock receipts.
- Stock adjustments.
- Stock transfers.
- Stock returns.
- Stock reservations where supported.
- Stock reconciliation.
- Opening balances.
- Damaged goods.
- Expired goods where applicable.
- Low-stock alerts.
- Out-of-stock alerts.
- Minimum and maximum stock levels.
- Inventory valuation.
- Stock movement history.
- Inventory audit trail.
- Warehouse-specific inventory.
- Branch-specific inventory.

Implement reliable stock transaction handling.

Never allow two simultaneous sales or transactions to silently consume the same available stock.

Prevent unauthorized negative stock and enforce configurable stock policies.

Ensure every stock change has a traceable source, reference, user, date, and reason.

## 2.4 Units of Measurement and Packaging

Support relevant hardware business units, such as:

- Piece.
- Packet.
- Box.
- Carton.
- Bag.
- Kilogram.
- Gram.
- Tonne.
- Litre.
- Millilitre.
- Metre.
- Centimetre.
- Foot.
- Roll.
- Bundle.
- Length.
- Sheet.

Support configurable conversion factors.

For example, where configured:

1 box = 12 pieces.

Ensure purchases, sales, stock balances, returns, and reports consistently use the correct base unit.

Never hardcode conversion assumptions for products that have different packaging specifications.

## 2.5 Point of Sale (POS)

Treat POS as one of the highest-priority modules.

Test the complete cashier workflow:

1. Open POS.
2. Select or scan products.
3. Add items to cart.
4. Change quantities.
5. Select appropriate units.
6. Apply permitted discounts.
7. Calculate subtotals.
8. Calculate applicable taxes.
9. Calculate the final payable amount.
10. Select customer or walk-in customer.
11. Select payment method.
12. Process full or split payments where supported.
13. Calculate cash received and change.
14. Process credit sales according to permissions and customer limits.
15. Complete the transaction.
16. Update stock.
17. Generate a unique transaction reference.
18. Generate an accurate receipt or invoice.
19. Print or export the receipt.
20. Verify the transaction in sales, inventory, finance, and reports.

Also verify:

- Held and resumed sales.
- Cart persistence where required.
- Product barcode scanning.
- Fast product search.
- Keyboard navigation.
- Cashier shifts.
- Opening cash.
- Cash withdrawals and deposits where supported.
- Shift reconciliation.
- Refunds.
- Sales returns.
- Voids and cancellations.
- Payment failures.
- Duplicate submission protection.
- Network interruption handling.
- Receipt reprinting.
- Customer credit sales.

POS must remain responsive and reliable during busy trading hours.

**Critical transaction requirements:**

- Use database transactions for sale completion.
- Lock or otherwise safely coordinate stock updates.
- Prevent duplicate sale submissions.
- Ensure payment records and sale records remain consistent.
- Do not deduct stock for failed or abandoned sales.
- Record all successful and reversed stock movements.
- Ensure refunds and returns reverse the correct financial and stock effects.
- Never trust totals calculated only by the browser; validate all prices, discounts, taxes, quantities, and totals on the server.

## 2.6 Sales and Invoicing

Verify:

- Sales listing.
- Sales details.
- Sales search.
- Sales filters.
- Sales status.
- Invoice generation.
- Invoice numbering.
- Payment status.
- Partial payments.
- Outstanding balances.
- Invoice printing.
- PDF generation.
- Email delivery where implemented.
- Sales returns.
- Refund records.
- Sales history.
- Customer statements.

Prevent incorrect invoice totals and duplicate financial records.

## 2.7 Procurement and Purchase Management

Verify:

- Purchase orders.
- Supplier selection.
- Purchase items.
- Purchase quantities.
- Unit conversions.
- Cost prices.
- Taxes and additional costs.
- Purchase approval where required.
- Goods Received Notes (GRNs).
- Partial deliveries.
- Remaining quantities.
- Purchase completion.
- Supplier invoices.
- Purchase payments.
- Purchase returns.
- Purchase history.
- Purchase reports.

Ensure stock increases only when goods are actually received and accepted according to the configured workflow.

Prevent duplicate goods receipt and duplicate supplier invoice processing.

## 2.8 Supplier Management

Verify:

- Supplier registration.
- Contact details.
- Supplier identification.
- Supplier status.
- Purchase history.
- Supplier balances.
- Amounts owed.
- Payments.
- Purchase returns.
- Supplier statements.
- Supplier-specific reporting.

## 2.9 Customer and Credit Management

Verify:

- Customer registration.
- Customer categories.
- Contact details.
- Customer history.
- Customer statements.
- Credit limits.
- Credit sales.
- Partial payments.
- Outstanding balances.
- Payment history.
- Overdue accounts.
- Customer account status.
- Returns and refunds.

Enforce credit limits and permissions on the server.

Prevent unauthorized users from overriding credit restrictions.

## 2.10 Payment Management

Verify all payment methods actually supported by the application, including:

- Cash.
- Mobile Money.
- Bank transfer.
- Card.
- Cheque.
- Credit.
- Split payments.

Ensure payment references, payment dates, amounts, transaction statuses, reversals, and reconciliation are recorded correctly.

Never mark an external payment as successful without confirmation from the relevant provider or a verified authorised manual process.

## 2.11 Expenses and Financial Management

Verify:

- Expense categories.
- Expense records.
- Expense approvals where applicable.
- Payment records.
- Cash inflows and outflows.
- Customer receivables.
- Supplier payables.
- Cost of goods sold.
- Gross profit.
- Net profit.
- Cash flow.
- Financial summaries.
- Financial reports.

Use accurate accounting calculations and consistent decimal precision.

Do not calculate profit using sales revenue alone.

Account for the appropriate cost of goods sold, returns, discounts, expenses, taxes, and other relevant financial adjustments.

Avoid treating revenue, cash received, and profit as interchangeable figures.

## 2.12 Warehouses, Branches, and Transfers

Verify:

- Multiple warehouses.
- Multiple business branches.
- Branch-specific inventory.
- Branch-specific users and permissions.
- Stock transfers.
- Transfer approvals.
- Dispatch records.
- Receiving records.
- In-transit stock.
- Partial transfer receipts.
- Transfer discrepancies.
- Branch reporting.

Ensure a transfer cannot accidentally create or destroy inventory.

## 2.13 Reports and Analytics

Verify all reports are based on real database records:

- Sales reports.
- Purchase reports.
- Inventory reports.
- Stock movement reports.
- Low-stock reports.
- Product performance.
- Profit and loss.
- Expense reports.
- Cash flow.
- Customer balances.
- Supplier balances.
- Tax reports.
- Payment reports.
- Cashier reports.
- Branch performance.

Support relevant filters, date ranges, sorting, pagination, printing, CSV export, and PDF export where implemented.

Verify report calculations independently against sample transactions.

## 2.14 User Management and Access Control

Implement and verify role-based access control.

Typical roles may include:

- Business Owner.
- Administrator.
- Manager.
- Accountant.
- Inventory Manager.
- Procurement Officer.
- Salesperson.
- Cashier.
- Auditor.

Verify:

- User registration and management.
- User activation and deactivation.
- Password changes.
- Password reset.
- Role assignment.
- Granular permissions.
- Branch restrictions.
- Session management.
- Login and logout.
- Failed-login handling.
- Account protection.
- Audit history.

Enforce authorization on the backend, not merely by hiding frontend buttons.

A user must not access restricted information by manually changing URLs or calling API endpoints.

## 2.15 Settings and Business Configuration

Verify:

- Business profile.
- Business name.
- Logo.
- Address.
- Contact information.
- Currency.
- Time zone.
- Date format.
- Tax settings.
- Invoice numbering.
- Receipt settings.
- Payment configuration.
- Branch settings.
- User preferences.
- Notification settings.
- Security settings.

Avoid hardcoding business identity, currency, tax rates, or operational settings.

---

# PHASE 3: DATABASE AND DATA INTEGRITY

XAMPP is installed on the development machine.

The application must run reliably with the existing MySQL/MariaDB environment while maintaining a clear migration path to PostgreSQL.

## 3.1 XAMPP and MySQL/MariaDB

Verify:

- Apache and MySQL/MariaDB startup.
- Correct database connection.
- Database creation and configuration.
- Table creation.
- Migrations.
- Seeders.
- Database constraints.
- Foreign keys.
- Unique indexes.
- Query performance.
- Database backups.
- Restore procedures.
- Connection failure handling.

Test the application against the actual local XAMPP environment.

Do not assume that a successful SQLite test proves MySQL/MariaDB compatibility.

## 3.2 PostgreSQL Migration Readiness

Design the data layer to support a future PostgreSQL migration with minimal application changes.

Verify:

- Database access is isolated from business logic.
- Queries do not depend unnecessarily on MySQL-only features.
- Database migrations are version-controlled.
- Money uses appropriate decimal/numeric types.
- Dates and timestamps are handled consistently.
- Foreign keys and constraints are portable where practical.
- Transactions are properly implemented.
- Database-specific SQL is isolated.
- Data export and migration procedures are documented.

If using an ORM, verify its actual MySQL/MariaDB and PostgreSQL compatibility.

Do not claim PostgreSQL support is tested until the application has actually been tested against PostgreSQL.

## 3.3 Data Integrity

Verify:

- No duplicate transaction identifiers.
- No orphaned records.
- No invalid foreign-key references.
- No accidental stock duplication.
- No unexplained negative stock.
- No duplicate payment records.
- No incorrect customer balances.
- No incorrect supplier balances.
- No inconsistent financial totals.
- No partial transactions caused by failed operations.

Use database transactions for operations involving multiple related records.

---

# PHASE 4: SECURITY AUDIT

Conduct a complete security review.

Verify:

1. Secure authentication.
2. Strong password hashing using an appropriate modern algorithm.
3. Secure session or token management.
4. HttpOnly, Secure, and appropriate SameSite cookie settings when using cookies.
5. CSRF protection where applicable.
6. SQL injection protection.
7. Cross-Site Scripting (XSS) prevention.
8. Input validation and sanitisation.
9. Server-side authorization.
10. Rate limiting.
11. Secure HTTP headers.
12. CORS restrictions.
13. File upload validation.
14. File size restrictions.
15. MIME-type and content validation.
16. Protection against malicious file uploads.
17. Safe error responses.
18. Environment variable protection.
19. No exposed secrets or API keys.
20. Dependency vulnerability review.
21. Audit logging.
22. Session expiry.
23. Protection against brute-force login attempts.
24. Sensitive information protection.
25. Secure production configuration.

Ensure passwords, tokens, secrets, and sensitive business information are never unnecessarily exposed in API responses or application logs.

Do not store production credentials in frontend source code or commit them to Git.

---

# PHASE 5: FRONTEND AND USER EXPERIENCE

Inspect every screen on:

- Mobile phones.
- Tablets.
- Laptops.
- Desktop monitors.

Ensure:

- Responsive layouts.
- Consistent navigation.
- Professional visual hierarchy.
- Consistent typography.
- Consistent spacing.
- Accessible colour contrast.
- Readable tables.
- Functional search.
- Functional filters.
- Pagination.
- Loading states.
- Empty states.
- Error states.
- Success feedback.
- Form validation.
- Confirmation dialogs.
- Modal behaviour.
- Keyboard accessibility.
- Accessible labels.
- Clear user feedback.

Every CRUD operation must provide appropriate feedback.

**Critical interaction policy:**

Before irreversible or potentially destructive actions, clearly inform the user and request confirmation.

Examples include:

- Deleting products.
- Deleting customers.
- Deleting suppliers.
- Cancelling sales.
- Voiding invoices.
- Removing users.
- Deleting stock records.
- Processing refunds.
- Reversing payments.
- Making significant stock adjustments.

Explain the action and its consequences before proceeding.

Use safe alternatives such as archive, deactivate, void, or reversal where financial and audit integrity requires historical records to remain available.

Prevent accidental double-click submissions.

Do not leave visible buttons that have no working action.

---

# PHASE 6: API AND BACKEND QUALITY

Inspect every endpoint.

Verify:

- Correct HTTP methods.
- Correct response status codes.
- Consistent response structures.
- Input validation.
- Authentication.
- Authorization.
- Error handling.
- Pagination.
- Search.
- Sorting.
- Filtering.
- Request size limits.
- Rate limiting.
- Transaction safety.
- Logging.
- API documentation.

Remove insecure test endpoints, debug routes, and unnecessary development-only code from production builds.

Never expose database stack traces, passwords, tokens, or internal implementation details to end users.

---

# PHASE 7: AUTOMATED TESTING AND QUALITY ASSURANCE

Create and run a meaningful test suite.

## 7.1 Unit Tests

Test:

- Calculations.
- Discounts.
- Tax calculations.
- Unit conversions.
- Stock calculations.
- Payment allocations.
- Customer balances.
- Supplier balances.
- Profit calculations.
- Permission checks.
- Validation rules.

## 7.2 Integration Tests

Test:

- Authentication.
- Product creation.
- Stock receipt.
- Stock adjustment.
- Purchase processing.
- Goods receipt.
- POS sale.
- Split payments.
- Credit sale.
- Returns.
- Refunds.
- Customer payment.
- Supplier payment.
- Expense recording.
- Stock transfers.
- Reports.

## 7.3 End-to-End Tests

Simulate complete business workflows:

**Workflow A: Procurement**

Create supplier → Create purchase order → Receive goods → Update inventory → Record supplier payable → Record payment → Verify reports.

**Workflow B: Cash Sale**

Open POS → Scan products → Add quantities → Calculate totals → Receive payment → Complete sale → Print receipt → Verify stock → Verify financial records.

**Workflow C: Credit Sale**

Select customer → Verify credit eligibility → Process credit sale → Update customer balance → Receive partial payment → Verify remaining balance.

**Workflow D: Sales Return**

Find original sale → Initiate return → Validate returned quantities → Approve refund or credit → Update inventory where appropriate → Verify financial records and audit history.

**Workflow E: Stock Transfer**

Create transfer → Approve → Dispatch → Receive → Verify source and destination inventory.

**Workflow F: Cashier Reconciliation**

Open shift → Process transactions → Record cash movements → Close shift → Reconcile expected and actual cash → Verify differences and audit records.

**Workflow G: User Permissions**

Log in as different roles → Attempt authorised actions → Attempt unauthorised actions → Verify backend restrictions.

Test both successful and unsuccessful scenarios.

## 7.4 Regression Testing

After fixing any defect, verify that related modules still work.

A correction in inventory must not break POS, purchases, reports, or financial calculations.

---

# PHASE 8: PERFORMANCE AND SCALABILITY

Evaluate:

- Initial page loading.
- Dashboard loading.
- Large product catalogues.
- Large sales histories.
- Database queries.
- API response times.
- Image optimisation.
- Lazy loading.
- Pagination.
- Caching where appropriate.
- Unnecessary React re-renders.
- Memory usage.
- Concurrent user activity.

Implement appropriate indexes, query optimisation, server-side pagination, and efficient data fetching.

Test realistic business volumes instead of relying only on a handful of sample records.

Do not introduce unnecessary caching that can cause incorrect stock or financial information.

---

# PHASE 9: BACKUP, RECOVERY, AND BUSINESS CONTINUITY

Implement and verify:

- Database backup procedures.
- Database restoration procedures.
- Backup scheduling where supported.
- Secure backup storage.
- Backup retention policies.
- Recovery documentation.
- File and document backup.
- Error logging.
- Operational monitoring.

Perform an actual backup-and-restore test.

A backup process is not verified simply because a backup command exists.

---

# PHASE 10: INTEGRATIONS AND UGANDA READINESS

Prepare the architecture for relevant external integrations.

Review:

- Uganda Shillings (UGX).
- Configurable VAT and other tax rules.
- Business-specific invoice information.
- Mobile Money integration readiness.
- Bank payment integration readiness.
- Email notifications.
- SMS notifications.
- Barcode scanners.
- Receipt printers.
- PDF generation.
- Uganda URA eFRIS integration readiness.

For eFRIS, separate the integration into a dedicated module or adapter.

Follow official URA documentation, credentials, authorisation, and certification requirements.

Do not fabricate API endpoints or claim a successful eFRIS integration without actual verification.

Do not hardcode tax rates or assume that all hardware products have identical tax treatment.

---

# PHASE 11: ERROR HANDLING AND APPLICATION STABILITY

Test:

- Database unavailable.
- Server unavailable.
- Invalid requests.
- Expired sessions.
- Insufficient stock.
- Duplicate transactions.
- Invalid payments.
- Failed uploads.
- Interrupted network connections.
- Missing records.
- Permission violations.
- Unexpected server exceptions.

Provide clear user-facing error messages and appropriate recovery instructions.

Ensure failures do not leave incomplete sales, corrupted inventory, or inconsistent financial records.

---

# PHASE 12: DEPLOYMENT AND PRODUCTION CONFIGURATION

Verify the application can be built and deployed using a documented production process.

Check:

- Production build.
- Environment configuration.
- Database connection.
- Database migrations.
- Secure secrets.
- HTTPS configuration.
- Production CORS.
- Logging.
- Error monitoring.
- Static asset handling.
- API routing.
- File storage.
- Database connection pooling where appropriate.
- Process management.
- Reverse proxy configuration where applicable.
- Health-check endpoint.
- Graceful shutdown.
- Deployment rollback procedure.

Ensure development configuration is not accidentally used in production.

Do not expose development credentials, sample accounts, debugging tools, or test data in a production environment.

---

# PHASE 13: DOCUMENTATION

Update documentation to reflect the actual implementation.

Provide:

1. Professional README.
2. Installation guide.
3. XAMPP setup guide.
4. Environment variable reference.
5. Database setup instructions.
6. Database migration guide.
7. PostgreSQL migration readiness guide.
8. API documentation.
9. System architecture documentation.
10. Security documentation.
11. Backup and recovery guide.
12. Deployment guide.
13. User guide.
14. Troubleshooting guide.
15. Known limitations and integration requirements.

Do not document imaginary functionality.

Clearly distinguish implemented features from planned features and integrations requiring external approval or credentials.

---

# PHASE 14: FINAL EXECUTION AND VERIFICATION

After completing the audit and corrections:

1. Install or verify dependencies.
2. Run type checking.
3. Run linting.
4. Run unit tests.
5. Run integration tests.
6. Run end-to-end tests.
7. Run the production build.
8. Start the application.
9. Connect it to the actual XAMPP database.
10. Test all critical workflows.
11. Review server and browser logs.
12. Verify there are no unresolved critical errors.
13. Verify database consistency.
14. Verify backup restoration.
15. Verify production environment configuration.

Do not stop after identifying issues. Fix them systematically and retest the affected functionality.

If a task requires external credentials, a physical device, an unavailable third-party service, or an environment that is not accessible, document the dependency and provide a precise verification procedure. Do not pretend it was tested.

---

# PHASE 15: FINAL PRODUCTION READINESS SCORECARD

Produce a final report with these categories:

| Area           | Required verification                             |
| -------------- | ------------------------------------------------- |
| Architecture   | Maintainable and correctly structured             |
| Frontend       | All pages and interactions functional             |
| Backend        | APIs secure and reliable                          |
| Database       | Consistent and transaction-safe                   |
| XAMPP          | Verified MySQL/MariaDB operation                  |
| PostgreSQL     | Migration readiness verified to the extent tested |
| POS            | Complete sales workflow verified                  |
| Inventory      | Accurate stock tracking                           |
| Procurement    | Complete purchasing workflow                      |
| Customers      | Accurate balances and credit controls             |
| Suppliers      | Accurate purchasing and payable records           |
| Finance        | Reliable financial calculations                   |
| Reporting      | Accurate database-driven reports                  |
| Authentication | Secure login and sessions                         |
| Authorisation  | Backend-enforced RBAC                             |
| Security       | Security audit and remediation                    |
| UX             | Responsive and accessible                         |
| Performance    | Tested under realistic workloads                  |
| Testing        | Automated tests executed                          |
| Backup         | Actual backup and restore verified                |
| Deployment     | Production build and deployment process verified  |
| Documentation  | Complete and accurate                             |

Assign each category one of the following statuses:

- **PASS:** Implemented and successfully verified.
- **PARTIAL:** Implemented but not fully verified or incomplete.
- **FAIL:** Broken, missing, insecure, or incorrectly implemented.
- **BLOCKED:** Requires an external dependency or unavailable environment.
- **NOT APPLICABLE:** Not relevant to the actual system scope.

For every PARTIAL, FAIL, or BLOCKED item, explain the reason, business impact, and remaining work.

Calculate the completion percentage based on verified applicable requirements, not the number of pages or components created.

Do not award a PASS simply because code exists.

---

# STRICT DEVELOPMENT RULES

1. Work with the existing codebase.
2. Do not unnecessarily replace the existing framework or architecture.
3. Do not remove working features to make implementation easier.
4. Do not redesign the entire application unless there is a demonstrated technical or usability reason.
5. Do not replace real database operations with localStorage or mock data.
6. Do not use hardcoded values where business configuration or database records should be used.
7. Do not leave TODOs, placeholder buttons, fake charts, or simulated transactions in critical workflows.
8. Do not bypass validation or permissions to make a test pass.
9. Do not silently discard historical business records.
10. Do not allow financial or inventory operations to bypass transaction integrity.
11. Do not expose sensitive information.
12. Do not introduce unnecessary dependencies.
13. Do not break existing functionality.
14. Use reusable components, services, hooks, and clear separation of concerns.
15. Follow consistent coding standards and meaningful naming conventions.
16. Maintain proper TypeScript types and avoid careless use of `any`.
17. Use accessible and responsive UI patterns.
18. Provide confirmation before destructive actions.
19. Record critical business activities in audit logs.
20. Document all important architectural and database changes.

**Work in manageable phases. Maintain a record of completed tasks, outstanding issues, changed files, migrations, tests, and any blockers.**

Before destructive database operations or large structural changes, preserve the existing data and establish a rollback path.

---

# FINAL ACCEPTANCE CRITERIA

The application is ready for production release only when:

- Critical and high-severity defects have been resolved.
- Core business workflows have passed end-to-end testing.
- POS transactions are reliable and transaction-safe.
- Inventory and financial records remain consistent.
- Backend authentication and permissions are enforced.
- Sensitive data and application secrets are protected.
- The application builds successfully for production.
- XAMPP/MySQL or MariaDB operation has been verified.
- Backup and restoration have been tested.
- Important user-facing features are functional.
- Documentation matches the actual application.
- Deployment procedures are documented and tested to the extent possible.

A successful build alone does not mean the system is production-ready.

A visually complete interface does not mean the business workflows are functional.

A working demo does not prove security, reliability, or data integrity.

**Never claim 100% production readiness without evidence.**

The final objective is a stable, secure, fully functional, professionally engineered Hardware Management System that can confidently support real business operations.

## REQUIRED FINAL DELIVERABLES

At completion, provide:

1. Executive production-readiness report.
2. Full audit checklist with PASS, PARTIAL, FAIL, BLOCKED, and NOT APPLICABLE statuses.
3. List of all defects identified and resolved.
4. List of files created, modified, or removed.
5. Database changes and migration details.
6. Security improvements.
7. Test results with actual execution summaries.
8. POS and critical workflow verification results.
9. XAMPP/MySQL/MariaDB verification results.
10. PostgreSQL migration readiness assessment.
11. Performance and deployment assessment.
12. Backup and restoration test results.
13. Outstanding issues and external dependencies.
14. Final verified completion percentage.
15. Exact commands for installing, running, testing, building, and deploying the application.

**START NOW: Inspect the existing project first, create the audit report, then systematically implement, test, and verify every required improvement. Do not stop at planning or recommendations.**
