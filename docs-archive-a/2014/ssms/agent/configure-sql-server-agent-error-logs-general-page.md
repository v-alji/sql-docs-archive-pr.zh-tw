---
title: 設定 SQL Server Agent 錯誤記錄檔 (一般頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.errorlog.configure.f1
ms.assetid: e08de622-6f87-470c-aee0-b2d6cb6cca88
author: stevestein
ms.author: sstein
ms.openlocfilehash: bd4c083ea7e7d220d5da20594079b7679c0bb724
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597545"
---
# <a name="configure-sql-server-agent-error-logs-general-page"></a><span data-ttu-id="50178-102">設定 SQL Server Agent 錯誤記錄檔 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="50178-102">Configure SQL Server Agent Error Logs (General Page)</span></span>
  <span data-ttu-id="50178-103">使用此畫面來檢視和更新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 錯誤記錄的設定。</span><span class="sxs-lookup"><span data-stu-id="50178-103">Use this screen to view and update settings for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error logging.</span></span>  
  
## <a name="options"></a><span data-ttu-id="50178-104">選項</span><span class="sxs-lookup"><span data-stu-id="50178-104">Options</span></span>  
 <span data-ttu-id="50178-105">**錯誤記錄檔**</span><span class="sxs-lookup"><span data-stu-id="50178-105">**Error log file**</span></span>  
 <span data-ttu-id="50178-106">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 要將錯誤記錄檔寫入的檔案。</span><span class="sxs-lookup"><span data-stu-id="50178-106">Specifies the file to which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent writes error logs.</span></span>  
  
 <span data-ttu-id="50178-107">**...**</span><span class="sxs-lookup"><span data-stu-id="50178-107">**...**</span></span>  
 <span data-ttu-id="50178-108">瀏覽錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="50178-108">Browse to the error log file.</span></span>  
  
 <span data-ttu-id="50178-109">**寫入 OEM 錯誤記錄檔**</span><span class="sxs-lookup"><span data-stu-id="50178-109">**Write OEM error log**</span></span>  
 <span data-ttu-id="50178-110">將錯誤記錄檔寫成非 Unicode 檔案。</span><span class="sxs-lookup"><span data-stu-id="50178-110">Writes the error log file as a non-Unicode file.</span></span> <span data-ttu-id="50178-111">如此可減少記錄檔所用的磁碟空間大小。</span><span class="sxs-lookup"><span data-stu-id="50178-111">This reduces the amount of disk space consumed by the log file.</span></span> <span data-ttu-id="50178-112">不過，啟用此選項時，可能更難以讀取包含 Unicode 資料的訊息。</span><span class="sxs-lookup"><span data-stu-id="50178-112">However, messages that include Unicode data may be more difficult to read when this option is enabled.</span></span>  
  
 <span data-ttu-id="50178-113">**錯誤**</span><span class="sxs-lookup"><span data-stu-id="50178-113">**Errors**</span></span>  
 <span data-ttu-id="50178-114">只將錯誤和參考用訊息寫入記錄檔。</span><span class="sxs-lookup"><span data-stu-id="50178-114">Writes only errors and informational messages to the log file.</span></span>  
  
 <span data-ttu-id="50178-115">**警告**</span><span class="sxs-lookup"><span data-stu-id="50178-115">**Warnings**</span></span>  
 <span data-ttu-id="50178-116">只將警告和參考用訊息寫入記錄檔。</span><span class="sxs-lookup"><span data-stu-id="50178-116">Writes only warnings and informational messages to the log file.</span></span>  
  
 <span data-ttu-id="50178-117">**資訊**</span><span class="sxs-lookup"><span data-stu-id="50178-117">**Information**</span></span>  
 <span data-ttu-id="50178-118">只將參考用訊息寫入記錄檔。</span><span class="sxs-lookup"><span data-stu-id="50178-118">Writes only informational messages to the log file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50178-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50178-119">See Also</span></span>  
 [<span data-ttu-id="50178-120">SQL Server Agent 錯誤記錄檔</span><span class="sxs-lookup"><span data-stu-id="50178-120">SQL Server Agent Error Log</span></span>](sql-server-agent-error-log.md)  
  
  
