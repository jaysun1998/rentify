# AppFolio Data Model for Europe

## 1. Property Entity

Stores details about each property in the system, including residential, commercial, and mixed-use properties.

| Field            | Data Type   | Description                                                       |
|------------------|-------------|-------------------------------------------------------------------|
| `property_id`    | Integer     | Unique identifier for the property.                               |
| `address`        | String      | Property address (localized for European format).                 |
| `city`           | String      | City name.                                                         |
| `country_id`     | Integer     | Foreign key to the `Country` entity.                              |
| `property_type`  | Enum        | Residential, Commercial, Mixed-use, etc.                           |
| `owner_id`       | Integer     | Foreign key to the `User` entity (Property Owner/Manager).         |
| `size`           | Float       | Property size (in square meters).                                 |
| `total_units`    | Integer     | Total number of units in the property.                            |
| `status`         | Enum        | Active, Inactive, Under Maintenance, etc.                          |
| `created_at`     | DateTime    | Timestamp of when the property was created.                       |
| `updated_at`     | DateTime    | Timestamp of last property update.                                |

## 2. Tenant Entity

Stores information about tenants renting units within properties.

| Field            | Data Type   | Description                                                       |
|------------------|-------------|-------------------------------------------------------------------|
| `tenant_id`      | Integer     | Unique identifier for the tenant.                                 |
| `first_name`     | String      | Tenant's first name.                                               |
| `last_name`      | String      | Tenant's last name.                                                |
| `email`          | String      | Tenant's email address.                                            |
| `phone_number`   | String      | Tenant's phone number.                                             |
| `date_of_birth`  | Date        | Tenant's date of birth (for age verification, etc.).               |
| `address`        | String      | Tenant's current address (if different from the property).         |
| `national_id`    | String      | National identification number (e.g., Social Security Number).    |
| `created_at`     | DateTime    | Timestamp of tenant creation.                                      |
| `updated_at`     | DateTime    | Timestamp of last update.                                          |

## 3. Lease Entity

Represents the lease contract between a tenant and a property. Tracks rental periods, deposits, and terms.

| Field            | Data Type   | Description                                                       |
|------------------|-------------|-------------------------------------------------------------------|
| `lease_id`       | Integer     | Unique identifier for the lease.                                  |
| `tenant_id`      | Integer     | Foreign key to the `Tenant` entity.                               |
| `property_id`    | Integer     | Foreign key to the `Property` entity.                             |
| `start_date`     | Date        | Lease start date.                                                  |
| `end_date`       | Date        | Lease end date.                                                    |
| `rent_amount`    | Float       | Monthly rent amount.                                               |
| `deposit_amount` | Float       | Deposit amount paid by the tenant.                                 |
| `lease_type`     | Enum        | Fixed Term, Month-to-Month, Commercial, etc.                       |
| `status`         | Enum        | Active, Ended, Terminated, etc.                                    |
| `renewal_option` | Boolean     | Whether the lease is renewable.                                    |
| `created_at`     | DateTime    | Timestamp of lease creation.                                       |
| `updated_at`     | DateTime    | Timestamp of last lease update.                                    |

## 4. Payment Entity

Tracks all payments made by tenants, linked to specific leases.

| Field            | Data Type   | Description                                                       |
|------------------|-------------|-------------------------------------------------------------------|
| `payment_id`     | Integer     | Unique identifier for the payment.                                |
| `tenant_id`      | Integer     | Foreign key to the `Tenant` entity.                               |
| `lease_id`       | Integer     | Foreign key to the `Lease` entity.                                |
| `amount`         | Float       | Amount of the payment made.                                       |
| `currency`       | String      | Currency used (e.g., EUR, GBP).                                   |
| `payment_method` | Enum        | Credit Card, Bank Transfer, SEPA, PayPal, etc.                    |
| `payment_status` | Enum        | Pending, Completed, Failed.                                       |
| `payment_date`   | DateTime    | Date and time of the payment.                                     |
| `invoice_id`     | Integer     | Foreign key to the `Invoice` entity.                              |

## 5. Maintenance Request Entity

Tracks tenant-initiated maintenance requests.

| Field            | Data Type   | Description                                                       |
|------------------|-------------|-------------------------------------------------------------------|
| `request_id`     | Integer     | Unique identifier for the request.                                |
| `tenant_id`      | Integer     | Foreign key to the `Tenant` entity.                               |
| `property_id`    | Integer     | Foreign key to the `Property` entity.                             |
| `description`    | String      | Description of the issue.                                         |
| `status`         | Enum        | Open, In Progress, Closed, Pending, etc.                           |
| `created_at`     | DateTime    | Timestamp of request creation.                                    |
| `updated_at`     | DateTime    | Timestamp of last update.                                         |

## 6. Service Provider Entity

Tracks external service providers handling maintenance requests.

| Field            | Data Type   | Description                                                       |
|------------------|-------------|-------------------------------------------------------------------|
| `provider_id`    | Integer     | Unique identifier for the service provider.                       |
| `name`           | String      | Name of the service provider.                                     |
| `service_type`   | Enum        | Electrician, Plumber, HVAC, etc.                                  |
| `contact_info`   | String      | Provider's contact information.                                   |
| `rating`         | Float       | Average rating (e.g., 4.5/5).                                      |
| `created_at`     | DateTime    | Timestamp of provider registration.                               |

## 7. Invoice Entity

Represents the invoices associated with payments.

| Field            | Data Type   | Description                                                       |
|------------------|-------------|-------------------------------------------------------------------|
| `invoice_id`     | Integer     | Unique identifier for the invoice.                                |
| `tenant_id`      | Integer     | Foreign key to the `Tenant` entity.                               |
| `lease_id`       | Integer     | Foreign key to the `Lease` entity.                                |
| `amount`         | Float       | Total amount of the invoice.                                      |
| `currency`       | String      | Currency used for invoicing.                                      |
| `tax`            | Float       | Tax applied to the invoice.                                        |
| `due_date`       | Date        | Invoice due date.                                                 |
| `status`         | Enum        | Paid, Pending, Overdue, etc.                                      |
| `created_at`     | DateTime    | Timestamp of invoice creation.                                    |

## 8. Country Entity

Supports multi-country compliance with data protection laws (GDPR) and other regional tax rules.

| Field            | Data Type   | Description                                                       |
|------------------|-------------|-------------------------------------------------------------------|
| `country_id`     | Integer     | Unique identifier for the country.                                |
| `name`           | String      | Name of the country (e.g., France, Germany, UK).                  |
| `currency`       | String      | Default currency for the country (e.g., EUR, GBP).                |
| `vat_rate`       | Float       | VAT rate for the country (if applicable).                         |
| `tax_code`       | String      | Country-specific tax code for invoicing.                          |
| `created_at`     | DateTime    | Timestamp of country registration.                                |

## 9. User Entity

Tracks users accessing the system, such as property managers, admins, and tenants.

| Field            | Data Type   | Description                                                       |
|------------------|-------------|-------------------------------------------------------------------|
| `user_id`        | Integer     | Unique identifier for the user.                                   |
| `first_name`     | String      | User's first name.                                                 |
| `last_name`      | String      | User's last name.                                                  |
| `email`          | String      | User's email address.                                              |
| `role`           | Enum        | Admin, Property Manager, Tenant, etc.                             |
| `country_id`     | Integer     | Foreign key to the `Country` entity (for locale and compliance).  |
| `created_at`     | DateTime    | Timestamp of user registration.                                   |

## 10. Audit Logs Entity

Stores logs of any system changes for security and compliance.

| Field            | Data Type   | Description                                                       |
|------------------|-------------|-------------------------------------------------------------------|
| `log_id`         | Integer     | Unique log identifier.                                            |
| `user_id`        | Integer     | Foreign key to `User` entity (who made the change).               |
| `action`         | String      | Description of the action (e.g., "Added property", "Updated lease"). |
| `timestamp`      | DateTime    | Timestamp of when the action occurred.                            |

---

## Relationships

- **Property ↔ Lease → Tenant**: One Property can have many leases; one Tenant can have many leases.
- **Lease ↔ Payment**: One Lease generates multiple payments.
- **Tenant ↔ Maintenance Request → Service Provider**: A Tenant can create multiple Maintenance Requests handled by Service Providers.
- **Payment ↔ Invoice**: Each Payment can correspond to an Invoice.
- **Tax ↔ Payment**: Payments are taxed according to the Country’s tax code.

---

This data model is designed to support **multi-currency**, **regional compliance**, and the unique needs of **property managers** in Europe. Let me know if you need any further changes!
