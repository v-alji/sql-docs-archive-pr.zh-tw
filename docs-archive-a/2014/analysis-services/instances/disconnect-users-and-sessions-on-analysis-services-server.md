---
title: 中斷 Analysis Services 伺服器上的使用者和會話連線 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ending user activity [Analysis Services]
- connections [Analysis Services]
- sessions [Analysis Services]
ms.assetid: 3b0145a2-f21d-4dd0-a09e-83afeb2ff4a9
author: minewiskan
ms.author: owend
ms.openlocfilehash: bac20b663b0a65902c70e7a3c3bfe3f27b7bf061
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698791"
---
# <a name="disconnect-users-and-sessions-on-analysis-services-server"></a><span data-ttu-id="fc8ed-102">中斷 Analysis Services 伺服器上的使用者和工作階段連接</span><span class="sxs-lookup"><span data-stu-id="fc8ed-102">Disconnect Users and Sessions on Analysis Services Server</span></span>
  <span data-ttu-id="fc8ed-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的管理員在執行工作負載管理時，可以選擇結束使用者活動。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-103">An administrator of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] may want to end user activity as part of workload management.</span></span> <span data-ttu-id="fc8ed-104">方法是您可以取消工作階段和連接來達成此目的。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-104">You do this by canceling sessions and connections.</span></span> <span data-ttu-id="fc8ed-105">工作階段可在查詢執行時自動形成 (隱含)，或在管理員建立時加以命名 (明確)。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-105">Sessions can be formed automatically when a query is run (implicit), or named at the time of creation by the administrator (explicit).</span></span> <span data-ttu-id="fc8ed-106">連接就像開啟的導管，可在上面執行查詢。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-106">Connections are open conduits over which queries can be run.</span></span> <span data-ttu-id="fc8ed-107">使用中的工作階段和連接都可以結束。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-107">Both sessions and connections can be ended while they are active.</span></span> <span data-ttu-id="fc8ed-108">例如，處理時間如果太長，或對於執行的命令是否撰寫正確有疑問時，管理員可以結束工作階段的處理。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-108">For example, an administrator may want to end processing for a session if the processing is taking too long or if some doubt has arisen as to whether the command being executed was written correctly.</span></span>  
  
## <a name="ending-sessions-and-connections"></a><span data-ttu-id="fc8ed-109">結束工作階段和連接</span><span class="sxs-lookup"><span data-stu-id="fc8ed-109">Ending Sessions and Connections</span></span>  
 <span data-ttu-id="fc8ed-110">若要管理工作階段和連接，您可以使用動態管理檢視 (DMV) 和 XMLA：</span><span class="sxs-lookup"><span data-stu-id="fc8ed-110">To manage sessions and connections, you can use Dynamic Management Views (DMVs) and XMLA:</span></span>  
  
1.  <span data-ttu-id="fc8ed-111">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接到 Analysis Services 執行個體。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-111">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to an Analysis Services instance.</span></span>  
  
2.  <span data-ttu-id="fc8ed-112">將下列任何一個 DMV 查詢貼入 MDX 查詢視窗中，以取得目前執行之所有工作階段、連接和命令的清單。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-112">Paste any one of the following DMV queries in an MDX query window to get a list of all sessions, connections, and commands that are currently executing:</span></span>  
  
     `Select * from $System.Discover_Sessions`  
  
     `Select * from $System.Discover_Connections`  
  
     `Select * from $System.Discover_Commands`  
  
3.  <span data-ttu-id="fc8ed-113">按 F5 執行查詢。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-113">Press F5 to execute the query.</span></span>  
  
     <span data-ttu-id="fc8ed-114">DMV 查詢會以易於閱讀和複製的表格形式，傳回工作階段與連接資訊的結果集。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-114">The DMV query returns session and connection information in a tabular result set that is easier read and copy from.</span></span>  
  
 <span data-ttu-id="fc8ed-115">讓查詢視窗保持開啟狀態。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-115">Keep the query window open.</span></span> <span data-ttu-id="fc8ed-116">在下一步中，您需要回到這個頁面，複製您要中斷連接之工作階段的 SPID。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-116">In the next step, you will want to return to this page to copy the SPIDs of the session you want to disconnect.</span></span>  
  
 <span data-ttu-id="fc8ed-117">若要結束工作階段，請開啟第二個 XMLA 查詢視窗。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-117">To end a session, open a second XMLA query window.</span></span>  
  
1.  <span data-ttu-id="fc8ed-118">將下列語法貼入 MDX 查詢視窗，並將 ConnectionID、SessionID 或 SPID 預留位置，以上一個步驟複製的有效值取代。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-118">Paste the following syntax into an MDX query window, replacing the ConnectionID, SessionID, or SPID placeholder with a valid value copied from the previous step.</span></span>  
  
    ```  
    <Cancel xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  
       <ConnectionID>111</ConnectionID>  
       <SessionID>222</SessionID>  
       <SPID>333</SPID>  
  
    <CancelAssociated>1</CancelAssociated>  
    </Cancel>  
  
    ```  
  
2.  <span data-ttu-id="fc8ed-119">按 F5 執行取消命令。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-119">Press F5 to execute the cancel command.</span></span>  
  
 <span data-ttu-id="fc8ed-120">結束連接會取消所有工作階段與 SPID，並關閉主機工作階段。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-120">Ending a connection cancels all sessions and SPIDs, closing the host session.</span></span>  
  
 <span data-ttu-id="fc8ed-121">結束工作階段會停止當做該工作階段一部分執行的所有命令 (SPID)。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-121">Ending a session stops all commands (SPIDs) that are running as part of that session.</span></span>  
  
 <span data-ttu-id="fc8ed-122">結束 SPID 會取消一個特定命令。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-122">Ending a SPID cancels a particular commend.</span></span>  
  
 <span data-ttu-id="fc8ed-123">在罕見的情況下， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 若無法追蹤與連接相關聯的所有工作階段和 SPID，則不會關閉連接 (例如，當某個 HTTP 案例中開啟了多個工作階段時)。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-123">In rare cases, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will not close a connection if it cannot track all the sessions and SPIDs associated with the connection (for example, when multiple sessions are open in an HTTP scenario).</span></span>  
  
 <span data-ttu-id="fc8ed-124">如需本主題中所參考之 XMLA 的詳細資訊，請參閱 [Execute 方法 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) 和 [Cancel 元素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla)。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-124">For more information about the XMLA referenced in this topic, see [Execute Method &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) and [Cancel Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc8ed-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc8ed-125">See Also</span></span>  
 <span data-ttu-id="fc8ed-126">[&#40;XMLA&#41;管理連接和會話](../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md) </span><span class="sxs-lookup"><span data-stu-id="fc8ed-126">[Managing Connections and Sessions &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md) </span></span>  
 <span data-ttu-id="fc8ed-127">[&#40;XMLA&#41;的 BeginSession 元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/beginsession-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="fc8ed-127">[BeginSession Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/beginsession-element-xmla) </span></span>  
 <span data-ttu-id="fc8ed-128">[&#40;XMLA&#41;的 EndSession 元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/endsession-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="fc8ed-128">[EndSession Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/endsession-element-xmla) </span></span>  
 [<span data-ttu-id="fc8ed-129">Session 元素 &#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="fc8ed-129">Session Element &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/session-element-xmla)  
  
  
