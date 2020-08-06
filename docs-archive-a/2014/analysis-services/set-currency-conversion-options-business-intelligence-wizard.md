---
title: " (商業智慧 Wizard) 中設定貨幣轉換選項 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.calculationsettings.f1
ms.assetid: a49d4e1f-bdda-4a83-ab4f-ce8c500e1d6d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 61877deb0bc422d65f977e3fc9de3e678f7d8477
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705514"
---
# <a name="set-currency-conversion-options-business-intelligence-wizard"></a><span data-ttu-id="a1b9a-102">設定貨幣轉換選項 (商業智慧精靈)</span><span class="sxs-lookup"><span data-stu-id="a1b9a-102">Set Currency Conversion Options (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="a1b9a-103">使用 **[設定貨幣轉換]** 頁面，即可定義包含匯率之量值群組的貨幣轉換計算。</span><span class="sxs-lookup"><span data-stu-id="a1b9a-103">Use the **Set Currency Conversion** page to define currency conversion calculations for a measure group that contains exchange rates.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1b9a-104">如果 [商業智慧精靈] 是從 [維度設計師] 啟動，或是在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中方案總管的某維度上按一下滑鼠右鍵來啟動，則不會出現此頁面。</span><span class="sxs-lookup"><span data-stu-id="a1b9a-104">This page does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="a1b9a-105">選項</span><span class="sxs-lookup"><span data-stu-id="a1b9a-105">Options</span></span>  
 <span data-ttu-id="a1b9a-106">**選取包含匯率的量值群組**</span><span class="sxs-lookup"><span data-stu-id="a1b9a-106">**Select the measure group that contains exchange rates**</span></span>  
 <span data-ttu-id="a1b9a-107">選取包含匯率的量值群組，這會由貨幣轉換計算參考。</span><span class="sxs-lookup"><span data-stu-id="a1b9a-107">Select the measure group that contains the exchange rates that the currency conversion calculations should reference.</span></span>  
  
 <span data-ttu-id="a1b9a-108">**指定樞紐貨幣**</span><span class="sxs-lookup"><span data-stu-id="a1b9a-108">**Specify the pivot currency**</span></span>  
 <span data-ttu-id="a1b9a-109">選取作為量值群組之樞紐貨幣的成員。</span><span class="sxs-lookup"><span data-stu-id="a1b9a-109">Select the member that serves as the pivot currency for the measure group.</span></span>  
  
 <span data-ttu-id="a1b9a-110">**選取如何輸入匯率 (選取範例貨幣)**</span><span class="sxs-lookup"><span data-stu-id="a1b9a-110">**Select how you entered your exchange rates (select a sample currency)**</span></span>  
 <span data-ttu-id="a1b9a-111">從貨幣維度選取代表範例貨幣的成員，即可變更每 1 個範例貨幣有 X 個樞紐貨幣與每 1 個樞紐貨幣有 X 個範例貨幣選項的文字，以改善匯率方向的顯示。</span><span class="sxs-lookup"><span data-stu-id="a1b9a-111">Select a member representing a sample currency from the currency dimension to change the text for the X pivot currency per 1 sample currency and X sample currency per 1 pivot currency options to better display the exchange rate direction.</span></span>  
  
 <span data-ttu-id="a1b9a-112">**每 1 個範例貨幣有 X 個樞紐貨幣**</span><span class="sxs-lookup"><span data-stu-id="a1b9a-112">**X pivot currency per 1 sample currency**</span></span>  
 <span data-ttu-id="a1b9a-113">選取即可指出比率量值群組中的匯率代表指定之樞紐貨幣的倍數。</span><span class="sxs-lookup"><span data-stu-id="a1b9a-113">Select to indicate that the exchange rates in the rate measure group represent a multiplier for the specified pivot currency.</span></span>  
  
 <span data-ttu-id="a1b9a-114">**每 1 個樞紐貨幣有 X 個範例貨幣**</span><span class="sxs-lookup"><span data-stu-id="a1b9a-114">**X sample currency per 1 pivot currency**</span></span>  
 <span data-ttu-id="a1b9a-115">選取即可指出比率量值群組中的匯率代表指定之範例貨幣的倍數。</span><span class="sxs-lookup"><span data-stu-id="a1b9a-115">Select to indicate that the exchange rates in the rate measure group represent a multiplier for the specified sample currency.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1b9a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1b9a-116">See Also</span></span>  
 <span data-ttu-id="a1b9a-117">[商業智慧 Wizard F1 說明](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="a1b9a-117">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="a1b9a-118">[Cube 設計工具 &#40;Analysis Services-多維度資料&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a1b9a-118">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="a1b9a-119">維度設計師 &#40;Analysis Services 多維資料&#41;</span><span class="sxs-lookup"><span data-stu-id="a1b9a-119">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
