---
title: 設定警示呼叫器號碼的格式 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- pager addresses [SQL Server]
- SQL Server Agent, alerts
- formats [SQL Server], pager addresses
- pager notifications [SQL Server]
- addresses [SQL Server]
- alerts [SQL Server], pager addresses
ms.assetid: a9797d01-1050-442c-9038-ed4bfee1e76a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 471f9a4958f51491b312d89239a2204c907e25e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584958"
---
# <a name="format-pager-addresses-for-alerts"></a><span data-ttu-id="b249b-102">設定警示的呼叫器位址格式</span><span class="sxs-lookup"><span data-stu-id="b249b-102">Format Pager Addresses for Alerts</span></span>
  <span data-ttu-id="b249b-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或，在中格式化 Agent 警示的呼機位址 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b249b-103">This topic describes how to format pager addresses for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="b249b-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="b249b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b249b-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="b249b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b249b-106">安全性</span><span class="sxs-lookup"><span data-stu-id="b249b-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b249b-107">**若要使用下列項目，格式化呼叫器號碼：**</span><span class="sxs-lookup"><span data-stu-id="b249b-107">**To format pager addresses, using:**</span></span>  
  
     [<span data-ttu-id="b249b-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b249b-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b249b-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="b249b-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b249b-110">Security</span><span class="sxs-lookup"><span data-stu-id="b249b-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b249b-111">權限</span><span class="sxs-lookup"><span data-stu-id="b249b-111">Permissions</span></span>  
 <span data-ttu-id="b249b-112">依預設， **系統管理員 (sysadmin)** 固定伺服器角色的成員可以檢視警示的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b249b-112">By default, members of the **sysadmin** fixed server role can view information about an alert.</span></span> <span data-ttu-id="b249b-113">其他使用者必須被授與 **msdb** 資料庫的 **SQLAgentOperatorRole** 固定資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="b249b-113">Other users must be granted the **SQLAgentOperatorRole** fixed database role in the **msdb** database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b249b-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b249b-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-format-pager-addresses"></a><span data-ttu-id="b249b-115">若要格式化呼叫器號碼</span><span class="sxs-lookup"><span data-stu-id="b249b-115">To format pager addresses</span></span>  
  
1.  <span data-ttu-id="b249b-116">在 **[物件總管]** 中，按一下加號展開伺服器，此伺服器包含要傳送至呼叫器的警示。</span><span class="sxs-lookup"><span data-stu-id="b249b-116">In **Object Explorer**, click the plus sign to expand the server that contains the alert that you want to send to a pager.</span></span>  
  
2.  <span data-ttu-id="b249b-117">以滑鼠右鍵按一下 [SQL Server Agent]\*\*\*\*，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b249b-117">Right-click **SQL Server Agent** and select **Properties**</span></span>  
  
3.  <span data-ttu-id="b249b-118">在 **[選取頁面]** 底下，選取 **[警示系統]**。</span><span class="sxs-lookup"><span data-stu-id="b249b-118">Under **Select a page**, select **Alert System**.</span></span>  
  
4.  <span data-ttu-id="b249b-119">在 [呼叫器電子郵件位址格式]\*\*\*\* 欄位的 [收件者]\*\*\*\* 和 [副本]\*\*\*\* 方塊中，輸入呼叫器號碼的前置詞和後置詞。</span><span class="sxs-lookup"><span data-stu-id="b249b-119">In the **To line** and **CC line** boxes of the **Address formatting for pager e-mails** field, enter the pager address prefix or suffix.</span></span> <span data-ttu-id="b249b-120">當傳送通知時，就會插入操作員的實際呼叫器號碼。</span><span class="sxs-lookup"><span data-stu-id="b249b-120">The operator's actual pager address is inserted when a notification is sent.</span></span>  
  
5.  <span data-ttu-id="b249b-121">在 **[主旨]** 方塊中，輸入主旨行前置詞或後置詞。</span><span class="sxs-lookup"><span data-stu-id="b249b-121">In the **Subject** box, enter the subject line prefix or suffix.</span></span>  
  
6.  <span data-ttu-id="b249b-122">選取 [將電子郵件的內文包含在通知訊息中]\*\*\*\* 核取方塊，表示會在呼叫器訊息中加入完整的電子郵件訊息 (而不是僅有主旨行)。</span><span class="sxs-lookup"><span data-stu-id="b249b-122">Select the **Include body of e-mail in notification page** check box to include the full e-mail message with the pager message (as opposed to the subject line only).</span></span>  
  
7.  <span data-ttu-id="b249b-123">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="b249b-123">When finished, click **OK**.</span></span>  
  
  
