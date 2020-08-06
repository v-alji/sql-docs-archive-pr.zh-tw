---
title: SqlXmlAdapter 物件 (SQLXML Managed 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- void Update(DataSet ds) method
- SqlXmlAdapter object
- void Fill(DataSet ds) method
- SQLXML Managed Classes, SqlXmlAdapter object
- Managed Classes [SQLXML], SqlXmlAdapter object
ms.assetid: 0a16eddf-fc26-4d92-82d4-359b5fb905d5
author: rothja
ms.author: jroth
ms.openlocfilehash: 1357ab7d070c7c2e451e31bccfda22c58eac42d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585244"
---
# <a name="sqlxmladapter-object-sqlxml-managed-classes"></a><span data-ttu-id="70b04-102">SqlXmlAdapter 物件 (SQLXML Managed 類別)</span><span class="sxs-lookup"><span data-stu-id="70b04-102">SqlXmlAdapter Object (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="70b04-103">這個物件會提供一些方法，方便您與 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 中的資料集進行互動。</span><span class="sxs-lookup"><span data-stu-id="70b04-103">This object provides methods that facilitate interaction with the dataset in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework.</span></span> <span data-ttu-id="70b04-104">如需實用範例，請參閱[存取 .Net 環境中的 SQLXML 功能](accessing-sqlxml-functionality-in-the-net-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="70b04-104">For a working sample, see [Accessing SQLXML Functionality in the .NET Environment](accessing-sqlxml-functionality-in-the-net-environment.md).</span></span>  
  
 <span data-ttu-id="70b04-105">SqlXmlAdapter 物件支援下列方法：</span><span class="sxs-lookup"><span data-stu-id="70b04-105">The SqlXmlAdapter object supports these methods:</span></span>  
  
 <span data-ttu-id="70b04-106">void Fill (資料集 ds) </span><span class="sxs-lookup"><span data-stu-id="70b04-106">void Fill(DataSet ds)</span></span>  
 <span data-ttu-id="70b04-107">將 .NET Framework 中的資料集填滿從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中擷取的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="70b04-107">Fills the dataset in the .NET Framework with the XML data retrieved from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="70b04-108">void Update (資料集 ds) </span><span class="sxs-lookup"><span data-stu-id="70b04-108">void Update(DataSet ds)</span></span>  
 <span data-ttu-id="70b04-109">從資料集中的資料，將更新套用至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的記錄。</span><span class="sxs-lookup"><span data-stu-id="70b04-109">Applies updates to records in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] from the data in the dataset.</span></span>  
  
 <span data-ttu-id="70b04-110">SqlXmlAdapter 物件支援下列函數：</span><span class="sxs-lookup"><span data-stu-id="70b04-110">The SqlXmlAdapter object supports these constructors:</span></span>  
  
```  
public SqlXmlAdapter(SqlXmlCommand  cmd)   
  
public SqlXmlAdapter(  
                     string commandText,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                      )   
  
public SqlXmlAdapter(  
                     Stream commandStream,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                     )   
```  
  
## <a name="see-also"></a><span data-ttu-id="70b04-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70b04-111">See Also</span></span>  
 <span data-ttu-id="70b04-112">[SqlXmlCommand 物件 &#40;SQLXML Managed 類別&#41;](sqlxml-4-0-net-framework-support-managed-classes.md) </span><span class="sxs-lookup"><span data-stu-id="70b04-112">[SqlXmlCommand Object &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md) </span></span>  
 [<span data-ttu-id="70b04-113">SqlXmlParameter 物件 &#40;SQLXML Managed 類別&#41;</span><span class="sxs-lookup"><span data-stu-id="70b04-113">SqlXmlParameter Object &#40;SQLXML Managed Classes&#41;</span></span>](sqlxml-managed-classes-sqlxmlparameter-object.md)  
  
  
