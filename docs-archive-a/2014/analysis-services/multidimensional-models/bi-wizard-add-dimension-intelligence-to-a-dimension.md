---
title: 將維度智慧加入至維度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Business Intelligence enhancements [Analysis Services], dimension intelligence
- dimensions [Analysis Services], Business Intelligence enhancements
- dimension intelligence [Analysis Services]
- Type property
ms.assetid: b64fa386-eac2-4286-a320-0631a1887aac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5cad591d3e89dc306571efa9aeef9d81a235c9fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593664"
---
# <a name="add-dimension-intelligence-to-a-dimension"></a><span data-ttu-id="7d6eb-102">將維度智慧加入至維度中</span><span class="sxs-lookup"><span data-stu-id="7d6eb-102">Add Dimension Intelligence to a Dimension</span></span>
  <span data-ttu-id="7d6eb-103">將維度智慧增強功能加入至 Cube 或維度，以指定維度的標準商務類型。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-103">Add the dimension intelligence enhancement to a cube or a dimension to specify a standard business type for a dimension.</span></span> <span data-ttu-id="7d6eb-104">此增強功能同時也會指定維度屬性的對應類型。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-104">This enhancement also specifies the corresponding types for dimension attributes.</span></span> <span data-ttu-id="7d6eb-105">用戶端應用程式在分析資料時可以使用這些類型規格。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-105">Client applications can use these type specifications when analyzing data.</span></span>  
  
 <span data-ttu-id="7d6eb-106">若要加入維度智慧，您可使用 [商業智慧精靈]，並於 [選擇增強功能]\*\*\*\* 頁面上選取 [定義維度智慧]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-106">To add dimension intelligence, you use the Business Intelligence Wizard, and select the **Define dimension intelligence** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="7d6eb-107">然後，此精靈會引導您逐步完成選取要套用維度智慧的維度，並為選取的維度識別屬性。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-107">This wizard then guides you through the steps of selecting a dimension to which you want to apply dimension intelligence and identifying the attributes for the selected dimension.</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="7d6eb-108">選取維度</span><span class="sxs-lookup"><span data-stu-id="7d6eb-108">Selecting a Dimension</span></span>  
 <span data-ttu-id="7d6eb-109">在精靈的第一個 [設定維度智慧選項]\*\*\*\* 頁面上，指定要套用維度智慧的維度。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-109">On the first **Set Dimension Intelligence Options** page of the wizard, you specify the dimension to which you want to apply dimension intelligence.</span></span> <span data-ttu-id="7d6eb-110">加入到此選取維度的維度智慧增強功能，會產生維度的變更。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-110">The dimension intelligence enhancement added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="7d6eb-111">包含選取之維度的所有 Cube，都會繼承這些變更。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-111">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7d6eb-112">如果選取 [帳戶]\*\*\*\* 作為維度，您將會指定維度的帳戶智慧。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-112">If you select **Account** as the dimension, you will be specifying account intelligence for the dimension.</span></span> <span data-ttu-id="7d6eb-113">如需詳細資訊，請參閱 [將帳戶智慧加入至維度中](bi-wizard-add-account-intelligence-to-a-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-113">For more information, see [Add Account Intelligence to a Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).</span></span>  
  
## <a name="specifying-dimension-attributes"></a><span data-ttu-id="7d6eb-114">指定維度屬性</span><span class="sxs-lookup"><span data-stu-id="7d6eb-114">Specifying Dimension Attributes</span></span>  
 <span data-ttu-id="7d6eb-115">在 [**定義維度智慧**] 頁面的 [**維度類型**] 清單中，您所做的選取專案會設定維度的 `Type` 屬性。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-115">On the **Define Dimension Intelligence** page, in **Dimension Type** list, the selection that you make sets the dimension's `Type` property.</span></span> <span data-ttu-id="7d6eb-116">`Type` 屬性設定會提供關於維度內容的資訊給伺服器和用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-116">The `Type` property setting provides information to servers and client applications about the contents of a dimension.</span></span> <span data-ttu-id="7d6eb-117">部份設定只為用戶端應用程式提供指導；這些設定是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-117">Some settings only provide guidance for client applications; these settings are optional.</span></span> <span data-ttu-id="7d6eb-118">其他設定 (例如帳戶或時間) 決定特定的行為，並可能對實作特殊商業智慧增強功能是必要的。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-118">Other settings, such as Accounts or Time, determine specific behaviors and may be required to implement particular business intelligence enhancements.</span></span> <span data-ttu-id="7d6eb-119">例如，SQL Server Management Studio 使用維度類型來識別貨幣維度，以及設定適當的貨幣轉換規則。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-119">For example, the SQL Server Management Studio uses the dimension type to identify a Currency dimension and set the appropriate currency conversion rules.</span></span> <span data-ttu-id="7d6eb-120">[維度類型]\*\*\*\* 的預設值為 [一般]\*\*\*\*，不會對維度內容做任何假設。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-120">The default setting for the **Dimension Type** is **Regular**, which makes no assumptions about the contents of the dimension.</span></span>  
  
 <span data-ttu-id="7d6eb-121">選取維度類型之後，在 [維度屬性]\*\*\*\* 的 [包含]\*\*\*\* 資料行中，針對在維度中有對應屬性的每個標準屬性類型，選取其旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-121">After selecting the dimension type, in **Dimension attributes**, in the **Include** column, select the check box next to each standard attribute type for which there is a corresponding attribute in the dimension.</span></span> <span data-ttu-id="7d6eb-122">最後，在 [維度屬性]\*\*\*\* 資料行中展開下拉式清單，並在對應到所選取屬性類型的維度中選取屬性。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-122">Finally, in the **Dimension Attribute** column, expand the drop-down list, and select the attribute in the dimension that corresponds to the selected attribute type.</span></span> <span data-ttu-id="7d6eb-123">從清單中選取屬性，會針對屬性設定屬性 `Type` 屬性。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-123">Selecting the attribute from the list sets the attribute `Type` property for the attributes.</span></span>  
  
 <span data-ttu-id="7d6eb-124">例如，您要將維度智慧加入至帳戶維度。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-124">For example, you want to add dimension intelligence to an Accounts dimension.</span></span> <span data-ttu-id="7d6eb-125">在 [維度屬性]\*\*\*\* 中，選取 [帳戶]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-125">In **Dimension Type**, you select **Accounts**.</span></span> <span data-ttu-id="7d6eb-126">然後，如果維度有 [帳戶類型]\*\*\*\* 和 [帳戶描述]\*\*\*\* 屬性，請在 [包含]\*\*\*\* 資料行中，選取 [帳戶名稱]\*\*\*\* 和 [帳戶類型]\*\*\*\* 帳戶類型的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-126">Then, if the dimension has **Account Type** and **Account Description** attributes, in the **Include** column, you select the check boxes for the **Account Name** and **Account Type** account types.</span></span> <span data-ttu-id="7d6eb-127">在 [維度屬性]\*\*\*\* 資料行中，將這些帳戶類型分別與維度內的 [帳戶描述]\*\*\*\* 和 [帳戶類型]\*\*\*\* 屬性產生關聯。</span><span class="sxs-lookup"><span data-stu-id="7d6eb-127">In the **Dimension Attribute** column, you then associate these account types with the **Account Description** and **Account Type** attributes, respectively, in the dimension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d6eb-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d6eb-128">See Also</span></span>  
 [<span data-ttu-id="7d6eb-129">使用商業智慧精靈定義時間智慧計算</span><span class="sxs-lookup"><span data-stu-id="7d6eb-129">Define Time Intelligence Calculations using the Business Intelligence Wizard</span></span>](define-time-intelligence-calculations-using-the-business-intelligence-wizard.md)  
  
  
