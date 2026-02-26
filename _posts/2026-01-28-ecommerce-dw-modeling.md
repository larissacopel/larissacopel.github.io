---
layout: project
title: "E-commerce Use Case: DW Data Modeling"
tech:
    - Data Modeling
    - Redshift
repository: 
---

This project consists of a use case description of an e-commerce and the design of a Data Warehouse to meet their needs.

### Problem

An e-commerce company operates across various regions of Brazil, selling a range of technology products, including computers, smartphones, and peripherals. The company serves both corporate clients and individual consumers. It aims to monitor and analyze its sales to better understand client behavior, product performance, and regional trends over time.


**Objective**

The company seeks to build a data analytics system for the detailed collection and analysis of sales data. This includes the ability to segment data by client, location, product, and time period. The system is intended to support strategic decision-making, such as launching new promotions, adjusting inventory levels, and expanding into new regions.

**Company Operations Details**

The company sells technology products to its customers, who can be individual consumers or businesses. Each sale is associated with a specific customer and occurs in a specific geographical location. The system needs to record the product sold, the quantity, the selling price, and the product cost.

The company's customer base consists of individuals and businesses. Each customer is uniquely identified and categorized by type (Corporate, Consumer, or Inactive/Deactivated). Information regarding the customer's name and type is essential for segmentation and analysis.

Sales occur in various cities across Brazil. The company needs to know in which city, state, and region each transaction took place to understand regional preferences and adjust its operations according to local demands.

The company sells a variety of technology products, which are organized into different categories and subcategories, such as notebooks, desktops, and smartphones. It is important to track the performance of each product to optimize the portfolio and marketing strategies.

Sales vary over time, with peaks during specific periods like the end of the year or new product launches. The system needs to capture the exact date of each sale, allowing for temporal analysis and the identification of seasonal trends.

## Data Warehouse Modeling

### Conceptual Data Model

<picture>
  <!-- Imagem para Modo Escuro -->
  <source media="(prefers-color-scheme: dark)" srcset="/assets/images/modelo_conceitual_dark.png">
  
  <!-- Imagem para Modo Claro (padrão) -->
  <img src="/assets/images/modelo_conceitual_light.png" alt="Descrição da imagem">
</picture>

### Dimensional Data Model

<pre class="mermaid">
erDiagram
    FCT_SALES ||--|{ FCT_SALES_PRODUCTS : contains
    FCT_SALES ||--|| DIM_CLIENT : is_made_by
    FCT_SALES ||--|| DIM_GEO_LOCATION : is_made_in
    FCT_SALES {
        string id_sale PK
        string id_client FK
        string id_geo_location FK
        date   date
        float  total_price
    }
    FCT_SALES_PRODUCTS ||--|| DIM_PRODUCTS : contains
    FCT_SALES_PRODUCTS {
        string id_sales_products PK
        string id_sale FK
        string id_product FK
        float  product_cost
        float  selling_price
    }
    DIM_CLIENT {
        string id_client PK
        string name
        string type
    }
    DIM_GEO_LOCATION {
        string id_geo_location PK
        string city
        string region
        string state
    }
    DIM_PRODUCTS {
        string id_product PK
        string name
        string category
        string subcategory
    }
</pre>
