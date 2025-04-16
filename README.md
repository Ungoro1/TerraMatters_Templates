# 🌀 Product Circularity Datasheet (PCDS)

Welcome to the **Product Circularity Datasheet (PCDS)** repository. This project provides a framework and tooling to define, generate, and validate circularity information for products in both human-readable and machine-readable formats.

## 🌱 What is a PCDS?

A **Product Circularity Datasheet** is a standardized document that communicates the circularity characteristics of a product. It enables better decision-making for reuse, recycling, and remanufacturing, supporting the transition to a circular economy.

This repository contains:
- 📄 Example templates of PCDS (human-readable)
- 🧾 Machine-readable versions (JSON)
- 📚 Documentation & usage guides

---

## 📁 Repository Structure
<details>
## 📄 PCDS ID Format & Implementation Guide

This guide describes how the **PCDS ID** is structured and how to implement it in a practical, scalable way.

---

## 🧩 PCDS ID Structure

Each PCDS ID is composed of:


**Example:**


---

## 📚 Field Descriptions

| Field                  | Length | Description                                                                 |
|------------------------|--------|-----------------------------------------------------------------------------|
| `Template Issuer`      | 3      | Identifies the template issuer (e.g., `010` for Terra Matters)             |
| `Document Type`        | 2      | Document type code (e.g., `02` for PCDS)                                   |
| `Template Code`        | 3      | Template-specific ID within the issuer/type context                        |
| `Check Digit`          | 1      | Validates the 8-digit prefix using a weighted algorithm                    |
| `PCDS Sequence Number` | 7      | Sequential number per PCDS document issued for this template               |
| `Revision` (optional)  | —      | Version number (e.g., `:001`)                                              |

---

## ✅ Check Digit Calculation

The **check digit** helps detect input errors (like in GTIN or barcode systems).

### Weights

| Position   | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|------------|---|---|---|---|---|---|---|---|
| Weight     | 1 | 3 | 1 | 3 | 1 | 3 | 1 | 3 |

### Example Calculation

For prefix: `01002001`


Resulting prefix = `010 02 001 2`

---

## 🚀 MVP Implementation Strategy

Since we only use one template issuer and one document type at launch, we **don't need to build registries yet**.

### Simplified Approach:
- Add the fixed prefix (`Template Issuer + Document Type + Template Code + Check Digit`) directly in each `template.json`.

#### Example `template.json`:

```json
{
  "template_uuid": "some-uuid",
  "template_name": "PCDS Sample Template",
  "pcds_id_prefix": "010 02 001 2"
}


PCDS ID: 010 02 001 2 0000075
With revision: 010 02 001 2 0000075:001

</details>

