---
title: 建立使用者定義階層 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- user-defined hierarchies [Analysis Services]
ms.assetid: 16715b85-0630-4a8e-99b0-c0d213cade26
author: minewiskan
ms.author: owend
ms.openlocfilehash: 17e870a2b20125132342db1845689b7c2481d623
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700324"
---
# <a name="create-user-defined-hierarchies"></a><span data-ttu-id="31187-102">建立使用者定義階層</span><span class="sxs-lookup"><span data-stu-id="31187-102">Create User-Defined Hierarchies</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="31187-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]可讓您建立使用者定義的階層。</span><span class="sxs-lookup"><span data-stu-id="31187-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] lets you create user-defined hierarchies.</span></span> <span data-ttu-id="31187-104">階層是以屬性為基礎的一組層級。</span><span class="sxs-lookup"><span data-stu-id="31187-104">A hierarchy is a collection of levels based on attributes.</span></span> <span data-ttu-id="31187-105">例如，時間階層可能包含年、季、月、週和日等層級。</span><span class="sxs-lookup"><span data-stu-id="31187-105">For example, a time hierarchy might contain the Year, Quarter, Month, Week, and Day levels.</span></span> <span data-ttu-id="31187-106">在某些階層中，每個成員屬性都會唯一隱含上面的成員屬性。</span><span class="sxs-lookup"><span data-stu-id="31187-106">In some hierarchies, each member attribute uniquely implies the member attribute above it.</span></span> <span data-ttu-id="31187-107">這種階層有時稱為自然階層。</span><span class="sxs-lookup"><span data-stu-id="31187-107">This is sometimes referred to as a natural hierarchy.</span></span> <span data-ttu-id="31187-108">使用者可以使用階層來瀏覽 Cube 資料。</span><span class="sxs-lookup"><span data-stu-id="31187-108">A hierarchy can be used by end users to browse cube data.</span></span> <span data-ttu-id="31187-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，使用 [維度設計師] 中的 [階層] 窗格來定義階層。</span><span class="sxs-lookup"><span data-stu-id="31187-109">Define hierarchies by using the Hierarchies pane of Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="31187-110">建立使用者定義階層時，該階層可能會變成「不完全」\*\*。</span><span class="sxs-lookup"><span data-stu-id="31187-110">When you create a user-defined hierarchy, the hierarchy might become *ragged*.</span></span> <span data-ttu-id="31187-111">在不完全階層中，至少一個成員的邏輯父成員不在成員的上一層級內。</span><span class="sxs-lookup"><span data-stu-id="31187-111">A ragged hierarchy is where the logical parent member of at least one member is not in the level immediately above the member.</span></span> <span data-ttu-id="31187-112">如果您有不完全階層，有些設定可以控制是否可以看到遺漏的成員，以及如何顯示遺漏的成員。</span><span class="sxs-lookup"><span data-stu-id="31187-112">If you have a ragged hierarchy, there are settings that control whether the missing members are visible and how to display the missing members.</span></span> <span data-ttu-id="31187-113">如需詳細資訊，請參閱 [不完全階層](user-defined-hierarchies-ragged-hierarchies.md)。</span><span class="sxs-lookup"><span data-stu-id="31187-113">For more information, see [Ragged Hierarchies](user-defined-hierarchies-ragged-hierarchies.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31187-114">如需與使用者定義階層的設計和組態相關之效能問題的詳細資訊，請參閱 [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide)(SQL Server 2005 Analysis Services 效能指南)。</span><span class="sxs-lookup"><span data-stu-id="31187-114">For more information about performance issues related to the design and configuration of user-defined hierarchies, see the [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31187-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31187-115">See Also</span></span>  
 <span data-ttu-id="31187-116">[使用者階層屬性](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md) </span><span class="sxs-lookup"><span data-stu-id="31187-116">[User Hierarchy Properties](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md) </span></span>  
 <span data-ttu-id="31187-117">[&#93;的層級屬性 &#91;Paved](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md) </span><span class="sxs-lookup"><span data-stu-id="31187-117">[Level Properties &#91;Paved Over&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md) </span></span>  
 [<span data-ttu-id="31187-118">父子式階層</span><span class="sxs-lookup"><span data-stu-id="31187-118">Parent-Child Hierarchy</span></span>](parent-child-dimension.md)  
  
  
