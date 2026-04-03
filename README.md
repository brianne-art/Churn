# Churn
 Customer Churn Analysis: Summary & Recommendations                                         
                                                                                             
  ---
  Exploratory Analysis                                                                       
                                                                                             
  Two features stood out as strong predictors of churn.                                      
                                                                                             
  Contract Type showed the most dramatic separation: month-to-month customers churned at     
  42.7%, compared to 11.3% for one-year contracts and just 2.8% for two-year contracts. This
  suggests that commitment level — or lack thereof — is one of the clearest signals of churn 
  risk.           

  Internet Service Type revealed an unexpected pattern: fiber optic customers churned at     
  41.9%, nearly as high as month-to-month subscribers, while DSL customers churned at 19% and
   customers with no internet service churned at only 7.4%. Given that fiber optic is the    
  premium offering, this elevated churn rate likely reflects unmet expectations around price,
   reliability, or competitive alternatives rather than dissatisfaction with the service tier
   itself.

  ---
  Model
       
  A Gradient Boosting classifier was trained on 80% of the data (5,625 customers) and
  evaluated on a held-out 20% test set (1,407 customers). The model achieved a precision of  
  0.623 and a recall of 0.521.
                                                                                             
  The feature importance rankings reinforced the EDA findings: contract type was by far the  
  most predictive feature, followed by monthly charges, total charges, and tenure. These four
   features together account for the bulk of the model's predictive power, which makes       
  intuitive sense — they collectively describe how financially committed and how
  long-standing a customer relationship is.

  The recall of 52% means the model misses roughly half of actual churners, which is a       
  meaningful limitation. In a retention context, false negatives (missed churners) are
  typically more costly than false positives (unnecessary outreach to loyal customers), so   
  this tradeoff is worth revisiting if the model is operationalized.

  ---
  Recommendations
                 
  1. Prioritize converting month-to-month customers to longer contracts.
  This is the highest-leverage action available. A targeted incentive program — discounts,   
  locked-in pricing, or bundled perks — aimed at month-to-month customers could meaningfully 
  reduce churn. Even moving a fraction of them to one-year contracts would cut their expected
   churn rate by nearly 75%.                                                                 
                  
  2. Investigate the fiber optic churn problem separately.
  A 42% churn rate among the premium service tier is a red flag that warrants its own
  investigation. Survey recently churned fiber customers to understand whether the driver is 
  pricing, service quality, or competitive offers. This is a retention and product issue, not
   just a sales one.                                                                         
                  
  3. Deploy the model for proactive outreach, with calibrated expectations.                  
  The model can reliably flag a subset of high-risk customers for retention intervention.
  Because recall is moderate, it should be treated as a prioritization tool — directing      
  outreach toward the customers it does flag — rather than a comprehensive churn detection
  system. Pairing model scores with tenure and contract data will help account teams focus on
   the right customers at the right time.

  4. Improve the model over time with richer data.                                           
  The current model relies entirely on account and billing attributes. Adding behavioral
  signals — support ticket frequency, usage trends, login patterns — would likely improve    
  recall substantially and make the model more actionable.
