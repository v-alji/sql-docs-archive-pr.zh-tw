---
title: SQL Server Management Studio 中的 Reporting Services (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], how-to topics
ms.assetid: 60685458-9108-47bf-820a-5e7db454d408
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3f4083d8b288c8816925723f4cfaef4342dd0298
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704837"
---
# <a name="reporting-services-in-sql-server-management-studio-ssrs"></a><span data-ttu-id="4f898-102">SQL Server Management Studio (SSRS) 中的 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="4f898-102">Reporting Services in SQL Server Management Studio (SSRS)</span></span>
  <span data-ttu-id="4f898-103">報表伺服器管理員可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="4f898-103">Report server administrators can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to:</span></span>  
  
-   <span data-ttu-id="4f898-104">啟用功能、設定伺服器預設值，以及管理正在執行的作業。</span><span class="sxs-lookup"><span data-stu-id="4f898-104">Enable features, set server defaults, and manage running jobs.</span></span>  
  
-   <span data-ttu-id="4f898-105">檢視及建立自訂報表。</span><span class="sxs-lookup"><span data-stu-id="4f898-105">View and create custom reports.</span></span> <span data-ttu-id="4f898-106">在物件總管中，許多節點會顯示一組與 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]一起安裝的標準報表。</span><span class="sxs-lookup"><span data-stu-id="4f898-106">In Object Explorer, many nodes display a set of standard reports that are installed with [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="4f898-107">您必須具有下列管理員權限：</span><span class="sxs-lookup"><span data-stu-id="4f898-107">You must have administrator permissions.</span></span> <span data-ttu-id="4f898-108">自訂報表的結構描述必須符合已安裝報表的結構描述。</span><span class="sxs-lookup"><span data-stu-id="4f898-108">The schema of a custom report must match the schema of the installed reports.</span></span> <span data-ttu-id="4f898-109">如需詳細資訊，請參閱 [Management Studio 中的自訂報表](../../ssms/object/custom-reports-in-management-studio.md)和[尋找報表定義結構描述版本 &#40;SSRS&#41;](../reports/find-the-report-definition-schema-version-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4f898-109">For more information, see [Custom Reports in Management Studio](../../ssms/object/custom-reports-in-management-studio.md) and [Find the Report Definition Schema Version &#40;SSRS&#41;](../reports/find-the-report-definition-schema-version-ssrs.md).</span></span>  
  
 <span data-ttu-id="4f898-110">報表作者可以使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="4f898-110">Report authors can use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to:</span></span>  
  
-   <span data-ttu-id="4f898-111">將對應報表查詢結果集的空間資料視覺化。</span><span class="sxs-lookup"><span data-stu-id="4f898-111">Visualize spatial data from a query result set for a map report.</span></span> <span data-ttu-id="4f898-112">執行查詢後，請使用 [結果集] 窗格中的 [空間結果]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="4f898-112">After you run the query, use the **Spatial results** tab in the result set pane.</span></span> <span data-ttu-id="4f898-113">如需詳細資訊，請參閱 [檢視物件總管中的空間資料](../../relational-databases/scripting/view-spatial-data-in-object-explorer.md)。</span><span class="sxs-lookup"><span data-stu-id="4f898-113">For more information, see [View Spatial Data in Object Explorer](../../relational-databases/scripting/view-spatial-data-in-object-explorer.md).</span></span>  
  
 <span data-ttu-id="4f898-114">本節包含使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]執行各種報表工作的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="4f898-114">This section contains step-by-step instructions for performing various reporting tasks using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="4f898-115">您也可以使用報表管理員來執行建立和管理共用排程的作業。</span><span class="sxs-lookup"><span data-stu-id="4f898-115">Creating and managing shared schedules can also be performed using Report Manager.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4f898-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="4f898-116">In This Section</span></span>  
  
-   [<span data-ttu-id="4f898-117">連接至 Management Studio 中的報表伺服器</span><span class="sxs-lookup"><span data-stu-id="4f898-117">Connect to a Report Server in Management Studio</span></span>](connect-to-a-report-server-in-management-studio.md)  
  
-   [<span data-ttu-id="4f898-118">設定報表伺服器屬性 &#40;Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="4f898-118">Set Report Server Properties &#40;Management Studio&#41;</span></span>](set-report-server-properties-management-studio.md)  
  
-   [<span data-ttu-id="4f898-119">建立、刪除或修改角色 &#40;Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="4f898-119">Create, Delete, or Modify a Role &#40;Management Studio&#41;</span></span>](../security/role-definitions-create-delete-or-modify.md)  
  
-   [<span data-ttu-id="4f898-120">刪除項目 &#40;Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="4f898-120">Delete an Item &#40;Management Studio&#41;</span></span>](delete-an-item-management-studio.md)  
  
-   [<span data-ttu-id="4f898-121">取消報表伺服器作業 &#40;Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="4f898-121">Cancel Report Server Jobs &#40;Management Studio&#41;</span></span>](cancel-report-server-jobs-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="4f898-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f898-122">See Also</span></span>  
 <span data-ttu-id="4f898-123">[Management Studio F1 說明中的報表伺服器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="4f898-123">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="4f898-124">SQL Server Management Studio 簡介</span><span class="sxs-lookup"><span data-stu-id="4f898-124">Introducing SQL Server Management Studio</span></span>](../../ssms/sql-server-management-studio-ssms.md)  
  
  
