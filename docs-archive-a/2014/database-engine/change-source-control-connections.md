---
title: 變更原始檔控制連接 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server Management Studio], source controls
- source controls [SQL Server Management Studio], connections
ms.assetid: 538e3beb-f99c-4095-bd65-6413e872d26e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 077a09cdca0c0aff777184f04467ca39592690aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597370"
---
# <a name="change-source-control-connections"></a><span data-ttu-id="4682a-102">變更原始檔控制連接</span><span class="sxs-lookup"><span data-stu-id="4682a-102">Change Source Control Connections</span></span>
  <span data-ttu-id="4682a-103">您第一次從原始檔控制中加入或開啟方案時，您的原始檔控制提供者會建立本機方案目錄的根資料夾及其對應的伺服器資料夾之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="4682a-103">The first time you add or open a solution from source control, your source control provider creates an association between the root folder of the local solution directory and its corresponding server folder.</span></span>  
  
 <span data-ttu-id="4682a-104">根資料夾 (也稱為統一的根) 在用戶端。</span><span class="sxs-lookup"><span data-stu-id="4682a-104">The root folder (also called unified root) resides on the client.</span></span> <span data-ttu-id="4682a-105">您可以在這個資料夾之下，找到方案或專案所參考的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="4682a-105">It is the folder beneath which all the files referenced by a solution or project can be found.</span></span> <span data-ttu-id="4682a-106">若要找到方案、方案記錄及其狀態資訊的最新版本，請先找出這個伺服器資料夾，它位於原始檔控制伺服器中。</span><span class="sxs-lookup"><span data-stu-id="4682a-106">To find the latest version of a solution, its history, and its status information, locate the server folder, which resides on the source control server.</span></span> <span data-ttu-id="4682a-107">在 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe 中，伺服器資料夾稱為專案。</span><span class="sxs-lookup"><span data-stu-id="4682a-107">In [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, server folders are called projects.</span></span>  
  
 <span data-ttu-id="4682a-108">在許多情況之下，您都必須從方案的伺服器資料夾中，將方案解除繫結或中斷連接。</span><span class="sxs-lookup"><span data-stu-id="4682a-108">In many situations, you need to unbind or disconnect a solution from its server folder.</span></span> <span data-ttu-id="4682a-109">例如，如果無法使用原始檔控制提供者所在的電腦，您便無法依照正常方式來連接到備份電腦，請將方案重新繫結到備份伺服器資料夾，並繼續工作。</span><span class="sxs-lookup"><span data-stu-id="4682a-109">For example, if the computer on which your source control provider resides is unavailable, you can connect to a backup computer, rebind your solution to a backed-up server folder, and resume working normally.</span></span> <span data-ttu-id="4682a-110">另外，如果原始檔控制專案分叉，您可能需要將方案繫結到新專案版本所在的伺服器資料夾。</span><span class="sxs-lookup"><span data-stu-id="4682a-110">Also, if a source control project is forked, you may have to bind your solution to the server folder where the new project version resides.</span></span>  
  
 <span data-ttu-id="4682a-111">請利用原始檔控制提供者的使用者介面來變更方案所繫結的伺服器資料夾。</span><span class="sxs-lookup"><span data-stu-id="4682a-111">Use the user interface of the source control provider to change the server folder that a solution is bound to.</span></span> <span data-ttu-id="4682a-112">您可以從 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 環境中開啟原始檔控制使用者介面。</span><span class="sxs-lookup"><span data-stu-id="4682a-112">You can open the source control user interface from within the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment.</span></span>  
  
#### <a name="to-open-the-source-control-user-interface-from-the-studio-environment"></a><span data-ttu-id="4682a-113">從 Studio 環境中開啟原始檔控制使用者介面</span><span class="sxs-lookup"><span data-stu-id="4682a-113">To open the source control user interface from the Studio environment</span></span>  
  
1.  <span data-ttu-id="4682a-114">**在 [檔案**] 功能表上，指向 [原始檔**控制**]，然後按一下 [**啟動 Microsoft Visual SourceSafe**]。</span><span class="sxs-lookup"><span data-stu-id="4682a-114">On the **File** menu, point to **Source Control**, and then click **Launch Microsoft Visual SourceSafe**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4682a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4682a-115">See Also</span></span>  
 <span data-ttu-id="4682a-116">[原始檔控制基本概念](../../2014/database-engine/source-control-basics.md) </span><span class="sxs-lookup"><span data-stu-id="4682a-116">[Source Control Basics](../../2014/database-engine/source-control-basics.md) </span></span>  
 <span data-ttu-id="4682a-117">[設定原始檔控制選項](../../2014/database-engine/set-source-control-options.md) </span><span class="sxs-lookup"><span data-stu-id="4682a-117">[Set Source Control Options](../../2014/database-engine/set-source-control-options.md) </span></span>  
 [<span data-ttu-id="4682a-118">從原始檔控制中排除檔案</span><span class="sxs-lookup"><span data-stu-id="4682a-118">Exclude Files from Source Control</span></span>](../../2014/database-engine/exclude-files-from-source-control.md)  
  
  
