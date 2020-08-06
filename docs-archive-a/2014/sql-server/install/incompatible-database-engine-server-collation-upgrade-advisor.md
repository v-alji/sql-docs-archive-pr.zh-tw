---
title: 資料庫引擎伺服器定序不相容 (Upgrade Advisor) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 80f499d6-2c90-49eb-a5b3-0bb5b7faaa3b
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b6ce0555bdf5a878e56d87a8bd55b5ce6c4b2649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606032"
---
# <a name="incompatible-database-engine-server-collation-upgrade-advisor"></a>不相容的 Database Engine 伺服器定序 (Upgrade Advisor)
  Upgrade Advisor 偵測到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 使用的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 設定為使用不相容的伺服器定序。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 模式。|  
  
## <a name="component"></a>元件  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>描述  
 Upgrade Advisor 偵測到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 使用的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 設定為使用不相容的伺服器定序。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Sharepoint 模式會利用 sharepoint 共用服務架構。 SharePoint 不支援針對區分大小寫或是伺服器定序或二進位伺服器定序設定的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]。 不相容的定序包括預設為區分大小寫或二進位的定序，以及預設不相容，但已透過下列任一定序指示項設定的基底定序：  
  
-   **二進位**  
  
-   **區分大小寫**  
  
-   **二進位字碼指標**  
  
 由於目前的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 伺服器定序不相容，因此升級遭到封鎖。  
  
## <a name="corrective-action"></a>更正動作  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 伺服器定序屬性無法變更。 您將無法完成 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的升級。 您需要將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝移轉至使用相容伺服器定序的新伺服器。 如需詳細資訊，請參閱下列：  
  
-   [升級和移轉 Reporting Services](https://go.microsoft.com/fwlink/?LinkId=233227)  
  
-   [選取 SQL Server 定序](https://go.microsoft.com/fwlink/?LinkId=233226)  
  
  
