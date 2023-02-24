# Использование XPATH в XML

Пример XML файла

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes" ?>
<SiebelMessage MessageId="07f33fa0-2045-46fd-b88b-5634a3de9a0b" MessageType="Integration Object" IntObjectName="" IntObjectFormat="Siebel Hierarchical" ReturnCode="0" ErrorMessage="">
    <listOfReadAudit >
        <readAudit id="root">
            <recordId mapping="Record ID"></recordId>
            <userId mapping="User ID"></userId>
            <customerId mapping="Customer ID"></customerId>
            <lastUpd mapping="Last Updated"></lastUpd>
            <lastUpdBy mapping="Last Updated By"></lastUpdBy>
            <busComp mapping="Entity Name"></busComp>
        </readAudit>
    </listOfReadAudit>
</SiebelMessage>
```

XPATCH запрос `//readAudit[@id='root']`

This selects all `readAudit` elements with the `id` attribute set to `root` (it should be just 1 element in your case).

You could make sure it returns maximum 1 element with this: `//readAudit[@id='root'][1]`

---

**Источник**

- [https://stackoverflow.com/questions/22556423/xpath-search-by-id-attribute-giving-npe-java](https://stackoverflow.com/questions/22556423/xpath-search-by-id-attribute-giving-npe-java)