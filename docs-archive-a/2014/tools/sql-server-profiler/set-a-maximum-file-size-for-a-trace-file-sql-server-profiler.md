---
title: 設定追蹤檔案的檔案大小上限 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- maximum file size for traces
- size [SQL Server], trace files
ms.assetid: e86dc4ce-5aa3-4c0d-acb5-c9e8871ed963
author: stevestein
ms.author: sstein
ms.openlocfilehash: aa990c610f7aa8bf82690c8c201c6643eb712191
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704553"
---
# <a name="set-a-maximum-file-size-for-a-trace-file-sql-server-profiler"></a><span data-ttu-id="e57ce-102">設定追蹤檔案的檔案大小上限 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="e57ce-102">Set a Maximum File Size for a Trace File (SQL Server Profiler)</span></span>
  <span data-ttu-id="e57ce-103">使用下列程序，可設定追蹤檔案的檔案大小上限。</span><span class="sxs-lookup"><span data-stu-id="e57ce-103">Use the following procedure to set the maximum file size for a trace file.</span></span>  
  
### <a name="to-set-a-maximum-file-size-for-a-trace-file"></a><span data-ttu-id="e57ce-104">若要設定追蹤檔的大小上限</span><span class="sxs-lookup"><span data-stu-id="e57ce-104">To set a maximum file size for a trace file</span></span>  
  
1.  <span data-ttu-id="e57ce-105">在 [檔案] 功能表上按一下 [新增追蹤]，然後連接到 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e57ce-105">On the **File** menu, click **New Trace**, and then connect to an instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="e57ce-106">會出現 [追蹤屬性] **[追蹤屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e57ce-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e57ce-107">如果選取 [進行連接後立即啟動追蹤]，將不會顯示 [追蹤屬性] 對話方塊，而是開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="e57ce-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="e57ce-108">於 [工具] 功能表，按一下 [選項]，並清除 [連接後立即啟動追蹤] 核取方塊，以關閉這項設定。</span><span class="sxs-lookup"><span data-stu-id="e57ce-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="e57ce-109">在 **[追蹤名稱]** 方塊中，輸入追蹤的名稱。</span><span class="sxs-lookup"><span data-stu-id="e57ce-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="e57ce-110">在 [範本名稱] 清單中，選取追蹤範本。</span><span class="sxs-lookup"><span data-stu-id="e57ce-110">In the **Template name**list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="e57ce-111">選取 [儲存至檔案]，然後指定要儲存追蹤資訊的檔案。</span><span class="sxs-lookup"><span data-stu-id="e57ce-111">Select **Save to file**, and then specify a file to store the trace information.</span></span>  
  
5.  <span data-ttu-id="e57ce-112">在 [設定最大檔案大小] 核取方塊中，指定追蹤的檔案大小上限。</span><span class="sxs-lookup"><span data-stu-id="e57ce-112">In the **Set maximum file size** check box, specify a maximum file size for the trace.</span></span> <span data-ttu-id="e57ce-113">當檔案的大小到達此上限時，此檔案中便不再記錄追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="e57ce-113">When the file size reaches this maximum, trace events are no longer recorded in this file.</span></span> <span data-ttu-id="e57ce-114">如果選取 [啟用檔案換用] (預設會選取)，將發生下列情況：</span><span class="sxs-lookup"><span data-stu-id="e57ce-114">If you select **Enable file rollover** (which is selected by default),the following occurs:</span></span>  
  
     <span data-ttu-id="e57ce-115">檔案換用選項會使得 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在達到最大檔案大小時，關閉目前的檔案並建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="e57ce-115">The file rollover option causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to close the current file and create a new file when the maximum file size is reached.</span></span> <span data-ttu-id="e57ce-116">新檔與前一個檔案同名，但是名稱後會加上一個整數，以指出其順序；例如，如果原始追蹤檔案名為 filename_1.trc，則下一個追蹤檔案名為 filename_2.trc，依此類推。</span><span class="sxs-lookup"><span data-stu-id="e57ce-116">The new file has the same name as the previous file, but an integer is appended to the name to indicate its sequence; for example, if the original trace file is named filename_1.trc, the next trace file is filename_2.trc, and so on.</span></span> <span data-ttu-id="e57ce-117">如果指派給新換用檔案的名稱已為現有檔案所用，除非現有檔案是唯讀，否則會覆寫現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="e57ce-117">If the name assigned to a new rollover file is already used by an existing file, the existing file is overwritten unless it is read-only.</span></span> <span data-ttu-id="e57ce-118">將追蹤資料儲存至檔案時，會預設啟用檔案復原選項。</span><span class="sxs-lookup"><span data-stu-id="e57ce-118">The file rollover option is enabled by default when you are saving trace data to a file.</span></span>  
  
     <span data-ttu-id="e57ce-119">檔案換用選項開啟時，追蹤會一直繼續，直到被其他方法停止為止。</span><span class="sxs-lookup"><span data-stu-id="e57ce-119">With the file rollover option on, the trace continues until it is stopped by some other means.</span></span> <span data-ttu-id="e57ce-120">若要在您達到檔案大小限制後停止追蹤，請停用檔案換用選項。</span><span class="sxs-lookup"><span data-stu-id="e57ce-120">To stop the trace after you have reached the file size limit, disable the file rollover option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e57ce-121">FAT32 檔案系統的檔案限制為略小於 4 GB。</span><span class="sxs-lookup"><span data-stu-id="e57ce-121">The FAT32 file system limits files to slightly less than 4 gigabytes (GB).</span></span> <span data-ttu-id="e57ce-122">當追蹤檔案到達該大小時，追蹤即失敗，並產生「磁碟空間不足」錯誤。</span><span class="sxs-lookup"><span data-stu-id="e57ce-122">When the trace file reaches that size, the trace fails with the error "Not enough disk space."</span></span> <span data-ttu-id="e57ce-123">若要建立更大的檔案，請使用 NTFS 檔案系統。</span><span class="sxs-lookup"><span data-stu-id="e57ce-123">To create larger files, use the NTFS file system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e57ce-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e57ce-124">See Also</span></span>  
 [<span data-ttu-id="e57ce-125">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="e57ce-125">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
