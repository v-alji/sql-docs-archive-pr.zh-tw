---
title: 使用共用記憶體通訊協定建立有效的連接字串 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine], shared memory
- aliases [SQL Server], shared memory
ms.assetid: 5fff42e8-377f-4b40-b0c8-b02393f8a1af
author: stevestein
ms.author: sstein
ms.openlocfilehash: ca97332a09a33fcfc15a3dbb2599af27dbe0e1db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686654"
---
# <a name="creating-a-valid-connection-string-using-shared-memory-protocol"></a><span data-ttu-id="cebaf-102">使用共用記憶體通訊協定建立有效的連接字串</span><span class="sxs-lookup"><span data-stu-id="cebaf-102">Creating a Valid Connection String Using Shared Memory Protocol</span></span>
  <span data-ttu-id="cebaf-103">從相同電腦上執行的用戶端連接到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，可使用共用記憶體通訊協定。</span><span class="sxs-lookup"><span data-stu-id="cebaf-103">Connections to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a client running on the same computer use the shared memory protocol.</span></span> <span data-ttu-id="cebaf-104">共用記憶體並沒有可設定的內容。</span><span class="sxs-lookup"><span data-stu-id="cebaf-104">Shared memory has no configurable properties.</span></span> <span data-ttu-id="cebaf-105">連接時永遠會先嘗試使用共用記憶體，而且您無法將它從 **[用戶端通訊協定內容]** 清單上之 **[啟用的通訊協定]** 清單的最高位置移除。</span><span class="sxs-lookup"><span data-stu-id="cebaf-105">Shared memory is always tried first, and cannot be moved from the top position of the **Enabled Protocols** list in the **Client Protocols Properties** list.</span></span> <span data-ttu-id="cebaf-106">您可以停用「共用記憶體」通訊協定，這在針對其他通訊協定中的其中一個通訊協定進行疑難排解時非常有幫助。</span><span class="sxs-lookup"><span data-stu-id="cebaf-106">The Shared Memory protocol can be disabled, which is useful when troubleshooting one of the other protocols.</span></span>  
  
 <span data-ttu-id="cebaf-107">您不能使用共用記憶體通訊協定來建立別名，但如果已啟用共用記憶體，則可以使用名稱來連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ，以建立共用記憶體連接。</span><span class="sxs-lookup"><span data-stu-id="cebaf-107">You cannot create an alias using the shared memory protocol, but if shared memory is enabled, then connecting to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by name, creates a shared memory connection.</span></span> <span data-ttu-id="cebaf-108">共用記憶體連接字串使用 `lpc:<servername>[\instancename]`格式。</span><span class="sxs-lookup"><span data-stu-id="cebaf-108">A shared memory connection string uses the format `lpc:<servername>[\instancename]`.</span></span>  
  
## <a name="connecting-to-the-local-server"></a><span data-ttu-id="cebaf-109">連接到本機伺服器</span><span class="sxs-lookup"><span data-stu-id="cebaf-109">Connecting to the Local Server</span></span>  
 <span data-ttu-id="cebaf-110">連接到與用戶端在同一部電腦上執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，可以使用 **(local)** 作為伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="cebaf-110">When connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the same computer as the client, you can use **(local)** as the server name.</span></span> <span data-ttu-id="cebaf-111">但不建議這麼做，因為會造成模糊不清，但是若確實知道用戶端正在預期的電腦上執行，這就很有用。</span><span class="sxs-lookup"><span data-stu-id="cebaf-111">This is not encouraged as it leads to ambiguity, however it can be useful when the client is known to be running on the intended computer.</span></span> <span data-ttu-id="cebaf-112">例如，為行動式、非連接的使用者 (例如銷售人員) 建立應用程式 (亦即 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將會在膝上型電腦上執行並儲存專案資料) 時，連接到 **(local)** 的用戶端一律會連接到在膝上型電腦上執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cebaf-112">For instance, when creating an application for mobile disconnected users, such as a sales force, where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will run on laptop computers and store project data, a client connecting to **(local)** would always connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the laptop.</span></span> <span data-ttu-id="cebaf-113">可以使用 **localhost** 或句點 ( **.** ) 來取代 **(local)** 。</span><span class="sxs-lookup"><span data-stu-id="cebaf-113">The word **localhost** or a period (**.**) can be used in place of **(local)**.</span></span>  
  
## <a name="verifying-your-connection-protocol"></a><span data-ttu-id="cebaf-114">驗證您的連接通訊協定</span><span class="sxs-lookup"><span data-stu-id="cebaf-114">Verifying your Connection Protocol</span></span>  
 <span data-ttu-id="cebaf-115">下列查詢會傳回目前連接所使用的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="cebaf-115">The following query will return the protocol used for the current connection.</span></span>  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a><span data-ttu-id="cebaf-116">範例：</span><span class="sxs-lookup"><span data-stu-id="cebaf-116">Examples:</span></span>  
 <span data-ttu-id="cebaf-117">您可以使用下列名稱來連接到具有共用記憶體通訊協定 (且已啟用) 的本機電腦：</span><span class="sxs-lookup"><span data-stu-id="cebaf-117">The following names will connect to the local computer with the shared memory protocol if it is enabled:</span></span>  
  
 `<servername>`  
  
 `<servername>\<instancename>`  
  
 `(local)`  
  
 `localhost`  
  
 <span data-ttu-id="cebaf-118">您不能建立共用記憶體連接的別名。</span><span class="sxs-lookup"><span data-stu-id="cebaf-118">You cannot create an alias for a shared memory connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cebaf-119">在 [伺服器]  方塊中指定 IP 位址會建立 TCP/IP 連接。</span><span class="sxs-lookup"><span data-stu-id="cebaf-119">Specifying an IP Address in the **Server** box will result in a TCP/IP connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cebaf-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cebaf-120">See Also</span></span>  
 <span data-ttu-id="cebaf-121">[使用 TCP IP 建立有效的連接字串](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md) </span><span class="sxs-lookup"><span data-stu-id="cebaf-121">[Creating a Valid Connection String Using TCP IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md) </span></span>  
 <span data-ttu-id="cebaf-122">[使用具名管道建立有效的連接字串](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md) </span><span class="sxs-lookup"><span data-stu-id="cebaf-122">[Creating a Valid Connection String Using Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md) </span></span>  
 [<span data-ttu-id="cebaf-123">選擇網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="cebaf-123">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
