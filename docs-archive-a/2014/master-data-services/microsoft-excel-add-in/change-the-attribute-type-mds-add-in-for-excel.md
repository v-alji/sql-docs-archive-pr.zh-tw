---
title: 變更屬性類型 (適用於 Excel 的 MDS 增益集) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9d3001d9-8d0f-4e4a-8e04-4f666bf0df69
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a55ca53fcf6923957e2196840aea2fb5914e1746
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698389"
---
# <a name="change-the-attribute-type-mds-add-in-for-excel"></a><span data-ttu-id="e3d19-102">變更屬性類型 (適用於 Excel 的 MDS 增益集)</span><span class="sxs-lookup"><span data-stu-id="e3d19-102">Change the Attribute Type (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="e3d19-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，當資料類型或是允許的字元數目不正確時，管理員可以變更屬性類型。</span><span class="sxs-lookup"><span data-stu-id="e3d19-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], administrators can change the attribute type when the data type or number of allowed characters is incorrect.</span></span>  
  
 <span data-ttu-id="e3d19-104">如果您想要變更屬性類型來建立受條件約束的清單 (網域屬性)，請參閱[建立網域屬性 &#40;適用於 Excel 的 MDS 增益集&#41;](create-a-domain-based-attribute-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="e3d19-104">If you want to change the attribute type to create a constrained list (domain-based attribute), see [Create a Domain-based Attribute &#40;MDS Add-in for Excel&#41;](create-a-domain-based-attribute-mds-add-in-for-excel.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e3d19-105">您不能更新 **Name** 或 **Code** 資料行的類型或長度。</span><span class="sxs-lookup"><span data-stu-id="e3d19-105">You cannot update the type or length of the **Name** or **Code** columns.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e3d19-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="e3d19-106">Prerequisites</span></span>  
 <span data-ttu-id="e3d19-107">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="e3d19-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="e3d19-108">您必須擁有存取 [系統管理]\*\*\*\* 和總管\*\*\*\* 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="e3d19-108">You must have permission to access the **System Administration** and **Explorer** functional areas.</span></span>  
  
-   <span data-ttu-id="e3d19-109">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="e3d19-109">You must be a model administrator.</span></span> <span data-ttu-id="e3d19-110">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](../administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e3d19-110">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="e3d19-111">必須有現有的模型、實體和屬性存在。</span><span class="sxs-lookup"><span data-stu-id="e3d19-111">There must be an existing model, entity, and attribute.</span></span>  
  
### <a name="to-change-the-attribute-type"></a><span data-ttu-id="e3d19-112">若要變更屬性類型</span><span class="sxs-lookup"><span data-stu-id="e3d19-112">To change the attribute type</span></span>  
  
1.  <span data-ttu-id="e3d19-113">在 Excel 中，載入包含您想要變更之資料行 (屬性) 的實體。</span><span class="sxs-lookup"><span data-stu-id="e3d19-113">In Excel, load the entity that contains the column (attribute) you want to change.</span></span> <span data-ttu-id="e3d19-114">如需詳細資訊，請參閱將[資料從 MDS 載入 Excel](export-data-to-excel-from-master-data-services.md)中。</span><span class="sxs-lookup"><span data-stu-id="e3d19-114">For more information, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
2.  <span data-ttu-id="e3d19-115">在您想要變更的資料行中按一下任何資料格。</span><span class="sxs-lookup"><span data-stu-id="e3d19-115">Click any cell in the column you want to change.</span></span>  
  
3.  <span data-ttu-id="e3d19-116">在 [建立模型]\*\*\*\* 群組中，按一下 [屬性內容]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e3d19-116">In the **Build Model** group, click **Attribute Properties**.</span></span>  
  
4.  <span data-ttu-id="e3d19-117">在 [屬性內容]\*\*\*\* 對話方塊中，視需要更新設定。</span><span class="sxs-lookup"><span data-stu-id="e3d19-117">In the **Attribute Properties** dialog box, update settings as needed.</span></span>  
  
5.  <span data-ttu-id="e3d19-118">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e3d19-118">Click **OK**.</span></span>  
  
## <a name="what-happens-when-you-change-the-attribute-type"></a><span data-ttu-id="e3d19-119">當您變更屬性類型時會發生什麼情況？</span><span class="sxs-lookup"><span data-stu-id="e3d19-119">What happens when you change the attribute type?</span></span>  
 <span data-ttu-id="e3d19-120">如果有屬性的相依性，例如屬性由任何 MDS 商務規則參考或屬性包含在訂閱檢視中，而且您變更屬性的資料類型，則 MDS 會：</span><span class="sxs-lookup"><span data-stu-id="e3d19-120">If there is any dependency on the attribute, such as the attribute is referenced by any MDS business rule or the attribute is included in a subscription view, and you change the data type of an attribute, MDS will:</span></span>  
  
-   <span data-ttu-id="e3d19-121">變更屬性的資料類型。</span><span class="sxs-lookup"><span data-stu-id="e3d19-121">Change the data type of the attribute.</span></span>  
  
-   <span data-ttu-id="e3d19-122">產生具有後置詞 "_old" 且不含任何值的屬性複本。</span><span class="sxs-lookup"><span data-stu-id="e3d19-122">Generate a copy of the attribute with the suffix "_old" that does not contain any value.</span></span> <span data-ttu-id="e3d19-123">這稱為已被**取代**的屬性。</span><span class="sxs-lookup"><span data-stu-id="e3d19-123">This is called a **deprecated** attribute.</span></span>  
  
 <span data-ttu-id="e3d19-124">不過，原始屬性的所有現有相依性會指向已被取代的屬性，而不會指向變更的屬性。</span><span class="sxs-lookup"><span data-stu-id="e3d19-124">However, all the existing dependencies on the original attribute will point to the deprecated attribute, and not to the changed one.</span></span>  
  
 <span data-ttu-id="e3d19-125">這表示：</span><span class="sxs-lookup"><span data-stu-id="e3d19-125">This implies that:</span></span>  
  
-   <span data-ttu-id="e3d19-126">因為在屬性的新資料類型中邏輯可能不同，您必須重新整理商務規則，指向已變更的屬性。</span><span class="sxs-lookup"><span data-stu-id="e3d19-126">You must refresh the business rules to point to the changed attribute because the logic may not be the same given the new data type of the attribute.</span></span> <span data-ttu-id="e3d19-127">您將需要編輯每個受影響的規則，然後重新組織運算式，以便移除已被取代之屬性 (_old) 的參考，指向更新屬性。</span><span class="sxs-lookup"><span data-stu-id="e3d19-127">You will have to edit each affected rule, and then rework the expressions to point to remove references from the deprecated attribute (_old) to point to the updated attribute.</span></span>  
  
-   <span data-ttu-id="e3d19-128">您必須開啟 [整合管理] 選取範圍下的任何訂用帳戶，選取 [view] 資料列，然後按一下鉛筆圖示以開啟它進行編輯，然後按一下 [**儲存檔**] 圖示來重新整理視圖定義。</span><span class="sxs-lookup"><span data-stu-id="e3d19-128">You must open any subscription views under the Integration Management selection, select the view row, open it for editing by clicking the pencil icon, and then click the **Save disk** icon to refresh the view definition.</span></span> <span data-ttu-id="e3d19-129">重新產生檢視語法不需要其他變更。</span><span class="sxs-lookup"><span data-stu-id="e3d19-129">No other change is needed to regenerate the view syntax.</span></span>  
  
-   <span data-ttu-id="e3d19-130">包含屬性的暫存資料表會加入一個已被取代的屬性資料行，這表示您的暫存碼會受到影響。</span><span class="sxs-lookup"><span data-stu-id="e3d19-130">Staging tables that include the attribute will have a deprecated attribute column added to them, which means that your staging code will be affected.</span></span> <span data-ttu-id="e3d19-131">若要移除已被取代的屬性，您可以在更新了商務規則和訂閱檢視之後刪除它。</span><span class="sxs-lookup"><span data-stu-id="e3d19-131">To get rid of the deprecated attribute, you can delete it after you have updated the business rules and subscription views.</span></span>  
  
 <span data-ttu-id="e3d19-132">**刪除已被取代的屬性**</span><span class="sxs-lookup"><span data-stu-id="e3d19-132">**Deleting the deprecated attribute**</span></span>  
  
 <span data-ttu-id="e3d19-133">刪除任何已被取代的屬性之前，您必須移除屬性的任何參考 (例如修正商務規則和重新產生訂閱檢視)，如前文所述。</span><span class="sxs-lookup"><span data-stu-id="e3d19-133">Before you delete any deprecated attribute, you must remove any references to the attribute such as fixing the business rules and regenerating subscription views as described earlier.</span></span> <span data-ttu-id="e3d19-134">否則，當您嘗試刪除已被取代的屬性時，系統管理網頁上會發生錯誤，表示屬性由物件參考，因此不能刪除。</span><span class="sxs-lookup"><span data-stu-id="e3d19-134">Otherwise, you will get an error in the System Administration web page when you attempt to delete the deprecated attribute stating that the attribute cannot be deleted because it is referenced by an object.</span></span>  
  
 <span data-ttu-id="e3d19-135">若要刪除屬性，請參閱[刪除屬性 &#40;Master Data Services&#41;](../delete-an-attribute-master-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="e3d19-135">To delete an attribute, see [Delete an Attribute &#40;Master Data Services&#41;](../delete-an-attribute-master-data-services.md)</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="e3d19-136">變更有現有資料和相關實體之 MDS 屬性的資料類型，方法相當繁雜，特別是如果有相依於實體、已宣告的商務規則或訂閱檢視時。</span><span class="sxs-lookup"><span data-stu-id="e3d19-136">It is cumbersome to change data types for MDS attributes that have existing data and related entities, especially if there is a business rule or subscription view declared which depends on the entity.</span></span> <span data-ttu-id="e3d19-137">最佳作法是一開始就讓資料類型具備足夠的彈性來保存必要值。</span><span class="sxs-lookup"><span data-stu-id="e3d19-137">The best practice is to start with a data type that is flexible enough to hold the necessary values.</span></span> <span data-ttu-id="e3d19-138">例如，字串一開始可能很小，不過在一段時間後可能變長，因此請考慮最嚴重的案例狀況。</span><span class="sxs-lookup"><span data-stu-id="e3d19-138">For example, strings may start small, but may need to be lengthened over time, so consider the worst case scenarios.</span></span> <span data-ttu-id="e3d19-139">額外的文字字串長度可能相當惱人 (例如，太寬的 GUI 文字方塊難以完整顯示在螢幕上)，因此請避免太長的字串長度。</span><span class="sxs-lookup"><span data-stu-id="e3d19-139">Extra text string length can be burdensome (for example, wide GUI text boxes are hard to fit on the screen), so avoid too long string length.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3d19-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3d19-140">See Also</span></span>  
 <span data-ttu-id="e3d19-141">[Master Data Services &#40;的屬性&#41;](../attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="e3d19-141">[Attributes &#40;Master Data Services&#41;](../attributes-master-data-services.md) </span></span>  
 [<span data-ttu-id="e3d19-142">建立模型 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="e3d19-142">Building a Model &#40;MDS Add-in for Excel&#41;</span></span>](building-a-model-mds-add-in-for-excel.md)  
  
  
