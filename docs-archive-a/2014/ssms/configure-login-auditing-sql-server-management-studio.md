---
title: 設定登入稽核 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], logins
- logins [SQL Server], auditing
ms.assetid: 16961116-57ac-4eef-8037-791b26ade548
author: stevestein
ms.author: sstein
ms.openlocfilehash: b7e05f6c254e098a67a5ce00435c009cd450af44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606552"
---
# <a name="configure-login-auditing-sql-server-management-studio"></a><span data-ttu-id="5c896-102">設定登入稽核 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5c896-102">Configure Login Auditing (SQL Server Management Studio)</span></span>
  <span data-ttu-id="5c896-103">此主題描述如何在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 中設定登入稽核，以監視 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 登入活動。</span><span class="sxs-lookup"><span data-stu-id="5c896-103">This topic describes how to configure login auditing in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] to monitor [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] login activity.</span></span> <span data-ttu-id="5c896-104">可設定登入稽核，針對以下事件寫入錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="5c896-104">Login auditing can be configured to write to the error log on the following events.</span></span>  
  
-   <span data-ttu-id="5c896-105">失敗的登入</span><span class="sxs-lookup"><span data-stu-id="5c896-105">Failed logins</span></span>  
  
-   <span data-ttu-id="5c896-106">成功的登入</span><span class="sxs-lookup"><span data-stu-id="5c896-106">Successful logins</span></span>  
  
-   <span data-ttu-id="5c896-107">失敗和成功的登入</span><span class="sxs-lookup"><span data-stu-id="5c896-107">Both failed and successful logins</span></span>  
  
 <span data-ttu-id="5c896-108">您必須重新啟動 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，這個選項才會生效。</span><span class="sxs-lookup"><span data-stu-id="5c896-108">You must restart [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] before this option will take effect.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5c896-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5c896-109">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-login-auditing"></a><span data-ttu-id="5c896-110">若要設定登入稽核</span><span class="sxs-lookup"><span data-stu-id="5c896-110">To configure login auditing</span></span>  
  
1.  <span data-ttu-id="5c896-111">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中，使用 [物件總管] 連接到 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5c896-111">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connect to an instance of the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] with Object Explorer.</span></span>  
  
2.  <span data-ttu-id="5c896-112">在物件總管中，以滑鼠右鍵按一下伺服器名稱，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="5c896-112">In Object Explorer, right-click the server name, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="5c896-113">在 [安全性]  頁面的 [登入稽核]  底下，按一下所需的選項並關閉 [伺服器屬性]  頁面。</span><span class="sxs-lookup"><span data-stu-id="5c896-113">On the **Security** page, under **Login** auditing, click the desired option and close the **Server Properties** page.</span></span>  
  
4.  <span data-ttu-id="5c896-114">在物件總管中，以滑鼠右鍵按一下伺服器名稱，然後按一下 [重新啟動]  。</span><span class="sxs-lookup"><span data-stu-id="5c896-114">In Object Explorer, right-click the server name, and then click **Restart**.</span></span>  
  
  
