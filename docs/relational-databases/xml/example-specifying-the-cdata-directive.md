---
title: "Example: Specifying the CDATA Directive | Microsoft Docs"
description: View an example of how to specify the CDATA directive to wrap the specified data in a CDATA section.
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: sql
ms.prod_service: "database-engine"
ms.reviewer: ""
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords: 
  - "CDATA directive"
ms.assetid: 949071e6-787f-480d-bb86-3ac16a027af1
author: MikeRayMSFT
ms.author: mikeray
---
# Example: Specifying the CDATA Directive
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  If the directive is set to **CDATA**, the contained data is not entity encoded, but is put in the CDATA section. The **CDATA** attributes must be nameless.  
  
 The following query wraps the product model summary description in a CDATA section.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        '<Summary>This is summary description</Summary>'     
            as [ProductModel!1!!CDATA] -- no attribute name so ELEMENT assumed  
FROM    Production.ProductModel  
WHERE   ProductModelID=19  
FOR XML EXPLICIT  
```  
  
 This is the result:  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
   <![CDATA[<Summary>This is summary description</Summary>]]>  
</ProductModel>  
```  
  
## See Also  
 [Use EXPLICIT Mode with FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
  
  
