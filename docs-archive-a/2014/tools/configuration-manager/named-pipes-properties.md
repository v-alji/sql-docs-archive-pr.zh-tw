---
title: 具名管道屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server]
- listening [SQL Server], pipes
- pipes [SQL Server], listening on pipes
- Named Pipes [SQL Server], listening on pipes
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
author: stevestein
ms.author: sstein
ms.openlocfilehash: 80790c1cb8830a0fd132721f375a70d2574421b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595338"
---
# <a name="named-pipes-properties"></a><span data-ttu-id="97f79-102">具名管道屬性</span><span class="sxs-lookup"><span data-stu-id="97f79-102">Named Pipes Properties</span></span>
  <span data-ttu-id="97f79-103">使用具名管道通訊協定時，您可以使用 [具名管道屬性]  對話方塊上的 [通訊協定]  頁面，以檢視或變更 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接聽的具名管道。</span><span class="sxs-lookup"><span data-stu-id="97f79-103">Use the **Protocol**page on the **Named Pipes Properties** dialog box to view or change the named pipe that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens to, when using the Named Pipes protocol.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="97f79-104">必須重新啟動，才能啟用或停用通訊協定或變更具名管道。</span><span class="sxs-lookup"><span data-stu-id="97f79-104">must be restarted to enable or disable the protocol, or change the named pipe.</span></span>  
  
## <a name="options"></a><span data-ttu-id="97f79-105">選項。</span><span class="sxs-lookup"><span data-stu-id="97f79-105">Options</span></span>  
 <span data-ttu-id="97f79-106">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="97f79-106">**Enabled**</span></span>  
 <span data-ttu-id="97f79-107">可能的值為 [是]  和 [否]  。</span><span class="sxs-lookup"><span data-stu-id="97f79-107">Possible values are **Yes** and **No**.</span></span>  
  
 <span data-ttu-id="97f79-108">**管道名稱**</span><span class="sxs-lookup"><span data-stu-id="97f79-108">**Pipe Name**</span></span>  
 <span data-ttu-id="97f79-109">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接聽的具名管道。</span><span class="sxs-lookup"><span data-stu-id="97f79-109">Specifies the named pipe on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens.</span></span> <span data-ttu-id="97f79-110">根據預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 對於預設執行個體會接聽： `\\.\pipe\sql\query` ，而對於具名執行個體會接聽： `\\.\pipe\MSSQL$<instancename>\sql\query` 。</span><span class="sxs-lookup"><span data-stu-id="97f79-110">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens on: `\\.\pipe\sql\query` for the default instance and `\\.\pipe\MSSQL$<instancename>\sql\query` for a named instance.</span></span> <span data-ttu-id="97f79-111">此欄位最長不可超過 2047 個字元。</span><span class="sxs-lookup"><span data-stu-id="97f79-111">This field is limited to 2047 characters.</span></span>  
  
## <a name="creating-an-alternate-named-pipe"></a><span data-ttu-id="97f79-112">建立替代具名管道</span><span class="sxs-lookup"><span data-stu-id="97f79-112">Creating an Alternate Named Pipe</span></span>  
 <span data-ttu-id="97f79-113">若要變更具名管道，請在 [具名管道]  方塊中輸入新的管道名稱，然後停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，之後再重新啟動。</span><span class="sxs-lookup"><span data-stu-id="97f79-113">To change the named pipe, type the new pipe name in the **Pipe Name** box and then stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="97f79-114">因為已知 **sql\query** 是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用的具名管道，所以變更管道有助於降低遭惡意程式攻擊的風險。</span><span class="sxs-lookup"><span data-stu-id="97f79-114">Since **sql\query** is well known as the named pipe used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], changing the pipe can help reduce the risk of attack by malicious programs.</span></span>  
  
### <a name="example"></a><span data-ttu-id="97f79-115">範例</span><span class="sxs-lookup"><span data-stu-id="97f79-115">Example</span></span>  
 <span data-ttu-id="97f79-116">輸入 **\\\\.\pipe\unit\app** 以接聽 **unit\app** 管道。</span><span class="sxs-lookup"><span data-stu-id="97f79-116">Type **\\\\.\pipe\unit\app** to listen on the **unit\app** pipe.</span></span>  
  
 <span data-ttu-id="97f79-117">輸入 **\\\\.\pipe\acct** 以接聽 **acct** 管道。</span><span class="sxs-lookup"><span data-stu-id="97f79-117">Type **\\\\.\pipe\acct** to listen on the **acct** pipe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97f79-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97f79-118">See Also</span></span>  
 <span data-ttu-id="97f79-119">[啟用或停用伺服器網路通訊協定](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="97f79-119">[Enable or Disable a Server Network Protocol](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) </span></span>  
 <span data-ttu-id="97f79-120">[選擇網路通訊協定](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="97f79-120">[Choosing a Network Protocol](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span></span>  
 [<span data-ttu-id="97f79-121">使用具名管道建立有效的連接字串</span><span class="sxs-lookup"><span data-stu-id="97f79-121">Creating a Valid Connection String Using Named Pipes</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)  
  
  
