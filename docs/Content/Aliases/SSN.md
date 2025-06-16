import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

## Concept
SSN (Social Security Number) is a unique person identifier. It should be used in queries/reports only when no viable alternative exists under the Social ...

## Code
SSN is a person-level alias stored in the PERSON_ALIAS table. As with all aliases, the type of alias can be specified either by alias type or alias pool.

```PERSON_ALIAS.person_alias_type_cd = 18```
 or  
```PERSON_ALIAS.alias_pool_cd = 683997```

<Tabs>
<TabItem value="ccl" label="CCL">
```ccl
SELECT ssn = ssn.alias
FROM PERSON_ALIAS ssn
PLAN ssn WHERE ssn.person_alias_type_cd = 18 ;SSN
    AND ssn.end_effective_dt_tm > SYSDATE ;only return current aliases
    AND ssn.active_ind = 1 ;only return active (valid) aliases
```
</TabItem>

<TabItem value="sql" label="SQL (HeA)">
```sql
SELECT ssn.alias AS ssn
FROM FEDERAL_P0630.PERSON_ALIAS ssn
WHERE ssn.person_alias_type_cd = 18 --SSN
    AND ssn.end_effective_dt_tm > SYSDATE --only return current aliases
    AND ssn.active_ind = 1 --only return active (valid) aliases
```
</TabItem>
</Tabs>

## Related Topics
* Alias