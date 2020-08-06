---
title: 取消隱藏執行自訂報表警告 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 0deed900-c910-4d12-aac0-6ab9e39eb068
author: stevestein
ms.author: sstein
ms.openlocfilehash: 725362ff7f8a6c282529f652e8813a8083257eb8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686734"
---
# <a name="unsuppress-run-custom-report-warnings"></a><span data-ttu-id="51f3d-102">取消隱藏執行自訂報表警告</span><span class="sxs-lookup"><span data-stu-id="51f3d-102">Unsuppress Run Custom Report Warnings</span></span>
  <span data-ttu-id="51f3d-103">自訂報表有兩個警告對話方塊。</span><span class="sxs-lookup"><span data-stu-id="51f3d-103">There are two warning dialog boxes for custom reports.</span></span> <span data-ttu-id="51f3d-104">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中取消隱藏這些方塊的顯示。</span><span class="sxs-lookup"><span data-stu-id="51f3d-104">This topic describes how to unsuppress the display of these boxes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="51f3d-105">根據預設，[執行自訂報表]  對話方塊會在自訂報表執行之前顯示。</span><span class="sxs-lookup"><span data-stu-id="51f3d-105">By default, the **Run Custom Reports** dialog box appears before a custom report runs.</span></span> <span data-ttu-id="51f3d-106">如果您選取了 [請不要再顯示這個警告]  核取方塊，將不再顯示此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="51f3d-106">If you select the **Please don't show this warning again** check box, the dialog box will no longer appear.</span></span> <span data-ttu-id="51f3d-107">此外，根據預設，當您開啟自訂報表，然後按一下連結來開啟另一份自訂報表時，就會顯示 [執行自訂報表]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="51f3d-107">Also by default, the **Run Custom Reports** dialog box appears when you open a custom report and then click a link to open another custom report.</span></span> <span data-ttu-id="51f3d-108">此對話方塊會顯示鑽研自訂報表檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="51f3d-108">This dialog box displays the fill path to the drill-through custom report file.</span></span> <span data-ttu-id="51f3d-109">如果您選取了 [請不要再顯示這個警告]  核取方塊，將不再顯示此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="51f3d-109">If you select the **Please don't show this warning again** check box, the dialog box will no longer appear.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="51f3d-110">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="51f3d-110">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-unsuppress-the-main-custom-report-warning-dialog-box"></a><span data-ttu-id="51f3d-111">取消隱藏主要自訂報表警告對話方塊</span><span class="sxs-lookup"><span data-stu-id="51f3d-111">To unsuppress the main custom report warning dialog box</span></span>  
  
1.  <span data-ttu-id="51f3d-112">連接至 \<*Server*> \\ < *共用* >| \<*Drive*> \Documents 和設定 \\<UserProfile \> \Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml。</span><span class="sxs-lookup"><span data-stu-id="51f3d-112">Connect to \<*Server*>\\<*Share*>|\<*Drive*>\Documents and Settings\\<UserProfile\>\Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml.</span></span>  
  
2.  <span data-ttu-id="51f3d-113">按一下滑鼠右鍵 `reports.xml` ，然後按一下 [**編輯**]。</span><span class="sxs-lookup"><span data-stu-id="51f3d-113">Right-click `reports.xml`, and then click **Edit**.</span></span>  
  
3.  <span data-ttu-id="51f3d-114">將\*\* \<SuppressWarning> true \</SuppressWarning> 變更 \<SuppressWarning> 為 \</SuppressWarning> false\*\*。</span><span class="sxs-lookup"><span data-stu-id="51f3d-114">Change**\<SuppressWarning>true\</SuppressWarning> to \<SuppressWarning>false\</SuppressWarning>**.</span></span>  
  
4.  <span data-ttu-id="51f3d-115">重新啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="51f3d-115">Restart [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-unsuppress-the-drill-through-custom-report-warning-dialog-box"></a><span data-ttu-id="51f3d-116">取消隱藏鑽研自訂報表警告對話方塊</span><span class="sxs-lookup"><span data-stu-id="51f3d-116">To unsuppress the drill-through custom report warning dialog box</span></span>  
  
1.  <span data-ttu-id="51f3d-117">連接至 \<*Server*> \\ < *共用* >| \<*Drive*> \Documents 和設定 \\<UserProfile \> \Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml。</span><span class="sxs-lookup"><span data-stu-id="51f3d-117">Connect to \<*Server*>\\<*Share*>|\<*Drive*>\Documents and Settings\\<UserProfile\>\Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml.</span></span>  
  
2.  <span data-ttu-id="51f3d-118">按一下滑鼠右鍵 `reports.xml` ，然後按一下 [**編輯**]。</span><span class="sxs-lookup"><span data-stu-id="51f3d-118">Right-click `reports.xml`, and click **Edit**.</span></span>  
  
3.  <span data-ttu-id="51f3d-119">將\*\* \<SuppressDrillthroughWarning> true \</SuppressDrillthroughWarning> 變更 \<SuppressDrillthroughWarning> 為 \</SuppressDrillthroughWarning> false\*\*。</span><span class="sxs-lookup"><span data-stu-id="51f3d-119">Change **\<SuppressDrillthroughWarning>true\</SuppressDrillthroughWarning>to \<SuppressDrillthroughWarning>false\</SuppressDrillthroughWarning>**.</span></span>  
  
4.  <span data-ttu-id="51f3d-120">重新啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="51f3d-120">Restart [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51f3d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51f3d-121">See Also</span></span>  
 <span data-ttu-id="51f3d-122">[Management Studio 中的自訂報表](custom-reports-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="51f3d-122">[Custom Reports in Management Studio](custom-reports-in-management-studio.md) </span></span>  
 <span data-ttu-id="51f3d-123">[將自訂報表加入至 Management Studio](add-a-custom-report-to-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="51f3d-123">[Add a Custom Report to Management Studio](add-a-custom-report-to-management-studio.md) </span></span>  
 [<span data-ttu-id="51f3d-124">使用自訂報表搭配物件總管節點屬性</span><span class="sxs-lookup"><span data-stu-id="51f3d-124">Use Custom Reports with Object Explorer Node Properties</span></span>](use-custom-reports-with-object-explorer-node-properties.md)  
  
  
