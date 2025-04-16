# 🌀 Product Circularity Datasheet (PCDS)

Welcome to the **Product Circularity Datasheet (PCDS)** repository. This project provides a framework and tooling to define, generate, and validate circularity information for products in both human-readable and machine-readable formats.

## 🌱 What is a PCDS?

A **Product Circularity Datasheet** is a standardized document that communicates the circularity characteristics of a product. It enables better decision-making for reuse, recycling, and remanufacturing, supporting the transition to a circular economy.

This repository contains:
- 📄 Example templates of PCDS (human-readable)
- 🧾 Machine-readable versions (JSON)
- 📚 Documentation & usage guides

---

# 📁 Templates IDs
<details>
  
## 📄 Templates IDs Format & Implementation Guide

This guide describes how the **Templates ID** is structured and how to implement it in a practical, scalable way.


## 📚 Field Descriptions

| Field                  | Length | Description                                                                 |
|------------------------|--------|-----------------------------------------------------------------------------|
| `Template Issuer`      | 3      | Identifies the template issuer (e.g. Terra Matters) — [see `registries/issuers`](./registries/issuers) |
| `Document Type`        | 2      | Document type code (e.g., `02` for PCDS) — [see `registries/documents`](./registries/documents)                                   |
| `Template Code`        | 3      | Template-specific ID within the issuer/type context — [see `registries/documents`](./registries/documents)                        |
| `Check Digit`          | 1      | Validates the 8-digit prefix using a weighted algorithm                     |
| `PCDS Sequence Number` | 7      | Sequential number per PCDS document issued for this template               |
| `Revision` (optional)  | —      | Version number (e.g., `:001`)                                              |

---

## ✅ Check Digit Calculation

The **check digit** helps detect input errors.

### Weights

| Position   | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|------------|---|---|---|---|---|---|---|---|
| Weight     | 1 | 3 | 1 | 3 | 1 | 3 | 1 | 3 |

### Example Calculation

For prefix: `010 02 001`

Step 1 : Multiply value of each position by their corresponding weight :
| Position   | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|------------|---|---|---|---|---|---|---|---|
| Weight     | 1 | 3 | 1 | 3 | 1 | 3 | 1 | 3 |
| Value     | 0 | 1 | 0 | 0 | 2 | 0 | 0 | 1 |
| result     | 0 | 3 | 0 | 0 | 2 | 0 | 0 | 3 |

Step 2 : Sum each resulting values
0+3+0+0+2+0+0+3 =8

Step 3: Subtract the sum from nearest equal or higher multiple of ten = Check Digit
Check digit = 10-8 = 2

## 📁 Document ID

A **Document ID** is a unique identifier for each document generated from a specific template. It is based on a simple incrementation of the number of existing documents using that template.

### 🔢 Example

**Template Prefix**:  
`010 02 001 2`

The 75th document created from this template will have the following PCDS ID:
`010 02 001 2 0000075`

### 🔁 Revision Support

A revision number can be added to reflect updates to the same document. For example:


This represents version 1 of the document `010 02 001 2 0000075:001`.


</details>

