---
title: 資料庫引擎伺服器定序不相容 (Upgrade Advisor) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 80f499d6-2c90-49eb-a5b3-0bb5b7faaa3b
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b6ce0555bdf5a878e56d87a8bd55b5ce6c4b2649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606032"
---
# <a name="incompatible-database-engine-server-collation-upgrade-advisor"></a><span data-ttu-id="d95ae-102">不相容的 Database Engine 伺服器定序 (Upgrade Advisor)</span><span class="sxs-lookup"><span data-stu-id="d95ae-102">Incompatible Database Engine Server Collation (Upgrade Advisor)</span></span>
  <span data-ttu-id="d95ae-103">Upgrade Advisor 偵測到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 使用的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 設定為使用不相容的伺服器定序。</span><span class="sxs-lookup"><span data-stu-id="d95ae-103">Upgrade Advisor detected [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is using an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that is configured to use an incompatible server collation.</span></span>  
  
||  
|-|  
|<span data-ttu-id="d95ae-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="d95ae-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="d95ae-105">元件</span><span class="sxs-lookup"><span data-stu-id="d95ae-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="d95ae-106">描述</span><span class="sxs-lookup"><span data-stu-id="d95ae-106">Description</span></span>  
 <span data-ttu-id="d95ae-107">Upgrade Advisor 偵測到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 使用的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 設定為使用不相容的伺服器定序。</span><span class="sxs-lookup"><span data-stu-id="d95ae-107">Upgrade Advisor detected [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is using an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that is configured to use an incompatible server collation.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="d95ae-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Sharepoint 模式會利用 sharepoint 共用服務架構。</span><span class="sxs-lookup"><span data-stu-id="d95ae-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode utilizes the SharePoint shared services architecture.</span></span> <span data-ttu-id="d95ae-109">SharePoint 不支援針對區分大小寫或是伺服器定序或二進位伺服器定序設定的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d95ae-109">SharePoint does not support [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] configured for case sensitive or server collations or binary server collations.</span></span> <span data-ttu-id="d95ae-110">不相容的定序包括預設為區分大小寫或二進位的定序，以及預設不相容，但已透過下列任一定序指示項設定的基底定序：</span><span class="sxs-lookup"><span data-stu-id="d95ae-110">Incompatible collations include collations that are by default case sensitive or binary and a base collation that by default is compatible but has been configured with any of the following collation designators:</span></span>  
  
-   <span data-ttu-id="d95ae-111">**二進位**</span><span class="sxs-lookup"><span data-stu-id="d95ae-111">**Binary**</span></span>  
  
-   <span data-ttu-id="d95ae-112">**區分大小寫**</span><span class="sxs-lookup"><span data-stu-id="d95ae-112">**Case-sensitive**</span></span>  
  
-   <span data-ttu-id="d95ae-113">**二進位字碼指標**</span><span class="sxs-lookup"><span data-stu-id="d95ae-113">**Binary-codepoint**</span></span>  
  
 <span data-ttu-id="d95ae-114">由於目前的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 伺服器定序不相容，因此升級遭到封鎖。</span><span class="sxs-lookup"><span data-stu-id="d95ae-114">Because the current [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] server collation is incompatible, upgrade is blocked.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="d95ae-115">更正動作</span><span class="sxs-lookup"><span data-stu-id="d95ae-115">Corrective Action</span></span>  
 <span data-ttu-id="d95ae-116">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 伺服器定序屬性無法變更。</span><span class="sxs-lookup"><span data-stu-id="d95ae-116">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] server collation property cannot be changed.</span></span> <span data-ttu-id="d95ae-117">您將無法完成 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的升級。</span><span class="sxs-lookup"><span data-stu-id="d95ae-117">You will not be able to complete an upgrade of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="d95ae-118">您需要將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝移轉至使用相容伺服器定序的新伺服器。</span><span class="sxs-lookup"><span data-stu-id="d95ae-118">You will need to migrate your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation to a new server which is using a compatible server collation.</span></span> <span data-ttu-id="d95ae-119">如需詳細資訊，請參閱下列：</span><span class="sxs-lookup"><span data-stu-id="d95ae-119">For more information, see the following:</span></span>  
  
-   [<span data-ttu-id="d95ae-120">升級和移轉 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="d95ae-120">Upgrade and Migrate Reporting Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=233227)  
  
-   [<span data-ttu-id="d95ae-121">選取 SQL Server 定序</span><span class="sxs-lookup"><span data-stu-id="d95ae-121">Selecting a SQL Server Collation</span></span>](https://go.microsoft.com/fwlink/?LinkId=233226)  
  
  
