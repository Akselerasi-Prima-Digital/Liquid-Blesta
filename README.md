# Liquid Blesta Registrar Modules

Automated domain registration and management for Blesta via Liquid APIs.

<p align="center">
<img src="https://img.shields.io/badge/version-2.2.0-blue.svg" />
<img src="https://img.shields.io/badge/php-%3E%3D_7.2-777BB4.svg" />
<img src="https://img.shields.io/badge/platform-Blesta-orange.svg" />
<a href="LICENSE">
<img alt="License" src="https://img.shields.io/badge/license-MIT-yellow.svg" target="_blank" />
</a>
<a href="https://github.com/Akselerasi-Prima-Digital/Liquid-Blesta/actions">
<img src="https://codecov.io/gh/Akselerasi-Prima-Digital/Liquid-Blesta/branch/main/graph/badge.svg" />
</a>
</p>

## Description
This repository contains production-ready registrar modules for Blesta that enable seamless integration with the Liquid domain registration platforms. It automates the entire lifecycle of domain management, from initial registration and transfers to renewals and DNS configuration. By bridging Blesta with the Liquid API, it eliminates manual provisioning tasks and provides a self-service interface for clients to manage their digital assets directly from the billing portal.

## Features
- Automated Domain Registration and Transfers with real-time API synchronization
- Intelligent Domain Renewals with automated expiry date validation
- Comprehensive DNS Management allowing clients to manage records within Blesta
- Robust Sandbox Mode for safe integration testing and workflow validation
- Automatic Customer and Contact creation on the registrar platform
- Support for specialized TLD requirements including .ASIA, .AU, .RU, .US, and .CO
- Extended WHOIS contact management with granular field validation
- Service suspension and unsuspension support for administrative control
- Multi-module support for both Liquid platforms

## Tech Stack
- **Language**: PHP 7.2+
- **Platform**: Blesta 4.x / 5.x
- **Integration**: Liquid HTTP API
- **Format**: Blesta Registrar Component Architecture

## Installation

### Prerequisites
- Blesta installation (v4.0 or higher recommended)
- PHP 7.2 or higher
- Valid Reseller account with Liquid

### Steps

1. Clone the repository to your local machine:
   ```bash
   git clone https://github.com/Akselerasi-Prima-Digital/Liquid-Blesta.git
   ```

2. Upload the module folders to your Blesta installation:
   - Copy the `liquid` directory to `/components/modules/`
   - Copy the `resellercampid` directory to `/components/modules/`

3. Access your Blesta Admin portal and navigate to **Settings > Modules > Available**.

4. Locate **Liquid** or **ResellerCampID** in the list and click **Install**.

5. Configure the module by adding a new Label/Row with your API credentials.

## Configuration

### API Credentials
To connect the module to the registrar platform, you must provide the following in the module configuration:
- **Reseller ID**: Your unique identifier from the Liquid/ResellerCamp panel.
- **API Key**: The security key generated in your reseller settings.
- **Sandbox**: Toggle this to `true` if you are using a test account (e.g., test.httpapi.com).

### TLD Management
After installing the module, navigate to **Packages > Browse Packages > Create Package** to set up your domain products:
1. Set the **Module** to Liquid or ResellerCampID.
2. Select the TLDs you wish to offer (e.g., .com, .net, .id).
3. Configure the required WHOIS fields based on the selected TLD requirements.

## Usage

### Automated Provisioning
Once a client completes a purchase for a domain package, Blesta will automatically trigger the `addService` method in the module. The module will:
1. Verify if the customer already exists on the registrar platform (by email).
2. Create a new customer and contact if necessary.
3. Submit the registration or transfer request to the API.
4. Store the remote Order ID within the Blesta service metadata.

### Client-Side Management
Clients can manage their domains via the Client Area:
- **Nameservers**: Update nameserver records in real-time.
- **DNS Records**: Add/Edit/Delete A, CNAME, MX, and TXT records if DNS Management is enabled.
- **Privacy**: Manage WHOIS privacy protection settings.

### Administrative Commands
Administrators can perform manual actions from the Service Management page:
- **Renew**: Manually trigger a renewal request.
- **Suspend/Unsuspend**: Control domain status for policy enforcement.

## Project Structure
```
liquid/                 # Core module files for Liquid Registrar
  apis/                 # API wrapper and command logic
  config/               # TLD and field definitions
  language/             # Translation strings (English, etc.)
  views/                # UI templates for Admin and Client areas
resellercampid/         # Core module files for ResellerCampID
  apis/                 # API communication logic
  config/               # Platform-specific configuration
  language/             # Multi-language support files
  views/                # Template files for Blesta integration
```

## Contributing
Contributions are encouraged to improve TLD support and API reliability.
1. Fork the repository.
2. Create a feature branch: `git checkout -b feature/improvement-name`.
3. Implement your changes following Blesta coding standards.
4. Submit a pull request with a detailed description of the improvements.

## License
Distributed under the MIT License. See `LICENSE` for more information.

## Author
Akselerasi Prima Digital
