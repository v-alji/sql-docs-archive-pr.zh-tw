---
title: XML 系統預存程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- system stored procedures [SQL Server], XML
- sp_xml_removedocument
- OPENXML statement, system stored procedures
- sp_xml_preparedocument
- XML [SQL Server], system stored procedures
ms.assetid: e60c7f85-6823-4d28-93d6-b053d08cc830
author: rothja
ms.author: jroth
ms.openlocfilehash: 2008294fe5bc532dfb6883656420b4189e4da7b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597673"
---
# <a name="xml-system-stored-procedures"></a><span data-ttu-id="84b4d-102">XML 系統預存程序</span><span class="sxs-lookup"><span data-stu-id="84b4d-102">XML System Stored Procedures</span></span>
  <span data-ttu-id="84b4d-103">SQL Server 提供以下系統預存程序，可與 OPENXML 一起使用：</span><span class="sxs-lookup"><span data-stu-id="84b4d-103">SQL Server provides the following system stored procedures that are used together with OPENXML:</span></span>  
  
-   [<span data-ttu-id="84b4d-104">sp_xml_preparedocument &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="84b4d-104">sp_xml_preparedocument &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql)  
  
-   [<span data-ttu-id="84b4d-105">sp_xml_removedocument &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="84b4d-105">sp_xml_removedocument &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql)  
  
 <span data-ttu-id="84b4d-106">若要利用 OPENXML 來寫入查詢，您必須先呼叫 **sp_xml_preparedocument**來建立 XML 文件的內部表示。</span><span class="sxs-lookup"><span data-stu-id="84b4d-106">To write queries by using OPENXML, you must first create an internal representation of the XML document by calling **sp_xml_preparedocument**.</span></span> <span data-ttu-id="84b4d-107">預存程序將控制代碼傳回 XML 文件的內部表示。</span><span class="sxs-lookup"><span data-stu-id="84b4d-107">The stored procedure returns a handle to the internal representation of the XML document.</span></span> <span data-ttu-id="84b4d-108">接著將此控制代碼傳遞至 OPENXML。</span><span class="sxs-lookup"><span data-stu-id="84b4d-108">This handle is then passed to OPENXML.</span></span> <span data-ttu-id="84b4d-109">OPENXML 提供以 XPath 為基礎的文件之資料列集檢視。</span><span class="sxs-lookup"><span data-stu-id="84b4d-109">OPENXML provides rowset views of the document based on XPaths.</span></span> <span data-ttu-id="84b4d-110">具體而言，這是一個資料列模式以及一或多個資料行模式。</span><span class="sxs-lookup"><span data-stu-id="84b4d-110">Specifically, this is one row pattern and one or more column patterns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84b4d-111">由 **sp_xml_preparedocument** 傳回的文件控制代碼在工作階段持續時間內是有效的。</span><span class="sxs-lookup"><span data-stu-id="84b4d-111">The document handle that is returned by **sp_xml_preparedocument** is valid for the duration of the session.</span></span>  
  
 <span data-ttu-id="84b4d-112">可呼叫 **sp_xml_removedocument** 系統預存程序來從記憶體中移除 XML 文件的內部表示法。</span><span class="sxs-lookup"><span data-stu-id="84b4d-112">The internal representation of an XML document can be removed from memory by calling the **sp_xml_removedocument** system stored procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b4d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84b4d-113">See Also</span></span>  
 <span data-ttu-id="84b4d-114">[OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="84b4d-114">[OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql) </span></span>  
 [<span data-ttu-id="84b4d-115">OPENXML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="84b4d-115">OPENXML &#40;SQL Server&#41;</span></span>](../xml/openxml-sql-server.md)  
  
  
