---
title: 匯入原則對話方塊 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.importpolicy.f1
ms.assetid: 78ab5f6e-2f13-4788-937e-8892ef4e2345
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2601c21ea08d00bf77e9b97a5186f2d6d1200a10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591983"
---
# <a name="import-policies-dialog-box"></a><span data-ttu-id="9a1fc-102">匯出原則對話方塊</span><span class="sxs-lookup"><span data-stu-id="9a1fc-102">Import Policies Dialog Box</span></span>
  <span data-ttu-id="9a1fc-103">使用此對話方塊，可將儲存為 XML 檔案的一個或多個原則 (和其參考條件) 匯入到目前的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體中。</span><span class="sxs-lookup"><span data-stu-id="9a1fc-103">Use this dialog box to import one or more policies (and their referenced condition) that are saved as XML files, into the current [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] instance.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9a1fc-104">選項。</span><span class="sxs-lookup"><span data-stu-id="9a1fc-104">Options</span></span>  
 <span data-ttu-id="9a1fc-105">**要匯入的檔案**</span><span class="sxs-lookup"><span data-stu-id="9a1fc-105">**Files to import**</span></span>  
 <span data-ttu-id="9a1fc-106">若要從 XML 檔案匯入原則，請輸入檔案的路徑和名稱，或是使用 [瀏覽]\( **...** ) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9a1fc-106">To import a policy from an XML file, type the path and name of the file or use the Browse (**...**) button.</span></span>  
  
 <span data-ttu-id="9a1fc-107">**以匯入的項目取代重複的項目**</span><span class="sxs-lookup"><span data-stu-id="9a1fc-107">**Replace duplicates with items imported**</span></span>  
 <span data-ttu-id="9a1fc-108">選取此選項可覆寫任何同名的現有原則或條件 (如果這個 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體上已經有該原則或條件存在)。</span><span class="sxs-lookup"><span data-stu-id="9a1fc-108">Select to overwrite any existing policy or condition of the same name if it already exists on this [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance.</span></span> <span data-ttu-id="9a1fc-109">具有相依原則的條件無法被覆寫，除非該相依原則也一起被覆寫。</span><span class="sxs-lookup"><span data-stu-id="9a1fc-109">A condition with a dependent policy cannot be overwritten unless the dependent policy is also being overwritten.</span></span> <span data-ttu-id="9a1fc-110">如果未選取這個選項，使用相同條件運算式的現有條件將不會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="9a1fc-110">If this option is not selected, an existing condition that is using the same condition expression will not cause an error.</span></span>  
  
 <span data-ttu-id="9a1fc-111">**原則狀態**</span><span class="sxs-lookup"><span data-stu-id="9a1fc-111">**Policy state**</span></span>  
 <span data-ttu-id="9a1fc-112">選取匯入的原則所要的狀態：</span><span class="sxs-lookup"><span data-stu-id="9a1fc-112">Select the state that you want for the imported policy:</span></span>  
  
-   <span data-ttu-id="9a1fc-113">**匯入時保留原則狀態**</span><span class="sxs-lookup"><span data-stu-id="9a1fc-113">**Preserve policy state on import**</span></span>  
  
-   <span data-ttu-id="9a1fc-114">**匯入時啟用所有原則**</span><span class="sxs-lookup"><span data-stu-id="9a1fc-114">**Enable all policies on import**</span></span>  
  
-   <span data-ttu-id="9a1fc-115">**匯入時停用所有原則**</span><span class="sxs-lookup"><span data-stu-id="9a1fc-115">**Disable all policies on import**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a1fc-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a1fc-116">See Also</span></span>  
 <span data-ttu-id="9a1fc-117">[使用原則式管理來管理伺服器](administer-servers-by-using-policy-based-management.md) </span><span class="sxs-lookup"><span data-stu-id="9a1fc-117">[Administer Servers by Using Policy-Based Management](administer-servers-by-using-policy-based-management.md) </span></span>  
 <span data-ttu-id="9a1fc-118">[匯入原則式管理原則](import-a-policy-based-management-policy.md) </span><span class="sxs-lookup"><span data-stu-id="9a1fc-118">[Import a Policy-Based Management Policy](import-a-policy-based-management-policy.md) </span></span>  
 [<span data-ttu-id="9a1fc-119">匯出原則式管理原則</span><span class="sxs-lookup"><span data-stu-id="9a1fc-119">Export a Policy-Based Management Policy</span></span>](export-a-policy-based-management-policy.md)  
  
  
