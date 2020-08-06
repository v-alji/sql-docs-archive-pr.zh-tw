---
title: " (資料採礦嚮導) 中指定資料表類型 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.specifytabletypes.f1
ms.assetid: 8209a707-faef-4ffc-8991-6c13bb350753
author: minewiskan
ms.author: owend
ms.openlocfilehash: 88c09f26958c37ed0a99efb54a5eb5c08505d16b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598547"
---
# <a name="specify-table-types-data-mining-wizard"></a><span data-ttu-id="6d4df-102">指定資料表類型 (資料採礦精靈)</span><span class="sxs-lookup"><span data-stu-id="6d4df-102">Specify Table Types (Data Mining Wizard)</span></span>
  <span data-ttu-id="6d4df-103">使用 [指定資料表類型]\*\*\*\* 頁面，即可識別要用來定義採礦結構的資料表。</span><span class="sxs-lookup"><span data-stu-id="6d4df-103">Use the **Specify Table Types** page to identify the tables to use to define the mining structure.</span></span> <span data-ttu-id="6d4df-104">如果未選取資料表，將不會使用它來定義採礦結構。</span><span class="sxs-lookup"><span data-stu-id="6d4df-104">If a table is not selected, it will not be used to define the mining structure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6d4df-105">您稍後可以從資料採礦設計師\*\*\*\* 中的 [採礦結構]\*\*\*\* 索引標籤加入資料表。</span><span class="sxs-lookup"><span data-stu-id="6d4df-105">You can add tables later from the **Mining Structure** tab in **Data Mining Designer**.</span></span>  
  
 <span data-ttu-id="6d4df-106">**如需詳細資訊，請參閱** [巢狀資料表 &#40;Analysis Services - 資料採礦&#41;](data-mining/nested-tables-analysis-services-data-mining.md)、[資料採礦精靈 &#40;Analysis Services - 資料採礦&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md)、[建立關聯式採礦結構](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="6d4df-106">**For More Information:** [Nested Tables &#40;Analysis Services - Data Mining&#41;](data-mining/nested-tables-analysis-services-data-mining.md), [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="6d4df-107">選項</span><span class="sxs-lookup"><span data-stu-id="6d4df-107">Options</span></span>  
 <span data-ttu-id="6d4df-108">**資料表**</span><span class="sxs-lookup"><span data-stu-id="6d4df-108">**Tables**</span></span>  
 <span data-ttu-id="6d4df-109">顯示您在精靈的 [選取資料來源檢視]\*\*\*\* 頁面上選取之資料來源檢視中的資料表。</span><span class="sxs-lookup"><span data-stu-id="6d4df-109">Displays the tables in the data source view that you selected on the **Select Data Source View** page of the wizard.</span></span>  
  
 <span data-ttu-id="6d4df-110">**例圖**</span><span class="sxs-lookup"><span data-stu-id="6d4df-110">**Case**</span></span>  
 <span data-ttu-id="6d4df-111">選取一個資料表以作為案例資料表。</span><span class="sxs-lookup"><span data-stu-id="6d4df-111">Select one table to use as the case table.</span></span>  
  
 <span data-ttu-id="6d4df-112">**巢狀**</span><span class="sxs-lookup"><span data-stu-id="6d4df-112">**Nested**</span></span>  
 <span data-ttu-id="6d4df-113">選取資料表以作為巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="6d4df-113">Select the tables to use as nested tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6d4df-114">這些資料表與案例資料表必須有多對一關聯性，而非一對多關聯性。</span><span class="sxs-lookup"><span data-stu-id="6d4df-114">These tables must have a many-to-one relationship with the case table, not a one-to-many relationship.</span></span> <span data-ttu-id="6d4df-115">您必須在資料來源檢視中指定此關聯性之後，才能選取資料表作為巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="6d4df-115">You must specify this relationship in the data source view before you can select the table as nested.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d4df-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d4df-116">See Also</span></span>  
 <span data-ttu-id="6d4df-117">[資料採礦嚮導 F1 說明 &#40;Analysis Services-資料採礦&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="6d4df-117">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="6d4df-118">[選取資料來源視圖 &#40;資料採礦嚮導&#41;](select-data-source-view-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="6d4df-118">[Select Data Source View &#40;Data Mining Wizard&#41;](select-data-source-view-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="6d4df-119">指定定型資料 &#40;資料採礦嚮導&#41;</span><span class="sxs-lookup"><span data-stu-id="6d4df-119">Specify the Training Data &#40;Data Mining Wizard&#41;</span></span>](specify-the-training-data-data-mining-wizard.md)  
  
  
