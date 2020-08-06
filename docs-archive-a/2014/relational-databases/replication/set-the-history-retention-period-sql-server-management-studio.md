---
title: 設定記錄保留週期 (SQL Server Management Studio) | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- history retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: c288daab-5181-4d4b-ba2a-8a147098e758
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 13dcf2ad9a9d619a7fdef9c1ed3f7b970e420cdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606750"
---
# <a name="set-the-history-retention-period-sql-server-management-studio"></a><span data-ttu-id="4b365-102">設定記錄保留週期 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="4b365-102">Set the History Retention Period (SQL Server Management Studio)</span></span>
  <span data-ttu-id="4b365-103">在 [散發資料庫屬性 - \<DistributionDatabase>] 對話方塊的 [一般] 頁面上指定記錄保留期間。</span><span class="sxs-lookup"><span data-stu-id="4b365-103">Specify the history retention period on the **General** page of the **Distribution Database Properties - \<DistributionDatabase>** dialog box.</span></span> <span data-ttu-id="4b365-104">此設定會控制複寫代理程式記錄的儲存時間。</span><span class="sxs-lookup"><span data-stu-id="4b365-104">This setting controls how long replication agent history is stored.</span></span> <span data-ttu-id="4b365-105">此頁面會在 [散發者屬性 - \<Distributor>] 對話方塊的 [一般] 頁面上提供。</span><span class="sxs-lookup"><span data-stu-id="4b365-105">This page is available from the **General** page of the **Distributor Properties - \<Distributor>** dialog box.</span></span> <span data-ttu-id="4b365-106">如需存取此對話方塊的詳細資訊，請參閱[檢視及修改散發者和發行者屬性](view-and-modify-distributor-and-publisher-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="4b365-106">For more information about accessing this dialog box, see [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
### <a name="to-specify-the-history-retention-period"></a><span data-ttu-id="4b365-107">若要指定記錄的保留期限</span><span class="sxs-lookup"><span data-stu-id="4b365-107">To specify the history retention period</span></span>  
  
1.  <span data-ttu-id="4b365-108">在 [散發者屬性 - \<Distributor>] 對話方塊的 [一般] 頁面上，按一下散發資料庫的屬性按鈕 ( **...** )。</span><span class="sxs-lookup"><span data-stu-id="4b365-108">On the **General** page of the **Distributor Properties - \<Distributor>** dialog box, click the properties button (**...**) for the distribution database.</span></span>  
  
2.  <span data-ttu-id="4b365-109">在 **[存放複寫效能記錄至少]** 方塊中輸入值。</span><span class="sxs-lookup"><span data-stu-id="4b365-109">Enter a value in the **Store replication performance history at least** box.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4b365-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b365-110">See Also</span></span>  
 [<span data-ttu-id="4b365-111">設定散發</span><span class="sxs-lookup"><span data-stu-id="4b365-111">Configure Distribution</span></span>](configure-distribution.md)  
  
  
