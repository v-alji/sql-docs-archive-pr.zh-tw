---
title: 作業屬性：新增作業 (通知頁面) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.notifications.f1
ms.assetid: ed393cbd-4496-4399-a177-e5baa92fb689
author: stevestein
ms.author: sstein
ms.openlocfilehash: 30eca88943b48bd81bd38e236711d19ee7ec4503
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585746"
---
# <a name="job-properties-new-job-notifications-page"></a><span data-ttu-id="bd49e-102">作業屬性：新增作業 (通知頁面)</span><span class="sxs-lookup"><span data-stu-id="bd49e-102">Job Properties: New Job (Notifications Page)</span></span>
  <span data-ttu-id="bd49e-103">使用此頁面來設定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 當作業完成時，Agent 要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="bd49e-103">Use this page to set actions for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform when the job completes.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bd49e-104">選項</span><span class="sxs-lookup"><span data-stu-id="bd49e-104">Options</span></span>  
 <span data-ttu-id="bd49e-105">**位址**</span><span class="sxs-lookup"><span data-stu-id="bd49e-105">**E-mail**</span></span>  
 <span data-ttu-id="bd49e-106">選取此選項，即可在作業完成時傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="bd49e-106">Select this option to send e-mail when the job completes.</span></span> <span data-ttu-id="bd49e-107">選取此選項之後，請選擇要通知的操作員及觸發通知的條件：[當作業成功時]\*\*\*\*、[當作業失敗時]\*\*\*\* 或 [作業完成時]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd49e-107">After selecting this option, choose the operator to notify and the condition that will trigger the notification: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
 <span data-ttu-id="bd49e-108">**頁面**</span><span class="sxs-lookup"><span data-stu-id="bd49e-108">**Page**</span></span>  
 <span data-ttu-id="bd49e-109">選取此選項，即可在作業完成時將電子郵件傳送給操作員的呼叫器。</span><span class="sxs-lookup"><span data-stu-id="bd49e-109">Select this option to send e-mail to an operator's pager when the job completes.</span></span> <span data-ttu-id="bd49e-110">選取此選項之後，請指定要通知的操作員及觸發通知的條件：[當作業成功時]\*\*\*\*、[當作業失敗時]\*\*\*\* 或 [作業完成時]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd49e-110">After selecting this option, specify the operator to notify and the condition that will trigger the notification: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
 <span data-ttu-id="bd49e-111">**Net send**</span><span class="sxs-lookup"><span data-stu-id="bd49e-111">**Net send**</span></span>  
 <span data-ttu-id="bd49e-112">選取此選項，即可在作業完成時使用 Net Send 來通知操作員。</span><span class="sxs-lookup"><span data-stu-id="bd49e-112">Select this option to use net send to notify an operator when the job completes.</span></span> <span data-ttu-id="bd49e-113">選取此選項之後，請指定要通知的操作員及觸發通知的條件：[當作業成功時]\*\*\*\*、[當作業失敗時]\*\*\*\* 或 [作業完成時]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd49e-113">After selecting this option, specify the operator to notify and the condition that will trigger the notification: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
 <span data-ttu-id="bd49e-114">**寫入 Windwos 應用程式事件記錄**</span><span class="sxs-lookup"><span data-stu-id="bd49e-114">**Write to the Windows Application event log**</span></span>  
 <span data-ttu-id="bd49e-115">選取此選項，即可在作業完成時將項目寫入應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="bd49e-115">Select this option to write an entry in the application event log when the job completes.</span></span> <span data-ttu-id="bd49e-116">選取此選項之後，請指定寫入項目時的條件：[當作業成功時]\*\*\*\*、[當作業失敗時]\*\*\*\* 或 [作業完成時]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd49e-116">After selecting this option, specify the condition that will cause the entry to be written: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
 <span data-ttu-id="bd49e-117">**自動刪除作業**</span><span class="sxs-lookup"><span data-stu-id="bd49e-117">**Automatically delete job**</span></span>  
 <span data-ttu-id="bd49e-118">選取此選項，即可在作業完成時刪除作業。</span><span class="sxs-lookup"><span data-stu-id="bd49e-118">Select this option to delete the job when the job completes.</span></span> <span data-ttu-id="bd49e-119">選取此選項之後，請指定觸發刪除作業的條件：[當作業成功時]\*\*\*\*、[當作業失敗時]\*\*\*\* 或 [作業完成時]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd49e-119">After selecting this option, specify the condition that will trigger deletion of the job: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd49e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd49e-120">See Also</span></span>  
 <span data-ttu-id="bd49e-121">[實作作業](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="bd49e-121">[Implement Jobs](implement-jobs.md) </span></span>  
 [<span data-ttu-id="bd49e-122">設定 SQL Server Agent Mail 使用 Database Mail</span><span class="sxs-lookup"><span data-stu-id="bd49e-122">Configure SQL Server Agent Mail to Use Database Mail</span></span>](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
  
  
