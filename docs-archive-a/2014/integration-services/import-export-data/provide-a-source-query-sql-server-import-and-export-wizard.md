---
title: 提供來源查詢 (SQL Server 匯入和匯出精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.providesourcequery.f1
ms.assetid: c8cbd07e-b9c3-422f-94b8-d6fc8cf31cf5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b21100f51c279e9ba764c8f82565af9d6e391ef3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597926"
---
# <a name="provide-a-source-query-sql-server-import-and-export-wizard"></a><span data-ttu-id="96f5e-102">提供來源查詢 (SQL Server 匯入和匯出精靈)</span><span class="sxs-lookup"><span data-stu-id="96f5e-102">Provide a Source Query (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="96f5e-103">使用 [**提供來源查詢**] 頁面，輸入將產生要從資料來源複製到目的地之資料的 SQL 語句。</span><span class="sxs-lookup"><span data-stu-id="96f5e-103">Use the **Provide a Source Query** page to type the SQL statement that will generate the data to copy from the data source to the destination.</span></span>  
  
 <span data-ttu-id="96f5e-104">若要深入瞭解此嚮導，請參閱[SQL Server 匯入和匯出嚮導](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="96f5e-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="96f5e-105">若要瞭解用來啟動精靈的選項，以及成功執行嚮導所需的許可權，請參閱[執行 SQL Server 匯入和匯出嚮導](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="96f5e-105">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="96f5e-106">「SQL Server 匯入和匯出精靈」的用途在於將資料從來源複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="96f5e-106">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="96f5e-107">這個精靈也可以為您建立目的地資料庫和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="96f5e-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="96f5e-108">不過，如果您必須複製多個資料庫或資料表，或複製其他種類的資料庫物件，則應該改用「複製資料庫精靈」。</span><span class="sxs-lookup"><span data-stu-id="96f5e-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="96f5e-109">如需詳細資訊，請參閱 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="96f5e-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="96f5e-110">選項</span><span class="sxs-lookup"><span data-stu-id="96f5e-110">Options</span></span>  
 <span data-ttu-id="96f5e-111">**SQL 語句**</span><span class="sxs-lookup"><span data-stu-id="96f5e-111">**SQL statement**</span></span>  
 <span data-ttu-id="96f5e-112">輸入查詢陳述式，即可從來源資料庫擷取選取的資料列。</span><span class="sxs-lookup"><span data-stu-id="96f5e-112">Type a query statement to retrieve selected rows of data from the source database.</span></span> <span data-ttu-id="96f5e-113">例如，下列查詢陳述式會從 AdventureWorks 資料庫中，擷取佣金百分比超過 1.5% 之業務員的 **SalesPersonID**、 **SalesQuota**以及 **SalesYTD** 。</span><span class="sxs-lookup"><span data-stu-id="96f5e-113">For example, the following query statement retrieves the **SalesPersonID**, **SalesQuota**, and **SalesYTD** from the AdventureWorks database for sales persons whose commission percentage is more than 1.5 percent.</span></span>  
  
```  
SELECT SalesPersonID, SalesQuota, SalesYTD  
FROM Sales.SalesPerson  
WHERE CommissionPct > 0.015  
```  
  
 <span data-ttu-id="96f5e-114">**剖析**</span><span class="sxs-lookup"><span data-stu-id="96f5e-114">**Parse**</span></span>  
 <span data-ttu-id="96f5e-115">檢查 [SQL 陳述式]\*\*\*\* 文字方塊中，SQL 陳述式的語法。</span><span class="sxs-lookup"><span data-stu-id="96f5e-115">Checks the syntax of the SQL statement in the **SQL statement** text box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="96f5e-116">如果檢查陳述式語法所需的時間超過逾時值 30 秒，剖析就會停止並產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="96f5e-116">If the time that is required to check the syntax of the statement exceeds the time-out value of 30 seconds, parsing stops and generates an error.</span></span> <span data-ttu-id="96f5e-117">在剖析成功之前，您將無法移過精靈的這個頁面。</span><span class="sxs-lookup"><span data-stu-id="96f5e-117">You will not be able to move past this page of the wizard until parsing succeeds.</span></span> <span data-ttu-id="96f5e-118">有一種解決方法是建立以查詢為基礎的資料庫檢視，然後從精靈查詢此檢視，而非直接輸入查詢文字。</span><span class="sxs-lookup"><span data-stu-id="96f5e-118">One solution is to create a database view based on the query, and to query the view from the wizard, instead of entering the query text directly.</span></span>  
  
 <span data-ttu-id="96f5e-119">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="96f5e-119">**Browse**</span></span>  
 <span data-ttu-id="96f5e-120">使用 [**開啟**] 對話方塊來選取包含 SQL 語句的檔案。</span><span class="sxs-lookup"><span data-stu-id="96f5e-120">Select a file containing a SQL statement by using the **Open** dialog box.</span></span> <span data-ttu-id="96f5e-121">選取檔案就會將該檔案的文字複製到 **[查詢陳述式]** 文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="96f5e-121">Selecting a file copies the text from the file into the **Query statement** text box.</span></span>  
  
  
