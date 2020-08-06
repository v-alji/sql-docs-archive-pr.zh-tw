---
title: 偵錯傳遞延伸模組程式碼 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], debugging
- debugging delivery extensions [Reporting Services]
- troubleshooting [Reporting Services], delivery extensions
ms.assetid: a7d959da-5005-4a50-aca7-2cef36aa9947
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fb80ac97f5c0e346b208784f1fa5b857ff93ef57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708922"
---
# <a name="debugging-delivery-extension-code"></a><span data-ttu-id="3d828-102">偵錯傳遞延伸模組程式碼</span><span class="sxs-lookup"><span data-stu-id="3d828-102">Debugging Delivery Extension Code</span></span>
  <span data-ttu-id="3d828-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 提供數個偵錯工具，可協助您分析傳遞延伸模組程式碼並尋找其中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="3d828-103">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides several debugging tools that can help you analyze your delivery extension code and locate errors in it.</span></span> <span data-ttu-id="3d828-104">效果最好的工具將視您嘗試要完成的項目而定。</span><span class="sxs-lookup"><span data-stu-id="3d828-104">The tool that works best will depend on what you are trying to accomplish.</span></span> <span data-ttu-id="3d828-105">此範例會使用 [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3d828-105">This example uses [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)].</span></span>  
  
#### <a name="to-debug-your-delivery-extension-code"></a><span data-ttu-id="3d828-106">偵錯傳遞延伸模組程式碼</span><span class="sxs-lookup"><span data-stu-id="3d828-106">To debug your delivery extension code</span></span>  
  
1.  <span data-ttu-id="3d828-107">啟動 [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)]，並開啟您的傳遞延伸模組專案。</span><span class="sxs-lookup"><span data-stu-id="3d828-107">Launch [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] and open your delivery extension project.</span></span>  
  
2.  <span data-ttu-id="3d828-108">建立專案，然後將傳遞延伸模組組件與隨附的 .pdb 檔案，部署到報表伺服器與報表管理員。</span><span class="sxs-lookup"><span data-stu-id="3d828-108">Build the project and deploy your delivery extension assembly and the accompanying .pdb file to the report server and Report Manager.</span></span> <span data-ttu-id="3d828-109">如需部署的詳細資訊，請參閱[部署傳遞延伸模組](deploying-a-delivery-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="3d828-109">For more information about deployment, see [Deploying a Delivery Extension](deploying-a-delivery-extension.md).</span></span>  
  
3.  <span data-ttu-id="3d828-110">如果您已撰寫訂閱使用者介面以擴充報表管理員，請開啟 Internet Explorer 並導覽至報表管理員，同時在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中將傳遞延伸模組程式碼保持為開啟的狀態。</span><span class="sxs-lookup"><span data-stu-id="3d828-110">If you have written a subscription user interface to extend Report Manager, open Internet Explorer and navigate to Report Manager while leaving your delivery extension code open in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="3d828-111">如果您沒有為報表管理員部署訂閱使用者介面，請直接開啟用戶端應用程式，並從這個應用程式中，呼叫使用 SOAP API 的傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="3d828-111">If you do not have a subscription user interface deployed for Report Manager, simply open the client application from which you call your delivery extension using the SOAP API.</span></span>  
  
4.  <span data-ttu-id="3d828-112">導覽至 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 與您的傳遞延伸模組專案，並在程式碼中設定某些中斷點。</span><span class="sxs-lookup"><span data-stu-id="3d828-112">Navigate to [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] and your delivery extension project, and set some break points in your code.</span></span>  
  
5.  <span data-ttu-id="3d828-113">當傳遞延伸模組專案仍為使用中視窗時，按一下 [偵錯] 功能表的 [附加至處理序]。</span><span class="sxs-lookup"><span data-stu-id="3d828-113">With the delivery extension project still the active window, click **Attach to Process** on the **Debug** menu.</span></span>  
  
     <span data-ttu-id="3d828-114">[附加至處理序]  對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="3d828-114">The **Attach to Process** dialog opens.</span></span>  
  
6.  <span data-ttu-id="3d828-115">從處理序清單中，選取 aspnet_wp.exe 處理序 (或者，如果在 IIS 6.0 上部署應用程式則選取 w3wp.exe)，然後按一下 [附加]  。</span><span class="sxs-lookup"><span data-stu-id="3d828-115">From the list of processes, select the aspnet_wp.exe process (or w3wp.exe if your application is deployed on IIS 6.0), and click **Attach**.</span></span>  
  
7.  <span data-ttu-id="3d828-116">使用您的傳遞延伸模組定義新的訂閱。</span><span class="sxs-lookup"><span data-stu-id="3d828-116">Define a new subscription using your delivery extension.</span></span> <span data-ttu-id="3d828-117">您很可能會使用報表管理員或是 SOAP API。</span><span class="sxs-lookup"><span data-stu-id="3d828-117">You will most likely use Report Manager or the SOAP API.</span></span> <span data-ttu-id="3d828-118">這應該會叫用偵錯工具並執行對應至中斷點的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3d828-118">This should invoke the debugger and execute code corresponding to your break points.</span></span>  
  
8.  <span data-ttu-id="3d828-119">使用 **F11** 鍵逐步執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="3d828-119">Step through your code using the **F11** key.</span></span> <span data-ttu-id="3d828-120">如需有關使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 進行偵錯的詳細資訊，請參閱您的 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 文件集。</span><span class="sxs-lookup"><span data-stu-id="3d828-120">For more information about using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] for debugging, see your [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d828-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d828-121">See Also</span></span>  
 <span data-ttu-id="3d828-122">[實作傳遞延伸模組](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="3d828-122">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="3d828-123">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="3d828-123">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
