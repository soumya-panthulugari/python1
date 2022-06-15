
``` mermaid
graph TB
    subgraph Mongo-DB
    User-Table;
    Products-Table;
    Orders-Table;
    end
    subgraph API
    auth;
    Catalog;
    Orders;
    end
    User-Interface-->|credentials|auth-->User-Table-->auth-->|token|User-Interface;
    
    
    User-Interface-->|token|Catalog-->Products-Table;
    Products-Table-->|Items-Data|Catalog-->|Items-Data-Json|User-Interface;
    
    User-Interface-->|token,Order Summary|Orders;
    Orders-->|Checking|Products-Table;
    Products-Table-->|Conforming|Orders;
    Orders-->|Order-Date|Orders-Table;
    Orders-Table-->|Order-Id|Orders;
    Orders-->|Order-Id|User-Interface;
    
```
