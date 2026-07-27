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

<img width="1422" height="778" alt="image" src="https://github.com/user-attachments/assets/46e03fa8-f0d1-4187-8386-5a939ee32745" />
<img width="1424" height="778" alt="image" src="https://github.com/user-attachments/assets/059f03d7-55ba-4ee0-b8fe-9f6e0d5147ec" />
<img width="1422" height="779" alt="image" src="https://github.com/user-attachments/assets/de6869db-571c-41a4-8f30-d9899cb24415" />
# Exercise 1: Initialize Microsoft 365 Tenant

<img width="1426" height="764" alt="image" src="https://github.com/user-attachments/assets/69e36982-ef16-4110-b5e5-e0a0d0f06142" />
<img width="1429" height="779" alt="image" src="https://github.com/user-attachments/assets/5dbfe48d-91b1-4200-9389-0e0afa69465f" />
<img width="1424" height="774" alt="image" src="https://github.com/user-attachments/assets/419d5ffe-ef12-4e97-8def-6e9d627aaef3" />
<img width="1422" height="777" alt="image" src="https://github.com/user-attachments/assets/dc304793-973d-42ac-a89b-5cce916d1ff9" />
<img width="1424" height="778" alt="image" src="https://github.com/user-attachments/assets/f99a9ad3-cccc-4ced-a149-478e4731997a" />
<img width="1427" height="778" alt="image" src="https://github.com/user-attachments/assets/df26baeb-ded4-4c2e-a60f-03fac1907755" />
<img width="1427" height="780" alt="image" src="https://github.com/user-attachments/assets/efd89b80-4cbd-4afa-9e5b-881c92a7b185" />
<img width="1416" height="764" alt="image" src="https://github.com/user-attachments/assets/7515391a-7eab-45df-b003-a64cfde0c1cd" />
<img width="1414" height="776" alt="image" src="https://github.com/user-attachments/assets/6042e1f9-d4bd-4ed8-aa27-67fc827179c0" />
## Overview
This exercise covers the initialization and security hardening of a Microsoft 365 tenant. It includes essential configuration steps for setting up organizational compliance, password policies, and security features to ensure a secure cloud environment.

<img width="1423" height="776" alt="image" src="https://github.com/user-attachments/assets/81db1100-e05f-459f-a8e5-0bfd85b0bf19" />
<img width="1430" height="782" alt="image" src="https://github.com/user-attachments/assets/d9186a94-20c3-4168-a007-60ee441ae1e8" />
<img width="1425" height="780" alt="image" src="https://github.com/user-attachments/assets/088091a8-94f7-4c87-b43e-dec3ccec71cf" />


<img width="1424" height="858" alt="image" src="https://github.com/user-attachments/assets/3958ef21-359b-48cd-8cd6-bbabebaf11b9" />
<img width="1417" height="858" alt="image" src="https://github.com/user-attachments/assets/9ca532e5-d6b1-4068-bce9-c0ad17f11cce" />
<img width="1420" height="837" alt="image" src="https://github.com/user-attachments/assets/e91d71f3-50b9-49ab-a2f3-8201320230fc" />
<img width="1417" height="835" alt="image" src="https://github.com/user-attachments/assets/7733011e-9812-46a8-8c27-6e4d5ab16700" />
<img width="1423" height="857" alt="image" src="https://github.com/user-attachments/assets/aa484880-369a-4b14-9f07-7ea6a62fe03a" />
