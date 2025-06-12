---
sidebar_position: 1
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Code Blocks

```jsx title="generic code block"
This is a generic code block
```

```js title="javascript"
console.log('This is a javascript code block.')
```

```ccl title="CCL"
SELECT *
FROM ENCOUNTER e
PLAN e WHERE e.end_effective_dt_tm > SYSDATE
  AND e.active_ind = 1 ;include only active rows
WITH TIME=30, MAXREC=30, UAR_CODE(D)
```

```ccl title="subroutine" showLineNumbers
/* This is a multiline comment.
    %i testing
    SELECT PLAN
   Is it captured correctly? */
%I cust_script:dalt_subroutines.inc
%i cust_script:secondary.inc
subroutine (get_eid_from_fin(input=c30) = f8)
  DECLARE output = f8 %i another
  SET output = $prompt_var
  SELECT INTO "NL:"
  FROM ENCNTR_ALIAS fin
  PLAN fin WHERE fin.alias = input
    AND fin.encntr_alias_type_cd = 1077 ;fin
    AND fin.active_ind = 1
  DETAIL
    IF(fin.encntr_id != 0)
      output = fin.encntr_id
      ids->success_ind = 1
    ELSE ids->success_ind = 0
    ENDIF
  WITH nocounter
  RETURN (output)
end ;get_eid_from_fin

fin = fin.alias
,encntr_type = UAR_GET_CODE_DISPLAY(e.encntr_type_cd)
,SUBSTRING(1,200, TRIM(UAR_GET_CODE_DESCRIPTION(e.loc_facility_cd)))

string = "this is a string"
```


<Tabs>
<TabItem value="ccl" label="CCL">

```ccl
SELECT *
FROM ENCOUNTER e
PLAN e WHERE e.active_ind = 1
WITH TIME=30, MAXREC=30, UAR_CODE(D)
```

</TabItem>
<TabItem value="sql" label="SQL">

```sql
SELECT *
FROM FEDERAL_P0630.ENCOUNTER e
WHERE e.active_ind = 1
LIMIT 30
```

</TabItem>
<TabItem value="java" label="Java">

```java
class HelloWorld {
  public static void main(String args[]) {
    System.out.println("Hello, World");
  }
}
```

</TabItem>
</Tabs>

Links:
 - [Code Blocks](https://docusaurus.io/docs/markdown-features/code-blocks)
