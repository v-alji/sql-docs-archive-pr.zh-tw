---
title: " (XMLA) 取消命令 |Microsoft Docs"
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- connections [XML for Analysis]
- associated connections [XML for Analysis]
- XML for Analysis, canceling
- associated sessions [XML for Analysis]
- canceling connections
- canceling commands
- canceling sessions
- SPID
- XMLA, canceling
- server process IDs [XML for Analysis]
- sessions [XML for Analysis]
ms.assetid: b59f8197-c33d-4e65-9022-848ccba540f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 003c70362c38ae1838b4679abf6485fa031a9143
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687302"
---
# <a name="canceling-commands-xmla"></a><span data-ttu-id="af58c-102">取消命令 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="af58c-102">Canceling Commands (XMLA)</span></span>
  <span data-ttu-id="af58c-103">視發出命令之使用者的系統管理許可權而定，XML for Analysis (XMLA) 中的 [[取消](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla)] 命令可以取消會話、會話、連接、伺服器進程或相關聯會話或連接上的命令。</span><span class="sxs-lookup"><span data-stu-id="af58c-103">Depending on the administrative permissions of the user issuing the command, the [Cancel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla) command in XML for Analysis (XMLA) can cancel a command on a session, a session, a connection, a server process, or an associated session or connection.</span></span>  
  
## <a name="canceling-commands"></a><span data-ttu-id="af58c-104">取消命令</span><span class="sxs-lookup"><span data-stu-id="af58c-104">Canceling Commands</span></span>  
 <span data-ttu-id="af58c-105">使用者可以傳送沒有指定屬性的 `Cancel` 命令，取消目前明確的工作階段內容中目前執行的命令。</span><span class="sxs-lookup"><span data-stu-id="af58c-105">A user can cancel the currently executing command within the context of the current explicit session by sending a `Cancel` command with no specified properties.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af58c-106">使用者無法取消在明確的工作階段中執行的命令。</span><span class="sxs-lookup"><span data-stu-id="af58c-106">A command running in an implicit session cannot be canceled by a user.</span></span>  
  
### <a name="canceling-batch-commands"></a><span data-ttu-id="af58c-107">取消批次命令</span><span class="sxs-lookup"><span data-stu-id="af58c-107">Canceling Batch Commands</span></span>  
 <span data-ttu-id="af58c-108">如果使用者取消 `Batch` 命令，則會取消 `Batch` 命令中尚未執行的所有其餘命令。</span><span class="sxs-lookup"><span data-stu-id="af58c-108">If a user cancels a `Batch` command, then all remaining commands not yet executed within the `Batch` command are canceled.</span></span> <span data-ttu-id="af58c-109">如果 `Batch` 命令是交易式的，則會回復在執行 `Cancel` 命令之前所執行的任何命令。</span><span class="sxs-lookup"><span data-stu-id="af58c-109">If the `Batch` command was transactional, any commands that were executed before the `Cancel` command runs are rolled back.</span></span>  
  
## <a name="canceling-sessions"></a><span data-ttu-id="af58c-110">取消工作階段</span><span class="sxs-lookup"><span data-stu-id="af58c-110">Canceling Sessions</span></span>  
 <span data-ttu-id="af58c-111">藉由在命令的[SessionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla)屬性中指定明確會話的會話識別碼 `Cancel` ，資料庫管理員或伺服器管理員可以取消會話，包括目前執行的命令。</span><span class="sxs-lookup"><span data-stu-id="af58c-111">By specifying a session identifier for an explicit session in the [SessionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) property of the `Cancel` command, a database administrator or server administrator can cancel a session, including the currently executing command.</span></span> <span data-ttu-id="af58c-112">資料庫管理員只能取消他或她擁有管理權限的資料庫之工作階段。</span><span class="sxs-lookup"><span data-stu-id="af58c-112">A database administrator can only cancel sessions for databases on which he or she has administrative permissions.</span></span>  
  
 <span data-ttu-id="af58c-113">資料庫管理員可以擷取 DISCOVER_SESSIONS 結構描述資料列集，以擷取指定資料庫的使用中工作階段。</span><span class="sxs-lookup"><span data-stu-id="af58c-113">A database administrator can retrieve the active sessions for a specified database by retrieving the DISCOVER_SESSIONS schema rowset.</span></span> <span data-ttu-id="af58c-114">為了抓取 DISCOVER_SESSIONS 架構資料列集，資料庫管理員會使用 XMLA `Discover` 方法，並為方法的[限制](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictions-element-xmla)屬性中的 SESSION_CURRENT_DATABASE 限制資料行指定適當的資料庫識別碼 `Discover` 。</span><span class="sxs-lookup"><span data-stu-id="af58c-114">To retrieve the DISCOVER_SESSIONS schema rowset, the database administrator uses the XMLA `Discover` method and specifies the appropriate database identifier for the SESSION_CURRENT_DATABASE restriction column in the [Restrictions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictions-element-xmla) property of the `Discover` method.</span></span>  
  
## <a name="canceling-connections"></a><span data-ttu-id="af58c-115">取消連接</span><span class="sxs-lookup"><span data-stu-id="af58c-115">Canceling Connections</span></span>  
 <span data-ttu-id="af58c-116">藉由在命令的[ConnectionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/connectionid-element-xmla)屬性中指定連接識別碼 `Cancel` ，伺服器管理員可以取消與指定連接相關聯的所有會話，包括所有執行中的命令，以及取消連接。</span><span class="sxs-lookup"><span data-stu-id="af58c-116">By specifying a connection identifier in the [ConnectionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/connectionid-element-xmla) property of the `Cancel` command, a server administrator can cancel all of the sessions associated with a given connection, including all running commands, and cancel the connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af58c-117">如果實例 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 無法找出並取消與連接相關聯的會話（例如，當資料提取在提供 HTTP 連接時開啟多個會話時），實例就無法取消連接。</span><span class="sxs-lookup"><span data-stu-id="af58c-117">If the instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cannot locate and cancel the sessions associated with a connection, such as when the data pump opens multiple sessions while providing HTTP connectivity, the instance cannot cancel the connection.</span></span> <span data-ttu-id="af58c-118">如果在 `Cancel` 命令期間遇到這個情況，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="af58c-118">If this case is encountered during the execution of a `Cancel` command, an error occurs.</span></span>  
  
 <span data-ttu-id="af58c-119">伺服器管理員可以擷取使用 `Discover` 方法的 DISCOVER_CONNECTIONS 結構描述資料列集，來為 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體擷取使用中的連接。</span><span class="sxs-lookup"><span data-stu-id="af58c-119">A server administrator can retrieve the active connections for an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance by retrieving the DISCOVER_CONNECTIONS schema rowset using the XMLA `Discover` method.</span></span>  
  
## <a name="canceling-server-processes"></a><span data-ttu-id="af58c-120">取消伺服器處理序</span><span class="sxs-lookup"><span data-stu-id="af58c-120">Canceling Server Processes</span></span>  
 <span data-ttu-id="af58c-121">藉由在命令的[spid](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla)屬性中指定伺服器處理序識別碼 (spid) `Cancel` ，伺服器管理員可以取消與指定之 spid 相關聯的命令。</span><span class="sxs-lookup"><span data-stu-id="af58c-121">By specifying a server process identifier (SPID) in the [SPID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) property of the `Cancel` command, a server administrator can cancel the commands associated with a given SPID.</span></span>  
  
## <a name="canceling-associated-sessions-and-connections"></a><span data-ttu-id="af58c-122">取消關聯的工作階段和連接。</span><span class="sxs-lookup"><span data-stu-id="af58c-122">Canceling Associated Sessions and Connections</span></span>  
 <span data-ttu-id="af58c-123">您可以將[CancelAssociated](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cancelassociated-element-xmla)屬性設定為 true，以取消與命令中指定之連線、會話或 SPID 相關聯的連接、會話和命令 `Cancel` 。</span><span class="sxs-lookup"><span data-stu-id="af58c-123">You can set the [CancelAssociated](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cancelassociated-element-xmla) property to true to cancel the connections, sessions, and commands associated with the connection, session, or SPID specified in the `Cancel` command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af58c-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af58c-124">See Also</span></span>  
 <span data-ttu-id="af58c-125">[&#40;XMLA&#41;的探索方法](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) </span><span class="sxs-lookup"><span data-stu-id="af58c-125">[Discover Method &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) </span></span>  
 [<span data-ttu-id="af58c-126">在 Analysis Services 中使用 XMLA 進行開發</span><span class="sxs-lookup"><span data-stu-id="af58c-126">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
