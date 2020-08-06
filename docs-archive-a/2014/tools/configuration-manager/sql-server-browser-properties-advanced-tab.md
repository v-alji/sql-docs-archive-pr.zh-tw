---
title: SQL Server Browser 屬性 (進階索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ba79137a-cb72-4bf3-a650-e11d02cfce10
author: stevestein
ms.author: sstein
ms.openlocfilehash: 480cd93c3feca44dd455a1a9ce2fd12994ca6100
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599291"
---
# <a name="sql-server-browser-properties-advanced-tab"></a><span data-ttu-id="bbdea-102">SQL Server Browser 屬性 (進階索引標籤)</span><span class="sxs-lookup"><span data-stu-id="bbdea-102">SQL Server Browser Properties (Advanced Tab)</span></span>
  <span data-ttu-id="bbdea-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 程式會以伺服器服務的方式執行。</span><span class="sxs-lookup"><span data-stu-id="bbdea-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser program runs as a service on the server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bbdea-104">Browser 會接聽 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源的內送要求，並提供有關在電腦上所安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的資訊。</span><span class="sxs-lookup"><span data-stu-id="bbdea-104">Browser listens for incoming requests for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources and provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bbdea-105">選項。</span><span class="sxs-lookup"><span data-stu-id="bbdea-105">Options</span></span>  
 <span data-ttu-id="bbdea-106">**叢集**</span><span class="sxs-lookup"><span data-stu-id="bbdea-106">**Clustered**</span></span>  
 <span data-ttu-id="bbdea-107">指出這項服務是否安裝為叢集伺服器的資源。</span><span class="sxs-lookup"><span data-stu-id="bbdea-107">Indicates if this service is installed as a resource of a clustered server.</span></span>  
  
 <span data-ttu-id="bbdea-108">**客戶回函報表**</span><span class="sxs-lookup"><span data-stu-id="bbdea-108">**Customer Feedback Reporting**</span></span>  
 <span data-ttu-id="bbdea-109">指出是否已在這項服務上啟用「服務品質監控」。</span><span class="sxs-lookup"><span data-stu-id="bbdea-109">Indicates whether Service Quality Monitoring has been enabled on this service.</span></span> <span data-ttu-id="bbdea-110">如需有關客戶回函報表的詳細資訊，請搜尋「線上叢書」的＜錯誤報告和使用方式報告設定＞主題。</span><span class="sxs-lookup"><span data-stu-id="bbdea-110">For more information on Customer Feedback Reporting, search Books Online for the topic, "Error and Usage Report Settings."</span></span>  
  
 <span data-ttu-id="bbdea-111">**傾印目錄**</span><span class="sxs-lookup"><span data-stu-id="bbdea-111">**Dump Directory**</span></span>  
 <span data-ttu-id="bbdea-112">在發生錯誤時放置記憶體傾印的位置。</span><span class="sxs-lookup"><span data-stu-id="bbdea-112">The location where memory dumps are placed in case of an error.</span></span>  
  
 <span data-ttu-id="bbdea-113">**錯誤報告**</span><span class="sxs-lookup"><span data-stu-id="bbdea-113">**Error Reporting**</span></span>  
 <span data-ttu-id="bbdea-114">若設定為 **[是]** ，一旦發生嚴重錯誤，Dr. Watson 程式會將資訊轉送至 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 或您的錯誤伺服器。</span><span class="sxs-lookup"><span data-stu-id="bbdea-114">When set to **Yes**, the Dr. Watson program forwards information to either [!INCLUDE[msCoName](../../includes/msconame-md.md)] or your error server if a serious failure occurs.</span></span> <span data-ttu-id="bbdea-115">如需錯誤報表的詳細資訊，請搜尋《線上叢書》的＜錯誤報告和使用方式報告設定＞主題。</span><span class="sxs-lookup"><span data-stu-id="bbdea-115">For more information on Error Reporting, search Books Online for the topic, "Error and Usage Report Settings."</span></span>  
  
 <span data-ttu-id="bbdea-116">**執行個體識別碼**</span><span class="sxs-lookup"><span data-stu-id="bbdea-116">**Instance ID**</span></span>  
 <span data-ttu-id="bbdea-117">指出使用此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 執行個體的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bbdea-117">Indicates the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that used this [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent instance.</span></span> <span data-ttu-id="bbdea-118">預設執行個體為 **MSSQL10_50.MSSQLSERVER**。</span><span class="sxs-lookup"><span data-stu-id="bbdea-118">The default instance is **MSSQL10_50.MSSQLSERVER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbdea-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbdea-119">See Also</span></span>  
 [<span data-ttu-id="bbdea-120">SQL Server Browser 服務</span><span class="sxs-lookup"><span data-stu-id="bbdea-120">SQL Server Browser Service</span></span>](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
