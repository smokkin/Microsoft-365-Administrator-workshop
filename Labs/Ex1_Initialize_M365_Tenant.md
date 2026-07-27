# Exercise 1: Initialize Microsoft 365 Tenant

## Overview
This exercise covers the initialization and security hardening of a Microsoft 365 tenant. It includes essential configuration steps for setting up organizational compliance, password policies, and security features to ensure a secure cloud environment.

---

## Table of Contents
1. [Task 1: Tenant Initial Setup](#task-1-tenant-initial-setup)
2. [Task 2: Password Policy Configuration](#task-2-password-policy-configuration)
3. [Task 3: Security Defaults and MFA](#task-3-security-defaults-and-mfa)
4. [Task 4: Conditional Access Setup](#task-4-conditional-access-setup)

---

## Task 1: Tenant Initial Setup

### Objectives
- Access the Microsoft 365 admin center
- Verify tenant information and settings
- Configure basic organizational settings

### Steps

1. **Navigate to Microsoft 365 Admin Center**
   - URL: `https://admin.microsoft.com`
   - Sign in with global administrator credentials

2. **Verify Tenant Configuration**
   - Go to **Settings** > **Org settings**
   - Review tenant name, organization profile, and contact information
   - Ensure correct domain information is displayed

3. **Configure Organization Profile**
   - Set organization name and primary domain
   - Configure contact information for important notifications
   - Review and update privacy settings

### Security Considerations
- Ensure only authorized administrators have access to the admin center
- Monitor admin center login attempts
- Document all configuration changes for audit purposes

---

## Task 2: Password Policy Configuration

### Objectives
- Implement strong password policies
- Configure password expiration settings
- Enable password history to prevent reuse

### Security Task Details

#### Password Policy Settings

**Implement the following password requirements:**

| Setting | Value | Purpose |
|---------|-------|---------|
| **Minimum Password Length** | 8 characters | Ensures passwords meet minimum complexity standards |
| **Password Expiration** | 90 days | Forces regular password updates to reduce risk of compromised credentials |
| **Password History** | Last 5 passwords | Prevents users from reusing recent passwords |
| **Special Characters Requirement** | Required | Increases password complexity and resistance to brute-force attacks |

#### Configuration Steps

1. **Access Password Policy Settings**
   - Navigate to **Settings** > **Security & privacy** > **Password policy**
   - Alternatively, use Azure AD admin center > **User settings** > **Password policy**

2. **Configure Password Requirements**
   - Enable **Enforce password history**: Prevent reuse of last 5 passwords
   - Set **Password expiration period**: 90 days
   - Set **Minimum password length**: 8 characters minimum
   - Enable **Password complexity requirements**: Require uppercase, lowercase, numbers, and special characters

3. **Apply Settings**
   - Click **Save** to apply policy across the organization
   - Policy applies to all new password changes and resets

#### Security Benefits
- **Reduced Risk of Account Compromise**: Regular password changes limit exposure window
- **Enhanced Credential Strength**: Complex password requirements prevent dictionary attacks
- **Audit Trail**: Password history tracking helps identify unauthorized access patterns
- **Compliance**: Meets industry standards (NIST, ISO 27001) for password policies

---

## Task 3: Security Defaults and Multi-Factor Authentication (MFA)

### Objectives
- Enable Microsoft 365 security defaults
- Configure multi-factor authentication requirements
- Ensure all users utilize MFA for account protection

### Security Task Details

#### Security Defaults Configuration

**What are Security Defaults?**
Security defaults provide a set of pre-configured security settings that protect your organization against common identity-based attacks:

- Enforce MFA for all users
- Block legacy authentication protocols
- Require secure sign-in for risky operations
- Disable app passwords (legacy authentication)

#### Implementation Steps

1. **Enable Security Defaults in Azure AD**
   - Navigate to Azure Active Directory admin center: `https://aad.portal.azure.com`
   - Go to **Properties** > **Manage security defaults**
   - Toggle **Security defaults enabled** to **Yes**
   - Click **Save**

2. **Multi-Factor Authentication Setup**
   - **Authentication Methods Available:**
     - Microsoft Authenticator app
     - Windows Hello for Business
     - FIDO2 security keys
     - SMS (less secure, not recommended as primary)

3. **User Enrollment**
   - Users are prompted to set up MFA on next login
   - Enforce MFA for all user accounts, including service accounts where applicable
   - Provide clear communication and training for users

#### Security Considerations
- **Legacy Authentication Blocking**: Prevents attackers from exploiting older, less secure protocols
- **Risk-Based Authentication**: Azure AD detects unusual sign-in patterns and requires additional verification
- **Phishing Resistance**: Security keys and Windows Hello provide phishing-resistant authentication

---

## Task 4: Conditional Access Setup

### Objectives
- Configure conditional access policies
- Restrict access based on device compliance
- Enforce security requirements for sensitive resources

### Security Task Details

#### Conditional Access Policies

**Policy 1: Require Compliant Devices for Sensitive Resources**
- **Target**: All users accessing SharePoint Online
- **Condition**: Device must be marked as compliant
- **Action**: Block access to non-compliant devices or require device registration

**Policy 2: Block Legacy Authentication**
- **Target**: All cloud applications
- **Condition**: Legacy authentication protocols detected
- **Action**: Block access

**Policy 3: Require MFA for Admin Access**
- **Target**: Global administrators and security administrators
- **Condition**: Admin portal access
- **Action**: Require multi-factor authentication

#### Implementation Steps

1. **Navigate to Conditional Access**
   - Azure AD admin center > **Security** > **Conditional Access**
   - Click **New policy**

2. **Create a Policy (Example: Require Compliant Devices)**
   - **Name**: "Require Compliant Devices - SharePoint Online"
   - **Assignments**:
     - Users: All users (or specific groups)
     - Cloud apps: SharePoint Online
     - Conditions: Device compliance = Required
   - **Access Controls**:
     - Grant: Require device to be marked as compliant
   - **Enable policy**: Set to **Report-only** (test phase) → **On** (enforcement)

3. **Monitor and Audit**
   - Review sign-in logs for policy impact
   - Adjust policies based on organizational needs
   - Document all policy changes

#### Security Benefits
- **Device Compliance Enforcement**: Only trusted devices access critical resources
- **Legacy Protocol Blocking**: Eliminates vulnerable authentication methods
- **Risk Mitigation**: Adaptive authentication based on sign-in risk
- **Zero Trust Model**: Implements principle of least privilege

---

## Verification Checklist

- [ ] Password policy applied to all users
- [ ] Security defaults enabled
- [ ] MFA configured and users enrolled
- [ ] Conditional access policies created and tested
- [ ] Admin accounts secured with MFA
- [ ] Sign-in logs monitored
- [ ] Documentation completed
- [ ] User training provided

---

## Best Practices

1. **Phase Implementation**: Deploy security features in stages (pilot → organization)
2. **Monitor Adoption**: Track MFA enrollment rates and security baseline compliance
3. **Regular Audits**: Review conditional access policies and security settings monthly
4. **User Communication**: Clearly communicate security requirements and training to users
5. **Backup Admin Accounts**: Maintain backup global administrator accounts with hardware security keys
6. **Documentation**: Keep detailed records of all security configurations and changes

---

## References

- [Microsoft 365 Admin Center Documentation](https://docs.microsoft.com/en-us/microsoft-365/admin/)
- [Azure AD Security Best Practices](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/identity-fundamental-principles)
- [Conditional Access in Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/)
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)

---

**Last Updated**: July 27, 2026  
**Status**: Complete
