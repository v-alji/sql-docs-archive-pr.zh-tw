---
title: 改善追蹤資料的存取 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], space
- SQL Server Profiler, space
- space [SQL Server], SQL Server Profiler
ms.assetid: c260c000-fd53-4831-993f-df6894f3228b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60e01ad04ddd9f7fe6d858c399abb552716f2bea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688697"
---
# <a name="improve-access-to-trace-data"></a><span data-ttu-id="1192d-102">改善追蹤資料的存取</span><span class="sxs-lookup"><span data-stu-id="1192d-102">Improve Access to Trace Data</span></span>
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="1192d-103">會使用 **temp** 目錄中的空間，來改進追蹤資料的存取。</span><span class="sxs-lookup"><span data-stu-id="1192d-103">uses space in the **temp** directory to improve access to trace data.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="1192d-104">需要至少 10 MB 的可用空間。</span><span class="sxs-lookup"><span data-stu-id="1192d-104">requires at least 10 megabytes (MB) of free space.</span></span> <span data-ttu-id="1192d-105">如果您使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]時，可用空間在 10 MB 以下，所有 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 功能都會停止運作。</span><span class="sxs-lookup"><span data-stu-id="1192d-105">If free space drops below 10 MB while you are using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], all [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] functions stop.</span></span>  
  
 <span data-ttu-id="1192d-106">當 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 使用 **temp** 目錄中的空間，這個空間用法可能會使 **temp** 目錄快速成長。</span><span class="sxs-lookup"><span data-stu-id="1192d-106">When [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] uses space in the **temp** directory, this space usage may cause the **temp** directory to grow rapidly.</span></span> <span data-ttu-id="1192d-107">為了避免發生檔案成長問題，您可以變更 TEMP 環境變數值，將 **temp** 目錄放在非系統磁碟機中。</span><span class="sxs-lookup"><span data-stu-id="1192d-107">To avoid file-growth problems, you can place the **temp** directory on a drive that is not a system drive by changing the value for the TEMP environment variable.</span></span>  
  
 <span data-ttu-id="1192d-108">下列程序說明如何在 Microsoft Windows 作業系統中，變更 TEMP 環境變數值。</span><span class="sxs-lookup"><span data-stu-id="1192d-108">The following procedure describes how to change the value for the TEMP environment variable in most Microsoft Windows operating systems.</span></span> <span data-ttu-id="1192d-109">如需有關設定環境變數的詳細資訊，請參閱您的 Windows 作業系統文件。</span><span class="sxs-lookup"><span data-stu-id="1192d-109">For more information about setting environment variables, see your Windows operating system documentation.</span></span>  
  
### <a name="to-change-the-temp-environment-variable-in-windows-operating-systems"></a><span data-ttu-id="1192d-110">在 Windows 作業系統中變更 TEMP 環境變數</span><span class="sxs-lookup"><span data-stu-id="1192d-110">To change the TEMP environment variable in Windows operating systems</span></span>  
  
1.  <span data-ttu-id="1192d-111">在 [開始]  功能表上，選擇 [控制台]  ，然後按一下 [系統]  。</span><span class="sxs-lookup"><span data-stu-id="1192d-111">On the **Start** menu, choose **Control Panel**, and then click **System**.</span></span>  
  
2.  <span data-ttu-id="1192d-112">在 [系統內容]  對話方塊中，按一下 [進階]  索引標籤，然後按一下 [環境變數]  。</span><span class="sxs-lookup"><span data-stu-id="1192d-112">In the **System Properties** dialog box, click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
3.  <span data-ttu-id="1192d-113">向下捲動 [系統變數]  清單，選取對應於 **TEMP** 變數的資料列，然後按一下 [編輯]  。</span><span class="sxs-lookup"><span data-stu-id="1192d-113">Scroll down the list of **System Variables**, select the row that corresponds to the **TEMP** variable, and click **Edit**.</span></span>  
  
4.  <span data-ttu-id="1192d-114">在 [編輯系統變數]  對話方塊中，輸入 **temp** 目錄要放在其中之磁碟機和目錄的路徑與名稱。</span><span class="sxs-lookup"><span data-stu-id="1192d-114">In the **Edit System Variable** dialog box, enter the path and name of the drive and directory where you want the **temp** directory to be located.</span></span>  
  
5.  <span data-ttu-id="1192d-115">按一下 [確定]  來儲存變更。</span><span class="sxs-lookup"><span data-stu-id="1192d-115">Click **OK** to save the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1192d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1192d-116">See Also</span></span>  
 <span data-ttu-id="1192d-117">[啟動 SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="1192d-117">[Start SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="1192d-118">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="1192d-118">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
