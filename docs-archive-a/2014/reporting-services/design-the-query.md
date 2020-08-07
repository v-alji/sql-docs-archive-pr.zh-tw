---
title: 設計查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.designquery.f1
ms.assetid: 2dad800f-10a1-453c-8761-2935b9826d84
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9b56d99ec11b50ce53ef223a01eb5fc2766238ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703926"
---
# <a name="design-the-query"></a>設計查詢
  使用報表精靈的這個頁面，即可透過手動輸入查詢、使用查詢產生器以互動方式建立查詢或從其他報表匯入查詢，藉以建立查詢。  
  
 您在 [選取資料來源] 頁面 (報表精靈中之前的頁面) 上所選擇的資料來源類型會決定您可以在這個頁面上輸入的查詢。 例如，如果資料來源類型為 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，您可以輸入 [!INCLUDE[tsql](../includes/tsql-md.md)] 語句或預存程式名稱。 如果資料來源類型為 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，則 [查詢] 窗格會停用，而且您無法直接輸入查詢。 您可以使用「查詢產生器」來指定查詢。  
  
## <a name="options"></a>選項。  
 **查詢字串**  
 輸入查詢，以擷取要在報表中使用的資料。  
  
 **查詢產生器**  
 按一下 [查詢產生器]**** 即可為資料來源開啟查詢設計工具，或從其他報表匯入查詢。  
  
 如需有關查詢設計工具的詳細資訊，請參閱＜ [Reporting Services Query Designers](../../2014/reporting-services/reporting-services-query-designers.md)＞。  
  
## <a name="example"></a>範例  
 針對**Microsoft SQL Server**的資料來源類型，下列查詢會從資料庫資料表中抓取姓氏清單 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] `Person` 。  
  
```  
SELECT LastName FROM Person.Person;  
```  
  
 針對**Microsoft SQL Server**的資料來源類型，下列查詢會 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] `uspGetEmployeeManagers` 針對識別碼為1的員工執行預存程式：  
  
```  
EXEC uspgetEmployeeManagers '1';  
```  
  
## <a name="see-also"></a>另請參閱  
 [報表精靈說明](../../2014/reporting-services/report-wizard-help.md)   
 [報表內嵌資料集和共用資料集 &#40;報表產生器和 SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [將資料加入報表 &#40;報表產生器和 SSRS&#41;](report-data/report-datasets-ssrs.md)  
  
  
