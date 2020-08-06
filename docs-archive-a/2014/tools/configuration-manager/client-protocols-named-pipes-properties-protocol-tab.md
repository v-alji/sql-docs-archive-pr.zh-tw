---
title: 用戶端通訊協定 - 具名管道屬性 ([通訊協定] 索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server], connecting to
- Named Pipes [SQL Server], default pipe
- client protocols [SQL Server]
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
author: stevestein
ms.author: sstein
ms.openlocfilehash: 169b6d98212c724b8d6c43615ae2fa7eba9cfc7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687401"
---
# <a name="client-protocols---named-pipes-properties-protocol-tab"></a><span data-ttu-id="c36c7-102">用戶端通訊協定 - 具名管道內容 (通訊協定索引標籤)</span><span class="sxs-lookup"><span data-stu-id="c36c7-102">Client Protocols - Named Pipes Properties (Protocol Tab)</span></span>
  <span data-ttu-id="c36c7-103">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員中，使用 [具名管道屬性]  對話方塊的 [通訊協定]  索引標籤來檢視或修改預設管道的描述。</span><span class="sxs-lookup"><span data-stu-id="c36c7-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager use the **Protocol** tab on the **Named Pipes Properties** dialog box to view or modify the description of default pipe.</span></span> <span data-ttu-id="c36c7-104">若要連接到其他管道，請在 **[預設管道]** 方塊內輸入管道名稱。</span><span class="sxs-lookup"><span data-stu-id="c36c7-104">To connect to a different pipe, type the pipe in the **Default Pipe** box.</span></span> <span data-ttu-id="c36c7-105">如需有關連接字串的詳細資訊，請參閱＜ [Creating a Valid Connection String Using Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="c36c7-105">For more information about connection strings, see [Creating a Valid Connection String Using Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c36c7-106">選項。</span><span class="sxs-lookup"><span data-stu-id="c36c7-106">Options</span></span>  
 <span data-ttu-id="c36c7-107">**[預設管道]**</span><span class="sxs-lookup"><span data-stu-id="c36c7-107">**Default Pipe**</span></span>  
 <span data-ttu-id="c36c7-108">指定「具名管道網路」程式庫嘗試連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的目標執行個體時要使用的預設管道。</span><span class="sxs-lookup"><span data-stu-id="c36c7-108">Specifies the default pipe the Named Pipes Net-library will use to attempt to connect to the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c36c7-109">根據預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會接聽： `\\.\pipe\sql\query`</span><span class="sxs-lookup"><span data-stu-id="c36c7-109">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens on: `\\.\pipe\sql\query`</span></span>  
  
 <span data-ttu-id="c36c7-110">若要連接到預設管道，請輸入 `sql\query`</span><span class="sxs-lookup"><span data-stu-id="c36c7-110">To connect to the default pipe, enter `sql\query`</span></span>  
  
 <span data-ttu-id="c36c7-111">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="c36c7-111">**Enabled**</span></span>  
 <span data-ttu-id="c36c7-112">可能的值為 [是]  和 [否]  。</span><span class="sxs-lookup"><span data-stu-id="c36c7-112">Possible values are **Yes** and **No**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c36c7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c36c7-113">See Also</span></span>  
 [<span data-ttu-id="c36c7-114">選擇網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="c36c7-114">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
