---
title: "WillChangeField and FieldChangeComplete Events (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: bc4455a6-2925-33dc-d04f-8ea570e5e370

---

# WillChangeField and FieldChangeComplete Events (ADO)

The **WillChangeField** event is called before a pending operation changes the value of one or more [Field](field-object-ado.md) objects in the [Recordset](recordset-object-ado.md). The **FieldChangeComplete** event is called after the value of one or more **Field** objects has changed. 
  
## Syntax

 **WillChangeField** *cFields*  ,  *Fields*  ,  *adStatus*  ,  *pRecordset* 
  
 **FieldChangeComplete** *cFields*  ,  *Fields*  ,  *pError*  ,  *adStatus*  ,  *pRecordset* 
  
## Parameters

-  *cFields* 
    
- A **Long** that indicates the number of **Field** objects in  *Fields*  . 
    
-  *Fields* 
    
- For **WillChangeField**, the  *Fields*  parameter is an array of **Variants** that contains **Field** objects with the original values. 
  
 For **FieldChangeComplete**, the  *Fields*  parameter is an array of **Variants** that contains **Field** objects with the changed values. 
    
-  *pError* 
    
- An [Error](error-object-ado.md) object. It describes the error that occurred if the value of  *adStatus*  is **adStatusErrorsOccurred**; otherwise it is not set. 
    
-  *adStatus* 
    
- [EventStatusEnum](eventstatusenum.md)
    
    When **WillChangeField** is called, this parameter is set to **adStatusOK** if the operation that caused the event was successful. It is set to **adStatusCantDeny** if this event cannot request cancellation of the pending operation. 
    
    When **FieldChangeComplete** is called, this parameter is set to **adStatusOK** if the operation that caused the event was successful, or to **adStatusErrorsOccurred** if the operation failed. 
    
    Before **WillChangeField** returns, set this parameter to **adStatusCancel** to request cancellation of the pending operation. 
    
    Before **FieldChangeComplete** returns, set this parameter to **adStatusUnwantedEvent** to prevent subsequent notifications. 
    
-  *pRecordset* 
    
- A **Recordset** object. The **Recordset** for which this event occurred. 
    
## Remarks

A **WillChangeField** or **FieldChangeComplete** event may occur when setting the [Value](value-property-ado.md) property and calling the [Update](update-method-ado.md) method with field and value array parameters. 
  
