# Supplier API Integration

**Supplier Product Data Integration | Promo Africa API | PowerShell | JSON | Shopify**

---

## 1. Introduction

This repository documents a supplier API integration project focused on retrieving product information from Promo Africa, processing the returned data and preparing it for import into Shopify.

The project involved working with structured JSON data, developing a PowerShell conversion script, mapping supplier product information and testing the resulting products and variants in a separate Shopify development store.

The development testing successfully imported:

- 10 products
- 88 product variants
- Product images
- Products saved as drafts

The project demonstrates practical experience in API data retrieval, JSON data processing, product-data mapping, scripting and e-commerce integration.

The work represents a development-stage implementation. A complete live supplier-to-Shopify synchronisation process remains future work.

---

## 2. Project Background

The project originated from the need to transfer supplier product information into Shopify more efficiently.

Manually capturing products, descriptions, pricing, sizes, variants and images can become time-consuming, particularly when dealing with large supplier catalogues or products with multiple variants.

The objective was to investigate how supplier information could be retrieved directly through an API and transformed into a format suitable for Shopify.

The work required understanding both the supplier's data structure and the information Shopify needed to create products correctly.

Rather than treating the task as a straightforward data transfer, the project involved examining the source data, identifying the relevant fields, resolving mapping differences and testing the resulting product information.

---

## 3. Project Objectives

The main objectives were to:

1. Connect to the Promo Africa supplier API and retrieve product information.
2. Examine the returned JSON data and understand its structure.
3. Develop a PowerShell script to process the supplier data.
4. Identify and map the relevant product information.
5. Process product variants and size information correctly.
6. Prepare the converted information for Shopify.
7. Test the import using a separate Shopify development store.
8. Identify the additional requirements for a complete automated integration.

The broader objective was to establish a practical foundation for reducing repetitive manual product capture and creating a more efficient supplier-to-e-commerce data workflow.

---

## 4. Technologies and Tools

The project involved the following technologies and platforms:

| Technology / Platform | Purpose |
|---|---|
| Promo Africa API | Source of supplier product information |
| JSON | Structured format used for the supplier data |
| PowerShell | Processing and conversion of JSON product data |
| Shopify | Destination e-commerce platform |
| Shopify development store | Environment used to test product imports |

The implementation focused on using the supplier's existing JSON response and processing it directly through PowerShell.

No intermediate CSV conversion stage was used in the original workflow.

---

## 5. Project Scope

### 5.1 Work completed

The following work was carried out:

- Connected to the supplier API.
- Retrieved structured product information.
- Received successful HTTP 200 responses during API testing.
- Worked with the original JSON data files.
- Examined product and variant data structures.
- Developed a PowerShell converter.
- Identified and corrected a nested size-field mapping issue.
- Handled stock-size information separately.
- Created a separate Shopify development environment.
- Successfully tested the import of 10 products and 88 variants.
- Confirmed that product images were included in the test import.
- Saved the imported products as drafts.

### 5.2 Remaining development

The following areas were not completed as part of the demonstrated development test:

- Full live-store authentication and connection verification.
- Complete automated supplier-to-Shopify synchronisation.
- Scheduled product updates.
- Automated stock and pricing updates.
- Ongoing synchronisation of existing products.
- Production-level duplicate handling and error recovery.
- Full production deployment and monitoring.

These items are identified as future development rather than completed functionality.

---

## 6. Integration Overview

The initial integration workflow consisted of retrieving supplier data, processing the JSON files, converting the relevant product information and using the resulting data for a Shopify development import.

### High-level workflow

```text
PROMO AFRICA API
       |
       v
SUPPLIER PRODUCT DATA
       |
       v
JSON RESPONSE
       |
       v
ORIGINAL JSON FILES
       |
       v
POWERSHELL CONVERTER
       |
       v
PRODUCT DATA EXTRACTION
       |
       v
PRODUCT AND VARIANT MAPPING
       |
       v
SHOPIFY-READY PRODUCT DATA
       |
       v
SHOPIFY DEVELOPMENT STORE
       |
       v
PRODUCT IMPORT AND VALIDATION
```

### Workflow explanation

**1. Supplier data retrieval**

Product information was requested from the Promo Africa API.

**2. JSON data handling**

The returned JSON data was retained and used as the source for the conversion process.

**3. Data processing**

A PowerShell script was developed to read and process the supplier's product information.

**4. Product mapping**

Relevant product and variant fields were identified and mapped for Shopify.

**5. Development import**

The processed information was used in a Shopify development-store import test.

**6. Validation**

The imported products, variants and images were checked in the development environment.

---

## 7. Supplier API Connection

The first technical stage involved connecting to the Promo Africa API and retrieving supplier product information.

### 7.1 API response

The API returned structured product data in JSON format.

During testing, the request returned an HTTP 200 response, indicating that the request was successfully processed by the API.

### 7.2 Retrieved information

The returned data contained product information that could be examined and processed for the Shopify import workflow.

The relevant information included product details and associated variant data.

The structure of the returned JSON needed to be understood before the conversion logic could be developed.

### 7.3 API testing

The API connection and returned response formed the starting point for the integration process.

Evidence of the original API request and response can be added to the repository after the relevant files and screenshots have been reviewed and sanitised.

API credentials, access tokens and confidential information must never be included in the public repository.

---

## 8. JSON Data Examination

The supplier API returned product information in JSON format. The original JSON files were used directly during development.

### 8.1 Understanding the data structure

Before converting the information, it was necessary to examine how the supplier organised its product records.

This included identifying:

- Product-level information.
- Product descriptions and attributes.
- Pricing information.
- Variant information.
- Size values.
- Stock-related information.
- Product image references.

### 8.2 Nested fields

Some information was stored within nested JSON objects rather than directly at the top level of a product record.

This meant that the conversion process needed to identify the correct field paths when extracting information.

A practical example was the size-mapping issue, where the required value was located in a nested field rather than the initially assumed field.

### 8.3 Data preparation

The JSON structure was used as the basis for the PowerShell conversion process.

The objective was to extract the relevant supplier information and prepare it for mapping into the Shopify product structure.

### 8.4 Data integrity

The original supplier data was retained as the source for processing.

Any sample JSON files published in this repository should be sanitised to remove confidential supplier information and other private data.

---

## 9. PowerShell Data Converter

A PowerShell converter was developed to process the supplier's JSON product data and prepare the information for the Shopify import workflow.

The purpose of the script was to extract relevant information from the supplier's data structure and convert it into a format that could be used for product creation.

### 9.1 Reading JSON data

The converter worked with the original JSON files retrieved from the supplier API.

PowerShell provided the ability to read the structured data and access the product information contained within the JSON objects.

### 9.2 Processing product information

The script was developed to process the supplier product records and identify the information required for the import.

This involved working with product-level fields and related variant information.

### 9.3 Preparing data for Shopify

The supplier's field structure did not necessarily correspond directly with Shopify's product structure.

The converter therefore needed to account for differences in field names, data organisation and nested values.

The resulting data was prepared for use in the Shopify import process.

### 9.4 Development and verification

The converted information was used in the successful development-store import test.

The original PowerShell script will be included in this repository once it has been reviewed to confirm its contents and remove any private information.

---

## 10. Product Data Mapping

An important part of the integration was identifying how supplier product information needed to be mapped for Shopify.

The supplier API provided the source information, but the data needed to be interpreted and organised according to the destination platform's requirements.

### 10.1 Mapping considerations

The conversion process involved examining information such as:

- Product identifiers and codes.
- Product titles and descriptions.
- Product attributes.
- Pricing information.
- Product images.
- Variant details.
- Size information.
- Stock-related values.

### 10.2 Source and destination differences

Supplier systems and e-commerce platforms may represent the same information differently.

For example, a supplier may store an attribute inside a nested object, while the destination platform expects that value as part of a product or variant record.

The mapping process therefore required an understanding of the source data rather than relying only on field names.

### 10.3 Mapping accuracy

Incorrect mapping can result in incomplete product information, incorrect variant options or information being assigned to the wrong field.

The development process included examining the returned data and correcting mapping logic where the initial assumptions did not match the actual JSON structure.

---

## 11. Variant and Size Mapping

Product variants required additional attention because a single product could have multiple options or sizes.

The supplier's variant information needed to be interpreted correctly so that the resulting Shopify products contained the appropriate variant structure.

### 11.1 Identifying variant information

The JSON data was examined to identify how product variants and their associated attributes were represented.

The conversion process needed to distinguish between information belonging to the overall product and information belonging to an individual variant.

### 11.2 Size-field mapping issue

During development, a size-mapping issue was identified.

The relevant size value was not stored in the field initially expected. It was located within the nested field:

```text
size.code
```

The mapping logic was corrected to use the appropriate field.

This was an important correction because using the wrong field could result in missing or incorrect size information when creating Shopify variants.

### 11.3 Stock-size handling

Stock-size information also required separate consideration.

The size assigned to a product variant and the stock information associated with that size serve different purposes.

The conversion process therefore needed to account for these distinctions rather than treating all size-related values as interchangeable.

### 11.4 Variant testing

The successful Shopify development import included 88 variants across 10 products.

This provided a practical test of the product and variant data prepared through the conversion workflow.

---

## 12. Shopify Development Environment

A separate Shopify development store was created to test the product import process.

This was necessary because the development work could not be carried out directly in the original partner store.

Using a separate environment provided a way to test the converted product information without making changes to the original store.

### 12.1 Development-store purpose

The development store was used to:

- Test the prepared product data.
- Import products and their variants.
- Check whether product images were included.
- Inspect the resulting product records.
- Review the imported variant information.
- Keep development testing separate from the original store.

### 12.2 Test environment

The development store provided a controlled environment for validating the initial import workflow.

The successful import demonstrated that the converted product information could be used to create Shopify products and variants.

### 12.3 Separation from production

The development store was used for testing purposes.

The successful test should not be interpreted as confirmation that the original partner store was connected for live synchronisation or that a production deployment had taken place.

---

## 13. Shopify Product Import

The converted supplier data was used in a development-store import test.

The test successfully created products and their associated variants in Shopify.

### 13.1 Import results

The development test produced the following results:

| Import result | Quantity / Status |
|---|---:|
| Products imported | 10 |
| Variants imported | 88 |
| Product images | Included |
| Product status | Draft |

### 13.2 Product creation

The imported records appeared in the Shopify development store as products.

The test demonstrated that the prepared supplier information could be used to create Shopify product records.

### 13.3 Variant creation

The import also included the associated product variants.

A total of 88 variants were imported across the 10 products tested.

### 13.4 Product images

Product images were included in the development import.

This was an important part of the test because product information in an e-commerce catalogue needs to include more than descriptions and pricing.

### 13.5 Draft status

The imported products were saved as drafts.

This allowed the imported information to be inspected in the development environment without publishing the products as active listings.

---

## 14. Testing and Validation

Testing was carried out to establish whether the supplier data could be processed and used to create products in Shopify.

The development import provided a practical way to assess the results of the conversion process.

### 14.1 API response validation

The supplier API request returned a successful HTTP 200 response during testing.

This confirmed that the API request successfully returned data.

### 14.2 Data-processing validation

The original JSON files were used by the PowerShell conversion workflow.

The product and variant information was examined and processed for the import.

### 14.3 Mapping validation

The size-mapping issue identified during development was corrected to use the relevant nested field.

This demonstrated the importance of validating the actual source-data structure rather than assuming that a particular field contained the required value.

### 14.4 Shopify import validation

The development-store test successfully imported:

- 10 products.
- 88 variants.
- Product images.

The products were saved as drafts for inspection.

### 14.5 Testing limitations

The successful import demonstrated the initial product-data conversion and import workflow for the tested sample.

It did not establish that every possible supplier product structure had been tested or that all future synchronisation scenarios were covered.

Additional testing would be required for larger product sets, updates to existing products, stock changes, pricing changes, missing information and API errors.

---

## 15. Challenges and Technical Considerations

The development process involved several practical considerations associated with integrating two systems that organise product information differently.

### 15.1 Understanding supplier data

The supplier's JSON structure needed to be examined before reliable mapping logic could be developed.

The presence of nested fields meant that the correct location of each required value had to be established.

### 15.2 Variant complexity

Products with multiple sizes or other variant options require careful handling.

The conversion process needed to distinguish between product-level information and variant-level information.

### 15.3 Correct field selection

The size-mapping issue demonstrated how selecting an incorrect field could affect the resulting Shopify product data.

Identifying the correct nested field and correcting the mapping logic was an important part of the development work.

### 15.4 Stock information

Stock-related values and size information required separate consideration.

A future synchronisation process would need to establish how supplier stock quantities correspond to the correct Shopify variants and inventory records.

### 15.5 Development versus live integration

Testing in a separate Shopify development store provided a controlled environment for the initial import.

A production integration requires additional authentication, permissions, update logic and safeguards before it can be used to modify a live product catalogue.

---

## 16. Current Limitations and Future Development

The project established a working foundation for retrieving, processing and importing supplier product information.

However, the successful development import represents an initial integration stage rather than a complete automated synchronisation solution.

The following areas remain for further development.

### 16.1 Shopify authentication

Complete and verify the Shopify application authentication process and the permissions required for the intended integration.

### 16.2 Repeatable API retrieval

Develop a repeatable process for retrieving supplier product data without relying on manually managed source files.

### 16.3 Existing-product updates

Extend the workflow to identify products that already exist in Shopify and update their information where appropriate, rather than creating duplicates.

### 16.4 Pricing synchronisation

Develop and test reliable updates for supplier pricing, including validation of the values being transferred.

### 16.5 Stock synchronisation

Establish and test how supplier stock information should be mapped to the correct Shopify product variants and inventory records.

### 16.6 Variant and image updates

Extend testing to cover changes to existing variants, product options and image information.

### 16.7 Error handling and logging

Introduce structured error handling and logging to help identify failed API requests, invalid data, mapping problems and unsuccessful Shopify operations.

### 16.8 Scheduled synchronisation

Investigate a scheduled process that can retrieve supplier updates and apply approved changes to Shopify at defined intervals.

### 16.9 Production testing

Once authentication, mapping and update functionality have been verified, conduct controlled testing against the authorised original Shopify store before considering production use.

---

## 17. Future Integration Workflow

The next stage of development is to extend the initial product import workflow into a repeatable supplier-to-Shopify integration.

The intended workflow would allow supplier product information to be retrieved, processed, validated and used to create or update Shopify products.

### 17.1 Proposed workflow

```text
PROMO AFRICA API
       |
       v
AUTHENTICATED API REQUEST
       |
       v
RETRIEVE LATEST PRODUCT DATA
       |
       v
PROCESS JSON RESPONSE
       |
       v
VALIDATE PRODUCT INFORMATION
       |
       v
MAP PRODUCTS AND VARIANTS
       |
       v
IDENTIFY EXISTING PRODUCTS
       |
       v
CREATE NEW PRODUCTS
       |
       v
UPDATE EXISTING PRODUCTS
       |
       v
UPDATE PRICES AND STOCK
       |
       v
LOG RESULTS AND ERRORS
       |
       v
SHOPIFY PRODUCT CATALOGUE
```

### 17.2 Proposed functionality

Further development could introduce:

- Automated retrieval of supplier product information.
- Validation of incoming product records.
- Product matching and duplicate prevention.
- Creation of new Shopify products.
- Updating of existing product information.
- Variant and size synchronisation.
- Pricing updates.
- Stock-level updates.
- Image updates.
- Error reporting and activity logs.
- Scheduled synchronisation.

These capabilities represent the intended direction of development and are not claimed as completed functionality.

---

## 18. Data Mapping Documentation

Data mapping documentation will be important for maintaining and extending the integration.

It will provide a reference showing how information from the supplier's JSON structure corresponds to the fields required by Shopify.

### 18.1 Proposed mapping reference

The following table identifies the main information categories that need to be documented.

| Data category | Source | Destination |
|---|---|---|
| Product identifier | Supplier product data | Shopify product matching |
| Product title | Supplier product data | Shopify product title |
| Product description | Supplier product data | Shopify product description |
| Product images | Supplier image information | Shopify product media |
| Product pricing | Supplier pricing data | Shopify product or variant pricing |
| Variant information | Supplier variant data | Shopify product variants |
| Size information | Nested supplier size data | Shopify variant options |
| Stock information | Supplier stock data | Shopify inventory |

The exact source field names, destination fields and transformation rules should be confirmed against the original JSON files and the implementation code before being documented as final mappings.

### 18.2 Why mapping documentation matters

Maintaining a clear mapping reference helps to:

- Explain how supplier information is transformed.
- Identify where individual values originate.
- Reduce incorrect field assignments.
- Support troubleshooting.
- Make future changes easier to manage.
- Provide a reference for additional supplier products and variants.

A separate `data-mapping.md` document can be maintained in the repository as the mapping is verified.

---

## 19. Repository Structure

The repository is intended to organise the integration scripts, sanitised sample data, technical documentation and supporting evidence in one place.

The proposed structure is:

```text
Supplier-API-Integration/
│
├── README.md
│
├── scripts/
│ ├── powershell-converter.ps1
│ └── additional-scripts.ps1
│
├── data/
│ ├── sample-product-data.json
│ ├── sample-variant-data.json
│ └── additional-sanitised-json.json
│
├── postman/
│ └── supplier-api-collection.json
│
├── documentation/
│ ├── data-mapping.md
│ ├── technical-workflow.md
│ └── testing-results.md
│
├── screenshots/
│ ├── api/
│ ├── json/
│ ├── powershell/
│ ├── shopify/
│ └── application/
│
└── diagrams/
    └── integration-workflow.png
```

### 19.1 Repository contents

**README.md**

Provides an overview of the project, implementation, testing, current limitations and future development.

**scripts/**

Contains the PowerShell converter and any additional scripts included in the project.

**data/**

Contains sanitised sample JSON files that demonstrate the supplier data structure.

**postman/**

Can contain a Postman collection for reproducing and documenting API requests, once the request configuration has been verified.

**documentation/**

Contains supporting technical documentation, data mapping references and testing results.

**screenshots/**

Contains selected screenshots demonstrating the development and testing process.

**diagrams/**

Contains visual representations of the integration workflow.

This is the intended repository layout. Files should only be added once they have been collected, reviewed and prepared for publication.

---

## 20. Testing Evidence and Screenshots

Supporting evidence will be used to demonstrate the work carried out during development.

The objective is to show the actual implementation and its results rather than relying only on written descriptions.

### 20.1 API evidence

Potential evidence includes:

- API request configuration.
- Successful HTTP 200 response.
- Returned JSON response.
- Example supplier product record.

### 20.2 JSON evidence

Potential evidence includes:

- Original JSON file opened in an editor.
- Example product record.
- Nested variant information.
- Relevant size and stock fields.

### 20.3 PowerShell evidence

Potential evidence includes:

- PowerShell converter source code.
- JSON-reading and processing logic.
- Product and variant mapping logic.
- Relevant execution output.

### 20.4 Shopify evidence

Potential evidence includes:

- Shopify development-store product list.
- An imported product record.
- Product images.
- Product variant information.
- Draft product status.
- Evidence of the 10-product and 88-variant import.

### 20.5 Evidence standards

All screenshots and sample files must be genuine and taken from the actual development work.

Before publication:

- Remove API credentials and access tokens.
- Hide private application configuration.
- Remove confidential supplier information.
- Avoid exposing private store details.
- Use sanitised sample data where necessary.

Evidence should clearly distinguish the successful development import from functionality that remains outstanding.

---

## 21. Security and Data Protection

API integrations involve credentials, supplier information and access to external platforms.

Security must therefore be considered throughout development and when publishing the project publicly.

### 21.1 Credential protection

API keys, access tokens, passwords and other authentication details must never be committed to a public GitHub repository.

Sensitive values should be stored securely and kept separate from publicly accessible scripts and documentation.

### 21.2 Supplier data

Supplier product information should be reviewed before publication.

Only information suitable for public demonstration should be included in sample files.

### 21.3 Shopify access

Shopify application credentials, access tokens and private store information must remain confidential.

Application configuration screenshots must be checked carefully before being added to the repository.

### 21.4 Public repository checks

Before publishing or updating the repository:

- Review all scripts for embedded credentials.
- Inspect JSON files for private information.
- Check screenshots for exposed tokens or account details.
- Remove private store identifiers where appropriate.
- Confirm that sample data is safe to publish.

The repository should demonstrate the technical work without exposing confidential business information.

---

## 22. Skills Demonstrated

This project demonstrates practical experience across several areas of data handling, scripting and e-commerce integration.

### API integration

- Connecting to a supplier API.
- Retrieving structured product information.
- Understanding API responses.
- Working with successful HTTP responses.

### JSON data handling

- Examining structured JSON data.
- Understanding nested objects and fields.
- Identifying product and variant information.
- Extracting relevant data for further processing.

### PowerShell scripting

- Developing a data conversion script.
- Reading and processing JSON files.
- Working with structured product records.
- Implementing data transformation and mapping logic.

### E-commerce integration

- Understanding Shopify product structures.
- Preparing product information for import.
- Working with product variants.
- Testing product images and draft products.
- Identifying requirements for future synchronisation.

### Problem-solving

- Investigating differences between supplier and destination data structures.
- Identifying incorrect field assumptions.
- Correcting nested size-field mapping.
- Considering stock and variant relationships.
- Validating the resulting imported products.

### Technical documentation

- Documenting an integration workflow.
- Identifying implementation limitations.
- Separating completed work from future development.
- Organising technical evidence and supporting files.

---

## 23. Project Outcomes

The project established a practical foundation for integrating supplier product information with Shopify.

The development work demonstrated that supplier product data could be retrieved through an API, processed using PowerShell and prepared for a Shopify product import.

### Demonstrated results

| Outcome | Result |
|---|---|
| Supplier API access | Successfully tested |
| API response | HTTP 200 received |
| Source data | Original JSON files |
| Conversion tool | PowerShell converter developed |
| Size mapping | Nested-field issue identified and corrected |
| Shopify development import | Successful |
| Products imported | 10 |
| Variants imported | 88 |
| Product images | Included |
| Product status | Draft |

### Practical value

The work demonstrated an approach to reducing repetitive product-data capture by using supplier data as the source for product creation.

It also provided practical experience in identifying data-structure differences, resolving mapping issues and validating imported information in an e-commerce environment.

The next development stage is to extend the tested import workflow into a properly authenticated and repeatable synchronisation process.

---

## 24. Conclusion

This project explored the integration of supplier product information with Shopify using the Promo Africa API, JSON and PowerShell.

The development work covered API data retrieval, JSON examination, product-data conversion, variant mapping and Shopify development-store testing.

The successful import of 10 products and 88 variants, including product images, demonstrated that the initial data-processing and import workflow could produce usable Shopify product records.

The project also highlighted practical considerations involved in integrating different systems, particularly the importance of understanding nested data structures and correctly mapping product and variant information.

Although the initial development test was successful, the complete live supplier-to-Shopify synchronisation process remains to be implemented and verified.

The repository documents the work completed, the results demonstrated and the remaining development requirements.

---
