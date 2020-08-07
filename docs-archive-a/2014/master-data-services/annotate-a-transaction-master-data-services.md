---
title: 為交易加上註解 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- annotations [Master Data Services], for transactions
ms.assetid: f5a6b2ca-56de-4e42-9da8-fba0ac3e8d92
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c384f4241d0ddcd78fd8942fe28da8c0b5b1e77c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703066"
---
# <a name="annotate-a-transaction-master-data-services"></a><span data-ttu-id="f26a4-102">為交易加上註解 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f26a4-102">Annotate a Transaction (Master Data Services)</span></span>
  <span data-ttu-id="f26a4-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，當您想要提供有關某個交易的支援詳細資料做為歷程記錄時，請為該交易加上註解。</span><span class="sxs-lookup"><span data-stu-id="f26a4-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], annotate a transaction when you want to provide supporting details about the transaction for historical purposes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f26a4-104">您無法刪除註解。</span><span class="sxs-lookup"><span data-stu-id="f26a4-104">You cannot delete annotations.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f26a4-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="f26a4-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="f26a4-106">若要為所建立的交易加上註解，您必須擁有存取 [總管]\*\*\*\* 功能區域的權限，而且至少必須擁有您要加上註解之模型物件的**更新**權限。</span><span class="sxs-lookup"><span data-stu-id="f26a4-106">To annotate transactions that you created, you must have permission to access the **Explorer** functional area, and have a minimum of **Update** permission to the model object you want to annotate.</span></span>  
  
-   <span data-ttu-id="f26a4-107">若要為所有使用者的交易加上註解，您必須擁有存取 [版本管理]\*\*\*\* 功能區域的權限，而且必須身為模型管理員。</span><span class="sxs-lookup"><span data-stu-id="f26a4-107">To annotate transactions for all users, you must have permission to access the **Version Management** functional area and be a model administrator.</span></span> <span data-ttu-id="f26a4-108">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f26a4-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-annotate-a-transaction-in-explorer"></a><span data-ttu-id="f26a4-109">若要在總管中為交易加上註解</span><span class="sxs-lookup"><span data-stu-id="f26a4-109">To annotate a transaction in Explorer</span></span>  
  
1.  <span data-ttu-id="f26a4-110">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 首頁上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="f26a4-110">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="f26a4-111">從 **[版本]** 清單中選取版本。</span><span class="sxs-lookup"><span data-stu-id="f26a4-111">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="f26a4-112">按一下 **[總管]**。</span><span class="sxs-lookup"><span data-stu-id="f26a4-112">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="f26a4-113">從功能表列指向 [實體]\*\*\*\*，然後按一下包含成員且具有您要加上註解之交易的實體。</span><span class="sxs-lookup"><span data-stu-id="f26a4-113">From the menu bar, point to **Entities** and click the entity that contains the member with a transaction you want to annotate.</span></span>  
  
5.  <span data-ttu-id="f26a4-114">在方格中，按一下成員的資料列。</span><span class="sxs-lookup"><span data-stu-id="f26a4-114">In the grid, click the row of the member.</span></span>  
  
6.  <span data-ttu-id="f26a4-115">按一下 [檢視交易]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f26a4-115">Click **View Transactions**.</span></span>  
  
7.  <span data-ttu-id="f26a4-116">在 [檢視交易]\*\*\*\* 對話方塊中，按一下您要加上註解的交易。</span><span class="sxs-lookup"><span data-stu-id="f26a4-116">In the **View Transactions** dialog box, click the transaction you want to annotate.</span></span>  
  
8.  <span data-ttu-id="f26a4-117">在對話方塊底部的方塊中，輸入您的註解。</span><span class="sxs-lookup"><span data-stu-id="f26a4-117">In the box at the bottom of the dialog box, type your annotation.</span></span>  
  
9. <span data-ttu-id="f26a4-118">按一下 [加入註解]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f26a4-118">Click **Add Annotation**.</span></span> <span data-ttu-id="f26a4-119">註解就會顯示在 [註解]\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="f26a4-119">The annotation is displayed in the **Annotations** pane.</span></span>  
  
### <a name="to-annotate-a-transaction-in-version-management-administrators-only"></a><span data-ttu-id="f26a4-120">若要在版本管理中為交易加上註解 (僅限系統管理員)</span><span class="sxs-lookup"><span data-stu-id="f26a4-120">To annotate a transaction in Version Management (administrators only)</span></span>  
  
1.  <span data-ttu-id="f26a4-121">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 首頁上，按一下 [版本管理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f26a4-121">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="f26a4-122">在功能表列上，按一下 [交易]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f26a4-122">On the menu bar, click **Transactions**.</span></span>  
  
3.  <span data-ttu-id="f26a4-123">在 [交易]\*\*\*\* 窗格中，針對您想要加上註解的交易，按一下方格中的資料列。</span><span class="sxs-lookup"><span data-stu-id="f26a4-123">In the **Transactions** pane, click the row in the grid for the transaction you want to annotate.</span></span>  
  
4.  <span data-ttu-id="f26a4-124">在 [交易註解]\*\*\*\* 窗格的 [註解]\*\*\*\* 方塊中，輸入您的註解。</span><span class="sxs-lookup"><span data-stu-id="f26a4-124">In the **Transaction Annotations** pane, in the **Annotation** box, type your annotation.</span></span>  
  
5.  <span data-ttu-id="f26a4-125">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="f26a4-125">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f26a4-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f26a4-126">See Also</span></span>  
 <span data-ttu-id="f26a4-127">[批註 &#40;Master Data Services&#41;](../../2014/master-data-services/annotations-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f26a4-127">[Annotations &#40;Master Data Services&#41;](../../2014/master-data-services/annotations-master-data-services.md) </span></span>  
 [<span data-ttu-id="f26a4-128">交易 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f26a4-128">Transactions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/transactions-master-data-services.md)  
  
  
