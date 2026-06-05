# Database Design

## Tables

### users
| Column | Type | Description |
|--------|------|-------------|
| id | UUID | Primary key |
| name | VARCHAR | Full name |
| email | VARCHAR | Unique email |
| phone | VARCHAR | Phone number |
| password_hash | VARCHAR | Hashed password |
| role | ENUM | donor, patient, admin |
| is_verified | BOOLEAN | Identity verified |
| created_at | TIMESTAMP | - |
| updated_at | TIMESTAMP | - |

### donors
| Column | Type | Description |
|--------|------|-------------|
| id | UUID | Primary key |
| user_id | UUID | FK → users |
| blood_type | ENUM | A, B, AB, O |
| rhesus | ENUM | positive, negative |
| last_donated_at | DATE | Last donation date |
| is_available | BOOLEAN | Ready to donate |
| city | VARCHAR | Current city |
| qr_code | VARCHAR | QR code string |

### blood_requests
| Column | Type | Description |
|--------|------|-------------|
| id | UUID | Primary key |
| requester_id | UUID | FK → users |
| blood_type | ENUM | A, B, AB, O |
| rhesus | ENUM | positive, negative |
| quantity | INTEGER | Bags needed |
| hospital | VARCHAR | Hospital name |
| city | VARCHAR | City |
| status | ENUM | pending, matched, fulfilled, cancelled |
| is_urgent | BOOLEAN | Urgent flag |
| created_at | TIMESTAMP | - |

### donations
| Column | Type | Description |
|--------|------|-------------|
| id | UUID | Primary key |
| donor_id | UUID | FK → donors |
| request_id | UUID | FK → blood_requests |
| status | ENUM | accepted, completed, cancelled |
| donated_at | TIMESTAMP | - |
| delivered_to_patient | BOOLEAN | Impact tracking |

### blood_stocks
| Column | Type | Description |
|--------|------|-------------|
| id | UUID | Primary key |
| institution_id | UUID | FK → users (admin) |
| blood_type | ENUM | A, B, AB, O |
| rhesus | ENUM | positive, negative |
| quantity | INTEGER | Current stock |
| updated_at | TIMESTAMP | - |

### notifications
| Column | Type | Description |
|--------|------|-------------|
| id | UUID | Primary key |
| user_id | UUID | FK → users |
| type | ENUM | urgent, reminder, info |
| title | VARCHAR | Notif title |
| body | TEXT | Notif content |
| is_read | BOOLEAN | Read status |
| created_at | TIMESTAMP | - |