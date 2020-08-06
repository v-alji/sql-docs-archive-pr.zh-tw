---
title: 修復 Distributed Replay 安裝 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6fcd8ca8-1ceb-457d-9545-096c74e274d7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 57f5b2bde308e48dbf14b52a8b159b30f6a98bc8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598145"
---
# <a name="repair-a-distributed-replay-installation"></a><span data-ttu-id="1b737-102">修復 Distributed Replay 安裝</span><span class="sxs-lookup"><span data-stu-id="1b737-102">Repair a Distributed Replay Installation</span></span>
  <span data-ttu-id="1b737-103">修復 Distributed Replay 元件 (控制器或用戶端) 會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1b737-103">Repairing a Distributed Replay component (controller or client) will do the following:</span></span>  
  
1.  <span data-ttu-id="1b737-104">再次於磁碟上安裝所有相關聯的檔案，並取代任何現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="1b737-104">Install all associated files on disk again, and replace any existing files.</span></span>  
  
2.  <span data-ttu-id="1b737-105">如果已移除對應的服務帳戶，則重新建立 Windows 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="1b737-105">Recreate the Windows service account if the corresponding service account was removed.</span></span>  
  
 <span data-ttu-id="1b737-106">您無法使用修復作業來加入或移除元件。</span><span class="sxs-lookup"><span data-stu-id="1b737-106">You cannot use the Repair operation to add or remove components.</span></span> <span data-ttu-id="1b737-107">若要新增或移除元件，請在安裝程式之 [**特徵選取**] 頁面的功能樹狀結構中，核取或取消核取對應的元件 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1b737-107">To add or remove components, check or uncheck the corresponding component in the Feature tree on the **Feature Selection** page in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span>  
  
### <a name="to-repair-a-failed-installation-of-distributed-replay"></a><span data-ttu-id="1b737-108">修復 Distributed Replay 的失敗安裝</span><span class="sxs-lookup"><span data-stu-id="1b737-108">To repair a failed installation of Distributed Replay</span></span>  
  
1.  <span data-ttu-id="1b737-109">在 [**開始**] 功能表中，按一下 [**控制台**]，然後按兩下 [**新增或移除程式**]。</span><span class="sxs-lookup"><span data-stu-id="1b737-109">From the **Start** menu, click **Control Panel**, and then double-click **Add or Remove Programs**.</span></span>  
  
2.  <span data-ttu-id="1b737-110">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]在 [**卸載或變更程式**] 視窗中選取，然後在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 對話方塊中按一下 [**修復**]。</span><span class="sxs-lookup"><span data-stu-id="1b737-110">Select [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in the **Uninstall or change a program** window, and then in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] dialog box, click **Repair**.</span></span>  
  
3.  <span data-ttu-id="1b737-111">依照嚮導中的步驟操作 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，然後在 [**選取功能**] 頁面上，選取您要修復的 Distributed Replay 元件，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="1b737-111">Follow the steps in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] wizard, and on the **Select Features** page, select the Distributed Replay components you want to repair, and then click **Next.**.</span></span>  
  
4.  <span data-ttu-id="1b737-112">完成 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝精靈，修復選取的 Distributed Replay 功能。</span><span class="sxs-lookup"><span data-stu-id="1b737-112">Complete the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Installation Wizard to repair the selected Distributed Replay features.</span></span>  
  
  
