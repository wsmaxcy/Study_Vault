## Overview
VoilaNorbert is a tool that helps you find and verify email addresses. It's widely used for lead generation, email outreach, and gathering contact information. VoilaNorbert offers both a web interface and an API for integrating email finding capabilities into other applications.

## Features
- Find email addresses based on name and domain
- Verify the existence and deliverability of email addresses
- Bulk email search and verification
- API access for automated email finding and verification
- Integrates with various CRM and email marketing platforms

## Website
- [VoilaNorbert](https://www.voilanorbert.com/)

## Usage

### Web Interface
1. Visit [VoilaNorbert](https://www.voilanorbert.com/)
2. Enter the first name, last name, and domain of the person you are looking for
3. Click on the "Go Ahead, Norbert!" button to find the email address

### API
VoilaNorbert provides an API for finding and verifying email addresses programmatically. Below are examples of how to use the API.

#### API Key
You need an API key to use VoilaNorbert's API. You can find your API key in your account settings on the VoilaNorbert website.

### Find Email Address
To find an email address using the API:
```sh
curl -X GET "https://api.voilanorbert.com/v2/email/lookup?name=FirstName LastName&domain=example.com" \
-H "Authorization: Bearer YOUR_API_KEY"
```

### Verify Email Address
To verify an email address using the API:
```sh
curl -X GET "https://api.voilanorbert.com/v2/email/verify?email=email@example.com" \
-H "Authorization: Bearer YOUR_API_KEY"
```

## Bulk Email Search and Verification
VoilaNorbert allows you to upload a CSV file containing names and domains to perform bulk email searches. The results can be downloaded as a CSV file with the found email addresses and their verification status.

## Integrations
VoilaNorbert integrates with several CRM and email marketing platforms to streamline your workflow. Some of the supported platforms include:
- Salesforce
- HubSpot
- Mailchimp
- Pipedrive
- Zoho CRM

## Best Practices
- **Validate emails before sending:** Always verify email addresses before sending outreach emails to avoid bounces and maintain a good sender reputation.
- **Use bulk search for large lists:** For efficiency, use the bulk search feature to find and verify email addresses in large quantities.
- **Integrate with CRM:** Use the integrations to automatically sync found email addresses with your CRM or email marketing platform.

## References
- [VoilaNorbert Website](https://www.voilanorbert.com/)
- [VoilaNorbert API Documentation](https://www.voilanorbert.com/docs)
