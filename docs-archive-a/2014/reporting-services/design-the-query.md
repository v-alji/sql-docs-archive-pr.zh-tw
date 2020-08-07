---
title: 設計查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.designquery.f1
ms.assetid: 2dad800f-10a1-453c-8761-2935b9826d84
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9b56d99ec11b50ce53ef223a01eb5fc2766238ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703926"
---
# <a name="design-the-query"></a><span data-ttu-id="9ab1f-102">設計查詢</span><span class="sxs-lookup"><span data-stu-id="9ab1f-102">Design the Query</span></span>
  <span data-ttu-id="9ab1f-103">使用報表精靈的這個頁面，即可透過手動輸入查詢、使用查詢產生器以互動方式建立查詢或從其他報表匯入查詢，藉以建立查詢。</span><span class="sxs-lookup"><span data-stu-id="9ab1f-103">Use this page of the Report Wizard to create a query by typing the query manually, by using Query Builder to interactively build a query, or by importing a query from another report.</span></span>  
  
 <span data-ttu-id="9ab1f-104">您在 [選取資料來源] 頁面 (報表精靈中之前的頁面) 上所選擇的資料來源類型會決定您可以在這個頁面上輸入的查詢。</span><span class="sxs-lookup"><span data-stu-id="9ab1f-104">The data source type you chose on the Select the Data Source page, a previous page in the Report Wizard, determines the query you can enter on this page.</span></span> <span data-ttu-id="9ab1f-105">例如，如果資料來源類型為 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，您可以輸入 [!INCLUDE[tsql](../includes/tsql-md.md)] 語句或預存程式名稱。</span><span class="sxs-lookup"><span data-stu-id="9ab1f-105">For example, if the data source type is [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you can enter [!INCLUDE[tsql](../includes/tsql-md.md)] statements or stored procedure names.</span></span> <span data-ttu-id="9ab1f-106">如果資料來源類型為 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，則 [查詢] 窗格會停用，而且您無法直接輸入查詢。</span><span class="sxs-lookup"><span data-stu-id="9ab1f-106">If the data source type is [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], the Query pane is disabled and you cannot enter a query directly.</span></span> <span data-ttu-id="9ab1f-107">您可以使用「查詢產生器」來指定查詢。</span><span class="sxs-lookup"><span data-stu-id="9ab1f-107">You can specify the query by using Query Builder.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9ab1f-108">選項。</span><span class="sxs-lookup"><span data-stu-id="9ab1f-108">Options</span></span>  
 <span data-ttu-id="9ab1f-109">**查詢字串**</span><span class="sxs-lookup"><span data-stu-id="9ab1f-109">**Query string**</span></span>  
 <span data-ttu-id="9ab1f-110">輸入查詢，以擷取要在報表中使用的資料。</span><span class="sxs-lookup"><span data-stu-id="9ab1f-110">Type a query that retrieves the data you want to use in your report.</span></span>  
  
 <span data-ttu-id="9ab1f-111">**查詢產生器**</span><span class="sxs-lookup"><span data-stu-id="9ab1f-111">**Query Builder**</span></span>  
 <span data-ttu-id="9ab1f-112">按一下 [查詢產生器]\*\*\*\* 即可為資料來源開啟查詢設計工具，或從其他報表匯入查詢。</span><span class="sxs-lookup"><span data-stu-id="9ab1f-112">Click **Query Builder** to open a query designer for the data source, or to import a query from another report.</span></span>  
  
 <span data-ttu-id="9ab1f-113">如需有關查詢設計工具的詳細資訊，請參閱＜ [Reporting Services Query Designers](../../2014/reporting-services/reporting-services-query-designers.md)＞。</span><span class="sxs-lookup"><span data-stu-id="9ab1f-113">For more information about query designers, see [Reporting Services Query Designers](../../2014/reporting-services/reporting-services-query-designers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ab1f-114">範例</span><span class="sxs-lookup"><span data-stu-id="9ab1f-114">Example</span></span>  
 <span data-ttu-id="9ab1f-115">針對**Microsoft SQL Server**的資料來源類型，下列查詢會從資料庫資料表中抓取姓氏清單 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] `Person` 。</span><span class="sxs-lookup"><span data-stu-id="9ab1f-115">For the data source type **Microsoft SQL Server**, the following query retrieves a list of last names from the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database `Person` table.</span></span>  
  
```  
SELECT LastName FROM Person.Person;  
```  
  
 <span data-ttu-id="9ab1f-116">針對**Microsoft SQL Server**的資料來源類型，下列查詢會 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] `uspGetEmployeeManagers` 針對識別碼為1的員工執行預存程式：</span><span class="sxs-lookup"><span data-stu-id="9ab1f-116">For the data source type **Microsoft SQL Server**, the following query runs the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] stored procedure `uspGetEmployeeManagers` for the employee with identification number 1:</span></span>  
  
```  
EXEC uspgetEmployeeManagers '1';  
```  
  
## <a name="see-also"></a><span data-ttu-id="9ab1f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ab1f-117">See Also</span></span>  
 <span data-ttu-id="9ab1f-118">[報表精靈說明](../../2014/reporting-services/report-wizard-help.md) </span><span class="sxs-lookup"><span data-stu-id="9ab1f-118">[Report Wizard Help](../../2014/reporting-services/report-wizard-help.md) </span></span>  
 <span data-ttu-id="9ab1f-119">[報表內嵌資料集和共用資料集 &#40;報表產生器和 SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9ab1f-119">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="9ab1f-120">將資料加入報表 &#40;報表產生器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9ab1f-120">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-data/report-datasets-ssrs.md)  
  
  
