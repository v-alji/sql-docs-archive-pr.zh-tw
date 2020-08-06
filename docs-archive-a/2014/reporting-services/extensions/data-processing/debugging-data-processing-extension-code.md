---
title: 偵錯資料處理延伸模組程式碼 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- debugging data processing extensions [Reporting Services]
- troubleshooting [Reporting Services], data processing extensions
- data processing extensions [Reporting Services], debugging
ms.assetid: e963e205-9ae0-446d-97df-028a1d2727d9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3bf7490145f91ee8b3cfc2357c34010bed593ed9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594940"
---
# <a name="debugging-data-processing-extension-code"></a><span data-ttu-id="7167b-102">偵錯資料處理延伸模組程式碼</span><span class="sxs-lookup"><span data-stu-id="7167b-102">Debugging Data Processing Extension Code</span></span>
  <span data-ttu-id="7167b-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 提供數個偵錯工具，可協助您分析資料處理延伸模組程式碼，並尋找其中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="7167b-103">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides several debugging tools that can help you analyze your data processing extension code and locate errors in it.</span></span> <span data-ttu-id="7167b-104">效果最好的工具將視您嘗試要完成的項目而定。</span><span class="sxs-lookup"><span data-stu-id="7167b-104">The tool that works best will depend on what you are trying to accomplish.</span></span> <span data-ttu-id="7167b-105">此範例會使用 [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7167b-105">This example uses [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)].</span></span>  
  
#### <a name="to-debug-your-data-processing-extension-code"></a><span data-ttu-id="7167b-106">偵錯資料處理延伸模組程式碼</span><span class="sxs-lookup"><span data-stu-id="7167b-106">To debug your data processing extension code</span></span>  
  
1.  <span data-ttu-id="7167b-107">啟動 [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)]，並開啟您的資料處理延伸模組專案。</span><span class="sxs-lookup"><span data-stu-id="7167b-107">Launch [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)], and open your data processing extension project.</span></span>  
  
2.  <span data-ttu-id="7167b-108">建立專案，然後將資料處理延伸模組組件與隨附的 .pdb 檔案，部署到報表設計師。</span><span class="sxs-lookup"><span data-stu-id="7167b-108">Build the project, and deploy your data processing extension assembly and the accompanying .pdb file to the Report Designer.</span></span> <span data-ttu-id="7167b-109">如需部署的詳細資訊，請參閱[如何：將資料處理延伸模組部署到報表設計師](deploying-a-data-processing-extension-to-report-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="7167b-109">For more information about deployment, see [How to: Deploy a Data Processing Extension to Report Designer](deploying-a-data-processing-extension-to-report-designer.md).</span></span>  
  
3.  <span data-ttu-id="7167b-110">在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中開啟新的 [報表專案]，同時在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 的個別視窗中，將資料處理延伸模組程式碼保持在開啟的狀態。</span><span class="sxs-lookup"><span data-stu-id="7167b-110">Open a new Report Project in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] while leaving your data processing extension code open in a separate window of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>  
  
4.  <span data-ttu-id="7167b-111">導覽到包含資料處理延伸模組專案的 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 視窗，並在程式碼中設定某些中斷點。</span><span class="sxs-lookup"><span data-stu-id="7167b-111">Navigate to the window of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] that contains your data processing extension project and set some break points in your code.</span></span>  
  
5.  <span data-ttu-id="7167b-112">當資料處理延伸模組專案視窗仍為使用中時，按一下 [偵錯] 功能表的 [附加至處理序]。</span><span class="sxs-lookup"><span data-stu-id="7167b-112">With the data processing extension project window still active, click **Attach to Process** on the **Debug** menu.</span></span>  
  
     <span data-ttu-id="7167b-113">[附加至處理序]  對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="7167b-113">The **Attach to Process** dialog opens.</span></span>  
  
6.  <span data-ttu-id="7167b-114">從處理序清單中，選取對應至報表專案的 devenv.exe 處理序，然後按一下 [附加]  。</span><span class="sxs-lookup"><span data-stu-id="7167b-114">From the list of processes, select the devenv.exe process that corresponds to your Report Project and click **Attach**.</span></span>  
  
7.  <span data-ttu-id="7167b-115">您可以使用報表專案的 [報表資料]  索引標籤來定義報表資料來源。</span><span class="sxs-lookup"><span data-stu-id="7167b-115">Define your report data source using the **Report Data** tab of the Report Project.</span></span> <span data-ttu-id="7167b-116">您最有可能使用一般查詢設計工具，以針對自訂資料來源來執行查詢。</span><span class="sxs-lookup"><span data-stu-id="7167b-116">You will most likely use the generic Query Designer to execute a query against your custom data source.</span></span> <span data-ttu-id="7167b-117">這應該會叫用偵錯工具並執行對應至中斷點的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7167b-117">This should invoke the debugger and execute code corresponding to your break points.</span></span>  
  
8.  <span data-ttu-id="7167b-118">使用 F11 鍵逐步執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="7167b-118">Step through your code using the F11 key.</span></span> <span data-ttu-id="7167b-119">如需有關使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 進行偵錯的詳細資訊，請參閱您的 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 文件集。</span><span class="sxs-lookup"><span data-stu-id="7167b-119">For more information about using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] for debugging, see your [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7167b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7167b-120">See Also</span></span>  
 <span data-ttu-id="7167b-121">[部署資料處理延伸模組](deploying-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="7167b-121">[Deploying a Data Processing Extension](deploying-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="7167b-122">[Reporting Services 延伸模組](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="7167b-122">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="7167b-123">[實作資料處理延伸模組](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="7167b-123">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="7167b-124">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="7167b-124">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
