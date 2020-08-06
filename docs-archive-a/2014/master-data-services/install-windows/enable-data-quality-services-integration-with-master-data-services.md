---
title: 啟用 Data Quality Services 與 Master Data Services 的整合 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ab32938d-a80e-4106-80d4-94b2de3d67dc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8d2fa25254cae2a129b6e08ff657d92af4ff9455
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594119"
---
# <a name="enable-data-quality-services-integration-with-master-data-services"></a>啟用 Data Quality Services 與 Master Data Services 的整合
  在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，比對功能是由 Data Quality Services (DQS) 提供。 此功能必須啟用才能使用。  
  
## <a name="prerequisites"></a>Prerequisites  
  
-   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web 應用程式和資料庫必須存在。  
  
-   Data Quality Services 功能和 Data Quality Client 必須安裝在裝載 MDS 資料庫的相同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上。 如需詳細資訊，請參閱 [安裝 Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)。  
  
### <a name="to-enable-data-quality-services-integration"></a>若要啟用 Data Quality Services 整合  
  
1.  開啟 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。  
  
2.  按一下左窗格中的 **[Web 組態]** 。  
  
3.  在 [Web 組態]**** 頁面上，選取網站和 Web 應用程式。  
  
4.  在 [啟用 DQS 整合]**** 區段中，按一下 [啟用與 Data Quality Services 整合]****。  
  
5.  在確認對話方塊中按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [適用于 Excel 的 MDS 增益集中的資料品質比對](../microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [適用於 Microsoft Excel 的 Master Data Services 增益集](../microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)   
 [安裝 Master Data Services](install-master-data-services.md)  
  
  
