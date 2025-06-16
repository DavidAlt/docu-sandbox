import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

## Concept
EDIPI (Electronic Data Interchange Personal Identifier) is a unique person identifier assigned to individuals in DEERS (Defense Enrollment Eligibility Reporting System). It may also be known as DODID.

## Code
EDIPI is a person-level alias with different mappings for patients (PERSON_ALIAS) and personnel (PRSNL_ALIAS). The method to query them is the same, but they use distinct code values. As with all aliases, the type of alias can be specified either by alias type or alias pool.

### Patient EDIPI
```PERSON_ALIAS.person_alias_type_cd = 22```
 or  
```PERSON_ALIAS.alias_pool_cd = 106931653```

<Tabs>
<TabItem value="ccl" label="CCL">
```ccl
SELECT patient_edipi = edipi.alias
FROM PERSON_ALIAS edipi
PLAN edipi WHERE edipi.person_alias_type_cd = 22 ;EDIPI
    AND edipi.end_effective_dt_tm > SYSDATE ;only return current aliases
    AND edipi.active_ind = 1 ;only return active (valid) aliases
```
</TabItem>

<TabItem value="sql" label="SQL (HeA)">
```sql
SELECT edipi.alias AS patient_edipi
FROM FEDERAL_P0630.PERSON_ALIAS edipi
WHERE edipi.person_alias_type_cd = 22 --EDIPI
    AND edipi.end_effective_dt_tm > SYSDATE --only return current aliases
    AND edipi.active_ind = 1 --only return active (valid) aliases
```
</TabItem>
</Tabs>

### Personnel EDIPI
```PRSNL_ALIAS.prsnl_alias_type_cd = 685806```
 or  
```PRSNL_ALIAS.alias_pool_cd = 106935631```

<Tabs>
<TabItem value="ccl" label="CCL">
```ccl
SELECT prsnl_edipi = edipi.alias
FROM PRSNL_ALIAS edipi
PLAN edipi WHERE edipi.prsnl_alias_type_cd = 685806 ;EDIPI
    AND edipi.end_effective_dt_tm > SYSDATE ;only return current aliases
    AND edipi.active_ind = 1 ;only return active (valid) aliases
```
</TabItem>

<TabItem value="sql" label="SQL (HeA)">
```sql
SELECT edipi.alias AS prsnl_edipi
FROM FEDERAL_P0630.PRSNL_ALIAS edipi
WHERE edipi.prsnl_alias_type_cd = 685806 --EDIPI
    AND edipi.end_effective_dt_tm > SYSDATE --only return current aliases
    AND edipi.active_ind = 1 --only return active (valid) aliases
```
</TabItem>
</Tabs>

## Related Topics
* Alias