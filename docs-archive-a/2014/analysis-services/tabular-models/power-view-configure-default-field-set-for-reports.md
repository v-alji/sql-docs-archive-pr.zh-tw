---
title: 設定 Power View 報表的預設欄位集 (SSAS 表格式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- ql12.asvs.bidtoolset.deffieldset.f1
ms.assetid: 6836b42f-28b8-4a98-a86d-2c3c109f0189
author: minewiskan
ms.author: owend
ms.openlocfilehash: c66fbbacd0cc2efd7d379bcc8e68149551476869
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687202"
---
# <a name="configure-default-field-set-for-power-view-reports-ssas-tabular"></a><span data-ttu-id="5d8d1-102">設定 Power View 報表的預設欄位集 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="5d8d1-102">Configure Default Field Set for Power View Reports (SSAS Tabular)</span></span>
  <span data-ttu-id="5d8d1-103">預設欄位集是預先定義的資料行和量值的清單，當您選取報表欄位清單中的資料表時，此清單會自動加入 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 報表畫布。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-103">A default field set is a predefined list of columns and measures that are automatically added to a [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] report canvas when the table is selected in the report field list.</span></span> <span data-ttu-id="5d8d1-104">表格式模型作者可以建立預設欄位集，針對在報表中使用此模型的報表作者移除多餘的步驟。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-104">Tabular model authors can create a default field set to eliminate redundant steps for report authors who use the model for their reports.</span></span> <span data-ttu-id="5d8d1-105">例如，如果您知道使用客戶連絡資訊的大部分報表作者都想要看到連絡人的名稱、主要電話號碼、電子郵件地址和公司名稱，您可以預先選取這些資料行，這樣當報表作者按一下 [客戶連絡人] 資料表時，這些資料行就會固定加入到報表畫布上。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-105">For example, if you know that most report authors who work with customer contact information always want to see a contact name, a primary phone number, an email address, and a company name, you can pre-select those columns so that they are always added to the report canvas when the author clicks the Customer Contact table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5d8d1-106">預設欄位集只會套用至 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]中當做資料模型使用的表格式模型。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-106">A default field set applies only to a tabular model used as a data model in [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span> <span data-ttu-id="5d8d1-107">Excel 的樞紐分析報表不支援預設欄位集。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-107">Default field sets are not supported in Excel pivot reports.</span></span>  
  
## <a name="creating-a-default-field-set"></a><span data-ttu-id="5d8d1-108">建立預設欄位集</span><span class="sxs-lookup"><span data-stu-id="5d8d1-108">Creating a Default Field Set</span></span>  
 <span data-ttu-id="5d8d1-109">您可以決定在 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]中選取特定資料表時，預設要包含哪些欄位 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-109">You can determine which fields, if any, are included by default whenever a specific table is selected in [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span> <span data-ttu-id="5d8d1-110">您也可以決定欄位出現在清單上的順序。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-110">You can also determine the order in which fields appear in the list.</span></span> <span data-ttu-id="5d8d1-111">若要指定預設欄位集，您必須在表格式模型專案中設定報表屬性。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-111">To specify a default field set, you set report properties in the tabular model project.</span></span>  
  
#### <a name="to-add-a-default-field-set"></a><span data-ttu-id="5d8d1-112">若要加入預設欄位集</span><span class="sxs-lookup"><span data-stu-id="5d8d1-112">To add a default field set</span></span>  
  
1.  <span data-ttu-id="5d8d1-113">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，按一下您要設定預設欄位清單的資料表 (標籤)。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-113">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the table (tab) for which you are configuring a default field list.</span></span>  
  
2.  <span data-ttu-id="5d8d1-114">在 [屬性]\*\*\*\* 視窗中，於 [預設欄位集]\*\*\*\* 屬性上按一下 [按一下可編輯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-114">In the **Properties** window, in the **Default Field Set** property, click **Click to edit**.</span></span>  
  
3.  <span data-ttu-id="5d8d1-115">在 [預設欄位集] 對話方塊中，選取一個或多個欄位。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-115">In the Default Field Set dialog, select one or more fields.</span></span> <span data-ttu-id="5d8d1-116">您可以選擇資料表中的任何欄位，包括量值在內。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-116">You can choose any field in the table, including measures.</span></span> <span data-ttu-id="5d8d1-117">按住 SHIFT 鍵選取範圍，或按 CTRL 鍵選取個別欄位。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-117">Hold down the Shift key to select a range, or the Ctrl key to select individual fields.</span></span>  
  
4.  <span data-ttu-id="5d8d1-118">按一下 [加入]\*\*\*\* 將它們加入預設欄位集。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-118">Click **Add** to add them to the default field set.</span></span>  
  
5.  <span data-ttu-id="5d8d1-119">使用向上箭號與向下箭號按鈕，指定欄位清單中的順序。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-119">Use the Up and Down buttons to specify an order to the field list.</span></span> <span data-ttu-id="5d8d1-120">欄位會依欄位集定義的順序加入至報告。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-120">Fields will be added to the report in the order defined for the field set.</span></span>  
  
6.  <span data-ttu-id="5d8d1-121">針對活頁簿中的其他資料表重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-121">Repeat these steps for other tables in your workbook.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="5d8d1-122">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5d8d1-122">Next Step</span></span>  
 <span data-ttu-id="5d8d1-123">您建立預設欄位集之後，可以透過指定預設標籤、預設影像、預設群組行為，或包含相同值的資料列是否群組在一資料列或是個別列出，進一步影響報表設計體驗。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-123">After you create a default field set, you can further influence the report design experience by specifying default labels, default images, default group behavior, or whether rows that contain the same value are grouped together in one row or listed individually.</span></span> <span data-ttu-id="5d8d1-124">如需詳細資訊，請參閱[設定 Power View 報表的資料表行為屬性 &#40;SSAS 表格式&#41;](power-view-configure-table-behavior-properties-for-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-124">For more information, see [Configure Table Behavior Properties for Power View Reports &#40;SSAS Tabular&#41;](power-view-configure-table-behavior-properties-for-reports.md).</span></span>  
  
  
