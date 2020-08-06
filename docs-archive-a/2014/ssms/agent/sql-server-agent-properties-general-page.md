---
title: SQL Server Agent 屬性 (一般頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.general.f1
ms.assetid: b51601e9-5454-43c6-bb5e-24eb2ff043c8
author: stevestein
ms.author: sstein
ms.openlocfilehash: a67d5431be4025c18b11d6791b016fa83e957810
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599309"
---
# <a name="sql-server-agent-properties-general-page"></a><span data-ttu-id="d7ac2-102">SQL Server Agent 屬性 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="d7ac2-102">SQL Server Agent Properties (General Page)</span></span>
  <span data-ttu-id="d7ac2-103">使用此頁面來查看和修改 Agent 服務的一般屬性 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d7ac2-103">Use this page to view and modify the general properties of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d7ac2-104">選項</span><span class="sxs-lookup"><span data-stu-id="d7ac2-104">Options</span></span>  
 <span data-ttu-id="d7ac2-105">**服務狀態**</span><span class="sxs-lookup"><span data-stu-id="d7ac2-105">**Service state**</span></span>  
 <span data-ttu-id="d7ac2-106">顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="d7ac2-106">Displays the current state of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
 <span data-ttu-id="d7ac2-107">**如果 SQL Server 非預期地停止，則自動予以重新啟動**</span><span class="sxs-lookup"><span data-stu-id="d7ac2-107">**Auto restart SQL Server if it stops unexpectedly**</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d7ac2-108">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 非預期地停止，Agent 就會重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d7ac2-108">Agent restarts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stops unexpectedly.</span></span>  
  
 <span data-ttu-id="d7ac2-109">**如果 SQL Server Agent 非預期地停止，則自動予以重新啟動**</span><span class="sxs-lookup"><span data-stu-id="d7ac2-109">**Auto restart SQL Server Agent if it stops unexpectedly**</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d7ac2-110">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 非預期地停止，就會重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent。</span><span class="sxs-lookup"><span data-stu-id="d7ac2-110">restarts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent stops unexpectedly.</span></span>  
  
 <span data-ttu-id="d7ac2-111">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="d7ac2-111">**Filename**</span></span>  
 <span data-ttu-id="d7ac2-112">指定錯誤記錄檔的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d7ac2-112">Specify the file name for the error log.</span></span>  
  
 <span data-ttu-id="d7ac2-113">**...**</span><span class="sxs-lookup"><span data-stu-id="d7ac2-113">**...**</span></span>  
 <span data-ttu-id="d7ac2-114">瀏覽錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="d7ac2-114">Browse to the error log file.</span></span>  
  
 <span data-ttu-id="d7ac2-115">**包含執行追蹤訊息**</span><span class="sxs-lookup"><span data-stu-id="d7ac2-115">**Include execution trace messages**</span></span>  
 <span data-ttu-id="d7ac2-116">在錯誤記錄檔中包含執行追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="d7ac2-116">Includes execution trace messages in the error log.</span></span> <span data-ttu-id="d7ac2-117">追蹤訊息提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d7ac2-117">Trace messages provide detailed information on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operation.</span></span> <span data-ttu-id="d7ac2-118">因此，選取此選項時，記錄檔需要更多磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="d7ac2-118">Therefore, the log file requires more disk space when this option is selected.</span></span> <span data-ttu-id="d7ac2-119">只有在疑難排解與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 相關的問題時，才應該選取此選項。</span><span class="sxs-lookup"><span data-stu-id="d7ac2-119">This option should only be selected while troubleshooting a problem that may involve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
 <span data-ttu-id="d7ac2-120">**寫入 OEM 檔**</span><span class="sxs-lookup"><span data-stu-id="d7ac2-120">**Write OEM file**</span></span>  
 <span data-ttu-id="d7ac2-121">將錯誤記錄檔寫成非 Unicode 檔案。</span><span class="sxs-lookup"><span data-stu-id="d7ac2-121">Writes the error log file as a non-Unicode file.</span></span> <span data-ttu-id="d7ac2-122">如此可減少記錄檔所用的磁碟空間大小。</span><span class="sxs-lookup"><span data-stu-id="d7ac2-122">This reduces the amount of disk space consumed by the log file.</span></span> <span data-ttu-id="d7ac2-123">不過，啟用此選項時，可能更難以讀取包含 Unicode 資料的訊息。</span><span class="sxs-lookup"><span data-stu-id="d7ac2-123">However, messages that include Unicode data may be more difficult to read when this option is enabled.</span></span>  
  
 <span data-ttu-id="d7ac2-124">**Net Send 收件者**</span><span class="sxs-lookup"><span data-stu-id="d7ac2-124">**Net send recipient**</span></span>  
 <span data-ttu-id="d7ac2-125">鍵入接收 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 寫入記錄檔之訊息的 Net Send 通知的操作員名稱。</span><span class="sxs-lookup"><span data-stu-id="d7ac2-125">Type the name of an operator to receive net send notification of messages that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent writes to the log file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7ac2-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7ac2-126">See Also</span></span>  
 <span data-ttu-id="d7ac2-127">[人員](operators.md) </span><span class="sxs-lookup"><span data-stu-id="d7ac2-127">[Operators](operators.md) </span></span>  
 [<span data-ttu-id="d7ac2-128">SQL Server Agent 錯誤記錄檔</span><span class="sxs-lookup"><span data-stu-id="d7ac2-128">SQL Server Agent Error Log</span></span>](sql-server-agent-error-log.md)  
  
  
