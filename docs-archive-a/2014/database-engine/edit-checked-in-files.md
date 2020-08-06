---
title: 編輯簽入的檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying checked-in files
- checking in files
ms.assetid: 560cd19f-ab22-4273-b00c-149993a630e6
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e2dbe1aad203dfdc83e438d5b7f4ed19c15038c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701626"
---
# <a name="edit-checked-in-files"></a><span data-ttu-id="fe9c5-102">編輯簽入的檔案</span><span class="sxs-lookup"><span data-stu-id="fe9c5-102">Edit Checked-In Files</span></span>
  <span data-ttu-id="fe9c5-103">您通常必須先簽出原始檔控制檔案，才能編輯它們。</span><span class="sxs-lookup"><span data-stu-id="fe9c5-103">You typically must check out source-controlled files before you can edit them.</span></span> <span data-ttu-id="fe9c5-104">不過，您可以設定， [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 讓您可以修改尚未簽出的檔案。這麼做時，您的變更會保留在記憶體中，直到您儲存檔案為止。</span><span class="sxs-lookup"><span data-stu-id="fe9c5-104">However, you can configure [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] so that you can modify files you have not checked out. When doing so, your changes are held in memory until you save the files.</span></span> <span data-ttu-id="fe9c5-105">之後，系統會提示您從原始檔控制中簽出檔案。</span><span class="sxs-lookup"><span data-stu-id="fe9c5-105">You will then be prompted to check out the file from source control.</span></span>  
  
 <span data-ttu-id="fe9c5-106">如果您在進行團隊工作，除非您的原始檔控制提供者支援簽出本機版本，也支援簽出伺服器版本，否則，不建議您允許編輯簽入的檔案。</span><span class="sxs-lookup"><span data-stu-id="fe9c5-106">If you work on a team, allowing checked-in files to be edited is not recommended unless your source control provider supports both local version and server version checkouts.</span></span> <span data-ttu-id="fe9c5-107">大部份提供者都不支援本機版本簽出項目。</span><span class="sxs-lookup"><span data-stu-id="fe9c5-107">Most providers do not support local version checkouts.</span></span> <span data-ttu-id="fe9c5-108">如果您的提供者不支援簽出本機版本，且您編輯簽入的檔案，您就必須先手動合併在記憶體中的版本和伺服器版本，之後，才能簽入檔案。</span><span class="sxs-lookup"><span data-stu-id="fe9c5-108">If your provider does not support local version checkouts and you edit a checked-in file, you have to merge the in-memory and server versions manually before the file can be checked in.</span></span> <span data-ttu-id="fe9c5-109">在這個情況下，不支援自動合併及提供者輔助的合併。</span><span class="sxs-lookup"><span data-stu-id="fe9c5-109">Automatic and provider-assisted merges are unsupported in this situation.</span></span>  
  
### <a name="to-edit-checked-in-files"></a><span data-ttu-id="fe9c5-110">編輯簽入的檔案</span><span class="sxs-lookup"><span data-stu-id="fe9c5-110">To edit checked-in files</span></span>  
  
1.  <span data-ttu-id="fe9c5-111">在 **[工具]** 功能表上，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="fe9c5-111">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="fe9c5-112">在 [**選項**] 對話方塊中，展開 [ **Source 控制**l] 資料夾，然後按一下 [**環境**]。</span><span class="sxs-lookup"><span data-stu-id="fe9c5-112">In the **Options** dialog box, expand the **Source Contro**l folder, and then click **Environment**.</span></span>  
  
3.  <span data-ttu-id="fe9c5-113">按一下 [**允許編輯簽入的專案**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="fe9c5-113">Click **Allow checked-in items to be edited**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe9c5-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe9c5-114">See Also</span></span>  
 <span data-ttu-id="fe9c5-115">[管理簽入](../../2014/database-engine/manage-checkins.md) </span><span class="sxs-lookup"><span data-stu-id="fe9c5-115">[Manage Checkins](../../2014/database-engine/manage-checkins.md) </span></span>  
 [<span data-ttu-id="fe9c5-116">管理簽出</span><span class="sxs-lookup"><span data-stu-id="fe9c5-116">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  
