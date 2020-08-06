---
title: 工作7：建立複合定義域 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ae778647-1df0-4952-9a69-0ef6177eea9c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 42936d25e267bcad5ba8ae512750f9e12f041579
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584877"
---
# <a name="task-7-creating-a-composite-domain"></a><span data-ttu-id="e67dd-102">工作 7：建立複合定義域</span><span class="sxs-lookup"><span data-stu-id="e67dd-102">Task 7: Creating a Composite Domain</span></span>
  <span data-ttu-id="e67dd-103">在這項工作中，您會建立複合定義域「**位址驗證**」，其中包含「**位址行**」、「**城市**」、「**州**」和「 **Zip** 」網域。</span><span class="sxs-lookup"><span data-stu-id="e67dd-103">In this task, you create a composite domain, **Address Validation**, which comprises **Address Line**, **City**, **State**, and **Zip** domains.</span></span> <span data-ttu-id="e67dd-104">複合定義域可讓您定義在規則中涉及多個定義域的跨定義域規則。</span><span class="sxs-lookup"><span data-stu-id="e67dd-104">A composite domain lets you define a cross-domain rule that involves multiple domains in a rule.</span></span> <span data-ttu-id="e67dd-105">複合定義域還有其他優點，例如能夠將欄位值剖析成多個定義域。</span><span class="sxs-lookup"><span data-stu-id="e67dd-105">There are other advantages to a composite domain such as being able to parse a field value into multiple domains.</span></span>  <span data-ttu-id="e67dd-106">例如，[完整名稱] 欄位的值可以剖析成個別的名字、中間名和姓氏等定義域。</span><span class="sxs-lookup"><span data-stu-id="e67dd-106">For example, a value for a Full Name field can be parsed into separate First Name, Middle Name, and Last Name domains.</span></span> <span data-ttu-id="e67dd-107">在本教學課程中，您只會定義跨定義域規則。</span><span class="sxs-lookup"><span data-stu-id="e67dd-107">In this tutorial, you only define a cross-domain rule.</span></span> <span data-ttu-id="e67dd-108">如需詳細資訊，請參閱[管理複合定義域](https://msdn.microsoft.com/library/hh510399.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e67dd-108">See [Managing a Composite Domain](https://msdn.microsoft.com/library/hh510399.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="e67dd-109">在左窗格中，按一下工具列上的 [**建立複合定義域**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e67dd-109">In the left pane, click **Create a composite domain** button on the toolbar.</span></span>  
  
     <span data-ttu-id="e67dd-110">![[建立複合定義域] 工具列按鈕](../../2014/tutorials/media/et-creatingacompositedomain-01.jpg "[建立複合定義域] 工具列按鈕")</span><span class="sxs-lookup"><span data-stu-id="e67dd-110">![Create a Composite Domain Toolbar Button](../../2014/tutorials/media/et-creatingacompositedomain-01.jpg "Create a Composite Domain Toolbar Button")</span></span>  
  
2.  <span data-ttu-id="e67dd-111">輸入**複合定義功能變數名稱稱**的**位址驗證**。</span><span class="sxs-lookup"><span data-stu-id="e67dd-111">Enter **Address Validation** for the **Composite Domain Name**.</span></span>  
  
     <span data-ttu-id="e67dd-112">![地址驗證複合定義域](../../2014/tutorials/media/et-creatingacompositedomain-02.jpg "地址驗證複合定義域")</span><span class="sxs-lookup"><span data-stu-id="e67dd-112">![Address Validation Composite Domain](../../2014/tutorials/media/et-creatingacompositedomain-02.jpg "Address Validation Composite Domain")</span></span>  
  
3.  <span data-ttu-id="e67dd-113">從 [網域] 清單中選取 [**位址行**]、[**城市**]、[**州**] 和 [**郵遞區號**]，然後按一下**向右箭**號，將它們加入 [**複合定義域中的定義域**]</span><span class="sxs-lookup"><span data-stu-id="e67dd-113">From the domain list select **Address Line**, **City**, **State**, and **Zip** and click **right arrow** to add them to the **Domains in Composite Domain** list.</span></span>  
  
4.  <span data-ttu-id="e67dd-114">按一下 **[確定]** ，關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e67dd-114">Click **OK** to close the dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="e67dd-115">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e67dd-115">Next Step</span></span>  
 [<span data-ttu-id="e67dd-116">工作 8：建立複合定義域規則</span><span class="sxs-lookup"><span data-stu-id="e67dd-116">Task 8: Creating a Composite Domain Rule</span></span>](../../2014/tutorials/task-8-creating-a-composite-domain-rule.md)  
  
  
