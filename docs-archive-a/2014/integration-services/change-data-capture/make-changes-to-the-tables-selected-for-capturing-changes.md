---
title: 變更為了擷取變更所選取的資料表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- makChanToTab
ms.assetid: a309f82a-c6ef-464d-a6ef-df555bfb609a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 258eb8e761ac697bebd630cc0e627941b4ffc7d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593515"
---
# <a name="make-changes-to-the-tables-selected-for-capturing-changes"></a><span data-ttu-id="edd21-102">變更為了擷取變更所選取的資料表</span><span class="sxs-lookup"><span data-stu-id="edd21-102">Make Changes to the Tables Selected for Capturing Changes</span></span>
  <span data-ttu-id="edd21-103">在此對話方塊中，您可以從要擷取變更的選定資料表中選取特定資料行。</span><span class="sxs-lookup"><span data-stu-id="edd21-103">In this dialog box, you can select specific columns from the selected table to capture changes from.</span></span> <span data-ttu-id="edd21-104">您也可以編輯 **[安全性角色]** 和 **[擷取執行個體]** 資訊。</span><span class="sxs-lookup"><span data-stu-id="edd21-104">You can also edit the **Security Role** and **Capture Instance** information.</span></span>  
  
 <span data-ttu-id="edd21-105">您可以針對您在此對話方塊中為了擷取變更所選取的資料表進行以下變更。</span><span class="sxs-lookup"><span data-stu-id="edd21-105">You can make the following changes to the tables you selected for capturing changes in this dialog box.</span></span>  
  
 <span data-ttu-id="edd21-106">**對資料行所做的變更會包含在 CDC 執行個體中：**</span><span class="sxs-lookup"><span data-stu-id="edd21-106">**Make changes to which columns are included in the CDC instance:**</span></span>  
  
 <span data-ttu-id="edd21-107">執行下列其中一項或兩項作業：</span><span class="sxs-lookup"><span data-stu-id="edd21-107">Do one or both of the following:</span></span>  
  
-   <span data-ttu-id="edd21-108">選取您要包含的其他任何資料行旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="edd21-108">Select the check box next to any additional column you want to include.</span></span>  
  
-   <span data-ttu-id="edd21-109">清除您不想再包含的任何資料行旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="edd21-109">Clear the check box next to any column that you no longer want to include.</span></span>  
  
 <span data-ttu-id="edd21-110">**變更特定資料行的資料類型**：</span><span class="sxs-lookup"><span data-stu-id="edd21-110">**Change the data type for a specific column**:</span></span>  
  
 <span data-ttu-id="edd21-111">您可以針對特定的資料行選取不同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="edd21-111">You can select a different data type for a specific column.</span></span> <span data-ttu-id="edd21-112">您只能將資料類型變更為與原始資料類型相容的資料類型。</span><span class="sxs-lookup"><span data-stu-id="edd21-112">You can only change the data type to a data type that is compatible with the original data type.</span></span>  
  
 <span data-ttu-id="edd21-113">若要變更資料類型，請按一下 **[資料類型]** 資料行，並選取不同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="edd21-113">To change the data type, click in the **Data Type** column and select a different data type.</span></span> <span data-ttu-id="edd21-114">只能使用與原始資料類型相容的資料類型。</span><span class="sxs-lookup"><span data-stu-id="edd21-114">Only data types that are compatible with the original data type are available.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="edd21-115">如果沒有其他資料類型可以選擇，就無法使用下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="edd21-115">If no additional data types can be selected, the drop-down list is not available.</span></span>  
  
 <span data-ttu-id="edd21-116">**變更安全性角色**</span><span class="sxs-lookup"><span data-stu-id="edd21-116">**Change the Security Role**</span></span>  
  
 <span data-ttu-id="edd21-117">在 **[安全性角色]** 欄位中，輸入新的名稱或是編輯安全性控制角色的名稱。</span><span class="sxs-lookup"><span data-stu-id="edd21-117">Type a new name or edit the name of the security gating role in the **Security Role** field.</span></span>  
  
 <span data-ttu-id="edd21-118">**變更或加入擷取執行個體**</span><span class="sxs-lookup"><span data-stu-id="edd21-118">**Change or add a capture instance**</span></span>  
  
 <span data-ttu-id="edd21-119">在 **[擷取執行個體]** 欄位中，輸入擷取執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="edd21-119">In the **Capture Instance** field enter a name for the capture instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edd21-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edd21-120">See Also</span></span>  
 <span data-ttu-id="edd21-121">[如何建立 SQL Server 變更資料庫執行個體](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="edd21-121">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="edd21-122">選取 Oracle 資料表和資料行</span><span class="sxs-lookup"><span data-stu-id="edd21-122">Select Oracle Tables and Columns</span></span>](select-oracle-tables-and-columns.md)  
  
  
