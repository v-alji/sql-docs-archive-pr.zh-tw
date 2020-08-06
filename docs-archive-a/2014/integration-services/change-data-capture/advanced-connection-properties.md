---
title: 進階連線屬性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4edfab68-7e68-45e8-a3f3-a0049ff7eb9e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8dc844d1fdfb1e82f0ffa8de93a6a1060ef190cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597985"
---
# <a name="advanced-connection-properties"></a><span data-ttu-id="be831-102">進階連接屬性</span><span class="sxs-lookup"><span data-stu-id="be831-102">Advanced Connection Properties</span></span>
  <span data-ttu-id="be831-103">使用 **[進階連接屬性]** 對話方塊可在連接字串中加入其他連接參數。</span><span class="sxs-lookup"><span data-stu-id="be831-103">Use the **Advanced Connection Properties** dialog box to add more connection parameters to the connection string.</span></span>  
  
 <span data-ttu-id="be831-104">其他連接參數可以是您使用之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫執行個體所支援的任何 ODBC 連接參數。</span><span class="sxs-lookup"><span data-stu-id="be831-104">The additional connection parameters can be any ODBC connection parameter that is supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database instance you are using.</span></span>  
  
 <span data-ttu-id="be831-105">您使用 **[進階連接屬性]** 對話方塊所加入的參數會加入至 **[連接到 SQL Server]** 對話方塊中所選取的參數。</span><span class="sxs-lookup"><span data-stu-id="be831-105">The parameters added using the **Advanced Connection Properties** dialog box are added to the parameters selected in the **Connect to SQL Server** dialog box.</span></span>  
  
 <span data-ttu-id="be831-106">提供之每一個參數的最後一個執行個體都會覆寫該參數之前的任何執行個體。</span><span class="sxs-lookup"><span data-stu-id="be831-106">The last instance of each parameter provided overrides any previous instances of the parameter.</span></span> <span data-ttu-id="be831-107">使用 **[進階連接參數]** 對話方塊加入的參數會遵循及取代 **[SQL Server 連接]** 對話方塊中所提供的參數。</span><span class="sxs-lookup"><span data-stu-id="be831-107">Parameters added using the **Advanced Connection Parameters** dialog box follow and replace the parameters provided in the **SQL Server Connection** dialog box.</span></span> <span data-ttu-id="be831-108">例如，如果 [SQL Server 連接]  對話方塊指定 SERVER1 當做伺服器名稱，而且 [其他連接參數]  頁面包含 ;SERVER=SERVER2，則會對 SERVER2 進行連接。</span><span class="sxs-lookup"><span data-stu-id="be831-108">For example, if the **SQL Server Connection** dialog box specifies SERVER1 as the Server name, and the **Additional Connection Parameters** page contains ;SERVER=SERVER2, the connection will be made to SERVER2.</span></span>  
  
 <span data-ttu-id="be831-109">使用 **[進階連接屬性]** 對話方塊加入的參數會以純文字格式傳遞。</span><span class="sxs-lookup"><span data-stu-id="be831-109">Parameters added using the **Advanced Connection Properties** dialog box are passed as plain text.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="be831-110">請勿在 **[進階連接屬性]** 對話方塊中包含登入認證。</span><span class="sxs-lookup"><span data-stu-id="be831-110">Do not include login credentials in the **Advanced Connection Properties** dialog box.</span></span> <span data-ttu-id="be831-111">當透過網路傳遞認證和密碼時，將不會加密。</span><span class="sxs-lookup"><span data-stu-id="be831-111">They will not be encrypted when they are passed across the network.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be831-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be831-112">See Also</span></span>  
 <span data-ttu-id="be831-113">[存取 CDC 設計工具主控台](access-the-cdc-designer-console.md) </span><span class="sxs-lookup"><span data-stu-id="be831-113">[Access the CDC Designer Console](access-the-cdc-designer-console.md) </span></span>  
 [<span data-ttu-id="be831-114">用來建立執行個體的 SQL Server 連接</span><span class="sxs-lookup"><span data-stu-id="be831-114">SQL Server Connection for Instance Creation</span></span>](sql-server-connection-for-instance-creation.md)  
  
  
