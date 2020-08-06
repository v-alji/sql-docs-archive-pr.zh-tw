---
title: Excel 連線管理員編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelconnection.f1
helpviewer_keywords:
- Excel Connection Manager Editor
ms.assetid: 7ff097e4-cafb-4885-a898-05b2a46628c1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7f66de13b710e5ccb577e6f2d67c215572e34767
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596803"
---
# <a name="excel-connection-manager-editor"></a>Excel 連接管理員編輯器
  使用 [Excel 連線管理員編輯器]**** 對話方塊，將連接加入現有或新的 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 活頁簿檔案。  
  
 若要深入了解快取連線管理員，請參閱 [Excel 連線管理員](connection-manager/excel-connection-manager.md)。  
  
> [!NOTE]  
>  您不能連接到受密碼保護的 Excel 檔案。  
  
## <a name="options"></a>選項  
 **Excel 檔案路徑**  
 輸入現有或新的 Excel 活頁簿檔案 (.xls) 的路徑和檔案名稱。  
  
> [!WARNING]  
>  當您選取指向新的/不存在檔案的**Excel 連接**，然後針對**Excel 工作表的 [名稱**] 按一下 [**新增**] 時，[ **Excel 目的地編輯器**] 會自動建立 excel 檔案。  
  
 **瀏覽**  
 使用 [**開啟**] 對話方塊，即可流覽至 excel 檔案所在的資料夾，或您要建立新檔案的位置。  
  
 **Excel 版本**  
 指定用於建立檔案的 Microsoft Excel 版本。  
  
|選項|描述|  
|------------|-----------------|  
|Excel 97-2003|檔案是使用 Excel 97 或更新版本建立的。|  
|Excel 3。0|檔案是使用 Excel 3.0 所建立。|  
|Excel 4。0|檔案是使用 Excel 4.0 建立的。|  
|Excel 5。0|檔案是使用 Excel 95 (7.0) 建立的。|  
  
 **第一個資料列有資料行名稱**  
 指定選取之工作表中資料的第一個資料列是否包含資料行名稱。 此選項的預設值是 **[True]**。  
  
## <a name="see-also"></a>另請參閱  
 [Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [使用 Foreach 迴圈容器來執行 Excel 檔案和資料表迴圈](control-flow/foreach-loop-container.md)  
  
  
