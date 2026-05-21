# Documentation & Reference Guides

This directory serves as the central repository for all architectural guidelines, standard operating procedures (SOPs), and technical documentation for the data platform. 

Keeping execution code separate from architectural rules ensures that our standards are easy to find, review, and maintain.

## Directory Contents

* **Architecture Guides:** Detailed breakdowns of the Medallion Architecture, including data flows between Azure Data Factory, Azure Databricks, and Power BI.
* **Deployment Handbooks:** Instructions for CI/CD pipelines, infrastructure-as-code (e.g., Terraform) deployments, and environment promotions (Dev -> Test -> Prod).
* **Security Protocols:** Reference documents for Unity Catalog configurations, Managed Identity assignments, and Virtual Network (VNet) boundaries.

## Guidelines for Adding Documentation

When adding new guides or readmes to this folder, you must adhere to the following standards:

1. **Format:** Use standard Markdown (`.md`) for living documents or PDF for finalized architectural diagrams and locked SOPs.
2. **Clarity:** Keep instructions concise, technical, and direct. Avoid ambiguous language or assumptions about the reader's environment setup.
3. **Maintenance:** If you update a core pipeline component, you must update the corresponding documentation here within the same pull request. Stale documentation is a critical technical debt.

Keeping these documents accurate is mandatory for team alignment, rapid onboarding, and pipeline stability.