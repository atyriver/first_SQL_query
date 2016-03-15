# first_SQL_query
Ran this query to determine the specific problem in a client's profitability reporting

SELECT delivery_order.time_delivered, manifest.driver_id, delivery_order.invoice, 
order_detail.unit_cost, order_detail.quantity,
order_detail.part_number, order_detail.description, order_detail.sale_cost, 
order_detail.sale_price 
FROM manifest FULL JOIN delivery_order ON manifest.id=delivery_order.manifest_ID 
FUll JOIN order_detail ON delivery_order.invoice=order_detail.invoice
WHERE delivery_order.delivered='TRUE' 
AND delivery_order.time_delivered IS NOT NULL
AND delivery_order.time_delivered>='2016-02-10 00:00:00-06' 
AND delivery_order.time_delivered<='2016-02-11 00:00:00-06'
AND manifest.driver_id IS NOT NULL
AND manifest.driver_id=6 
ORDER BY delivery_order.time_delivered DESC;
