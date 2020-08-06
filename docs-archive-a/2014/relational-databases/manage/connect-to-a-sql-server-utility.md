---
title: 連接至 SQL Server 公用程式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b9b90b8d-241f-4b74-ac14-de7b10ea1821
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e8e59a28e083fc302faebbcba932c18a04e73a7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592688"
---
# <a name="connect-to-a-sql-server-utility"></a><span data-ttu-id="e00b1-102">連接至 SQL Server 公用程式</span><span class="sxs-lookup"><span data-stu-id="e00b1-102">Connect to a SQL Server Utility</span></span>
  <span data-ttu-id="e00b1-103">在您可以連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式之前，您必須建立公用程式控制點 (UCP)。</span><span class="sxs-lookup"><span data-stu-id="e00b1-103">Before you can connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, you must create a utility control point (UCP).</span></span> <span data-ttu-id="e00b1-104">如需詳細資訊，請參閱 [SQL Server 公用程式的功能與工作](sql-server-utility-features-and-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="e00b1-104">For more information, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>

 <span data-ttu-id="e00b1-105">若要檢視及管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源健全狀況，請使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) 連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式。</span><span class="sxs-lookup"><span data-stu-id="e00b1-105">To view and manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource health, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>

 <span data-ttu-id="e00b1-106">若要透過 SSMS 連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式：</span><span class="sxs-lookup"><span data-stu-id="e00b1-106">To connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility through SSMS:</span></span>

1.  <span data-ttu-id="e00b1-107">啟動 SSMS。</span><span class="sxs-lookup"><span data-stu-id="e00b1-107">Launch SSMS.</span></span>

2.  <span data-ttu-id="e00b1-108">在 SSMS 中，連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e00b1-108">In SSMS, connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>

3.  <span data-ttu-id="e00b1-109">按一下 [檢視]，然後按一下 [公用程式總管]。</span><span class="sxs-lookup"><span data-stu-id="e00b1-109">Click **View** and then **Utility Explorer**.</span></span>

4.  <span data-ttu-id="e00b1-110">在公用程式總管導覽窗格中，按一下 ![[連線到公用程式]](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility")。</span><span class="sxs-lookup"><span data-stu-id="e00b1-110">In the Utility Explorer navigation pane, click ![](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility")**Connect to Utility**.</span></span>

5.  <span data-ttu-id="e00b1-111">在 [連接到伺服器] 對話方塊中，指定 UCP 執行個體名稱，然後按一下 [連接]。</span><span class="sxs-lookup"><span data-stu-id="e00b1-111">In the **Connect to Server** dialog box, specify the UCP instance name, then click **Connect**.</span></span>

6.  <span data-ttu-id="e00b1-112">檢視公用程式總管導覽窗格，以查看 UCP 中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源的樹狀檢視。</span><span class="sxs-lookup"><span data-stu-id="e00b1-112">View the Utility Explorer Navigation Pane to see a tree view of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources in the UCP.</span></span>

 <span data-ttu-id="e00b1-113">建立新的 UCP 也會連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式。</span><span class="sxs-lookup"><span data-stu-id="e00b1-113">Creating a new UCP also connects you to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="e00b1-114">如需詳細資訊，請參閱[建立 SQL Server 公用程式控制點 &#40;SQL Server 公用程式&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="e00b1-114">For more information, see [Create a SQL Server Utility Control Point &#40;SQL Server Utility&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e00b1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e00b1-115">See Also</span></span>
 <span data-ttu-id="e00b1-116">[SQL Server 公用程式功能和](sql-server-utility-features-and-tasks.md)工作][視圖資源健康狀態原則結果 &#40;SQL Server 公用程式&#41;](view-resource-health-policy-results-sql-server-utility.md)</span><span class="sxs-lookup"><span data-stu-id="e00b1-116">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) [View Resource Health Policy Results &#40;SQL Server Utility&#41;](view-resource-health-policy-results-sql-server-utility.md)</span></span>


