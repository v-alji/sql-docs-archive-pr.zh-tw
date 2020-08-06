---
title: 使用維度 Wizard 建立維度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], creating
ms.assetid: d84f66ae-7551-49bf-99d0-88368ca2dd0e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9ec38dc7170b915dce0cedea60c93385560e11f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705613"
---
# <a name="create-a-dimension-using-the-dimension-wizard"></a><span data-ttu-id="132b8-102">使用維度精靈建立維度</span><span class="sxs-lookup"><span data-stu-id="132b8-102">Create a Dimension Using the Dimension Wizard</span></span>
  <span data-ttu-id="132b8-103">您可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的 [維度精靈] 來建立新的維度。</span><span class="sxs-lookup"><span data-stu-id="132b8-103">You can create a new dimension by using the Dimension Wizard in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="to-create-a-new-dimension"></a><span data-ttu-id="132b8-104">建立新維度</span><span class="sxs-lookup"><span data-stu-id="132b8-104">To create a new dimension</span></span>  
  
1.  <span data-ttu-id="132b8-105">在**方案總管**中，以滑鼠右鍵按一下 [**維度**]，然後按一下 [**新增維度**]。</span><span class="sxs-lookup"><span data-stu-id="132b8-105">In **Solution Explorer**, right-click **Dimensions**, and then click **New Dimension**.</span></span>  
  
2.  <span data-ttu-id="132b8-106">在「維度精靈」的 [選取建立方法]\*\*\*\* 頁面上，選取 [使用現有的資料表]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="132b8-106">On the **Select Creation Method** page of the Dimension Wizard, select **Use an existing table**, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="132b8-107">您可能偶爾必須在不使用現有資料表的情況下建立維度。</span><span class="sxs-lookup"><span data-stu-id="132b8-107">You might occasionally have to create a dimension without using an existing table.</span></span> <span data-ttu-id="132b8-108">如需詳細資訊，請參閱 [在資料來源中產生非時間資料表來建立維度](create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md) 和 [Create a Time Dimension by Generating a Time Table](create-a-time-dimension-by-generating-a-time-table.md)(透過產生時間資料表來建立時間維度)。</span><span class="sxs-lookup"><span data-stu-id="132b8-108">For more information, see [Create a Dimension by Generating a Non-Time Table in the Data Source](create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md) and [Create a Time Dimension by Generating a Time Table](create-a-time-dimension-by-generating-a-time-table.md).</span></span>  
  
3.  <span data-ttu-id="132b8-109">在 [指定來源資訊]\*\*\*\* 頁面上，執行下列程序：</span><span class="sxs-lookup"><span data-stu-id="132b8-109">On the **Specify Source Information** page, do the following procedures:</span></span>  
  
    1.  <span data-ttu-id="132b8-110">在 [資料來源檢視]\*\*\*\* 清單中，選取資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="132b8-110">In the **Data source view** list, select a data source view.</span></span>  
  
    2.  <span data-ttu-id="132b8-111">在 [主資料表]\*\*\*\* 中，選取主維度資料表。</span><span class="sxs-lookup"><span data-stu-id="132b8-111">In the **Main table** list, select the main dimension table.</span></span>  
  
    3.  <span data-ttu-id="132b8-112">在 [索引鍵資料行]\*\*\*\* 清單中，檢閱精靈根據您在主維度資料表中定義之主索引鍵，自動選取的索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="132b8-112">In the **Key columns** list, review the key columns that the wizard has automatically selected based on the primary key that is defined in the main dimension table.</span></span> <span data-ttu-id="132b8-113">若要變更此預設值，指定連結維度資料表和事實資料表的索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="132b8-113">To change this default setting, specify the key columns that link the dimension table to the fact table.</span></span>  
  
    4.  <span data-ttu-id="132b8-114">在 [名稱資料行]\*\*\*\* 下拉式清單中，檢閱精靈已經自動選取的名稱資料行。</span><span class="sxs-lookup"><span data-stu-id="132b8-114">In the **Name column** drop-down list, review the name column that the wizard has automatically selected.</span></span>  
  
         <span data-ttu-id="132b8-115">當資料行包含描述性資訊時，適合使用這個預設名稱。</span><span class="sxs-lookup"><span data-stu-id="132b8-115">This default name is appropriate when the column contains descriptive information.</span></span> <span data-ttu-id="132b8-116">不過，您可能想要指定包含對於使用者更有意義之值的名稱。</span><span class="sxs-lookup"><span data-stu-id="132b8-116">However, you might want to specify a name that contains values that are more meaningful for the end user.</span></span> <span data-ttu-id="132b8-117">例如，如果 Products 維度中的產品類別目錄屬性使用 **ProductCategoryKey** 資料行作為其索引鍵資料行，您可以指定 **ProductCategoryName** 資料行作為其名稱資料行。</span><span class="sxs-lookup"><span data-stu-id="132b8-117">For example, if a product category attribute in a Products dimension uses the **ProductCategoryKey** column as its key column, you can specify the **ProductCategoryName** column as its name column.</span></span>  
  
         <span data-ttu-id="132b8-118">如果 [索引鍵資料行]\*\*\*\* 清單包含多個索引鍵資料行，您必須可針對索引鍵屬性提供成員值的名稱資料行。</span><span class="sxs-lookup"><span data-stu-id="132b8-118">If the **Key columns** list contains multiple key columns, you must specify a name column that provides the member values for the key attribute.</span></span> <span data-ttu-id="132b8-119">若要這樣做，您可以在資料來源檢視中，建立具名計算，並將其當做名稱資料行使用。</span><span class="sxs-lookup"><span data-stu-id="132b8-119">To do this, you can create a named calculation in the data source view and use that as the name column.</span></span>  
  
    5.  <span data-ttu-id="132b8-120">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="132b8-120">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="132b8-121">在 [選取相關資料表]\*\*\*\* 頁面上，選取您要包含在維度中的相關資料表，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="132b8-121">On the **Select Related Tables** page, select the related tables that you want to include in your dimension, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="132b8-122">如果您指定的主維度資料表與其他維度資料表有關聯性，會出現 [選取相關資料表]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="132b8-122">The **Select Related Tables** page appears if the main dimension table that you specified has relationships to other dimension tables.</span></span>  
  
5.  <span data-ttu-id="132b8-123">在 [選取維度屬性]\*\*\*\* 頁面上，選取您要包含在維度中的屬性，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="132b8-123">On the **Select Dimension Attributes** page, select the attributes that you want to include in the dimension, and then click **Next**.</span></span>  
  
     <span data-ttu-id="132b8-124">您可以選擇性地變更屬性名稱、啟用或停用瀏覽，以及指定屬性類型。</span><span class="sxs-lookup"><span data-stu-id="132b8-124">Optionally, you can change the attribute names, enable or disable browsing, and specify the attribute type.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="132b8-125">若要啟用屬性的 [啟用瀏覽]\*\*\*\* 和 [屬性類型]\*\*\*\* 欄位，必須選取該屬性才能包含到維度中。</span><span class="sxs-lookup"><span data-stu-id="132b8-125">To make the **Enable Browsing** and **Attribute Type** fields of an attribute active, the attribute must be selected for inclusion in the dimension.</span></span>  
  
6.  <span data-ttu-id="132b8-126">在 [定義帳戶智慧]\*\*\*\* 頁面的 [內建帳戶類型]\*\*\*\* 資料行上，選取帳戶類型，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="132b8-126">On the **Define Account Intelligence** page, in the **Built-In Account Types** column, select the account type, and then click **Next**.</span></span>  
  
     <span data-ttu-id="132b8-127">帳戶類型必須對應到 [來源資料表帳戶類型]\*\*\*\* 資料行中所列之來源資料表的帳戶類型。</span><span class="sxs-lookup"><span data-stu-id="132b8-127">The account type must correspond to the account type of the source table that is listed in the **Source Table Account Types** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="132b8-128">如果您在精靈的 [選取維度屬性]\*\*\*\* 頁面上定義 [帳戶類型]\*\*\*\* 維度屬性，會出現 [定義帳戶智慧]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="132b8-128">The **Define Account Intelligence** page appears if you defined an **Account Type** dimension attribute on the **Select Dimension Attributes** page of the wizard.</span></span>  
  
7.  <span data-ttu-id="132b8-129">在 [正在完成精靈]\*\*\*\* 頁面上，輸入新維度的名稱，然後檢閱維度的結構。</span><span class="sxs-lookup"><span data-stu-id="132b8-129">On the **Completing the Wizard** page, enter a name for the new dimension and review the dimension structure.</span></span> <span data-ttu-id="132b8-130">如果您要進行任何變更，按一下 [上一步]\*\*\*\*，否則，按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="132b8-130">If you want to make changes, click **Back**; otherwise, click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="132b8-131">您可以在完成「維度精靈」之後，使用 [維度設計師] 在維度中加入、移除和設定屬性與階層。</span><span class="sxs-lookup"><span data-stu-id="132b8-131">You can use Dimension Designer after you complete the Dimension Wizard to add, remove, and configure attributes and hierarchies in the dimension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="132b8-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="132b8-132">See Also</span></span>  
 [<span data-ttu-id="132b8-133">使用現有的資料表建立維度</span><span class="sxs-lookup"><span data-stu-id="132b8-133">Create a Dimension by Using an Existing Table</span></span>](create-a-dimension-by-using-an-existing-table.md)  
  
  
