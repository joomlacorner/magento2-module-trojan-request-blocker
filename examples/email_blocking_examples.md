# Email Blocking Examples

This document demonstrates how the fake user registration restriction feature blocks both email domains and specific email addresses.

## Configuration Examples

### Blocked Email Domains
```
temp-mail.org
10minutemail.com
guerrillamail.com
mailinator.com
tempmail.com
throwaway.email
fakeinbox.com
sharklasers.com
getairmail.com
mailnesia.com
```

### Blocked Email Addresses
```
test@example.com
fake@domain.com
admin@test.com
user@fake.org
demo@example.net
```

## How It Works

### 1. Specific Email Address Blocking
The system first checks if the exact email address is in the blocked list:

- ✅ `test@example.com` → **BLOCKED** (exact match)
- ✅ `fake@domain.com` → **BLOCKED** (exact match)
- ❌ `john@example.com` → **ALLOWED** (not in blocked list)

### 2. Email Domain Blocking
If the specific email is not blocked, the system then checks the domain:

- ✅ `user@temp-mail.org` → **BLOCKED** (domain blocked)
- ✅ `customer@subdomain.temp-mail.org` → **BLOCKED** (subdomain of blocked domain)
- ✅ `test@10minutemail.com` → **BLOCKED** (domain blocked)
- ❌ `user@legitimate.com` → **ALLOWED** (domain not blocked)

### 3. Priority Order
1. **Specific Email Address Check** (highest priority)
2. **Email Domain Check** (if specific address not blocked)

## Real-World Examples

### Blocked Registrations:
```
Email: test@example.com          → BLOCKED (specific address)
Email: fake@domain.com           → BLOCKED (specific address)
Email: user@temp-mail.org        → BLOCKED (domain)
Email: customer@10minutemail.com → BLOCKED (domain)
Email: admin@sub.temp-mail.org   → BLOCKED (subdomain)
```

### Allowed Registrations:
```
Email: john@example.com          → ALLOWED (domain allowed)
Email: customer@legitimate.com   → ALLOWED (domain allowed)
Email: user@company.org          → ALLOWED (domain allowed)
```

## Admin Configuration

In the Magento admin panel:
1. Go to **Stores > Configuration > System > Fake User Registration Restriction**
2. Enable the feature
3. Add blocked email domains (one per line)
4. Add blocked email addresses (one per line)
5. Save configuration

## Benefits

- **Granular Control**: Block specific problematic email addresses
- **Domain Protection**: Block entire domains known for fake emails
- **Flexible**: Easy to add/remove blocked entries via admin panel
- **Case Insensitive**: Works regardless of email case
- **Subdomain Support**: Automatically blocks subdomains of blocked domains
