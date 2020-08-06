---
title: 連接到 MDS 儲存機制 (適用於 Excel 的 MDS 增益集) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 8f427312-4c09-4c8b-b9f9-8b235557a74b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c1db0594f07da7ff8a78642e4b2de0eb9e507164
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698380"
---
# <a name="connect-to-an-mds-repository-mds-add-in-for-excel"></a><span data-ttu-id="8ed31-102">連接到 MDS 儲存機制 (適用於 Excel 的 MDS 增益集)</span><span class="sxs-lookup"><span data-stu-id="8ed31-102">Connect to an MDS Repository (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="8ed31-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，您必須先連接到 MDS 儲存機制，然後才能載入或發行資料。</span><span class="sxs-lookup"><span data-stu-id="8ed31-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you must connect to an MDS repository before you can load or publish data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8ed31-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="8ed31-104">Prerequisites</span></span>  
 <span data-ttu-id="8ed31-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="8ed31-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="8ed31-106">您必須擁有存取 [ **Explorer** ] 功能區域的許可權。</span><span class="sxs-lookup"><span data-stu-id="8ed31-106">You must have permission to access the **Explorer** functional area.</span></span>  
  
### <a name="to-connect-to-an-mds-repository"></a><span data-ttu-id="8ed31-107">若要連接到 MDS 儲存機制</span><span class="sxs-lookup"><span data-stu-id="8ed31-107">To connect to an MDS repository</span></span>  
  
1.  <span data-ttu-id="8ed31-108">在 MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 的 [主要資料]\*\*\*\* 索引標籤上，於 [連接和載入]\*\*\*\* 群組中，按一下 [連接]\*\*\*\* 按鈕底下的箭號，然後按一下 [管理連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ed31-108">In the MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], on the **Master Data** tab, in the **Connect and Load** group, click the arrow under the **Connect** button and click **Manage Connections**.</span></span>  
  
2.  <span data-ttu-id="8ed31-109">在 [管理連接]\*\*\*\* 對話方塊的 [新增連接]\*\*\*\* 區段中，按一下 [建立新連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ed31-109">On the **Manage Connections** dialog box, in the **New connection** section, click **Create a new connection**.</span></span>  
  
3.  <span data-ttu-id="8ed31-110">按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="8ed31-110">Click **New**.</span></span>  
  
4.  <span data-ttu-id="8ed31-111">在 [加入新連接]\*\*\*\* 對話方塊的 [描述]\*\*\*\* 欄位中，輸入連接的描述。</span><span class="sxs-lookup"><span data-stu-id="8ed31-111">On the **Add New Connection** dialog box, in the **Description** field, type a description for your connection.</span></span> <span data-ttu-id="8ed31-112">當您在工具列上按一下 [連接]\*\*\*\* 按鈕底下的箭號時，就會顯示這個連接。</span><span class="sxs-lookup"><span data-stu-id="8ed31-112">This connection will be displayed when you click the arrow under the **Connect** button on the toolbar.</span></span>  
  
5.  <span data-ttu-id="8ed31-113">在 [MDS 伺服器位址]\*\*\*\* 方塊中，鍵入 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式的 URL，例如 http://contoso/mds。</span><span class="sxs-lookup"><span data-stu-id="8ed31-113">In the **MDS server address** box, type the URL of the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application, for example http://contoso/mds.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8ed31-114">請確認您使用的是電腦名稱，請不要使用 "localhost"。</span><span class="sxs-lookup"><span data-stu-id="8ed31-114">Ensure that you use the computer name; do not use "localhost".</span></span>  
  
6.  <span data-ttu-id="8ed31-115">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8ed31-115">Click **OK**.</span></span> <span data-ttu-id="8ed31-116">此名稱就會顯示在 [現有連接]\*\*\*\* 區段中。</span><span class="sxs-lookup"><span data-stu-id="8ed31-116">The name is displayed in the **Existing Connections** section.</span></span>  
  
7.  <span data-ttu-id="8ed31-117">(選擇性) 按一下 [測試]\*\*\*\* 測試連接。</span><span class="sxs-lookup"><span data-stu-id="8ed31-117">Optionally, click **Test** to test the connection.</span></span> <span data-ttu-id="8ed31-118">此時會顯示確認或錯誤對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8ed31-118">A confirmation or error dialog is displayed.</span></span> <span data-ttu-id="8ed31-119">按一下 [確定]\*\*\*\* 關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8ed31-119">Click **OK** to close it.</span></span>  
  
8.  <span data-ttu-id="8ed31-120">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="8ed31-120">Click **Connect**.</span></span> <span data-ttu-id="8ed31-121">[Master Data Services]\*\*\*\* 窗格隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="8ed31-121">The **Master Data Services** pane is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8ed31-122">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8ed31-122">Next Steps</span></span>  
  
-   [<span data-ttu-id="8ed31-123">將資料從 MDS 載入 Excel 中</span><span class="sxs-lookup"><span data-stu-id="8ed31-123">Load Data from MDS into Excel</span></span>](export-data-to-excel-from-master-data-services.md)  
  
-   [<span data-ttu-id="8ed31-124">載入 &#40;適用于 Excel 的 MDS 增益集之前先篩選資料&#41;</span><span class="sxs-lookup"><span data-stu-id="8ed31-124">Filter Data before Loading &#40;MDS Add-in for Excel&#41;</span></span>](filter-data-before-exporting-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="8ed31-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ed31-125">See Also</span></span>  
 [<span data-ttu-id="8ed31-126">連接 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="8ed31-126">Connections &#40;MDS Add-in for Excel&#41;</span></span>](connections-mds-add-in-for-excel.md)  
  
  
