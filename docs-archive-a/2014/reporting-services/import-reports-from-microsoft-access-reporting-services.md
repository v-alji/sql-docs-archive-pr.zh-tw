---
title: 從 Microsoft Access (Reporting Services 匯入報表) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Access reports [Reporting Services]
- importing reports
ms.assetid: 4f29d5b8-b77d-4714-a84a-05523df55646
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 862d8b90f3c91dffda35971677db7fdc231c1b63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598754"
---
# <a name="import-reports-from-microsoft-access-reporting-services"></a><span data-ttu-id="1452f-102">從 Microsoft Access 匯入報表 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="1452f-102">Import Reports from Microsoft Access (Reporting Services)</span></span>
  <span data-ttu-id="1452f-103">在報表設計師中，您可以從 [!INCLUDE[msCoName](../includes/msconame-md.md)] Access 資料庫或專案匯入報表。</span><span class="sxs-lookup"><span data-stu-id="1452f-103">In Report Designer, you can import reports from a [!INCLUDE[msCoName](../includes/msconame-md.md)] Access database or project.</span></span> <span data-ttu-id="1452f-104">您必須將 Access 2002 或更新版本安裝在安裝報表設計師的相同電腦上。</span><span class="sxs-lookup"><span data-stu-id="1452f-104">Access 2002 or a later version must be installed on the same computer on which Report Designer is installed.</span></span>  
  
 <span data-ttu-id="1452f-105">當您使用匯入功能時，會匯入資料庫或專案檔案的所有報表。</span><span class="sxs-lookup"><span data-stu-id="1452f-105">When you use the import feature, all reports in the database or project file are imported.</span></span> <span data-ttu-id="1452f-106">如果 Access 檔案包含許多報表，您可以建立個別的報表專案以匯入報表，然後再於主要報表專案中開啟個別的 RDL 檔案。</span><span class="sxs-lookup"><span data-stu-id="1452f-106">If your Access file contains many reports, you may want to create a separate report project into which to import the reports, and then open the individual RDL files in your main report project.</span></span> <span data-ttu-id="1452f-107">報表匯入報表設計師之後，就可以編輯報表了。</span><span class="sxs-lookup"><span data-stu-id="1452f-107">You can edit the reports after they are imported into Report Designer.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="1452f-108">不支援所有 Access 報表物件。</span><span class="sxs-lookup"><span data-stu-id="1452f-108">does not support all Access report objects.</span></span> <span data-ttu-id="1452f-109">未轉換的專案會顯示在 [**工作清單**] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="1452f-109">Items that are not converted are displayed in the **Task List** window.</span></span> <span data-ttu-id="1452f-110">如需詳細資訊，請參閱[支援的存取報告功能 &#40;SSRS&#41;](../../2014/reporting-services/supported-access-report-features-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1452f-110">For more information, see [Supported Access Report Features &#40;SSRS&#41;](../../2014/reporting-services/supported-access-report-features-ssrs.md).</span></span>  
  
### <a name="to-import-reports-from-microsoft-access"></a><span data-ttu-id="1452f-111">從 Microsoft Access 匯入報表</span><span class="sxs-lookup"><span data-stu-id="1452f-111">To import reports from Microsoft Access</span></span>  
  
1.  <span data-ttu-id="1452f-112">開啟或建立用來匯入報表的專案。</span><span class="sxs-lookup"><span data-stu-id="1452f-112">Open or create a project into which to import the reports.</span></span>  
  
2.  <span data-ttu-id="1452f-113">在 [**專案**] 功能表上，指向 [匯**入報表**]，然後按一下 [ **Microsoft Access**]。</span><span class="sxs-lookup"><span data-stu-id="1452f-113">On the **Project** menu, point to **Import Reports**, and then click **Microsoft Access**.</span></span> <span data-ttu-id="1452f-114">或者，以滑鼠右鍵按一下方案總管中的專案，指向 [匯**入報表**]，然後按一下 [ **Microsoft Access**]。</span><span class="sxs-lookup"><span data-stu-id="1452f-114">Alternatively, right-click the project in Solution Explorer, point to **Import Reports**, and then click **Microsoft Access**.</span></span>  
  
3.  <span data-ttu-id="1452f-115">在 [**開啟**] 對話方塊中，選取包含報表的 Access 資料庫 ( .mdb、.accdb) 或專案 ( adp) ，然後按一下 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="1452f-115">In the **Open** dialog box, select the Access database (.mdb, .accdb) or project (.adp) that contains the reports, and then click **Open**.</span></span> <span data-ttu-id="1452f-116">資料庫或專案檔案中的所有報表都會匯入並列在 [方案總管] 的 [報表] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="1452f-116">All the reports in the database or project file are imported and listed in the Reports folder in Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="1452f-117">檢查 [**工作清單**] 視窗中是否有組建錯誤。</span><span class="sxs-lookup"><span data-stu-id="1452f-117">Check the **Task List** window for build errors.</span></span> <span data-ttu-id="1452f-118">若要查看 [**工作清單**] 視窗，請開啟 [ **view** ] 功能表，指向 [**其他視窗**]，然後按一下 [**工作清單**]。</span><span class="sxs-lookup"><span data-stu-id="1452f-118">To view the **Task List** window, open the **View** menu, point to **Other Windows**, and then click **Task List**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1452f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1452f-119">See Also</span></span>  
 [<span data-ttu-id="1452f-120">使用報表設計師設計報表 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1452f-120">Design Reports with Report Designer &#40;SSRS&#41;</span></span>](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
