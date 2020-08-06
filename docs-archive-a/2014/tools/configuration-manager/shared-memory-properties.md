---
title: 共用記憶體屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6275215afdb6de3aa134dbffe74aa22b9e7b6f5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605968"
---
# <a name="shared-memory-properties"></a><span data-ttu-id="3df41-102">共用記憶體屬性</span><span class="sxs-lookup"><span data-stu-id="3df41-102">Shared Memory Properties</span></span>
  <span data-ttu-id="3df41-103">您可以使用 [共用記憶體屬性] 對話方塊上的 [通訊協定] 頁面來檢視與啟用共用記憶體通訊協定。</span><span class="sxs-lookup"><span data-stu-id="3df41-103">Use the **Protocol**page on the **Shared Memory Properties** dialog box to enable or disable the shared memory protocol.</span></span> <span data-ttu-id="3df41-104">共用記憶體是使用上最簡單的通訊協定，而且不用設定任何設定。</span><span class="sxs-lookup"><span data-stu-id="3df41-104">Shared memory is the simplest protocol to use and has no configurable settings.</span></span> <span data-ttu-id="3df41-105">因為使用共用記憶體通訊協定的用戶端，只能連線到在相同電腦上執行的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，所以不適用於大部分資料庫活動。</span><span class="sxs-lookup"><span data-stu-id="3df41-105">Because clients using the shared memory protocol can only connect to a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance running on the same computer, it is not useful for most database activity.</span></span> <span data-ttu-id="3df41-106">當您懷疑其他通訊協定的設定不正確時，請使用共用記憶體通訊協定進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="3df41-106">Use the shared memory protocol for troubleshooting when you suspect the other protocols are configured incorrectly.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3df41-107">必須重新啟動下列項目，才能啟用或停用通訊協定。</span><span class="sxs-lookup"><span data-stu-id="3df41-107">must be restarted to enable or disable the protocol.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3df41-108">選項。</span><span class="sxs-lookup"><span data-stu-id="3df41-108">Options</span></span>  
 <span data-ttu-id="3df41-109">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="3df41-109">**Enabled**</span></span>  
 <span data-ttu-id="3df41-110">可能的值為 [是]  和 [否]  。</span><span class="sxs-lookup"><span data-stu-id="3df41-110">Possible values are **Yes** and **No**.</span></span> <span data-ttu-id="3df41-111">根據預設，已啟用共用記憶體通訊協定。</span><span class="sxs-lookup"><span data-stu-id="3df41-111">The shared memory protocol is enabled by default.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3df41-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3df41-112">See Also</span></span>  
 <span data-ttu-id="3df41-113">[選擇網路通訊協定](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="3df41-113">[Choosing a Network Protocol](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span></span>  
 [<span data-ttu-id="3df41-114">使用共用記憶體通訊協定建立有效的連接字串</span><span class="sxs-lookup"><span data-stu-id="3df41-114">Creating a Valid Connection String Using Shared Memory Protocol</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
  
