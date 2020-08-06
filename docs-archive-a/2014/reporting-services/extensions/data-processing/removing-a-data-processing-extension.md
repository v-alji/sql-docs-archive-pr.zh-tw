---
title: 移除資料處理延伸模組 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deleting data processing extensions
- data processing extensions [Reporting Services], removing
- removing data processing extensions
ms.assetid: 1d89e32b-0631-44f6-8178-a57fb791d26d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9f5dfd3a6a7615fa3fd91c917bba6dbf0808f0f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708945"
---
# <a name="removing-a-data-processing-extension"></a><span data-ttu-id="0a9f9-102">移除資料處理延伸模組</span><span class="sxs-lookup"><span data-stu-id="0a9f9-102">Removing a Data Processing Extension</span></span>
  <span data-ttu-id="0a9f9-103">若要移除資料處理延伸模組，請直接從設定檔移除資料處理延伸模組的 **Extension** 項目。</span><span class="sxs-lookup"><span data-stu-id="0a9f9-103">To remove a data processing extension, simply remove the **Extension** element for your data processing extension from the configuration file.</span></span> <span data-ttu-id="0a9f9-104">如果您已經為報表伺服器以及報表設計師建立項目，請從 RSReportServer.config 與 RSReportDesigner.config 檔案移除 **Extension** 項目。</span><span class="sxs-lookup"><span data-stu-id="0a9f9-104">If you made entries for a report server as well as Report Designer, remove the **Extension** element from both the RSReportServer.config and RSReportDesigner.config files.</span></span> <span data-ttu-id="0a9f9-105">在移除組態資訊之後，資料處理延伸模組將無法再供元件使用。</span><span class="sxs-lookup"><span data-stu-id="0a9f9-105">After the configuration information is removed, the data processing extension is no longer available to the component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a9f9-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a9f9-106">See Also</span></span>  
 <span data-ttu-id="0a9f9-107">[Reporting Services 延伸模組](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="0a9f9-107">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="0a9f9-108">[執行資料處理延伸模組](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="0a9f9-108">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="0a9f9-109">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="0a9f9-109">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
