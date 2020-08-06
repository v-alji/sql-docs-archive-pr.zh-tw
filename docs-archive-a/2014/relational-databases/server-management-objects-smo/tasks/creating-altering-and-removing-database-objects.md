---
title: 使用資料庫物件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- database objects [SMO]
- objects [SMO]
ms.assetid: 702fd63d-8734-4a02-872e-aecfb037c787
author: stevestein
ms.author: sstein
ms.openlocfilehash: 14dd0c0175a23f809fc925c5104ac15ac408805b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707350"
---
# <a name="working-with-database-objects"></a><span data-ttu-id="0acd5-102">使用資料庫物件</span><span class="sxs-lookup"><span data-stu-id="0acd5-102">Working with Database Objects</span></span>
  <span data-ttu-id="0acd5-103">建立 SMO 物件的階段如下：</span><span class="sxs-lookup"><span data-stu-id="0acd5-103">The stages of SMO object creation are as follows:</span></span>  
  
1.  <span data-ttu-id="0acd5-104">建立物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0acd5-104">Create an instance of the object.</span></span>  
  
2.  <span data-ttu-id="0acd5-105">設定物件屬性。</span><span class="sxs-lookup"><span data-stu-id="0acd5-105">Set the object properties.</span></span>  
  
3.  <span data-ttu-id="0acd5-106">建立子物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0acd5-106">Create instances of the child objects.</span></span>  
  
4.  <span data-ttu-id="0acd5-107">設定子物件屬性。</span><span class="sxs-lookup"><span data-stu-id="0acd5-107">Set the child object properties.</span></span>  
  
5.  <span data-ttu-id="0acd5-108">建立物件。</span><span class="sxs-lookup"><span data-stu-id="0acd5-108">Create the object.</span></span>  
  
 <span data-ttu-id="0acd5-109">在 SMO 應用程式中建立 SMO 物件的執行個體時，它們不會存在於 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體上，直到發出 `Create` 方法。</span><span class="sxs-lookup"><span data-stu-id="0acd5-109">When instances of SMO objects are created in an SMO application, they do not exist on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] until the `Create` method is issued.</span></span> <span data-ttu-id="0acd5-110">不過，並非每個個別物件都需要發出 `Create` 方法。</span><span class="sxs-lookup"><span data-stu-id="0acd5-110">However, it is not necessary to issue a `Create` method for every individual object.</span></span> <span data-ttu-id="0acd5-111">如果某個物件包含一組子物件，只需要父物件才能執行 `Create` 方法。</span><span class="sxs-lookup"><span data-stu-id="0acd5-111">If an object has a set of child objects, only the parent object is required to run the `Create` method.</span></span> <span data-ttu-id="0acd5-112">例如，資料表的定義要求資料表至少要包含一個資料行才能存在。</span><span class="sxs-lookup"><span data-stu-id="0acd5-112">For example, the definition of a table requires that it contains at least one column to exist.</span></span> <span data-ttu-id="0acd5-113">同時，如果沒有資料表，資料行無法獨立存在。</span><span class="sxs-lookup"><span data-stu-id="0acd5-113">Also, a column cannot exist in isolation without a table.</span></span> <span data-ttu-id="0acd5-114">在資料表及其資料行之間有一個共同相依的關聯性。</span><span class="sxs-lookup"><span data-stu-id="0acd5-114">There is a codependent relationship between the table and its columns.</span></span>  
  
 <span data-ttu-id="0acd5-115"> 方法可讓您對物件進行變更。</span><span class="sxs-lookup"><span data-stu-id="0acd5-115">The <xref:Microsoft.SqlServer.Management.Dmf.Policy.Alter%2A> method lets you make changes to an object.</span></span> <span data-ttu-id="0acd5-116">對於物件的數個變更 (例如，將子物件加入到其中一個物件的集合，或變更屬性值)，會一起進行批次處理，並當做一個變更來執行。</span><span class="sxs-lookup"><span data-stu-id="0acd5-116">Several changes to an object, such as adding child objects to one of the object's collections or changing a property value, are batched together and run as one.</span></span> <span data-ttu-id="0acd5-117">`Alter` 方法會降低網路流量並改善整體效能。</span><span class="sxs-lookup"><span data-stu-id="0acd5-117">The `Alter` method reduces network traffic and improves overall performance.</span></span>  
  
 <span data-ttu-id="0acd5-118">`Drop` 陳述式用於移除一開始建立物件所需的物件及其所有共同相依的子物件。</span><span class="sxs-lookup"><span data-stu-id="0acd5-118">The `Drop` statement is used to remove an object and all its codependent child objects that were required to create the object initially.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0acd5-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0acd5-119">See Also</span></span>  
 [<span data-ttu-id="0acd5-120">SMO 物件模型</span><span class="sxs-lookup"><span data-stu-id="0acd5-120">SMO Object Model</span></span>](../smo-object-model.md)  
  
  
