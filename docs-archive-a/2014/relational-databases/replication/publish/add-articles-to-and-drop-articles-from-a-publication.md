---
title: 在發行集中加入和卸載發行項 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], dropping
- deleting articles
- dropping articles
- adding articles
- articles [SQL Server replication], adding
ms.assetid: d5a3e536-62d2-4473-a178-877ba52f7d7f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f7af1cac1f3ee8ecc9cb79632f8a4ef1e66ec82f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606770"
---
# <a name="add-articles-to-and-drop-articles-from-a-publication-sql-server-management-studio"></a><span data-ttu-id="d0635-102">從發行集中加入和卸除發行項 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="d0635-102">Add Articles to and Drop Articles from a Publication (SQL Server Management Studio)</span></span>
  <span data-ttu-id="d0635-103">當您在「新增發行集精靈」中建立發行集後，最開始要向其中新增發行項。</span><span class="sxs-lookup"><span data-stu-id="d0635-103">Initially add articles to a publication when you create it in the New Publication Wizard.</span></span> <span data-ttu-id="d0635-104">如需使用此精靈的詳細資訊，請參閱[建立發行集](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="d0635-104">For more information about using this wizard, see [Create a Publication](create-a-publication.md).</span></span>  
  
 <span data-ttu-id="d0635-105">建立發行集之後，在 [發行集屬性 - \<Publication>] 對話方塊的 [發行項] 頁面中，新增和刪除發行項。</span><span class="sxs-lookup"><span data-stu-id="d0635-105">After a publication is created, add and delete articles on the **Articles** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="d0635-106">如需有關存取這個對話方塊的詳細資訊，請參閱＜ [View and Modify Publication Properties](view-and-modify-publication-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d0635-106">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span> <span data-ttu-id="d0635-107">如需新增及卸除發行項的詳細資訊，請參閱[在現有發行集中新增和卸除發行項](add-articles-to-and-drop-articles-from-existing-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="d0635-107">For information about the considerations for adding and dropping articles, see [Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
### <a name="to-add-an-article-after-a-publication-is-created"></a><span data-ttu-id="d0635-108">若要在建立發行集之後新增發行項</span><span class="sxs-lookup"><span data-stu-id="d0635-108">To add an article after a publication is created</span></span>  
  
1.  <span data-ttu-id="d0635-109">在 [發行集屬性 - \<Publication>] 對話方塊的 [發行項] 頁面中，清除 [僅顯示清單中已核取的物件] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d0635-109">On the **Articles** page of the **Publication Properties - \<Publication>** dialog box, clear the **Show only checked objects in the list** check box.</span></span> <span data-ttu-id="d0635-110">這將允許您查看發行集資料庫中的未發行物件。</span><span class="sxs-lookup"><span data-stu-id="d0635-110">This allows you to see the unpublished objects in the publication database.</span></span>  
  
2.  <span data-ttu-id="d0635-111">選取您要新增之每一個發行項旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d0635-111">Select the check box next to each article you want to add.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-delete-an-article"></a><span data-ttu-id="d0635-112">若要刪除發行項</span><span class="sxs-lookup"><span data-stu-id="d0635-112">To delete an article</span></span>  
  
1.  <span data-ttu-id="d0635-113">在 [發行集屬性 - \<Publication>] 對話方塊的 [發行項] 頁面中，清除所要刪除每個發行項旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d0635-113">On the **Articles** page of the **Publication Properties - \<Publication>** dialog box, clear the check box next to each article you want to delete.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d0635-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0635-114">See Also</span></span>  
 <span data-ttu-id="d0635-115">[Define an Article](define-an-article.md) </span><span class="sxs-lookup"><span data-stu-id="d0635-115">[Define an Article](define-an-article.md) </span></span>  
 [<span data-ttu-id="d0635-116">發行資料和資料庫物件</span><span class="sxs-lookup"><span data-stu-id="d0635-116">Publish Data and Database Objects</span></span>](publish-data-and-database-objects.md)  
  
  
