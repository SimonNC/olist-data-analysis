### Data source configuration
The dashboard uses a single Power BI parameter `DataFolder`.
Update this parameter to point to the local `data_cleaned/` directory before refreshing the model.


## Power BI Dashboard

### Pages
- Sales: revenue structure and trends
- Delivery: logistics performance and reliability
- Review: customer satisfaction drivers

### Data Model
- orders_clean (fact)
- order_items_clean (fact)
- customers_clean (dim)
- products_clean (dim)
- reviews_clean (fact)

### Key Metrics
- Total Revenue
- AOV
- On-Time Delivery Rate
- Avg Review Score
