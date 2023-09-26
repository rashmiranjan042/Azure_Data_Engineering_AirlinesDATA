```dax
// creating a table called as business kpi
//under that creating measure one by one
//drag charts
//mostly card chart type used in this report

Total_revenue = SUM('fact_table'[total_amount])  

fare_amount = SUM(fact_table[fare_amount])

Tip_amount = SUM('fact_table'[tip_amount]) 

Totaltrips = COUNTROWS('fact_table')

mta_tax = SUM(fact_table[mta_tax])

tolls_amount = sum(fact_table[tolls_amount])

extra = sum(fact_table[extra])

improvement_surcharge = sum(fact_table[improvement_surcharge])

CountVendorID1 = 
    COUNTROWS(
        FILTER(
            'fact_table',
            'fact_table'[VendorID] = 1
        )
    )


CountVendorID2 = 
    COUNTROWS(
        FILTER(
            'fact_table',
            'fact_table'[VendorID] = 2
        )
    )

standardratetrips = 
 COUNTROWS(
        FILTER(
            'rate_code_dim',
            'rate_code_dim'[RatecodeID] = 1
        )
    )


JFKrate = 
 COUNTROWS(
        FILTER(
            'rate_code_dim',
            'rate_code_dim'[RatecodeID] = 2
        )
    )


Newark = COUNTROWS(
        FILTER(
            'rate_code_dim',
            'rate_code_dim'[RatecodeID] = 3
        )
    )


Nassau or Westchester = COUNTROWS(
        FILTER(
            'rate_code_dim',
            'rate_code_dim'[RatecodeID] = 4
        )
    )

Negotiated fare = COUNTROWS(
        FILTER(
            'rate_code_dim',
            'rate_code_dim'[RatecodeID] = 5
        )
    )

Group ride = COUNTROWS(
        FILTER(
            'rate_code_dim',
            'rate_code_dim'[RatecodeID] = 6
        )
    )

creditcard = 
    COUNTROWS(
        FILTER(
            'payment_type_dim',
            'payment_type_dim'[payment_type] = 1
        )
    )

cash = COUNTROWS(
        FILTER(
            'payment_type_dim',
            'payment_type_dim'[payment_type] = 2
        )
    )

No charge = COUNTROWS(
        FILTER(
            'payment_type_dim',
            'payment_type_dim'[payment_type] = 3
        )
    )

Unknown = 
IF
(ISBLANK(COUNTROWS(
        FILTER(
            'payment_type_dim',
            'payment_type_dim'[payment_type] = 5
        )
    )
),0)

Voided trip = 
IF
(ISBLANK(COUNTROWS(
        FILTER(
            'payment_type_dim',
            'payment_type_dim'[payment_type] = 6
        )
    )
),0)
