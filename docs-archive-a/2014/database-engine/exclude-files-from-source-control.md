---
title: 從原始檔控制排除檔案 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- excluding files from source control
- source controls [SQL Server Management Studio], file exclusions
ms.assetid: 7dcb6514-db5c-49eb-8b5a-2c766ce39aa7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9fb3c5ccb4fcaad062236eec6d04f995557dc2b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701599"
---
# <a name="exclude-files-from-source-control"></a><span data-ttu-id="75455-102">從原始檔控制中排除檔案</span><span class="sxs-lookup"><span data-stu-id="75455-102">Exclude Files from Source Control</span></span>
  <span data-ttu-id="75455-103">如果您處理的方案包含不需要原始檔控制服務的檔案，您可以使用 [**從原始檔控制排除**] 命令，將檔案從原始檔控制中排除。</span><span class="sxs-lookup"><span data-stu-id="75455-103">If the solution you are working on contains files that do not require source control services, you can use the **Exclude from Source Control** command to exclude the file from source control.</span></span> <span data-ttu-id="75455-104">當您執行這個動作時，檔案會保留在 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe 資料庫中，但不會再隨著專案而簽入或簽出。</span><span class="sxs-lookup"><span data-stu-id="75455-104">When you do this, the file remains in the [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe database, but it is no longer checked in or out with the project.</span></span>  
  
 <span data-ttu-id="75455-105">您應該只在產生的檔案上使用 [**從原始檔控制排除**] 命令。</span><span class="sxs-lookup"><span data-stu-id="75455-105">You should use the **Exclude from Source Control** command only on generated files.</span></span> <span data-ttu-id="75455-106">產生的檔案是可以 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 根據方案中另一個檔案的內容，完全重新建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="75455-106">A generated file is one that can be entirely re-created by [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] based on the contents of another file in the solution.</span></span>  
  
### <a name="to-exclude-a-file-from-source-control"></a><span data-ttu-id="75455-107">從原始檔控制中排除檔案</span><span class="sxs-lookup"><span data-stu-id="75455-107">To exclude a file from source control</span></span>  
  
1.  <span data-ttu-id="75455-108">在 [方案總管] 中，選取要排除的檔案。</span><span class="sxs-lookup"><span data-stu-id="75455-108">In Solution Explorer, select the file to exclude.</span></span>  
  
2.  <span data-ttu-id="75455-109">**在 [檔案**] 功能表上，指向 [原始檔**控制**]，然後按一下 [ **Exclude** *\<file name>* **從原始檔控制**排除]。</span><span class="sxs-lookup"><span data-stu-id="75455-109">On the **File** menu, point to **Source Control**, and then click **Exclude** *\<file name>* **from Source Control**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75455-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75455-110">See Also</span></span>  
 <span data-ttu-id="75455-111">[原始檔控制基本概念](../../2014/database-engine/source-control-basics.md) </span><span class="sxs-lookup"><span data-stu-id="75455-111">[Source Control Basics](../../2014/database-engine/source-control-basics.md) </span></span>  
 <span data-ttu-id="75455-112">[設定原始檔控制選項](../../2014/database-engine/set-source-control-options.md) </span><span class="sxs-lookup"><span data-stu-id="75455-112">[Set Source Control Options](../../2014/database-engine/set-source-control-options.md) </span></span>  
 [<span data-ttu-id="75455-113">變更原始檔控制連接</span><span class="sxs-lookup"><span data-stu-id="75455-113">Change Source Control Connections</span></span>](../../2014/database-engine/change-source-control-connections.md)  
  
  
