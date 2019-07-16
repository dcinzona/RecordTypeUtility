##Generic RecordType utility helper class 
Assists with getting and working with Salesforce record types.

```
RecordTypeUtility rtUtil = new RecordTypeUtility();
Id rtID = rtUtil.forObject('ObjectAPIName__c')
    .withPermissions(true)
    .getRecordTypeIdByDeveloperName('RecordType_Developer_Name');
```

Shorthand:
- This is case insensitive.  No need to make sure the character case matches the RecordType character case.  When the query runs, it checks against all lowercase versions of the RecordType.DeveloperName.  This only works with DeveloperName as that must be unique to the object.
```
Id rtId = new RecordTypeUtility('Account')
    .getRecordTypeIdByDeveloperName('my_record_type');
```

Maps:
- When `withPermissions` is passed in, the map returned will only contain the record types that the user can access)
- RecordType.DeveloperName maps have case insentive keys (so you can call `rtUtil.getMap().get('UPPERCASE_RT')` and `rtUtil.getMap().get('lowercase_rt')`)
```
Map<String,RecordTypeInfo> rtInfoMap = new RecordTypeUtility('Account').getMap();
```
```
Map<String,Id> rtIDsMap = new RecordTypeUtility('Account').getIdsMap();
```