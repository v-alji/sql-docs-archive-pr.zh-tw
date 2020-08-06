---
title: " (查詢結果和相依性服務頁面的選項) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.DependencyServicesGeneral
ms.assetid: dd7f6c31-7d7f-4972-854a-1419a2826dca
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 356714ee933fb40eda7038f4088309b6187f3ed8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599178"
---
# <a name="options-query-results-and-dependency-services-page"></a>選項 (查詢結果和相依性服務頁面)
  使用此頁面可指定要針對相依性服務連接的伺服器。 相依性服務可讓您擷取在不同伺服器上儲存的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 物件之間的相依性資訊。 您可以使用中的 [**物件**相依性] 對話方塊來查看物件相依性 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 。  
  
 **您想要做什麼事？**  
  
1.  [開啟選項 (查詢結果/相依性服務頁面) 對話方塊](#open_dialog)  
  
2.  [設定選項](#options)  
  
##  <a name="open-the-options-query-resultsdependency-services-page-dialog-box"></a><a name="open_dialog"></a>開啟 (查詢結果/相依性服務頁面) 對話方塊中的選項  
  
1.  在中 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] ，按一下 [**工具**] 功能表上的 [**選項**]。  
  
2.  展開 [查詢結果]****，然後按一下 [相依性服務]****。  
  
##  <a name="configure-the-options"></a><a name="options"></a> 設定選項  
  
### <a name="options"></a>選項。  
 **相依性服務伺服器**  
 指定安裝相依性服務的伺服器。  
  
 **驗證**  
 選取 Windows 驗證來以 Microsoft Windows 使用者帳戶登入，或是選取 SQL Server 驗證。  
  
 當使用者透過不信任連接並指定登入名稱和密碼進行連接時，SQL Server 本身會執行驗證，檢查是否已建立 SQL Server 登入帳戶，而且指定的密碼是否符合先前記錄的密碼。 如果 SQL Server 找不到登入帳戶，驗證將會失敗，而且使用者會收到錯誤訊息。  
  
 **使用者名稱**  
 如果使用 SQL Server 驗證，請提供使用者名稱。  
  
 **密碼**  
 如果使用 SQL Server 驗證，請提供密碼。  
  
 **Test**  
 按一下來測試連接。