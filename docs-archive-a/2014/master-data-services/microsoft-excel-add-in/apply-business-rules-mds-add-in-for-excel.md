---
title: 套用商務規則 (適用於 Excel 的 MDS 增益集) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cd106345-f561-4966-88d3-a69139b2bd78
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: aad5ce6bcebb635fa4659c32654d67406d4ba0dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698395"
---
# <a name="apply-business-rules-mds-add-in-for-excel"></a><span data-ttu-id="a62d6-102">套用商務規則 (適用於 Excel 的 MDS 增益集)</span><span class="sxs-lookup"><span data-stu-id="a62d6-102">Apply Business Rules (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="a62d6-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 中，當您想要驗證資料並確認資料是否有效時，請套用商務規則。</span><span class="sxs-lookup"><span data-stu-id="a62d6-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] apply business rules when you want to validate data and confirm that it is valid.</span></span> <span data-ttu-id="a62d6-104">您可以更正驗證並且重新發行資料。</span><span class="sxs-lookup"><span data-stu-id="a62d6-104">You can correct validations and re-publish the data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a62d6-105">資料驗證會在您發行資料時自動進行。</span><span class="sxs-lookup"><span data-stu-id="a62d6-105">Data validation occurs automatically when you publish data.</span></span> <span data-ttu-id="a62d6-106">如需詳細資訊，請參閱 [驗證預存程序 &#40;Master Data Services&#41;](../validation-stored-procedure-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a62d6-106">For more information, see [Validation Stored Procedure &#40;Master Data Services&#41;](../validation-stored-procedure-master-data-services.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a62d6-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="a62d6-107">Prerequisites</span></span>  
 <span data-ttu-id="a62d6-108">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="a62d6-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="a62d6-109">您必須擁有總管\*\*\*\* 功能區域的存取權。</span><span class="sxs-lookup"><span data-stu-id="a62d6-109">You must have access to the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="a62d6-110">您必須擁有包含 MDS 管理之資料的使用中工作表。</span><span class="sxs-lookup"><span data-stu-id="a62d6-110">You must have an active worksheet that contains MDS-managed data.</span></span>  
  
### <a name="to-apply-business-rules"></a><span data-ttu-id="a62d6-111">若要套用商務規則</span><span class="sxs-lookup"><span data-stu-id="a62d6-111">To apply business rules</span></span>  
  
1.  <span data-ttu-id="a62d6-112">按一下 [發行和驗證]\*\*\*\* 群組中的 [套用規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a62d6-112">In the **Publish and Validate** group, click **Apply Rules**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a62d6-113">單次驗證的成員 (資料列) 數目主要取決於 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]中的設定。</span><span class="sxs-lookup"><span data-stu-id="a62d6-113">The number of members (rows) that are validated at one time depends on a setting in [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span> <span data-ttu-id="a62d6-114">如需詳細資訊，請參閱 [商務規則設定](../system-settings-master-data-services.md#BusinessRules)。</span><span class="sxs-lookup"><span data-stu-id="a62d6-114">For more information, see [Business Rule Settings](../system-settings-master-data-services.md#BusinessRules).</span></span>  
  
2.  <span data-ttu-id="a62d6-115">系統會根據商務規則驗證資料，並且顯示兩個狀態資料行。</span><span class="sxs-lookup"><span data-stu-id="a62d6-115">The data is validated against business rules and two status columns are displayed.</span></span> <span data-ttu-id="a62d6-116">如果未自動顯示這些資料行，請按一下 [發行和驗證]\*\*\*\* 群組中的 [顯示狀態]\*\*\*\* 檢視它們。</span><span class="sxs-lookup"><span data-stu-id="a62d6-116">If these columns are not displayed automatically, in the **Publish and Validate** group, click **Show Status** to view them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a62d6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a62d6-117">See Also</span></span>  
 [<span data-ttu-id="a62d6-118">發行資料 &#40;適用于 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="a62d6-118">Publishing Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
