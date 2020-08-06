---
title: 從 PowerPivot 還原 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql11.asvs.ssmsimbi.RestoreFromPP.f1
ms.assetid: 232ac8ed-77fe-47d8-acd3-59bc2fdfdf48
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4dbb0e7867451e67eaa1503c54d7e3da1c276965
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706794"
---
# <a name="restore-from-powerpivot"></a><span data-ttu-id="3c222-102">從 PowerPivot 還原</span><span class="sxs-lookup"><span data-stu-id="3c222-102">Restore from PowerPivot</span></span>
  <span data-ttu-id="3c222-103">您可以在 SQL Server Management Studio 中使用 [從 PowerPivot 還原] 功能，於 Analysis Services 執行個體上建立新的表格式模型資料庫 (以表格式模式執行)，或是從 PowerPivot 活頁簿 (.xlsx) 還原到現有的資料庫。</span><span class="sxs-lookup"><span data-stu-id="3c222-103">You can use the Restore from PowerPivot feature in SQL Server Management Studio to create a new Tabular model database on an Analysis Services instance (running in Tabular mode), or restore to an existing database from a PowerPivot workbook (.xlsx).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c222-104">SQL Server Data Tools 中的 [從 PowerPivot 匯入] 專案範本提供了類似的功能。</span><span class="sxs-lookup"><span data-stu-id="3c222-104">The Import from PowerPivot project template in SQL Server Data Tools provides similar functionality.</span></span> <span data-ttu-id="3c222-105">如需詳細資訊，請參閱[從 PowerPivot 匯入 &#40;SSAS 表格式&#41;](import-from-power-pivot-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="3c222-105">For more information, see [Import from PowerPivot &#40;SSAS Tabular&#41;](import-from-power-pivot-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="3c222-106">使用 [從 PowerPivot 還原] 功能時，請牢記以下事項：</span><span class="sxs-lookup"><span data-stu-id="3c222-106">When using Restore from PowerPivot, keep the following in mind:</span></span>  
  
-   <span data-ttu-id="3c222-107">若要使用 [從 PowerPivot 還原] 功能，您必須以 Analysis Services 執行個體上伺服器管理員角色的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="3c222-107">In order to use Restore from PowerPivot, you must be logged on as a member of the Server Administrators role on the Analysis Services instance.</span></span>  
  
-   <span data-ttu-id="3c222-108">Analysis Services 執行個體服務帳戶必須對您要從中還原的活頁簿檔案具有讀取權限。</span><span class="sxs-lookup"><span data-stu-id="3c222-108">The Analysis Services instance service account must have Read permissions on the workbook file you are restoring from.</span></span>  
  
-   <span data-ttu-id="3c222-109">依預設，當您從 PowerPivot 還原資料庫時，表格式模型資料庫的 [資料來源模擬資訊] 屬性會設為 [預設值]，而這是指定 Analysis Services 執行個體服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="3c222-109">By default, when you restore a database from PowerPivot, the Tabular model database Data Source Impersonation Info property is set to Default, which specifies the Analysis Services instance service account.</span></span> <span data-ttu-id="3c222-110">建議您在 [資料庫屬性] 中，將模擬認證變更為 Windows 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="3c222-110">It is recommended you change the impersonation credentials to a Windows user account in Database Properties.</span></span> <span data-ttu-id="3c222-111">如需詳細資訊，請參閱[模擬 &#40;SSAS 表格式&#41;](impersonation-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="3c222-111">For more information, see [Impersonation &#40;SSAS Tabular&#41;](impersonation-ssas-tabular.md).</span></span>  
  
-   <span data-ttu-id="3c222-112">PowerPivot 資料模型中的資料將會複製到 Analysis Services 執行個體上現有或新的表格式模型資料庫。</span><span class="sxs-lookup"><span data-stu-id="3c222-112">Data in the PowerPivot data model will be copied into an existing or new Tabular model database on the Analysis Services instance.</span></span> <span data-ttu-id="3c222-113">如果您的 PowerPivot 活頁簿包含連結資料表，這些資料表將會重新建立成為不具資料來源的資料表，類似於使用 [貼上至新資料表] 所建立的資料表。</span><span class="sxs-lookup"><span data-stu-id="3c222-113">If your PowerPivot workbook contains linked tables, they will be recreated as a table without a data source, similar to a table created using Paste To New table.</span></span>  
  
### <a name="to-restore-from-powerpivot"></a><span data-ttu-id="3c222-114">從 PowerPivot 還原</span><span class="sxs-lookup"><span data-stu-id="3c222-114">To Restore from PowerPivot</span></span>  
  
1.  <span data-ttu-id="3c222-115">在 SSMS 中，于您想要還原的 Active Directory 實例中，以滑鼠右鍵按一下 [**資料庫**]，然後按一下 [**從 PowerPivot 還原**]。</span><span class="sxs-lookup"><span data-stu-id="3c222-115">In SSMS, in the Active Directory instance you want to restore to, right click **Databases**, and then click **Restore from PowerPivot**.</span></span>  
  
2.  <span data-ttu-id="3c222-116">在 [**從 PowerPivot 還原**] 對話方塊的 [**還原來源**] 中，按一下 [**備份檔案**] 中的 **[流覽]**，然後選取要從中還原的 .abf 或 xslx 檔案。</span><span class="sxs-lookup"><span data-stu-id="3c222-116">In the **Restore from PowerPivot** dialog box, in **Restore Source**, in **Backup file**, click **Browse**, and then select an .abf or .xslx file to restore from.</span></span>  
  
3.  <span data-ttu-id="3c222-117">在 [還原目標]\*\*\*\* 的 [還原資料庫]\*\*\*\* 中，輸入新資料庫或現有資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="3c222-117">In **Restore Target**, in **Restore database**, type a name for a new database or for an existing database.</span></span> <span data-ttu-id="3c222-118">如果您沒有指定名稱，就會使用活頁簿的名稱。</span><span class="sxs-lookup"><span data-stu-id="3c222-118">If you do not specify a name, the name of the workbook is used.</span></span>  
  
4.  <span data-ttu-id="3c222-119">按一下 [儲存位置]\*\*\*\* 中的 [瀏覽]\*\*\*\*，然後選取要儲存資料庫的位置。</span><span class="sxs-lookup"><span data-stu-id="3c222-119">In **Storage location**, click **Browse**, and then select a location to store the database.</span></span>  
  
5.  <span data-ttu-id="3c222-120">在 [選項]\*\*\*\* 中，保持核取 [包含安全性資訊]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c222-120">In **Options**, leave **Include security information** checked.</span></span> <span data-ttu-id="3c222-121">從 PowerPivot 活頁簿還原時，這項設定並不適用。</span><span class="sxs-lookup"><span data-stu-id="3c222-121">When restoring from a PowerPivot workbook, this setting does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c222-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c222-122">See Also</span></span>  
 <span data-ttu-id="3c222-123">[表格式模型資料庫 &#40;SSAS 表格式&#41;](tabular-model-databases-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="3c222-123">[Tabular Model Databases &#40;SSAS Tabular&#41;](tabular-model-databases-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="3c222-124">從 PowerPivot 匯入 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="3c222-124">Import from PowerPivot &#40;SSAS Tabular&#41;</span></span>](import-from-power-pivot-ssas-tabular.md)  
  
  
