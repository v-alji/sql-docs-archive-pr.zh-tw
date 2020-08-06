---
title: 設定屬性階層的 (所有) 層級 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- All members
- IsAggregatable property
- topmost levels [Analysis Services]
- (All) levels
- AttributeAllMemberName property
- levels [Analysis Services]
- members [Analysis Services], All
- AllMemberName property
ms.assetid: 0cb35e6f-b10f-483d-b893-78f6ca3979fd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9874a8c8a6861bc7d9e44271b089e8af3a4c0ae2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698695"
---
# <a name="configure-the-all-level-for-attribute-hierarchies"></a><span data-ttu-id="0d8eb-102">設定屬性階層的 (全部) 層級</span><span class="sxs-lookup"><span data-stu-id="0d8eb-102">Configure the (All) Level for Attribute Hierarchies</span></span>
  <span data-ttu-id="0d8eb-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ， (所有) 層級都是選擇性的系統產生層級。</span><span class="sxs-lookup"><span data-stu-id="0d8eb-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the (All) level is an optional, system-generated level.</span></span> <span data-ttu-id="0d8eb-104">它只包含一個成員，而這個成員的值是直屬層級中所有成員的值彙總。</span><span class="sxs-lookup"><span data-stu-id="0d8eb-104">It contains only one member whose value is the aggregation of the values of all members in the immediately subordinate level.</span></span> <span data-ttu-id="0d8eb-105">此成員叫作全部成員。</span><span class="sxs-lookup"><span data-stu-id="0d8eb-105">This member is called the All member.</span></span> <span data-ttu-id="0d8eb-106">它是系統產生的成員，不包含在維度資料表中。</span><span class="sxs-lookup"><span data-stu-id="0d8eb-106">It is a system-generated member that is not contained in the dimension table.</span></span> <span data-ttu-id="0d8eb-107">因為 (全部) 層級中的成員是在階層頂端，所以該成員值是此階層中所有成員值的合併彙總。</span><span class="sxs-lookup"><span data-stu-id="0d8eb-107">Because the member in the (All) level is at the top of the hierarchy, the member's value is the consolidated aggregation of the values of all members in the hierarchy.</span></span> <span data-ttu-id="0d8eb-108">全部成員通常是做為階層的預設成員。</span><span class="sxs-lookup"><span data-stu-id="0d8eb-108">The All member often serves as the default member of a hierarchy.</span></span>  
  
 <span data-ttu-id="0d8eb-109">(全部) 層級是否出現在屬性階層中，視該屬性的 `IsAggregatable` 屬性設定而定，(全部) 層級是否出現在使用者自訂階層中，視使用者自訂階層最上層之該屬性的 `IsAggregatable` 屬性而定。</span><span class="sxs-lookup"><span data-stu-id="0d8eb-109">The presence of an (All) level in an attribute hierarchy depends on the `IsAggregatable` property setting for the attribute and the presence of an (All) level in a user-defined hierarchy depends on the `IsAggregatable` property of the attribute at the top-most level of user-defined hierarchy.</span></span> <span data-ttu-id="0d8eb-110">如果 `IsAggregatable` 屬性設為 `True`，則 (全部) 層級會存在。</span><span class="sxs-lookup"><span data-stu-id="0d8eb-110">If the `IsAggregatable` property is set to `True`, an (All) level will exist.</span></span> <span data-ttu-id="0d8eb-111">如果 `IsAggregatable` 屬性設為 `False`，則階層沒有 (全部) 層級。</span><span class="sxs-lookup"><span data-stu-id="0d8eb-111">A hierarchy has no (All) level if the `IsAggregatable` property is set to `False`.</span></span>  
  
## <a name="establishing-the-topmost-level"></a><span data-ttu-id="0d8eb-112">建立最上層</span><span class="sxs-lookup"><span data-stu-id="0d8eb-112">Establishing the Topmost Level</span></span>  
 <span data-ttu-id="0d8eb-113">如果 `IsAggregatable` 屬性設為階層中某層級之來源屬性上的 `False`，則可彙總層級不會出現在階層中的該層級上方。</span><span class="sxs-lookup"><span data-stu-id="0d8eb-113">If the `IsAggregatable` property is set to `False` on the source attribute of a level in a hierarchy, then no aggregatable level can appear in the hierarchy above that level.</span></span> <span data-ttu-id="0d8eb-114">不可彙總層級必須是任何階層的最上層，否則，它上方層級之來源屬性的 `IsAggregatable` 屬性也必須設為 `False`。</span><span class="sxs-lookup"><span data-stu-id="0d8eb-114">A non-aggregatable level must be the topmost level of any hierarchy or the `IsAggregatable` property of the source attributes for any levels above it must also be set to `False`.</span></span>  
  
## <a name="all-member-and-all-level"></a><span data-ttu-id="0d8eb-115">全部成員和 (全部) 層級</span><span class="sxs-lookup"><span data-stu-id="0d8eb-115">All Member and (All) Level</span></span>  
 <span data-ttu-id="0d8eb-116">(全部) 層級的單一成員叫做全部成員。</span><span class="sxs-lookup"><span data-stu-id="0d8eb-116">The single member of the (All) level is called the All member.</span></span> <span data-ttu-id="0d8eb-117">`AttributeAllMemberName`維度上的屬性會指定維度中屬性的所有成員名稱。</span><span class="sxs-lookup"><span data-stu-id="0d8eb-117">The `AttributeAllMemberName`property on a dimension specifies the name of the All member for attributes in a dimension.</span></span> <span data-ttu-id="0d8eb-118">階層的 `AllMemberName` 屬性指定階層的全部成員名稱。</span><span class="sxs-lookup"><span data-stu-id="0d8eb-118">The `AllMemberName` property on a hierarchy specifies the name of the All member for the hierarchy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d8eb-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d8eb-119">See Also</span></span>  
 [<span data-ttu-id="0d8eb-120">定義預設成員</span><span class="sxs-lookup"><span data-stu-id="0d8eb-120">Define a Default Member</span></span>](attribute-properties-define-a-default-member.md)  
  
  
