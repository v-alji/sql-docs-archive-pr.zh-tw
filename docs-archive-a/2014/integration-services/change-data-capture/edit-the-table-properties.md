---
title: 編輯資料表屬性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- editTabProps
ms.assetid: 95ea72ba-8e40-4177-a963-0fb4d10c56e3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1ba0809b99474704ec0e93e417a04d776bb26d9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593520"
---
# <a name="edit-the-table-properties"></a><span data-ttu-id="e95c3-102">編輯資料表屬性</span><span class="sxs-lookup"><span data-stu-id="e95c3-102">Edit the Table Properties</span></span>
  <span data-ttu-id="e95c3-103">使用此對話方塊，從正在擷取變更的選定資料表中編輯特定資料行。</span><span class="sxs-lookup"><span data-stu-id="e95c3-103">Use this dialog box to edit the specific columns from the selected table where changes are being captured.</span></span> <span data-ttu-id="e95c3-104">您也可以編輯 **[安全性角色]** 和 **[擷取執行個體]** 資訊。</span><span class="sxs-lookup"><span data-stu-id="e95c3-104">You can also edit the **Security Role** and **Capture Instance** information.</span></span>  
  
### <a name="to-edit-the-columns-to-include-in-the-cdc-instance"></a><span data-ttu-id="e95c3-105">若要編輯 CDC 執行個體中所包含的資料行</span><span class="sxs-lookup"><span data-stu-id="e95c3-105">To edit the columns to include in the CDC instance</span></span>  
  
1.  <span data-ttu-id="e95c3-106">執行下列其中一項或兩項作業：</span><span class="sxs-lookup"><span data-stu-id="e95c3-106">Do one or both of the following:</span></span>  
  
    -   <span data-ttu-id="e95c3-107">選取您要包含的其他任何資料行旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e95c3-107">Select the check box next to any additional column you want to include.</span></span>  
  
    -   <span data-ttu-id="e95c3-108">清除您不想再包含的任何資料行旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e95c3-108">Clear the check box next to any column that you no longer want to include.</span></span>  
  
### <a name="to-edit-the-security-role"></a><span data-ttu-id="e95c3-109">若要編輯安全性角色</span><span class="sxs-lookup"><span data-stu-id="e95c3-109">To edit the Security Role</span></span>  
  
1.  <span data-ttu-id="e95c3-110">在 **[安全性角色]** 欄位中，輸入新的名稱或是編輯安全性角色的名稱。</span><span class="sxs-lookup"><span data-stu-id="e95c3-110">Type a new name or edit the name of the security role in the **Security Role** field.</span></span>  
  
### <a name="to-create-a-new-capture-instance"></a><span data-ttu-id="e95c3-111">若要建立新的擷取執行個體</span><span class="sxs-lookup"><span data-stu-id="e95c3-111">To create a new capture instance</span></span>  
  
1.  <span data-ttu-id="e95c3-112">在 **[安全性角色]** 區段的 **[名稱]** 欄位中，輸入擷取執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="e95c3-112">In the **Security Role** section, **Name** field enter a name for the capture instance.</span></span> <span data-ttu-id="e95c3-113">根據預設，在此欄位中輸入的名稱會是名稱結尾加上 **_NEW** 的目前擷取執行個體名稱 (例如 **old_instance_NEW**)。</span><span class="sxs-lookup"><span data-stu-id="e95c3-113">By default, the name entered in the field is the name of the current capture instance with **_NEW** added to the end of the name (for example, **old_instance_NEW**).</span></span>  
  
2.  <span data-ttu-id="e95c3-114">將擷取執行個體儲存為下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="e95c3-114">Save the capture instance as one of the following:</span></span>  
  
    -   <span data-ttu-id="e95c3-115">**新的擷取執行個體**：此情況下會儲存新的擷取執行個體，而且不會刪除舊的擷取執行個體。</span><span class="sxs-lookup"><span data-stu-id="e95c3-115">**New Capture Instance**: In this case a new capture instance is saved and the old capture instance is not deleted.</span></span>  
  
         <span data-ttu-id="e95c3-116">**注意**：每一個資料表不能有兩個以上的擷取執行個體。</span><span class="sxs-lookup"><span data-stu-id="e95c3-116">**Note**: You can have no more than two capture instances per table.</span></span> <span data-ttu-id="e95c3-117">如果已經有兩個擷取執行個體，就無法使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="e95c3-117">If there are already two capture instances, this option is not available.</span></span>  
  
    -   <span data-ttu-id="e95c3-118">**取代現有的**：此情況下會刪除目前的擷取執行個體，並由您建立的擷取執行個體取代。</span><span class="sxs-lookup"><span data-stu-id="e95c3-118">**Replace Existing**: In this case the current capture instance is deleted and replaced by the capture instance you created.</span></span> <span data-ttu-id="e95c3-119">如果已經為此資料表定義兩個擷取執行個體，您必須選取其中一個來替換。</span><span class="sxs-lookup"><span data-stu-id="e95c3-119">If there are two capture instances defined for this table, you must select one to replace.</span></span>  
  
 <span data-ttu-id="e95c3-120">**注意**：您可以從 **[資料表]** 索引標籤的資料表清單中移除擷取執行個體。</span><span class="sxs-lookup"><span data-stu-id="e95c3-120">**Note**: You can remove a capture instance from the list of tables in the **Table** tab.</span></span>  
  
 <span data-ttu-id="e95c3-121">在此對話方塊中輸入資訊完畢後，請按一下 **[確定]** 接受變更。</span><span class="sxs-lookup"><span data-stu-id="e95c3-121">After you finish entering the information in this dialog box, click **OK** to accept the changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e95c3-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e95c3-122">See Also</span></span>  
 <span data-ttu-id="e95c3-123">[如何編輯 CDC 執行個體屬性](how-to-edit-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="e95c3-123">[How to Edit the CDC Instance Properties](how-to-edit-the-cdc-instance-properties.md) </span></span>  
 [<span data-ttu-id="e95c3-124">針對為了擷取變更所選取的資料表進行變更</span><span class="sxs-lookup"><span data-stu-id="e95c3-124">Make Changes to the Tables Selected for Capturing Changes</span></span>](make-changes-to-the-tables-selected-for-capturing-changes.md)  
  
  
