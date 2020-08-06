---
title: 設定報表或文字方塊的地區設定 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- locales [Reporting Services]
ms.assetid: df115b01-184b-47f0-b5ec-0ad965ff9bee
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bb2b0cbd6e4216138520834216358ee455729386
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592439"
---
# <a name="set-the-locale-for-a-report-or-text-box-reporting-services"></a><span data-ttu-id="5fb89-102">設定報表或文字方塊的地區設定 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="5fb89-102">Set the Locale for a Report or Text Box (Reporting Services)</span></span>
  <span data-ttu-id="5fb89-103">報表或文字方塊上的 **[Language]** 屬性包含地區設定，地區設定會決定用來顯示依語言和地區而不同之報表資料的預設格式，例如日期、貨幣或數值。</span><span class="sxs-lookup"><span data-stu-id="5fb89-103">The **Language** property on a report or a text box contains the locale setting, which determines the default formats for displaying report data that differ by language and region, for example, date, currency, or number values.</span></span> <span data-ttu-id="5fb89-104">文字方塊上的 **[Language]** 屬性會覆寫報表上的 **[Language]** 屬性。</span><span class="sxs-lookup"><span data-stu-id="5fb89-104">The **Language** property on a text box overrides the **Language** property on the report.</span></span> <span data-ttu-id="5fb89-105">如果 **[Language]** 未指定任何值，Reporting Services 會針對發行的報表使用報表伺服器上作業系統的地區設定，或是針對報表預覽使用報表撰寫電腦的地區設定。</span><span class="sxs-lookup"><span data-stu-id="5fb89-105">If no value is specified for **Language**, Reporting Services uses the locale of the operating system on the report server for published reports or of the report authoring computer for report preview.</span></span>  
  
 <span data-ttu-id="5fb89-106">如果是 HTML 報表，您可以覆寫預設的 **Language** 值，並使用瀏覽器用戶端之 HTTP 標頭所指定的語言，其方式是在報表或文字方塊之 **Language** 屬性的運算式內使用內建的 User!Language 欄位。</span><span class="sxs-lookup"><span data-stu-id="5fb89-106">For HTML reports, you can override the default **Language** value and use the language specified by the HTTP header of the browser client by using the built-in field User!Language in an expression for the **Language** property of a report or a text box.</span></span>  
  
 <span data-ttu-id="5fb89-107">您也可以在 URL 中指定報表的 **[Language]** 屬性。</span><span class="sxs-lookup"><span data-stu-id="5fb89-107">You can also specify the **Language** property for a report in a URL.</span></span> <span data-ttu-id="5fb89-108">如需詳細資訊，請參閱 [設定 URL 中報表參數的語言言](../set-the-language-for-report-parameters-in-a-url.md)。</span><span class="sxs-lookup"><span data-stu-id="5fb89-108">For more information, see [Set the Language for Report Parameters in a URL](../set-the-language-for-report-parameters-in-a-url.md).</span></span>  
  
### <a name="to-set-the-locale-for-a-report"></a><span data-ttu-id="5fb89-109">若要設定報表的地區設定</span><span class="sxs-lookup"><span data-stu-id="5fb89-109">To set the locale for a report</span></span>  
  
1.  <span data-ttu-id="5fb89-110">在 [設計] 檢視中，按一下報表設計介面的外面來選取報表。</span><span class="sxs-lookup"><span data-stu-id="5fb89-110">In Design view, click outside the report design surface to select the report.</span></span>  
  
2.  <span data-ttu-id="5fb89-111">在 [屬性] 窗格中，針對 **[Language]** 屬性輸入或選取您要用於報表的語言。</span><span class="sxs-lookup"><span data-stu-id="5fb89-111">In the Properties pane, for the **Language** property, type or select the language that you want to use for the report.</span></span>  
  
### <a name="to-set-the-locale-for-a-text-box"></a><span data-ttu-id="5fb89-112">若要設定文字方塊的地區設定</span><span class="sxs-lookup"><span data-stu-id="5fb89-112">To set the locale for a text box</span></span>  
  
1.  <span data-ttu-id="5fb89-113">在 [設計] 檢視中，選取要套用地區設定的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="5fb89-113">In Design view, select the text box to which you want to apply the locale settings.</span></span>  
  
2.  <span data-ttu-id="5fb89-114">在 [屬性] 窗格中執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="5fb89-114">In the Properties pane, do the following:</span></span>  
  
    -   <span data-ttu-id="5fb89-115">針對 **[Calendar]** 屬性，請輸入或選取用於日期的日曆。</span><span class="sxs-lookup"><span data-stu-id="5fb89-115">For the **Calendar** property, type or select the calendar that you want to use for dates.</span></span>  
  
    -   <span data-ttu-id="5fb89-116">針對 **[Direction]** 屬性，輸入或選取文字的書寫方向。</span><span class="sxs-lookup"><span data-stu-id="5fb89-116">For the **Direction** property, type or select the direction in which the text is written.</span></span>  
  
    -   <span data-ttu-id="5fb89-117">針對 **[Language]** 屬性，請輸入或選取要用於文字方塊的語言。</span><span class="sxs-lookup"><span data-stu-id="5fb89-117">For the **Language** property, type or select the language that you want to use for the text box.</span></span> <span data-ttu-id="5fb89-118">這個值會覆寫報表的 **[Language]** 屬性。</span><span class="sxs-lookup"><span data-stu-id="5fb89-118">This value overrides the **Language** property for the Report.</span></span>  
  
    -   <span data-ttu-id="5fb89-119">針對 **[NumeralLanguage]** 屬性，請輸入或選取文字方塊中所使用的數字格式。</span><span class="sxs-lookup"><span data-stu-id="5fb89-119">For the **NumeralLanguage** property, type or select the format to use for numbers in the text box.</span></span>  
  
    -   <span data-ttu-id="5fb89-120">針對 **[NumeralVariant]** 屬性，輸入或選取文字方塊中所使用之數字格式的變數。</span><span class="sxs-lookup"><span data-stu-id="5fb89-120">For the **NumeralVariant** property, type or select the variant of the format to use for numbers in the text box.</span></span>  
  
    -   <span data-ttu-id="5fb89-121">針對 **[UnicodeBiDi]** 屬性，選取文字方塊中所使用之雙向內嵌的層級。</span><span class="sxs-lookup"><span data-stu-id="5fb89-121">For the **UnicodeBiDi** property, select the level of bidirectional embedding to use in the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fb89-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fb89-122">See Also</span></span>  
 [<span data-ttu-id="5fb89-123">報表中的運算式用法 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5fb89-123">Expression Uses in Reports &#40;Report Builder and SSRS&#41;</span></span>](expression-uses-in-reports-report-builder-and-ssrs.md)  
  
  
