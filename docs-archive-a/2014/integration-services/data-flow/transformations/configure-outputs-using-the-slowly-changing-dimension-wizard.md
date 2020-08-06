---
title: 使用緩時變維度精靈來設定輸出 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Slowly Changing Dimension transformation
- slowly changing dimensions
- Slowly Changing Dimension Wizard
ms.assetid: da111731-1ffa-49b9-bcaa-3c93fd0eb619
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f6ec3dfb34de8eb7e20b255ce485ee506f070749
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597245"
---
# <a name="configure-outputs-using-the-slowly-changing-dimension-wizard"></a><span data-ttu-id="379b7-102">使用緩時變維度精靈來設定輸出</span><span class="sxs-lookup"><span data-stu-id="379b7-102">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>
  <span data-ttu-id="379b7-103">「緩時變維度精靈」做為「緩時變維度」轉換的編輯器使用。</span><span class="sxs-lookup"><span data-stu-id="379b7-103">The Slowly Changing Dimension Wizard functions as the editor for the Slowly Changing Dimension transformation.</span></span> <span data-ttu-id="379b7-104">為緩時變維度資料建立並設定資料流程會是一個複雜的工作。</span><span class="sxs-lookup"><span data-stu-id="379b7-104">Building and configuring the data flow for slowly changing dimension data can be a complex task.</span></span> <span data-ttu-id="379b7-105">「緩時變維度精靈」可引導您執行對應資料行、選取商務索引鍵資料行、設定資料行變更屬性，以及設定對推斷之維度成員的支援等步驟，為「緩時變維度」轉換輸出提供建立資料流程的最簡單方法。</span><span class="sxs-lookup"><span data-stu-id="379b7-105">The Slowly Changing Dimension Wizard offers the simplest method of building the data flow for the Slowly Changing Dimension transformation outputs by guiding you through the steps of mapping columns, selecting business key columns, setting column change attributes, and configuring support for inferred dimension members.</span></span>

 <span data-ttu-id="379b7-106">您必須在維度資料表中選取至少一個商務索引鍵資料行，並將其對應到輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="379b7-106">You must choose at least one business key column in the dimension table and map it to an input column.</span></span> <span data-ttu-id="379b7-107">商務索引鍵值會將來源中的記錄連結到維度資料表中的記錄。</span><span class="sxs-lookup"><span data-stu-id="379b7-107">The value of the business key links a record in the source to a record in the dimension table.</span></span> <span data-ttu-id="379b7-108">轉換會使用這個對應尋找維度資料表中的記錄，並判斷記錄是新的還是變更的。</span><span class="sxs-lookup"><span data-stu-id="379b7-108">The transformation uses this mapping to locate the record in the dimension table and to determine whether a record is new or changing.</span></span> <span data-ttu-id="379b7-109">通常，商務索引鍵是來源中的主索引鍵，但只要它會唯一識別記錄且其值不變更，就可以是替代索引鍵。</span><span class="sxs-lookup"><span data-stu-id="379b7-109">The business key is typically the primary key in the source, but it can be an alternate key as long as it uniquely identifies a record and its value does not change.</span></span> <span data-ttu-id="379b7-110">商務索引鍵也可以是包含多個資料行的複合索引鍵。</span><span class="sxs-lookup"><span data-stu-id="379b7-110">The business key can also be a composite key, consisting of multiple columns.</span></span> <span data-ttu-id="379b7-111">維度資料表中的主索引鍵通常是代理索引鍵，表示由識別欄位或自訂方案 (例如指令碼) 自動產生的數值。</span><span class="sxs-lookup"><span data-stu-id="379b7-111">The primary key in the dimension table is usually a surrogate key, which means a numeric value generated automatically by an identity column or by a custom solution such as a script.</span></span>

 <span data-ttu-id="379b7-112">在可執行「緩時變維度精靈」之前，必須先將來源和「緩時變維度」轉換加入到資料流程，然後將來源的輸出連接到「緩時變維度」轉換的輸入。</span><span class="sxs-lookup"><span data-stu-id="379b7-112">Before you can run the Slowly Changing Dimension Wizard, you must add a source and a Slowly Changing Dimension transformation to the data flow, and then connect the output from the source to the input of the Slowly Changing Dimension transformation.</span></span> <span data-ttu-id="379b7-113">(選擇性) 資料流程可以包含資料來源和「緩時變維度」轉換之間的其他轉換。</span><span class="sxs-lookup"><span data-stu-id="379b7-113">Optionally, the data flow can include other transformations between the data source and the Slowly Changing Dimension transformation.</span></span>

 <span data-ttu-id="379b7-114">若要開啟 [ [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師] 中的 [緩時變維度精靈]，請按兩下「緩時變維度」轉換。</span><span class="sxs-lookup"><span data-stu-id="379b7-114">To open the Slowly Changing Dimension Wizard in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, double-click the Slowly Changing Dimension transformation.</span></span>

## <a name="creating-slowly-changing-dimension-outputs"></a><span data-ttu-id="379b7-115">建立緩時變維度輸出</span><span class="sxs-lookup"><span data-stu-id="379b7-115">Creating Slowly Changing Dimension Outputs</span></span>

#### <a name="to-create-slowly-changing-dimension-transformation-outputs"></a><span data-ttu-id="379b7-116">若要建立緩時變維度轉換輸出</span><span class="sxs-lookup"><span data-stu-id="379b7-116">To create Slowly Changing Dimension transformation outputs</span></span>

1.  <span data-ttu-id="379b7-117">選擇連接管理員，以存取包含您要更新之維度資料表的資料來源。</span><span class="sxs-lookup"><span data-stu-id="379b7-117">Choose the connection manager to access the data source that contains the dimension table that you want to update.</span></span>

     <span data-ttu-id="379b7-118">您可以從封裝包含的連接管理員清單中選取。</span><span class="sxs-lookup"><span data-stu-id="379b7-118">You can select from a list of connection managers that the package includes.</span></span>

2.  <span data-ttu-id="379b7-119">選取您要更新的維度資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="379b7-119">Choose the dimension table or view you want to update.</span></span>

     <span data-ttu-id="379b7-120">選取連接管理員後，可以從資料來源選取資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="379b7-120">After you select the connection manager, you can select the table or view from the data source.</span></span>

3.  <span data-ttu-id="379b7-121">在資料行上設定索引鍵屬性，並將輸入資料行對應到維度資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="379b7-121">Set key attributes on columns and map input columns to columns in the dimension table.</span></span>

     <span data-ttu-id="379b7-122">您必須在維度資料表中選取至少一個商務索引鍵資料行，並將其對應到輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="379b7-122">You must choose at least one business key column in the dimension table and map it to an input column.</span></span> <span data-ttu-id="379b7-123">其他輸入資料行可以做為非索引鍵對應，對應到維度資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="379b7-123">Other input columns can be mapped to columns in the dimension table as non-key mappings.</span></span>

4.  <span data-ttu-id="379b7-124">為每個資料行選取變更類型。</span><span class="sxs-lookup"><span data-stu-id="379b7-124">Choose the change type for each column.</span></span>

    -   <span data-ttu-id="379b7-125">[變更屬性]  會覆寫記錄中的現有值。</span><span class="sxs-lookup"><span data-stu-id="379b7-125">**Changing attribute** overwrites existing values in records.</span></span>

    -   <span data-ttu-id="379b7-126">[歷程記錄屬性]  會新建記錄而不是更新現有的記錄。</span><span class="sxs-lookup"><span data-stu-id="379b7-126">**Historical attribute** creates new records instead of updating existing records.</span></span>

    -   <span data-ttu-id="379b7-127">[固定屬性]  指示資料行的值不得變更。</span><span class="sxs-lookup"><span data-stu-id="379b7-127">**Fixed attribute** indicates that the column value must not change.</span></span>

5.  <span data-ttu-id="379b7-128">設定固定和變更屬性選項。</span><span class="sxs-lookup"><span data-stu-id="379b7-128">Set fixed and changing attribute options.</span></span>

     <span data-ttu-id="379b7-129">如果設定資料行使用 [固定屬性]  變更類型，您可以指定在這些資料行中偵測到變更時，「緩時變維度」轉換是否失敗。</span><span class="sxs-lookup"><span data-stu-id="379b7-129">If you configure columns to use the **Fixed attribute** change type, you can specify whether the Slowly Changing Dimension transformation fails when changes are detected in these columns.</span></span> <span data-ttu-id="379b7-130">如果設定資料行使用 [變更屬性]  變更類型，則可以指定是否更新所有符合的記錄，包括過期記錄。</span><span class="sxs-lookup"><span data-stu-id="379b7-130">If you configure columns to use the **Changing attribute** change type, you can specify whether all matching records, including outdated records, are updated.</span></span>

6.  <span data-ttu-id="379b7-131">設定記錄屬性選項。</span><span class="sxs-lookup"><span data-stu-id="379b7-131">Set historical attribute options.</span></span>

     <span data-ttu-id="379b7-132">如果設定資料行使用 [歷程記錄屬性]  變更類型，您必須選擇如何區分目前記錄和過期記錄。</span><span class="sxs-lookup"><span data-stu-id="379b7-132">If you configure columns to use the **Historical attribute** change type, you must choose how to distinguish between current and expired records.</span></span> <span data-ttu-id="379b7-133">您可以使用目前資料列指標資料行或兩個日期資料行，以識別目前資料列和過期資料列。</span><span class="sxs-lookup"><span data-stu-id="379b7-133">You can use a current row indicator column or two date columns to identify current and expired rows.</span></span> <span data-ttu-id="379b7-134">如果使用目前資料列指標資料行，可以將其設定為 **Current**、 **True** ，和 **Expired,** 或 **False** 。</span><span class="sxs-lookup"><span data-stu-id="379b7-134">If you use the current row indicator column, you can set it to **Current**, **True** when current and **Expired,** or **False** when expired.</span></span> <span data-ttu-id="379b7-135">您也可以輸入自訂值。</span><span class="sxs-lookup"><span data-stu-id="379b7-135">You can also enter custom values.</span></span> <span data-ttu-id="379b7-136">如果您使用兩個日期資料行，即開始日期和結束日期，則當透過輸入日期或選取系統變數然後使用其值的方式設定日期資料行值時，您可以指定要使用的日期。</span><span class="sxs-lookup"><span data-stu-id="379b7-136">If you use two date columns, a start date and an end date, you can specify the date to use when setting the date column values by typing a date or by selecting a system variable and then using its value.</span></span>

7.  <span data-ttu-id="379b7-137">指定對推斷成員的支援，並選擇推斷成員記錄包含的資料行。</span><span class="sxs-lookup"><span data-stu-id="379b7-137">Specify support for inferred members and choose the columns that the inferred member record contains.</span></span>

     <span data-ttu-id="379b7-138">將量值載入到事實資料表時，您可以為尚不存在的推斷成員建立最低記錄。</span><span class="sxs-lookup"><span data-stu-id="379b7-138">When loading measures into a fact table, you can create minimal records for inferred members that do not yet exist.</span></span> <span data-ttu-id="379b7-139">稍後，當有意義的資料可用時，可以更新維度記錄。</span><span class="sxs-lookup"><span data-stu-id="379b7-139">Later, when meaningful data is available, the dimension records can be updated.</span></span> <span data-ttu-id="379b7-140">可以建立下列類型的最低記錄：</span><span class="sxs-lookup"><span data-stu-id="379b7-140">The following types of minimal records can be created:</span></span>

    -   <span data-ttu-id="379b7-141">其所包含的所有變更類型之資料行均為 Null 的記錄。</span><span class="sxs-lookup"><span data-stu-id="379b7-141">A record in which all columns with change types are null.</span></span>

    -   <span data-ttu-id="379b7-142">其所包含的布林資料行指示該記錄為推斷成員的記錄。</span><span class="sxs-lookup"><span data-stu-id="379b7-142">A record in which a Boolean column indicates the record is an inferred member.</span></span>

8.  <span data-ttu-id="379b7-143">檢閱「緩時變維度精靈」建立的組態。</span><span class="sxs-lookup"><span data-stu-id="379b7-143">Review the configurations that the Slowly Changing Dimension Wizard builds.</span></span> <span data-ttu-id="379b7-144">視所支援的變更類型而定，可以將不同的資料流程元件組加入到封裝中。</span><span class="sxs-lookup"><span data-stu-id="379b7-144">Depending on which change types are supported, different sets of data flow components are added to the package.</span></span>

     <span data-ttu-id="379b7-145">下圖顯示一個資料流程範例，它支援固定屬性、變更屬性和記錄屬性變更、推斷的成員以及對符合記錄的變更。</span><span class="sxs-lookup"><span data-stu-id="379b7-145">The following diagram shows an example of a data flow that supports fixed attribute, changing attribute, and historical attribute changes, inferred members, and changes to matching records.</span></span>

     <span data-ttu-id="379b7-146">![來自緩時變維度精靈的資料流程](../../media/dimensionwizard.gif "來自緩時變維度精靈的資料流程")</span><span class="sxs-lookup"><span data-stu-id="379b7-146">![Data flow from Slowly Changing Dimension Wizard](../../media/dimensionwizard.gif "Data flow from Slowly Changing Dimension Wizard")</span></span>

## <a name="updating-slowly-changing-dimension-outputs"></a><span data-ttu-id="379b7-147">更新緩時變維度輸出</span><span class="sxs-lookup"><span data-stu-id="379b7-147">Updating Slowly Changing Dimension Outputs</span></span>
 <span data-ttu-id="379b7-148">更新「緩時變維度」轉換輸出之組態的最簡單方法，就是重新執行「緩時變維度精靈」並修改精靈頁面中的屬性。</span><span class="sxs-lookup"><span data-stu-id="379b7-148">The simplest way to update the configuration of the Slowly Changing Dimension transformation outputs is to rerun the Slowly Changing Dimension Wizard and modify properties from the wizard pages.</span></span> <span data-ttu-id="379b7-149">您還可以使用 [進階編輯器]  對話方塊或以程式設計方式更新「緩時變維度」轉換。</span><span class="sxs-lookup"><span data-stu-id="379b7-149">You can also update the Slowly Changing Dimension transformation using the **Advanced Editor** dialog box or programmatically.</span></span>

## <a name="see-also"></a><span data-ttu-id="379b7-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="379b7-150">See Also</span></span>
 [<span data-ttu-id="379b7-151">緩時變維度轉換</span><span class="sxs-lookup"><span data-stu-id="379b7-151">Slowly Changing Dimension Transformation</span></span>](slowly-changing-dimension-transformation.md)


