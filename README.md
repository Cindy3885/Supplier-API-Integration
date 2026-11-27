
# Supplier API Integration

**Supplier Product Feed → Data Extraction & Transformation → Shopify Admin API → Inventory Update**

A practical API integration project demonstrating how supplier product and stock data can be retrieved, processed, mapped to Shopify product variants, and used to update inventory through the Shopify GraphQL Admin API.

This project documents the integration workflow, data preparation, variant mapping, API testing, inventory update process, validation and results.

---

## Project Overview

The objective was to connect an external supplier API to a Shopify development store and demonstrate a working data flow between the two systems.

The project focused on one selected product rather than attempting to import an entire supplier catalogue.

The integration involved:

- Authenticating with a supplier API.
- Retrieving supplier product feed data.
- Extracting a specific product from a larger JSON response.
- Processing product, image, variant and stock information.
- Matching supplier colour and size combinations to Shopify variants.
- Retrieving Shopify inventory item identifiers.
- Updating Shopify inventory using a GraphQL mutation.
- Validating the API response and checking the result inside Shopify.

**Result:** A successful inventory update was completed in Shopify for 114 product variants using supplier-feed quantity data.

## Integration Architecture

```text
EXTERNAL SUPPLIER API
        |
        | Customer authentication
        |
        v
SUPPLIER PRODUCT FEED
        |
        | JSON response
        |
        v
PRODUCT DATA EXTRACTION
        |
        | Selected product record
        | Product information
        | Images
        | Colour and size data
        | Stock records
        |
        v
DATA PROCESSING & MAPPING
        |
        | Match colour and size combinations
        | Validate variant records
        | Prepare Shopify inventory data
        |
        v
SHOPIFY GRAPHQL ADMIN API
        |
        | Retrieve product variants
        | Retrieve inventory item IDs
        | Submit inventory mutation
        |
        v
SHOPIFY INVENTORY
        |
        | 114 variants updated
        |
        v
VALIDATION & RESULTS
```

## Technologies and Tools

| Technology / Tool | Purpose |
|---|---|
| Supplier REST API | Source of product and stock information |
| JSON | Product and inventory data format |
| Postman | API requests, authentication, testing and response inspection |
| PowerShell | Data extraction, processing and JSON handling |
| Shopify Admin API | Communication with Shopify |
| GraphQL | Shopify product and inventory operations |
| Shopify development store | Testing and verifying the integration |

## 1. Supplier API Authentication

The first stage was establishing an authenticated connection to the supplier API.

A customer login request was submitted using:

`POST /api/customer/login`

The authentication response was used to obtain the access credentials required for subsequent supplier API requests.

The authentication process was tested in Postman.

**Authentication result:** Successful.

Sensitive authentication information, including passwords, access tokens and API credentials, is deliberately excluded from this repository.

## 2. Retrieving Supplier Product Data

After authentication, the supplier product feed was retrieved using:

`GET /api/product/feed`

The feed returned product information in JSON format.

The original response contained a large catalogue, making it impractical to process the entire response repeatedly during development.

Instead, a selected product was extracted into a smaller JSON file for focused processing and integration testing.

This allowed the integration to work with a manageable dataset without repeatedly downloading or processing the complete supplier catalogue.

## 3. Product Data Extraction

A selected product record was extracted from the supplier feed.

The extracted product contained:

- Product code and description.
- Product information.
- Product images.
- Colour information.
- Size information.
- Variant-related data.
- Stock records.
- Pricing quantity information.

The extracted JSON file was approximately 334 KB.

The original full supplier response was approximately 49 MB.

This extraction step significantly reduced the amount of data required for testing.

### Selected product data

| Field | Result |
|---|---|
| Product | Kiddies Crew Neck T-shirt, Fitted Long Sleeve |
| Supplier product code | +27KCNFLSBPR |
| Product images | 19 |
| Stock records | 228 |
| Unique colour-size combinations | 114 |
| Available sizes | 6 |
| Available colours | 19 |

## 4. Understanding the Supplier Stock Structure

One important part of the integration was identifying how the supplier represented stock.

The extracted product contained 228 stock records.

However, these did not represent 228 separate colour-size combinations.

The supplier returned two material records for each colour-size combination:

- 140g Birdseye
- 140g Reverse Birdseye

This resulted in:

**228 supplier stock records ÷ 2 material records = 114 unique colour-size combinations.**

The product contained:

- 19 colours.
- 6 sizes.
- 114 unique colour-size combinations.

The integration therefore needed to distinguish between the supplier's 228 stock records and Shopify's 114 product variants.

This was an important data-mapping consideration. Simply treating every supplier stock record as a separate Shopify variant would have produced an incorrect mapping.

### Colour data

The extracted product included the following colours:

White, Royal Blue, Yellow, Hi-Viz Yellow, Maroon, Lime, Emerald Green, Brown, Charcoal, Red, Black, Sky Blue, Hi-Viz Lime, Hi-Viz Orange, Grey, Bottle Green, Gold, Orange and Navy.

### Size data

- 3–4
- 5–6
- 7–8
- 9–10
- 11–12
- 13–14

## 5. Shopify Product and Variant Preparation

The selected product was prepared in a Shopify development store.

The integration used Shopify's GraphQL Admin API.

The Shopify product was configured with:

- 19 colour options.
- 6 size options.
- 114 product variants.
- Inventory tracking enabled.
- Inventory levels associated with the selected Shopify location.
- Product images uploaded.

The Shopify product was retained as a **Draft** during testing.

Publishing the product was not required to demonstrate the API integration.

Retail pricing and product publication were outside the scope of the inventory update.

## 6. Shopify Variant Identification and Mapping

Before inventory could be updated, the integration needed to identify the Shopify inventory item associated with each variant.

Shopify uses unique identifiers for products, variants and inventory items.

The relevant inventory item IDs were retrieved through the Shopify GraphQL Admin API.

The supplier colour-size combinations were then matched against the Shopify variants.

The mapping process needed to account for:

1. Supplier colour values.
2. Supplier size values.
3. Duplicate material stock records.
4. Shopify variant identifiers.
5. Shopify inventory item identifiers.
6. The selected Shopify inventory location.

The resulting inventory update dataset contained 114 unique Shopify variants.

This stage was essential because Shopify inventory updates operate on inventory item identifiers and location identifiers, not simply on product names or descriptions.

## 7. Shopify Inventory Update

The final integration step used Shopify's GraphQL Admin API mutation:

`inventorySetQuantities`

The mutation submitted inventory quantities for the selected variants.

The request used:

- Inventory quantity name: `available`
- Adjustment reason: `correction`
- Inventory location: selected Shopify location
- Quantity source: extracted supplier feed
- Number of variants submitted: 114

The request used `ignoreCompareQuantity: true` for this test operation.

The purpose was to demonstrate that the supplier-derived inventory data could be submitted to Shopify and applied to the corresponding inventory items.

### Important quantity clarification

The supplier feed returned a quantity value of `99999` for the stock records used in this test.

That value was passed through to the Shopify inventory update.

It should be understood as the quantity supplied by the feed, not as independently verified physical stock held by the supplier.

A production implementation should establish what this value means with the supplier before treating it as an accurate stock-on-hand figure.

## 8. API Response and Validation

The final inventory mutation was executed successfully.

The Postman Visualizer displayed the following results:

| Validation item | Result |
|---|---:|
| HTTP status | 200 |
| Variants submitted | 114 |
| Supplier feed quantity | 99,999 |
| GraphQL errors | 0 |
| Shopify user errors | 0 |
| Changes returned | 228 |

### Understanding the 228 returned changes

The response returned 228 inventory adjustment entries.

These represented two quantity changes for each of the 114 variants:

- 114 `available` changes.
- 114 `on_hand` changes.

Therefore, the response did not represent 228 separate product variants.

It represented 228 inventory adjustment entries across 114 variants.

### Independent Shopify verification

Following the successful API response, the inventory was checked in the Shopify Admin interface.

The inventory update was visible in Shopify.

This confirmed that the submitted inventory changes had been applied in the development store.

The mutation response also contained no GraphQL errors or Shopify user errors.

## 9. Final Project Results

The project successfully demonstrated the following:

- Supplier API authentication.
- Retrieval of supplier product feed data.
- Extraction of an individual product from a larger JSON catalogue.
- Processing of product information and images.
- Identification of supplier stock records.
- Recognition of duplicate material records.
- Mapping of 114 unique colour-size combinations.
- Retrieval of Shopify inventory item identifiers.
- Submission of inventory quantities through Shopify GraphQL.
- Successful API response with HTTP 200.
- Zero GraphQL errors.
- Zero Shopify user errors.
- Verification of the inventory update inside Shopify.

<details>
<summary>Project result summary</summary>

**Supplier data processed:** 1 selected product

**Supplier stock records:** 228

**Unique Shopify variants:** 114

**Inventory adjustment entries returned:** 228

**HTTP response:** 200

**GraphQL errors:** 0

**Shopify user errors:** 0

**Shopify inventory update:** Successfully verified

</details>

## 10. Challenges and Technical Considerations

Several practical challenges were encountered during the integration.

### Large supplier feed

The original supplier feed was approximately 49 MB.

Repeatedly retrieving and processing the complete catalogue created unnecessary processing overhead.

**Approach:** Extracting a single product record into a smaller JSON file made testing more manageable.

### Supplier and Shopify data structures

The supplier's 228 stock records did not correspond directly to Shopify's 114 variants.

**Approach:** Identifying the two material records associated with each colour-size combination made it possible to prepare the correct number of Shopify variant mappings.

### Inventory item identification

Shopify inventory operations require inventory item IDs and location IDs.

**Approach:** Retrieving the Shopify identifiers before submitting the inventory mutation ensured that the update targeted the intended inventory records.

### API response validation

A successful HTTP response alone does not guarantee that every operation inside a GraphQL request succeeded.

**Approach:** The final response was checked for both GraphQL errors and Shopify user errors. The resulting inventory was also verified directly in Shopify.

### Inventory quantity interpretation

The supplier feed returned `99999` as the quantity value.

**Approach:** The value was documented as supplier-feed data rather than assumed to be verified physical inventory.

## 11. Current Scope and Future Improvements

The completed project demonstrates a successful supplier-feed-driven inventory update.

It is important to distinguish this from a fully automated, continuously running integration.

The current demonstration involved a manually initiated workflow and a successful inventory update for one selected product.

The following improvements would be appropriate for a production-ready implementation:

- Automated scheduled supplier feed retrieval.
- Incremental updates instead of processing an entire catalogue.
- Supplier stock quantity validation.
- Clear handling of duplicate material records.
- More comprehensive colour and size matching rules.
- Inventory comparison before updates.
- Error logging and retry handling.
- Protection against accidental inventory overwrites.
- Monitoring and reporting of failed updates.
- Automated synchronisation across multiple products.
- Secure deployment and credential management.

For production use, inventory updates should use suitable quantity comparison controls rather than automatically overwriting quantities without checking whether stock has changed since the last read.

## 12. Security and Data Handling

This repository is intended to demonstrate the integration process without exposing private supplier or store information.

The following information must not be committed to GitHub:

- Supplier passwords.
- Supplier access tokens.
- Shopify Admin API access tokens.
- Private API credentials.
- Customer information.
- Private supplier catalogue data.
- Sensitive store configuration.

Credentials should be stored in secure environment variables or an appropriate secrets manager.

The demonstration documentation intentionally uses generic descriptions for the external supplier and client.

## 13. Evidence and Screenshots

Screenshots can be added to a `screenshots` folder to document the completed workflow.

Recommended evidence:

1. Supplier API authentication response showing successful authentication, with sensitive information hidden.
2. Supplier product feed request showing a successful response.
3. Extracted product JSON showing the selected product and stock structure.
4. Postman response showing the Shopify variants and inventory item mapping.
5. Final Postman Visualizer showing HTTP 200, 114 variants submitted and zero errors.
6. Shopify Admin inventory screen showing the updated inventory.

Suggested repository structure:

```text
Supplier-API-Integration/
│
├── README.md
│
└── screenshots/
    ├── supplier-authentication.png
    ├── supplier-product-feed.png
    ├── extracted-product-data.png
    ├── shopify-variant-mapping.png
    ├── inventory-update-result.png
    └── shopify-inventory-verification.png
```

Only add screenshots that have actually been captured. Sensitive credentials and private supplier information should be concealed before uploading.

## 14. Project Summary

This project demonstrates a practical integration between an external supplier API and Shopify.

It covers more than simply retrieving an API response. The work involved understanding the supplier's JSON structure, extracting relevant product information, identifying duplicate stock records, matching supplier data to Shopify variants, retrieving inventory identifiers and submitting inventory changes through Shopify's GraphQL Admin API.

The successful update of 114 Shopify variants demonstrates that supplier-derived data can be processed and transferred into a separate e-commerce platform through an API integration workflow.

**Project status:** Successful inventory update demonstrated for one selected product.

**Automation status:** Manual execution demonstrated; recurring automated synchronisation is not yet implemented.

---



Project concept, workflow planning, data mapping, API testing, integration validation and documentation.


