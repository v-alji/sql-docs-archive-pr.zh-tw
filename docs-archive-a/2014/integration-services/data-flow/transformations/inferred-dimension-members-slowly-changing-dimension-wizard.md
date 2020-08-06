---
title: 推斷的維度成員 (緩時變維度精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.inferrdim.f1
ms.assetid: 809e395f-2e10-48ff-8860-56403f130628
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dda4345b91c69b134516baab2e5ba9b9990bd6af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599100"
---
# <a name="inferred-dimension-members-slowly-changing-dimension-wizard"></a><span data-ttu-id="d1670-102">推斷的維度成員 (緩時變維度精靈)</span><span class="sxs-lookup"><span data-stu-id="d1670-102">Inferred Dimension Members (Slowly Changing Dimension Wizard)</span></span>
  <span data-ttu-id="d1670-103">使用 [推斷的維度成員]  對話方塊來指定使用推斷的成員之選項。</span><span class="sxs-lookup"><span data-stu-id="d1670-103">Use the **Inferred Dimension Members** dialog box to specify options for using inferred members.</span></span> <span data-ttu-id="d1670-104">在事實資料表參考尚未載入的維度成員時，推斷的成員即已存在。</span><span class="sxs-lookup"><span data-stu-id="d1670-104">Inferred members exist when a fact table references dimension members that are not yet loaded.</span></span> <span data-ttu-id="d1670-105">當載入推斷成員的資料時，可以更新現有的記錄而不是建立新記錄。</span><span class="sxs-lookup"><span data-stu-id="d1670-105">When data for the inferred member is loaded, you can update the existing record rather than create a new one.</span></span>  
  
 <span data-ttu-id="d1670-106">若要深入了解這個精靈，請參閱＜ [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d1670-106">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d1670-107">選項。</span><span class="sxs-lookup"><span data-stu-id="d1670-107">Options</span></span>  
 <span data-ttu-id="d1670-108">**啟用推斷的成員支援**</span><span class="sxs-lookup"><span data-stu-id="d1670-108">**Enable inferred member support**</span></span>  
 <span data-ttu-id="d1670-109">如果您選擇啟用推斷的成員，就必須選取下列兩個選項的其中之一。</span><span class="sxs-lookup"><span data-stu-id="d1670-109">If you choose to enable inferred members, you must select one of the two options that follow.</span></span>  
  
 <span data-ttu-id="d1670-110">**所有具有變更類型的資料行皆為 Null**</span><span class="sxs-lookup"><span data-stu-id="d1670-110">**All columns with a change type are null**</span></span>  
 <span data-ttu-id="d1670-111">指定是否在新推斷的成員記錄中之具有變更類型的所有資料行中，輸入 Null 值。</span><span class="sxs-lookup"><span data-stu-id="d1670-111">Specify whether to enter null values in all columns with a change type in the new inferred member record.</span></span>  
  
 <span data-ttu-id="d1670-112">**使用布林資料行以指出目前記錄是否為推斷的成員**</span><span class="sxs-lookup"><span data-stu-id="d1670-112">**Use a Boolean column to indicate whether the current record is an inferred member**</span></span>  
 <span data-ttu-id="d1670-113">指定是否使用現有的布林資料行，來指出目前記錄是否為推斷的成員。</span><span class="sxs-lookup"><span data-stu-id="d1670-113">Specify whether to use an existing Boolean column to indicate whether the current record is an inferred member.</span></span>  
  
 <span data-ttu-id="d1670-114">**推斷的成員指標**</span><span class="sxs-lookup"><span data-stu-id="d1670-114">**Inferred member indicator**</span></span>  
 <span data-ttu-id="d1670-115">如果您已經選擇使用布林資料行來指出上述推斷的成員，請從清單中選取資料行。</span><span class="sxs-lookup"><span data-stu-id="d1670-115">If you have chosen to use a Boolean column to indicate inferred members as described above, select the column from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1670-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1670-116">See Also</span></span>  
 [<span data-ttu-id="d1670-117">使用緩時變維度精靈來設定輸出</span><span class="sxs-lookup"><span data-stu-id="d1670-117">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
