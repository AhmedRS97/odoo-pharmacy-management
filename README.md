# Odoo Pharmacy Management Module

This Odoo module provides enhanced functionality for pharmacy management, addressing key operational needs.

## Features

This module incorporates the following features, designed to streamline pharmacy operations:

**1. Prescription Management Enhancements:**

* **Prescription Expiration Tracking:**
    * Tracks the expiration dates of prescriptions.
    * Provides automated alerts when prescriptions are nearing or have reached their expiration date.
* **Customized Prescription Printing:**
    * Allows for customization of prescription printouts.
    * Enables the inclusion of specific information, formatting, and branding elements.

**2. Inventory and Controlled Substance Management:**

* **Controlled Substance Management:**
    * Implements a robust system for tracking controlled substances.
    * Maintains detailed audit trails for all transactions involving controlled substances.
    * Provides reporting for regulatory compliance.

**3. Patient Communication and Engagement:**

* **Automated Refill Reminders:**
    * Sends automated refill reminders to patients.
    * Supports reminders via email or SMS.

**4. Future Enhancements (More Complex):**

* **Custom Drug Interaction Alerts:**
    * Implements a system to check for potential drug interactions.
    * Uses predefined rules to identify and alert pharmacists about potential interactions.
* **Integration with a Drug Database:**
    * Integrates Odoo with an external drug database.
    * Automatically populates drug information, reducing manual data entry.

## Installation (Using Docker Compose - Recommended)

1.  **Clone this repository:**

    ```bash
    git clone [[odoo-pharmacy-management repo](https://github.com/AhmedRS97/odoo-pharmacy-management)]
    cd [your-repository-directory]
    ```

2.  **Create a `docker-compose.yml` file** (if you don't already have one) in the root of your repository. Example content:

    ```yaml
    
    version: '3.8'
    services:
      odoo:
        image: odoo:latest # or a specific version like odoo:17.0
        depends_on:
          - db
        ports:
          - "8069:8069"
        environment:
          - POSTGRES_USER=odoo
          - POSTGRES_PASSWORD=odoo
          - POSTGRES_HOST=db
        command: odoo -i base
        volumes:
          - ./addons:/mnt/extra-addons
          - odoo-web-data:/var/lib/odoo
          - ./config:/etc/odoo
      db:
        image: postgres:13 # or a supported version
        environment:
          - POSTGRES_USER=odoo
          - POSTGRES_PASSWORD=odoo
          - POSTGRES_DB=odoo
        volumes:
          - odoo-db-data:/var/lib/postgresql/data
    volumes:
      odoo-web-data:
      odoo-db-data:
    ```

    **Note:**
    * Make sure the `./addons` path is correct relative to your `docker-compose.yml` file.

3.  **Start the containers:**

    ```bash
    docker-compose up -d
    ```

4.  **Access Odoo:** Open your web browser and navigate to `http://localhost:8069`.

5.  **Install the module:**
    * Log in to Odoo.
    * Navigate to "Apps."
    * Search for "Pharmacy Management" and install the module.

## Installation (Manual - If not using docker-compose)

1.  Clone this repository into your Odoo addons directory.
2.  Restart the Odoo server.
3.  Navigate to "Apps" in Odoo.
4.  Search for "Pharmacy Management" and install the module.

## Usage

* **Prescription Expiration Tracking:** When creating a sales order for a prescription, enter the prescription expiry date. Scheduled actions will alert users of expiring prescriptions.
* **Customized Prescription Printing:** Modify the QWeb report templates to customize the prescription printouts.
* **Controlled Substance Management:** Use the new models to track controlled substances.
* **Automated Refill Reminders:** Configure automated actions to send email or sms reminders.

## Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues.

## License

This module is licensed under the [Specify License, e.g., LGPL-3].

## Contact

[Your Name/Organization]
[Your Email]
[Your GitHub Profile/Website (Optional)]
