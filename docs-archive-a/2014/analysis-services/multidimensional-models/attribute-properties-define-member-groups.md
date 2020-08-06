---
title: 定義成員群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- member groups [Analysis Services]
- grouping members
- DiscretizationMethod property
ms.assetid: 006cc915-c499-4781-b9a7-01ad31bebf6a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 95f9516c7a0077e97af348afa863fe15c8d4528b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708797"
---
# <a name="define-member-groups"></a><span data-ttu-id="b0e96-102">定義成員群組</span><span class="sxs-lookup"><span data-stu-id="b0e96-102">Define Member Groups</span></span>
  <span data-ttu-id="b0e96-103">如果屬性有大量成員，您可以選擇將這些成員分組成值區，減少使用者在階層中瀏覽資料時所看到的成員數目。</span><span class="sxs-lookup"><span data-stu-id="b0e96-103">If an attribute has a large number of members, you can choose to group those members into buckets, reducing the number of members that users see when they browse the data in a hierarchy.</span></span> <span data-ttu-id="b0e96-104">您也可以決定成員分組的值區數目和設定值區的命名配置。</span><span class="sxs-lookup"><span data-stu-id="b0e96-104">You can also determine the number of buckets in which the members are groups and set a naming scheme for the buckets.</span></span> <span data-ttu-id="b0e96-105">如需詳細資訊，請參閱[群組屬性成員 &#40;離散化&#41;](attribute-properties-group-attribute-members.md)。</span><span class="sxs-lookup"><span data-stu-id="b0e96-105">For more information, see [Group Attribute Members &#40;Discretization&#41;](attribute-properties-group-attribute-members.md).</span></span>  
  
 <span data-ttu-id="b0e96-106">您可藉由設定 **[DiscretizationMethod]** 屬性來群組成員，這個屬性是透過 **中的** [屬性] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]視窗來加以存取。</span><span class="sxs-lookup"><span data-stu-id="b0e96-106">You group members by setting the **DiscretizationMethod** property, which is accessed through the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="b0e96-107">當您建立成員群組時，要等到您處理該維度之後，使用者才能看到您所做的變更。</span><span class="sxs-lookup"><span data-stu-id="b0e96-107">When you create member groups, your changes are not available to users until you process the dimension.</span></span> <span data-ttu-id="b0e96-108">如需詳細資訊，請參閱多[維度模型物件處理](processing-a-multidimensional-model-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b0e96-108">For more information, see [Multidimensional Model Object Processing](processing-a-multidimensional-model-analysis-services.md).</span></span>  
  
### <a name="to-create-member-groups"></a><span data-ttu-id="b0e96-109">若要建立成員群組</span><span class="sxs-lookup"><span data-stu-id="b0e96-109">To create member groups</span></span>  
  
1.  <span data-ttu-id="b0e96-110">開啟您要使用的維度。</span><span class="sxs-lookup"><span data-stu-id="b0e96-110">Open the dimension that you want to work with.</span></span> <span data-ttu-id="b0e96-111">依預設，會開啟 **[維度結構]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b0e96-111">The **Dimension Structure** tab opens by default.</span></span>  
  
2.  <span data-ttu-id="b0e96-112">在 [屬性]\*\*\*\* 中，以滑鼠右鍵按一下您要將其成員分組的屬性，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b0e96-112">In **Attributes**, right-click the attribute whose members you want to group, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="b0e96-113">從 [DiscretizationMethod]\*\*\*\* 旁邊的下拉式清單中，選取將成員分組的方法。</span><span class="sxs-lookup"><span data-stu-id="b0e96-113">From the drop-down list next to **DiscretizationMethod**, select a method by which to group the members.</span></span> <span data-ttu-id="b0e96-114">如需 **DiscretizationMethod** 設定的詳細資訊，請參閱 [Group Attribute Members &#40;Discretization&#41;](attribute-properties-group-attribute-members.md) (群組屬性成員 (分隔))。</span><span class="sxs-lookup"><span data-stu-id="b0e96-114">For more information about **DiscretizationMethod** settings, see [Group Attribute Members &#40;Discretization&#41;](attribute-properties-group-attribute-members.md).</span></span>  
  
  
