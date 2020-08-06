---
title: CLR 常式的自訂屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- SqlFacet attribute
- SqlTrigger attribute
- SqlProcedure attribute
- custom attributes [CLR integration]
- SqlUserDefinedAggregate attribute
- attributes [CLR integration]
- SqlMethod attribute
- SqlFunction attribute
- common language runtime [SQL Server], attributes
- SqlUserDefinedTypeAttribute attribute
ms.assetid: 95069d22-b05d-4670-b053-15ee2a664e33
author: rothja
ms.author: jroth
ms.openlocfilehash: 058bbec7f0f1f63fbd96258a0abe7a6c3d543d88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584581"
---
# <a name="custom-attributes-for-clr-routines"></a><span data-ttu-id="e63d9-102">CLR 常式的自訂屬性</span><span class="sxs-lookup"><span data-stu-id="e63d9-102">Custom Attributes for CLR Routines</span></span>
  <span data-ttu-id="e63d9-103">列出的屬性可以套用到 common language runtime (CLR) 常式、使用者定義型別，以及在中註冊的使用者定義匯總 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e63d9-103">The attributes listed can be applied to common language runtime (CLR) routines, user-defined types, and user-defined aggregates that are registered in [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e63d9-104">如果沒有套用屬性，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會假設預設值。</span><span class="sxs-lookup"><span data-stu-id="e63d9-104">If the attribute is not applied, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] assumes the default value.</span></span> <span data-ttu-id="e63d9-105">列出的屬性是在 `Microsoft.SqlServer.Server` 命令空間中定義的。</span><span class="sxs-lookup"><span data-stu-id="e63d9-105">The attributes listed are defined in the `Microsoft.SqlServer.Server` namespace.</span></span>  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a><span data-ttu-id="e63d9-106">SqlUserDefinedAggregate 屬性</span><span class="sxs-lookup"><span data-stu-id="e63d9-106">The SqlUserDefinedAggregate Attribute</span></span>  
 <span data-ttu-id="e63d9-107">`SqlUserDefinedAggregate` 屬性會指出應該將方法註冊為使用者定義彙總。</span><span class="sxs-lookup"><span data-stu-id="e63d9-107">The `SqlUserDefinedAggregate` attribute indicates that the method should be registered as a user-defined aggregate.</span></span> <span data-ttu-id="e63d9-108">每個使用者定義彙總都必須使用這個屬性加註。</span><span class="sxs-lookup"><span data-stu-id="e63d9-108">Every user-defined aggregate must be annotated with this attribute.</span></span>  
  
 <span data-ttu-id="e63d9-109">如需詳細資訊，請參閱[SqlUserDefinedAggregateAttribute](https://go.microsoft.com/fwlink/?LinkId=124626)。</span><span class="sxs-lookup"><span data-stu-id="e63d9-109">For more information, see [SqlUserDefinedAggregateAttribute](https://go.microsoft.com/fwlink/?LinkId=124626).</span></span>  
  
## <a name="the-sqlfunction-attribute"></a><span data-ttu-id="e63d9-110">SqlFunction 屬性</span><span class="sxs-lookup"><span data-stu-id="e63d9-110">The SqlFunction Attribute</span></span>  
 <span data-ttu-id="e63d9-111">`SqlFunction` 屬性會利用適當的函數屬性集指出應該將方法註冊為函數。</span><span class="sxs-lookup"><span data-stu-id="e63d9-111">The `SqlFunction` attribute indicates the method should be registered as a function, with the appropriate function attributes set.</span></span>  
  
 <span data-ttu-id="e63d9-112">如需詳細資訊，請參閱[SqlFunctionAttribute](https://go.microsoft.com/fwlink/?LinkId=128019)。</span><span class="sxs-lookup"><span data-stu-id="e63d9-112">For more information, see [SqlFunctionAttribute](https://go.microsoft.com/fwlink/?LinkId=128019).</span></span>  
  
## <a name="the-sqlfacet-attribute"></a><span data-ttu-id="e63d9-113">SqlFacet 屬性</span><span class="sxs-lookup"><span data-stu-id="e63d9-113">The SqlFacet Attribute</span></span>  
 <span data-ttu-id="e63d9-114">`SqlFacet` 屬性用於傳回使用者定義型別 (UDT) 運算式之傳回類型的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e63d9-114">The `SqlFacet` attribute is used to return information about the return type of a user-defined type (UDT) expression.</span></span>  
  
 <span data-ttu-id="e63d9-115">如需詳細資訊，請參閱[SqlFacetAttribute](https://go.microsoft.com/fwlink/?LinkId=128020)。</span><span class="sxs-lookup"><span data-stu-id="e63d9-115">For more information, see [SqlFacetAttribute](https://go.microsoft.com/fwlink/?LinkId=128020).</span></span>  
  
## <a name="the-sqlprocedure-attribute"></a><span data-ttu-id="e63d9-116">SqlProcedure 屬性</span><span class="sxs-lookup"><span data-stu-id="e63d9-116">The SqlProcedure Attribute</span></span>  
 <span data-ttu-id="e63d9-117">`SqlProcedure` 屬性會指出應該將方法註冊為預存程序。</span><span class="sxs-lookup"><span data-stu-id="e63d9-117">The `SqlProcedure` attribute indicates the method should be registered as a stored procedure.</span></span> <span data-ttu-id="e63d9-118">這個屬性只由 Visual Studio 用於自動將指定的方法註冊為預存程序；[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不會使用該屬性。</span><span class="sxs-lookup"><span data-stu-id="e63d9-118">This attribute is used only by Visual Studio to register the specified method as a stored procedure automatically; it is not used by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="e63d9-119">如需詳細資訊，請參閱[SqlProcedureAttribute](https://go.microsoft.com/fwlink/?LinkId=128021)。</span><span class="sxs-lookup"><span data-stu-id="e63d9-119">For more information, see [SqlProcedureAttribute](https://go.microsoft.com/fwlink/?LinkId=128021).</span></span>  
  
## <a name="the-sqltrigger-attribute"></a><span data-ttu-id="e63d9-120">SqlTrigger 屬性</span><span class="sxs-lookup"><span data-stu-id="e63d9-120">The SqlTrigger Attribute</span></span>  
 <span data-ttu-id="e63d9-121">`SqlTrigger` 屬性會指出應該將方法註冊為觸發程序。</span><span class="sxs-lookup"><span data-stu-id="e63d9-121">The `SqlTrigger` attribute indicates the method should be registered as a trigger.</span></span>  
  
 <span data-ttu-id="e63d9-122">如需詳細資訊，請參閱[SqlTriggerCoNtext](https://go.microsoft.com/fwlink/?LinkId=128022)和[SqlTriggerAttribute](https://go.microsoft.com/fwlink/?LinkId=203898)。</span><span class="sxs-lookup"><span data-stu-id="e63d9-122">For more information, see [SqlTriggerContext](https://go.microsoft.com/fwlink/?LinkId=128022) and [SqlTriggerAttribute](https://go.microsoft.com/fwlink/?LinkId=203898).</span></span>  
  
## <a name="the-sqluserdefinedtypeattribute"></a><span data-ttu-id="e63d9-123">SqlUserDefinedTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="e63d9-123">The SqlUserDefinedTypeAttribute</span></span>  
 <span data-ttu-id="e63d9-124">您可以將 SqlUserDefinedTypeAttribute 套用到組件中的類別定義。</span><span class="sxs-lookup"><span data-stu-id="e63d9-124">You can apply the SqlUserDefinedTypeAttribute to a class definition in the assembly.</span></span> <span data-ttu-id="e63d9-125">它會使 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 建立繫結至包含此自訂屬性之類別定義的使用者定義型別。</span><span class="sxs-lookup"><span data-stu-id="e63d9-125">It causes [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to create a user-defined type that is bound to the class definition which has this custom attribute.</span></span>  
  
 <span data-ttu-id="e63d9-126">如需詳細資訊，請參閱[SqlUserDefinedTypeAttribute](https://go.microsoft.com/fwlink/?LinkId=128024)。</span><span class="sxs-lookup"><span data-stu-id="e63d9-126">For more information, see [SqlUserDefinedTypeAttribute](https://go.microsoft.com/fwlink/?LinkId=128024).</span></span>  
  
## <a name="the-sqlmethod-attribute"></a><span data-ttu-id="e63d9-127">SqlMethod 屬性</span><span class="sxs-lookup"><span data-stu-id="e63d9-127">The SqlMethod Attribute</span></span>  
 <span data-ttu-id="e63d9-128">`SqlMethod` 屬性用於表示 UDT 之方法或屬性的決定機制和資料存取屬性。</span><span class="sxs-lookup"><span data-stu-id="e63d9-128">The `SqlMethod` attribute is used to indicate the determinism and data access properties of a method or a property on a UDT.</span></span>  
  
 <span data-ttu-id="e63d9-129">如需詳細資訊，請參閱[SqlMethodAttribute](https://go.microsoft.com/fwlink/?LinkId=128025)。</span><span class="sxs-lookup"><span data-stu-id="e63d9-129">For more information, see [SqlMethodAttribute](https://go.microsoft.com/fwlink/?LinkId=128025).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e63d9-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e63d9-130">See Also</span></span>  
 <span data-ttu-id="e63d9-131">[CLR 使用者定義匯總](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md) </span><span class="sxs-lookup"><span data-stu-id="e63d9-131">[CLR User-Defined Aggregates](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md) </span></span>  
 <span data-ttu-id="e63d9-132">[CLR 使用者定義函數](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md) </span><span class="sxs-lookup"><span data-stu-id="e63d9-132">[CLR User-Defined Functions](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md) </span></span>  
 <span data-ttu-id="e63d9-133">[CLR 使用者定義類型](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) </span><span class="sxs-lookup"><span data-stu-id="e63d9-133">[CLR User-Defined Types](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) </span></span>  
 <span data-ttu-id="e63d9-134">[CLR 預存程式](../../../database-engine/dev-guide/clr-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="e63d9-134">[CLR Stored Procedures](../../../database-engine/dev-guide/clr-stored-procedures.md) </span></span>  
 [<span data-ttu-id="e63d9-135">CLR 觸發程序</span><span class="sxs-lookup"><span data-stu-id="e63d9-135">CLR Triggers</span></span>](../../../database-engine/dev-guide/clr-triggers.md)  
  
  
