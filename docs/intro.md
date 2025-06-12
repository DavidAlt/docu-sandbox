---
sidebar_position: 1
---


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
PLAN e WHERE e.active_ind = 1
WITH TIME=30, MAXREC=30, UAR_CODE(D)
```

```sql title="Health Analytics"
SELECT *
FROM FEDERAL_P0630.ENCOUNTER e
WHERE e.active_ind = 1
LIMIT 30
```


import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

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
