## Overview
Clearbit is a powerful tool for enriching data, finding emails, and gaining insights into companies and individuals. It offers a range of APIs that provide detailed information about companies, people, and more, making it valuable for sales, marketing, and analytics.
## Features
- **Enrichment:** Enhance your records with detailed company and personal data.
- **Prospector:** Find and generate leads by searching for people who match specific criteria.
- **Reveal:** Identify anonymous website visitors by their IP address.
- **Risk:** Assess the risk level of an email address or domain.
- **Autocomplete:** Autocomplete company names and provide additional information.
## Website
- [Clearbit](https://clearbit.com/)
## Usage

### Enrichment API
The Enrichment API allows you to append detailed information to your existing customer data.
#### Enrich Person
To enrich a person’s data:
```sh
curl -H "Authorization: Bearer YOUR_API_KEY" \
"https://person.clearbit.com/v2/people/find?email=email@example.com"
```
#### Enrich Company
To enrich a company’s data:
```sh
curl -H "Authorization: Bearer YOUR_API_KEY" \
"https://company.clearbit.com/v2/companies/find?domain=example.com"
```

### Prospector API
The Prospector API helps you find contacts at companies.

#### Find Contacts
To find contacts at a specific company:
```sh
curl -H "Authorization: Bearer YOUR_API_KEY" \
"https://prospector.clearbit.com/v1/people/search?domain=example.com&title=marketing"
```

### Reveal API
The Reveal API identifies anonymous website visitors by their IP address.

#### Identify Visitors
To reveal visitor information:
```sh
curl -H "Authorization: Bearer YOUR_API_KEY" \
"https://reveal.clearbit.com/v1/companies/find?ip=IP_ADDRESS"
```
### Risk API
The Risk API provides information to assess the risk associated with an email address or domain.
#### Assess Risk
To assess the risk of an email address:
```sh
curl -H "Authorization: Bearer YOUR_API_KEY" \
"https://risk.clearbit.com/v1/calculate?email=email@example.com"
```
### Autocomplete API
The Autocomplete API helps you complete company names and provides additional company data.
#### Autocomplete Company
To autocomplete a company name:
```sh
curl -H "Authorization: Bearer YOUR_API_KEY" \
"https://autocomplete.clearbit.com/v1/companies/suggest?query=clearb"
```
## Best Practices
- **Use Enrichment to enhance data:** Integrate the Enrichment API to automatically append detailed information to your customer records.
- **Leverage Prospector for lead generation:** Use the Prospector API to find potential leads that match your target criteria.
- **Identify website visitors with Reveal:** Implement the Reveal API to gain insights into anonymous visitors and tailor your marketing efforts.
- **Assess risk before engagement:** Utilize the Risk API to evaluate the potential risk of engaging with an email address or domain.
- **Integrate with your CRM:** Use Clearbit’s integrations to sync enriched data with your CRM for better sales and marketing strategies.
## References
- [Clearbit Website](https://clearbit.com/)
- [Clearbit API Documentation](https://clearbit.com/docs)
