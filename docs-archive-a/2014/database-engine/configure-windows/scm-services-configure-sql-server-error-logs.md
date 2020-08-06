---
title: 設定 SQL Server 錯誤記錄檔 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.configurelogs.configureerrorlogs.f1
ms.assetid: 03f0d463-9b0b-4af9-a853-da936d75e5af
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8acc27150f42049384e2789ef83ae66a737da9bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607093"
---
# <a name="configure-sql-server-error-logs"></a><span data-ttu-id="0726c-102">設定 SQL Server 錯誤記錄檔</span><span class="sxs-lookup"><span data-stu-id="0726c-102">Configure SQL Server Error Logs</span></span>
  <span data-ttu-id="0726c-103">此主題描述如何檢視或修改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔的回收方式。</span><span class="sxs-lookup"><span data-stu-id="0726c-103">This topic describes how to view or modify the way [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error logs are recycled.</span></span>  
  
## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a><span data-ttu-id="0726c-104">若要開啟 [設定 SQL Server 錯誤記錄檔] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="0726c-104">To open the Configure SQL Server Error Logs dialog box</span></span>  
  
1.  <span data-ttu-id="0726c-105">在 [物件總管] 中展開 SQL Server 執行個體，展開 [管理]，以滑鼠右鍵按一下 [SQL Server 記錄檔]，然後按一下 [設定]。</span><span class="sxs-lookup"><span data-stu-id="0726c-105">In Object Explorer, expand the instance of SQL Server, expand **Management**, right-click **SQL Server Logs**, and then click **Configure**.</span></span>  
  
2.  <span data-ttu-id="0726c-106">在 **[設定 SQL Server 錯誤記錄檔]** 對話方塊中，從下列選項中進行選擇。</span><span class="sxs-lookup"><span data-stu-id="0726c-106">In the **Configure SQL Server Error Logs** dialog box, choose from the following options.</span></span>  
  
     <span data-ttu-id="0726c-107">**限制回收錯誤記錄檔之前，所允許的檔案數目**</span><span class="sxs-lookup"><span data-stu-id="0726c-107">**Limit the number of the error log files before they are recycled**</span></span>  
     <span data-ttu-id="0726c-108">核取進行錯誤記錄檔的回收之前，可建立之錯誤記錄檔的數目。</span><span class="sxs-lookup"><span data-stu-id="0726c-108">Check to limit the number of error logs created before they are recycled.</span></span> <span data-ttu-id="0726c-109">每次啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體，就會建立一個新的錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0726c-109">A new error log is created each time an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0726c-110">會保留前六個記錄檔備份，除非您核取此選項，並在下面另行指定錯誤記錄檔的最大數目。</span><span class="sxs-lookup"><span data-stu-id="0726c-110">retains backups of the previous six logs, unless you check this option, and specify a different maximum number of error log files below.</span></span>  
  
     <span data-ttu-id="0726c-111">**錯誤記錄檔的最大數目**</span><span class="sxs-lookup"><span data-stu-id="0726c-111">**Maximum number of error log files**</span></span>  
     <span data-ttu-id="0726c-112">指定回收之前建立之錯誤記錄檔的最大數目。</span><span class="sxs-lookup"><span data-stu-id="0726c-112">Specify the maximum number of error log files created before they are recycled.</span></span> <span data-ttu-id="0726c-113">預設值是 6，這是回收錯誤記錄檔之前， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 保留的先前備份記錄檔數目。</span><span class="sxs-lookup"><span data-stu-id="0726c-113">The default is 6, which is the number of previous backup logs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retains before recycling them.</span></span>  
  
  
