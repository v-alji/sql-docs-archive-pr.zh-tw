---
title: 共用檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- sharing files
- file sharing [SQL Server]
- version control services [SQL Server], file sharing
ms.assetid: 645f5c0a-e949-4e87-8988-85e4d6128464
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 79909fcdb09e349798edfe285475f8a898c3bf04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708581"
---
# <a name="share-files"></a><span data-ttu-id="8eee2-102">共用檔案</span><span class="sxs-lookup"><span data-stu-id="8eee2-102">Share Files</span></span>
  <span data-ttu-id="8eee2-103">您可以利用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 來跨越不同的原始檔控制專案共用項目。</span><span class="sxs-lookup"><span data-stu-id="8eee2-103">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to share items across source control projects.</span></span> <span data-ttu-id="8eee2-104">當您共用某個項目時，這個項目的任何變更都會反映在共用這個項目的每個專案中。</span><span class="sxs-lookup"><span data-stu-id="8eee2-104">When you share an item, any changes to the item are reflected in every project to which the item is shared.</span></span>  
  
 <span data-ttu-id="8eee2-105">「項目共用」為原始檔控制的使用者帶來下列好處：</span><span class="sxs-lookup"><span data-stu-id="8eee2-105">Item sharing provides the following advantages to source control users:</span></span>  
  
-   <span data-ttu-id="8eee2-106">不需要每個使用共用項目的專案都儲存一份個別的項目副本，可以節省原始檔控制用戶端和伺服器的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="8eee2-106">Makes it unnecessary for each project that uses the shared item to store a separate copy of the item, conserving disk space on both the source control client and server.</span></span> <span data-ttu-id="8eee2-107">原始檔控制提供者將共用項目儲存在單一中央位置，每個共用它的專案都會儲存一個指向這個位置的指標。</span><span class="sxs-lookup"><span data-stu-id="8eee2-107">The source control provider stores the shared item in one central location, and every project to which it is shared stores a pointer to that location.</span></span>  
  
-   <span data-ttu-id="8eee2-108">避免版本不相容。</span><span class="sxs-lookup"><span data-stu-id="8eee2-108">Avoids version incompatibilities.</span></span> <span data-ttu-id="8eee2-109">由於共用項目的每個專案都使用相同的項目版本，因此，當各個項目副本在多個專案內個別變更時，不會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="8eee2-109">Because every project to which the item is shared uses the same version of the item, you avoid the conflicts that arise when each copy of an item is changing independently within multiple projects.</span></span>  
  
### <a name="to-share-an-item"></a><span data-ttu-id="8eee2-110">共用項目</span><span class="sxs-lookup"><span data-stu-id="8eee2-110">To share an item</span></span>  
  
1.  <span data-ttu-id="8eee2-111">在 [方案總管] 中，選取共用檔案要放在其中的資料夾或專案。</span><span class="sxs-lookup"><span data-stu-id="8eee2-111">In Solution Explorer, select either the folder or project in which you want to place the shared files.</span></span>  
  
2.  <span data-ttu-id="8eee2-112">**在 [檔案**] 功能表上，指向 [原始檔**控制**]，然後按一下 [**共用**]。</span><span class="sxs-lookup"><span data-stu-id="8eee2-112">On the **File** menu, point to **Source Control**, and then click **Share**.</span></span>  
  
3.  <span data-ttu-id="8eee2-113">在 [**共用方式**] 對話方塊中，流覽目錄清單中您想要共用的專案，然後按一下該專案。</span><span class="sxs-lookup"><span data-stu-id="8eee2-113">In the **Share with** dialog box, browse the directory list for the item you want to share, and click that item.</span></span>  
  
4.  <span data-ttu-id="8eee2-114">按一下 [共用]。</span><span class="sxs-lookup"><span data-stu-id="8eee2-114">Click **Share**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eee2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8eee2-115">See Also</span></span>  
 [<span data-ttu-id="8eee2-116">原始檔控制基本概念</span><span class="sxs-lookup"><span data-stu-id="8eee2-116">Source Control Basics</span></span>](../../2014/database-engine/source-control-basics.md)  
  
  
