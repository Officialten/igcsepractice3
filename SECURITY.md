# Security Measures

This document outlines the security measures implemented in the IGCSE Practice Platform.

## Authentication & Authorization

### Password Security
- ✅ Passwords hashed using bcrypt with salt rounds of 10
- ✅ Minimum password length: 6 characters
- ✅ Passwords never exposed in API responses
- ✅ JWT tokens for session management
- ✅ Token expiration implemented

### Access Control
- ✅ Role-based access control (User/Admin)
- ✅ Protected routes require authentication
- ✅ Admin routes require admin role verification
- ✅ User can only access their own data
- ✅ Unauthorized access attempts are logged

## Input Validation & Sanitization

### Data Validation
- ✅ Email validation using express-validator
- ✅ Username validation (min 3 characters, lowercase, trimmed)
- ✅ Password validation (min 6 characters)
- ✅ NoSQL injection prevention using express-mongo-sanitize
- ✅ Input sanitization on all user inputs

### File Upload Security
- ✅ File type validation (extension + MIME type)
- ✅ File size limits (10MB max)
- ✅ Secure file naming (timestamp + random number)
- ✅ Files stored outside web root
- ✅ Only allowed file types: PDF, DOC, DOCX, PPT, PPTX

## Rate Limiting & DDoS Protection

### Rate Limits
- ✅ General API: 100 requests per 15 minutes per IP
- ✅ Login endpoint: 5 attempts per 15 minutes per IP
- ✅ Registration endpoint: 5 attempts per 15 minutes per IP
- ✅ Prevents brute force attacks

## HTTP Security Headers

### Helmet.js Protection
- ✅ XSS Protection
- ✅ Content Security Policy
- ✅ DNS Prefetch Control
- ✅ Frame Guard (clickjacking protection)
- ✅ HSTS (HTTP Strict Transport Security)
- ✅ IE No Open
- ✅ No Sniff
- ✅ Referrer Policy

## Data Privacy

### User Data Protection
- ✅ Passwords never stored in plain text
- ✅ Sensitive fields excluded from API responses
- ✅ User can only view their own progress
- ✅ Email verification required
- ✅ Verification codes expire after 24 hours

### Database Security
- ✅ MongoDB connection with authentication
- ✅ Environment variables for sensitive data
- ✅ .env file excluded from version control
- ✅ NoSQL injection prevention

## CORS & Cross-Origin Security

### CORS Configuration
- ✅ Restricted to specific origins
- ✅ Credentials support enabled
- ✅ Production/development environment separation

## File System Security

### Uploaded Files
- ✅ Files stored in dedicated upload directory
- ✅ Unique filenames prevent overwrites
- ✅ File cleanup on failed operations
- ✅ Old files deleted when updated/removed

## Environment Variables

### Required Security Variables
```
JWT_SECRET=<strong-random-secret>  # MUST be changed from default
MONGODB_URI=<database-connection>
SENDGRID_API_KEY=<email-service-key>
OPENROUTER_API_KEY=<ai-service-key>
```

⚠️ **CRITICAL**: Never commit .env file to version control!

## Security Best Practices

### For Developers
1. Always validate and sanitize user input
2. Use parameterized queries (Mongoose does this)
3. Keep dependencies updated
4. Review code for security vulnerabilities
5. Use HTTPS in production
6. Implement proper error handling (don't expose stack traces)
7. Log security events
8. Regular security audits

### For Deployment
1. Change all default secrets
2. Use environment variables for configuration
3. Enable HTTPS/SSL
4. Set up firewall rules
5. Regular backups
6. Monitor for suspicious activity
7. Keep server and dependencies updated
8. Use strong database passwords

## Known Limitations

1. Email verification codes are 6 digits (consider longer codes for production)
2. File uploads limited to 10MB (adjust based on needs)
3. Rate limiting is IP-based (consider user-based for authenticated routes)

## Reporting Security Issues

If you discover a security vulnerability, please email: [security@example.com]

**DO NOT** create public GitHub issues for security vulnerabilities.

## Compliance

- GDPR considerations: Users can request data deletion
- Data minimization: Only collect necessary information
- Right to access: Users can view their own data
- Secure data storage: Encrypted passwords, secure file storage

## Regular Security Tasks

- [ ] Update dependencies monthly
- [ ] Review access logs weekly
- [ ] Audit user permissions quarterly
- [ ] Security penetration testing annually
- [ ] Backup verification monthly

---

Last Updated: November 2025
