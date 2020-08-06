---
title: 瞭解用來建立部署腳本的輸入檔 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- Analysis Services Deployment Wizard, scripts
- deploying [Analysis Services], input files
- Analysis Services Deployment Wizard, input files
- scripts [Analysis Services], deployment
- Analysis Services deployments, input files
- modifying input files
ms.assetid: 20e080cd-6a0e-4591-b022-ea4cd3638e36
author: minewiskan
ms.author: owend
ms.openlocfilehash: 34695993d4f153c6c0b97fef744d92c682517c99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596380"
---
# <a name="understanding-the-input-files-used-to-create-the-deployment-script"></a>了解用來建立部署指令碼的輸入檔
  當您建立 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案時，會 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 為專案產生 XML 檔案。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 會將這些 XML 檔案放置在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案的輸出資料夾中。 依預設，輸出是放在 \Bin 資料夾中。 下表列出 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 建立的 XML 檔案。  
  
|XMLA 檔案|描述|  
|---------------|-----------------|  
|\<*project name*>. .asdatabase|包含專案中所有 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件的宣告式定義。|  
|\<*project name*>. .deploymenttargets|包含將建立 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體和資料庫的名稱。|  
|\<*project name*>. .configsettings|包含環境特定設定，例如資料來源連接資訊和物件儲存位置。 此檔案中的設定會覆寫 .asdatabase 檔案中的設定 \<*project name*> 。|  
|\<*project name*>. d|包含部署選項，例如部署是否為交易式，以及部署之後是否應處理部署的物件。|  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 絕不會將密碼儲存在專案檔中。  
  
## <a name="modifying-the-input-files"></a>修改輸入檔  
 修改輸入檔中的值，或從輸入檔中抓取的值，可讓您變更部署目的地、設定設定和部署選項，而不需要編輯整個 (.asdatabase 檔案，而是 \<*project name*> 從現有的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫) 產生腳本。 您可以修改個別的檔案，以輕鬆地針對各種用途建立不同的部署指令碼。  
  
 下列主題說明如何修改各種輸入檔中的值：  
  
-   [指定安裝目標](deployment-script-files-specifying-the-installation-target.md)  
  
-   [指定資料分割和角色部署選項](deployment-script-files-partition-and-role-deployment-options.md)  
  
-   [指定方案部署的組態設定](deployment-script-files-solution-deployment-config-settings.md)  
  
-   [指定處理選項](deployment-script-files-specifying-processing-options.md)  
  
## <a name="see-also"></a>另請參閱  
 [執行 Analysis Services 部署嚮導](running-the-analysis-services-deployment-wizard.md)   
 [了解 Analysis Services 部署指令碼](understanding-the-analysis-services-deployment-script.md)  
  
  
