---
title: 使用者定義資料類型 (UDT) 的 FOR XML 支援 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- UDTs [SQL Server], XML
- user-defined types [SQL Server], XML
ms.assetid: 354e2150-fa2a-4583-b1aa-6b78ae4378b6
author: rothja
ms.author: jroth
ms.openlocfilehash: b668ad2da13fdfc880ab26cb2b2759ff3693f7d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710446"
---
# <a name="for-xml-support-for-the-user-defined-data-types-udt"></a><span data-ttu-id="353b0-102">使用者自訂資料類型 (UDT) 的 FOR XML 支援</span><span class="sxs-lookup"><span data-stu-id="353b0-102">FOR XML Support for the User-Defined Data Types (UDT)</span></span>
  <span data-ttu-id="353b0-103">FOR XML 不支援 Common Language Runtime (CLR) 使用者定義資料類型 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="353b0-103">FOR XML does not support common language runtime (CLR) user-defined data types (UDTs).</span></span>  
  
 <span data-ttu-id="353b0-104">若要搭配 CLR 使用者定義資料類型使用 FOR XML，請確定此資料類型有 XML 序列化，並在 FOR XML SELECT 子句中使用 XML 的明確轉換。</span><span class="sxs-lookup"><span data-stu-id="353b0-104">To use FOR XML with CLR user-defined data types, make sure that the data type has an XML serialization, and use an explicit cast to XML in the FOR XML select clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="353b0-105">另請參閱</span><span class="sxs-lookup"><span data-stu-id="353b0-105">See Also</span></span>  
 [<span data-ttu-id="353b0-106">各個 SQL Server 資料類型的 FOR XML 支援</span><span class="sxs-lookup"><span data-stu-id="353b0-106">FOR XML Support for Various SQL Server Data Types</span></span>](for-xml-support-for-various-sql-server-data-types.md)  
  
  
