---
title: 反轉交易 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Master Data Services], reversing
ms.assetid: 6f7c3f07-0f64-4283-8c9c-93facd00a046
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fb5b1b0932b65b1d6f8fe7b1bc842836e21aaca6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698344"
---
# <a name="reverse-a-transaction-master-data-services"></a><span data-ttu-id="595fb-102">反轉交易 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="595fb-102">Reverse a Transaction (Master Data Services)</span></span>
  <span data-ttu-id="595fb-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，系統管理員可以在需要復原動作時，反轉交易。</span><span class="sxs-lookup"><span data-stu-id="595fb-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], administrators can reverse a transaction when an action needs to be undone.</span></span> <span data-ttu-id="595fb-104">交易的範例包括屬性值變更、階層移動或成員刪除。</span><span class="sxs-lookup"><span data-stu-id="595fb-104">Examples of transactions are attribute value changes, hierarchy moves, or member deletions.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="595fb-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="595fb-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="595fb-106">您必須擁有存取 **[版本管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="595fb-106">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="595fb-107">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="595fb-107">You must be a model administrator.</span></span> <span data-ttu-id="595fb-108">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="595fb-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-reverse-a-transaction"></a><span data-ttu-id="595fb-109">若要反轉交易</span><span class="sxs-lookup"><span data-stu-id="595fb-109">To reverse a transaction</span></span>  
  
1.  <span data-ttu-id="595fb-110">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 首頁上，按一下 [版本管理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="595fb-110">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="595fb-111">在功能表列上，按一下 [交易]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="595fb-111">On the menu bar, click **Transactions**.</span></span>  
  
3.  <span data-ttu-id="595fb-112">在 [交易]\*\*\*\* 頁面上，選取 [模型]\*\*\*\* 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="595fb-112">On the **Transactions** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="595fb-113">從 **[版本]** 清單中選取版本。</span><span class="sxs-lookup"><span data-stu-id="595fb-113">From the **Version** list, select a version.</span></span>  
  
5.  <span data-ttu-id="595fb-114">針對您想要反轉的交易，按一下方格中的資料列。</span><span class="sxs-lookup"><span data-stu-id="595fb-114">Click the row in the grid for the transaction you want to reverse.</span></span>  
  
6.  <span data-ttu-id="595fb-115">按一下 [反轉交易]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="595fb-115">Click **Reverse Transaction**.</span></span>  
  
7.  <span data-ttu-id="595fb-116">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="595fb-116">In the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="595fb-117">如此就會將另一個交易加入至方格，以便記錄反轉的交易。</span><span class="sxs-lookup"><span data-stu-id="595fb-117">Another transaction is added to the grid to record the reversed transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="595fb-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="595fb-118">See Also</span></span>  
 <span data-ttu-id="595fb-119">[交易 &#40;Master Data Services&#41;](../../2014/master-data-services/transactions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="595fb-119">[Transactions &#40;Master Data Services&#41;](../../2014/master-data-services/transactions-master-data-services.md) </span></span>  
 [<span data-ttu-id="595fb-120">重新啟用成員或集合 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="595fb-120">Reactivate a Member or Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md)  
  
  
