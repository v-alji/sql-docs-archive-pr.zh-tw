---
title: 無法載入檔案或元件 &#39;的3.5.0.0、Culture = 中性、PublicKeyToken = b77a5c561934e089&#39; 或其相依性的其中之一。 系統找不到指定的檔案。 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 81ed0f44-8782-462d-af8f-0ba5b975df27
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3f9eed7ad90c1e720d07c714e351c24ae6657717
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598586"
---
# <a name="could-not-load-file-or-assembly-39microsoftdataservices-version3500-cultureneutral-publickeytokenb77a5c561934e08939-or-one-of-its-dependencies-the-system-cannot-find-the-file-specified"></a><span data-ttu-id="f6c50-104">無法載入檔案或元件 &#39;的3.5.0.0、Culture = 中性、PublicKeyToken = b77a5c561934e089&#39; 或其相依性的其中之一。</span><span class="sxs-lookup"><span data-stu-id="f6c50-104">Could not load file or assembly &#39;Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089&#39; or one of its dependencies.</span></span> <span data-ttu-id="f6c50-105">系統找不到指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="f6c50-105">The system cannot find the file specified.</span></span>
  <span data-ttu-id="f6c50-106">在擁有 PowerPivot for SharePoint 的 SharePoint 2010 環境中，如果您嘗試匯出資料摘要而且系統遺漏必要的 Microsoft ADO.NET Data Services 版本，將會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="f6c50-106">In SharePoint 2010 environments that have PowerPivot for SharePoint, this error will occur if you attempt a data feed export and the system is missing the required version of Microsoft ADO.NET Data Services.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f6c50-107">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f6c50-107">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f6c50-108">適用於</span><span class="sxs-lookup"><span data-stu-id="f6c50-108">Applies to</span></span>|<span data-ttu-id="f6c50-109">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="f6c50-109">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="f6c50-110">產品版本</span><span class="sxs-lookup"><span data-stu-id="f6c50-110">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="f6c50-111">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6c50-111">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="f6c50-112">原因</span><span class="sxs-lookup"><span data-stu-id="f6c50-112">Cause</span></span>|<span data-ttu-id="f6c50-113">找不到 ADO.NET Data Services 3.5 SP1。</span><span class="sxs-lookup"><span data-stu-id="f6c50-113">ADO.NET Data Services 3.5 SP1 was not found.</span></span>|  
|<span data-ttu-id="f6c50-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f6c50-114">Message Text</span></span>|<span data-ttu-id="f6c50-115">無法載入檔案或組件 'Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' 或是它的其中一個相依性。</span><span class="sxs-lookup"><span data-stu-id="f6c50-115">Could not load file or assembly 'Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.</span></span> <span data-ttu-id="f6c50-116">系統找不到指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="f6c50-116">The system cannot find the file specified</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f6c50-117">說明</span><span class="sxs-lookup"><span data-stu-id="f6c50-117">Explanation</span></span>  
 <span data-ttu-id="f6c50-118">SharePoint 2010 包含一個 [匯出為資料摘要] 按鈕，您可以用它來匯出 SharePoint 清單當做 XML 資料摘要。</span><span class="sxs-lookup"><span data-stu-id="f6c50-118">SharePoint 2010 includes an Export as Data Feed button that you can use to export a SharePoint list as an XML data feed.</span></span> <span data-ttu-id="f6c50-119">此外，SharePoint 模式的 Reporting Services 和 PowerPivot for SharePoint 都支援需要 ADO.NET Data Services 的資料摘要功能。</span><span class="sxs-lookup"><span data-stu-id="f6c50-119">In addition, both Reporting Services in SharePoint mode and PowerPivot for SharePoint support data feed features that require ADO.NET Data Services.</span></span>  
  
 <span data-ttu-id="f6c50-120">如果尚未安裝 ADO.NET Data Services，則當您要求資料摘要時將會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="f6c50-120">If ADO.NET Data Services is not installed, this error will occur when you request a data feed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f6c50-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f6c50-121">User Action</span></span>  
  
1.  <span data-ttu-id="f6c50-122">請移至 SharePoint 2010 的硬體和軟體需求檔，[判斷 (sharepoint 2010)  (的硬體和軟體需求](https://go.microsoft.com/fwlink/?LinkId=169734) https://go.microsoft.com/fwlink/?LinkId=169734) 。</span><span class="sxs-lookup"><span data-stu-id="f6c50-122">Go to the hardware and software requirements documentation for SharePoint 2010, [Determine Hardware and Software Requirements (SharePoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734) (https://go.microsoft.com/fwlink/?LinkId=169734).</span></span>  
  
2.  <span data-ttu-id="f6c50-123">在 [Installing software prerequisites]\*\*\*\* 中，尋找對應到您所使用之作業系統的 ADO.NET Data Services 3.5 連結。</span><span class="sxs-lookup"><span data-stu-id="f6c50-123">In **Installing software prerequisites**, find the link for ADO.NET Data Services 3.5 that corresponds to the operating system you are using.</span></span>  
  
3.  <span data-ttu-id="f6c50-124">按一下該連結，並執行安裝程式來安裝服務。</span><span class="sxs-lookup"><span data-stu-id="f6c50-124">Click the link and run the setup program that installs the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6c50-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6c50-125">See Also</span></span>  
 [<span data-ttu-id="f6c50-126">將 PowerPivot 方案部署到 SharePoint</span><span class="sxs-lookup"><span data-stu-id="f6c50-126">Deploy PowerPivot Solutions to SharePoint</span></span>](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
