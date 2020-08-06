---
title: 管理簽入 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- checkins [SQL Server Management Studio]
- checking in files
- source controls [SQL Server Management Studio], checkins
ms.assetid: 293e60f3-15e3-4258-b73a-8baabe15c760
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a868aafff6d9bd389671544b5f1898e82707d933
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607025"
---
# <a name="manage-checkins"></a><span data-ttu-id="08abf-102">管理簽入</span><span class="sxs-lookup"><span data-stu-id="08abf-102">Manage Checkins</span></span>
  <span data-ttu-id="08abf-103">若要變更其他使用者能夠使用的原始檔控制檔案，您必須簽入檔案。</span><span class="sxs-lookup"><span data-stu-id="08abf-103">To make changes to a source-controlled file available to other users, you must check in the file.</span></span> <span data-ttu-id="08abf-104">當您簽入檔案時，您建立的版本會複製到原始檔控制提供者中，且會成為檔案的最新版本，有適當權限的使用者通常都可以使用它。</span><span class="sxs-lookup"><span data-stu-id="08abf-104">When you check in a file, the version you have created is copied to the source control provider, becomes the latest version of the file, and is generally available to users who have the appropriate permissions.</span></span>  
  
 <span data-ttu-id="08abf-105">用 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 來簽入檔案。</span><span class="sxs-lookup"><span data-stu-id="08abf-105">Use [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to check in files.</span></span> <span data-ttu-id="08abf-106">當您需要定期更新原始檔控制存放區，但又需要維護對某一組檔案的控制時，您可以指定您簽入的檔案，對您而言，要維持簽出的狀態。</span><span class="sxs-lookup"><span data-stu-id="08abf-106">When you need to update the source control store periodically, but also need to maintain control over a set of files, you can specify that files you check in remain checked out to you.</span></span>  
  
 <span data-ttu-id="08abf-107">下表描述此章節的主題。</span><span class="sxs-lookup"><span data-stu-id="08abf-107">The following table describes the topics in this section.</span></span>  
  
|<span data-ttu-id="08abf-108">主題</span><span class="sxs-lookup"><span data-stu-id="08abf-108">Topic</span></span>|<span data-ttu-id="08abf-109">描述</span><span class="sxs-lookup"><span data-stu-id="08abf-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="08abf-110">簽入檔案</span><span class="sxs-lookup"><span data-stu-id="08abf-110">Check In Files</span></span>](../../2014/database-engine/check-in-files.md)|<span data-ttu-id="08abf-111">提供如何簽入您已修改之檔案的指示。</span><span class="sxs-lookup"><span data-stu-id="08abf-111">Provides instructions on how to check in a file you have modified.</span></span>|  
|[<span data-ttu-id="08abf-112">檢視修改檔案清單</span><span class="sxs-lookup"><span data-stu-id="08abf-112">View a List of Modified Files</span></span>](../../2014/database-engine/view-a-list-of-modified-files.md)|<span data-ttu-id="08abf-113">說明如何顯示工作完成時能夠一起簽入的修改檔案清單。</span><span class="sxs-lookup"><span data-stu-id="08abf-113">Explains how to display a list of modified files that you can check in together when you are finished working.</span></span>|  
|[<span data-ttu-id="08abf-114">編輯簽入的檔案</span><span class="sxs-lookup"><span data-stu-id="08abf-114">Edit Checked-In Files</span></span>](../../2014/database-engine/edit-checked-in-files.md)|<span data-ttu-id="08abf-115">說明如何設定 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 環境，以便修改尚未簽出的檔案。</span><span class="sxs-lookup"><span data-stu-id="08abf-115">Explains how to configure the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment so that you can modify files that are not checked out.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08abf-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08abf-116">See Also</span></span>  
 [<span data-ttu-id="08abf-117">管理簽出</span><span class="sxs-lookup"><span data-stu-id="08abf-117">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  
