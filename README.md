# Delivery Delays and Customer Satisfaction in Brazilian E-commerce (Olist)

Exploratory data analysis of how late deliveries relate to customer reviews on the Olist marketplace, and where the delays come from (regions and sellers).

**Tools:** Python, pandas, matplotlib, Google Colab, kagglehub

**Notebook:** [`EDA_Project_Masnyk.ipynb`](./EDA_Project_Masnyk.ipynb)

## Business questions

1. Which Brazilian states most often receive orders later than the delivery date promised to the customer?
2. Are late deliveries associated with lower review scores, and does the score fall as the delay grows?
3. Are late orders concentrated among a small share of sellers? Are there problematic sellers, and where are they located?

## Data

[Olist Brazilian E-commerce dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) (Kaggle): about 100,000 orders from September 2016 to October 2018, spread across linked tables. This project uses `orders`, `customers`, `order_items`, `order_reviews` and `sellers`.

Only orders with status `delivered` are analyzed (96,456 orders after removing 22 rows with missing dates). Delay is defined as `actual delivery date − estimated delivery date`, in whole days.

## Key findings

- **Late delivery is rare overall, but uneven by region.** About 6.8% of delivered orders arrive after the estimated date, and the median order arrives 12 days early, so the estimate contains a large safety buffer. The delay rate is highest in the north-east (Alagoas 21.4%, Maranhão 17.5%, Sergipe 15.2%) and lowest in the south and south-east (São Paulo 4.5%, Minas Gerais 4.6%, Paraná 4.0%).
- **Late orders get much worse reviews.** Mean review score is 4.29 for on-time orders and 2.27 for late ones. The share of 1–2 star reviews rises from 9% (on time or early) to 32% (1–3 days late) and 68% (4–7 days late), then levels off at about 80%. The first days of delay matter most.
- **The sellers with the most late orders are not the worst sellers.** 14 sellers (0.5% of all sellers) account for 20% of late orders, but they also handle about 16% of all orders, and their delay rates are close to the marketplace average. Sellers with a truly high delay rate (at least 30 orders and 15%+ late: 35 of 614 sellers, rates of 20–36%) are mid-sized, and most of them are in São Paulo, where most sellers are.

## Recommendations

- Focus on the first few days of delay, as they cause the biggest drop in review scores.
- Review how the estimated delivery date is calculated: most orders arrive far earlier than promised.
- Monitor sellers by delay rate (30+ orders and 15%+ late), not by the number of late orders, which mostly reflects seller size.

## Limitations

- The analysis shows association, not causation. Reviews also depend on the product and the seller, and 646 delivered orders have no review.
- Delay is attributed to the seller, but part of it may come from the carrier or the distance.
- Only delivered and single-seller orders are analyzed.
- Small states have few orders, so their rates can be noisy.

## How to run

Open the notebook in Google Colab (the dataset is downloaded in the first cell with `kagglehub`), or run it locally:
   ```bash
   pip install kagglehub pandas matplotlib jupyter
   jupyter notebook EDA_Project_Masnyk.ipynb
   ```


## Author
**Mykhailo Masnyk**
