# Value Proposition of Data Centric Teams

The article **An imagined healthy structure for company truely cares about data** 
([LinkedIn link](https://www.linkedin.com/posts/stanley-xu-06871814_an-imagined-healthy-structure-for-company-activity-6595825115664125952-Y_M2) 
or [Github link](https://aftersound.github.io/thoughts/data-organization-in-imagination)) roughly captures some of my 
thoughts on values of data centric teams, I want to expand that topic a bit more after several conversations with my 
co-workers and friends.

## Recap
First, recap the points mentioned in that article.

Data centric teams’ focus is data. They are closer to business and their values are realized in
- business decisions influenced by data
- business metrics driven by data
- product healthiness indicated by data
- product features powered by data
- product improvement driven by data
- etc. by data

## Expanded Discussion

Those values could be classified into several categories and levels by the nature of data from data work and the type of
 impact the data work/data has on business/product.
 
### Raw data sets  

Raw data sets are unprocessed, typically consists of transactional data generated from business and product flows and 
activity data of users of product.  The most important part of data work about raw data sets is to maintain their 
life-cycles, 
  - make sure they get delivered to where further process is possible on time at expected intervals 
  without loss.
  - make sure they have proper bookkeeping, such as sources, locations, schemas, relations, chronicle 
  records, etc. for discovery, exploration and further processing.  

  Raw data sets are the foundation data layer. Data work handling raw data sets sounds mundane, and the value of such 
  data work is often ignored, overlooked, underestimated. But in fact, it has to be solid as rock simply because the 
  data sets are so fundamental.

### Integrated data sets  

Integrated data sets are derived from raw data sets by applying
  - cleansing
  - integrity validation
  - schema/relation rectification
  - schema/relation adjustment/optimization
  - tagging (typically for user activity data)
  - sessionization (typically for user activity data)
  - other lightweight processing

  Integrated data sets are certified/trusted, also systematically optimized, data layer, which is expected to be 
  consumed by further data processing/mining. Data work that produces and maintains integrated data sets has the 
  similar rhythms as that for raw data sets, the difference is it does many heavy liftings for those working on insights 
  data sets, including analytic folks, data scientists, data engineers, for downstream systems relying on high quality 
  source data somewhat integrated.

### Insight data sets  

Insight data sets are what business/product teams are constantly looking for. They could be grouped into three levels.

  - Level 1
    - insight data sets which could tell whether business is performing and whether product is healthy, but they can 
    not tell why business is performing or not performing, or how to improve product. They are basic, they are must-have.
    
  - Level 2
    - insight data sets which could influence business decision, guide business operation, improve product. Typically, 
    at this level, business teams and product teams know exactly what kind of data insight they are looking for to meet 
    the needs at their end, no matter it's supporting data for a pending decision or a missing data for a product 
    feature. Insight data sets at this level have direct impact on driving business and product metrics.
  
  - Level 3
    - insight data sets which could predict how business/product should/could be improved. Insight data sets at this 
    level also have direct impact on driving business and product metrics. The differences from level 2 are (1) Data 
    teams mines data insight which identifies the opportunities which are out of mind of business/product team, (2) 
    the impact could be more significant.

## Conclusion

With that, here is the conclusion by reiterating the points. The value proposition of data centric teams is lying in 
mining and managing those data sets which could  

- indicate business and product healthiness
- influence business decisions
- guide business operation
- improve product features
- drive business and product metrics
- power new products and new business territories

The KPIs to measure the success of data centric teams is expected to be set around these points instead of supporting 
KPIs, like unit test coverage, etc.