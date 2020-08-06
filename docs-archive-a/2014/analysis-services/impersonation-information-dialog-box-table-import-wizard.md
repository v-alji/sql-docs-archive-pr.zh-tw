---
title: '[模擬資訊] 對話方塊 (資料表匯入 Wizard) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.impersonationinfo.f1
ms.assetid: bee7eee5-0650-41f1-a372-5076ae97a58c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5300f8b6106a7f29f51018b4e039c2a8c28aa729
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687329"
---
# <a name="impersonation-information-dialog-box-table-import-wizard"></a>模擬資訊對話方塊 (資料表匯入精靈)
  使用 **[模擬資訊]** 頁面可指定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 將用來連接資料來源的認證。 如需有關認證模擬的詳細資訊，請參閱[&#40;SSAS 表格式&#41;](tabular-models/impersonation-ssas-tabular.md)的模擬。  
  
## <a name="options"></a>選項  
 **特定的 Windows 使用者名稱和密碼**  
 選取此選項，可讓表格式模型使用指定之 Windows 使用者帳戶的安全性認證。  
  
 **使用者名稱**  
 輸入要使用之使用者帳戶的網域和名稱。 請使用下列格式：  
  
 *\<Domain name>* **\\** *\<User account name>*  
  
 唯有選取 **[使用特定的使用者名稱和密碼]** 之後，才會啟用此選項。  
  
 **密碼**  
 輸入表格式模型所要使用之使用者帳戶的密碼。  
  
 唯有選取 **[使用特定的使用者名稱和密碼]** 之後，才會啟用此選項。  
  
 **服務帳戶**  
 選取此選項，可使用與管理模型之 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服務相關聯的安全性認證。  
  
## <a name="see-also"></a>另請參閱  
 [模擬 &#40;SSAS 表格式&#41;](tabular-models/impersonation-ssas-tabular.md)  
  
  
