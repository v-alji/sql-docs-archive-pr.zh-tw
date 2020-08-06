---
title: ATOM 裝置資訊設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fe4a56a4-5552-423c-85c1-895e2e212fee
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bdbac1500063accf868d4b538b82ba9f3b5aebb0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595819"
---
# <a name="atom-device-information-settings"></a><span data-ttu-id="41c7b-102">ATOM 裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="41c7b-102">ATOM Device Information Settings</span></span>
  <span data-ttu-id="41c7b-103">Atom 轉譯延伸模組的裝置資訊設定支援提交 Atom 摘要名稱以及要使用的字元編碼。</span><span class="sxs-lookup"><span data-stu-id="41c7b-103">The device information settings for the Atom rendering extension support submittal of the name of an Atom feed and character encoding to use.</span></span>  
  
 <span data-ttu-id="41c7b-104">下表列出用來轉譯至資料服務文件的裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="41c7b-104">The following table lists the device information settings for rendering to a data service document.</span></span>  
  
|<span data-ttu-id="41c7b-105">設定</span><span class="sxs-lookup"><span data-stu-id="41c7b-105">Setting</span></span>|<span data-ttu-id="41c7b-106">值</span><span class="sxs-lookup"><span data-stu-id="41c7b-106">Value</span></span>|  
|-------------|-----------|  
|`DataFeed`|<span data-ttu-id="41c7b-107">如果指定這個設定，則會轉譯對應到此設定中所提供之摘要名稱的 Atom 摘要。</span><span class="sxs-lookup"><span data-stu-id="41c7b-107">If specified, renders the Atom feed corresponding to the feed name provided in this setting.</span></span> <span data-ttu-id="41c7b-108">如果不指定的話，則會轉譯報表的 Atom 服務文件。</span><span class="sxs-lookup"><span data-stu-id="41c7b-108">If not, renders the Atom service document for the report.</span></span> <span data-ttu-id="41c7b-109">資料摘要的唯一自動產生的識別碼。</span><span class="sxs-lookup"><span data-stu-id="41c7b-109">The unique auto-generated identifier of the data feed.</span></span> <span data-ttu-id="41c7b-110">這個值是在內部使用，您不應該變更它。</span><span class="sxs-lookup"><span data-stu-id="41c7b-110">This  value is used internally and you should not change it.</span></span>|  
|<span data-ttu-id="41c7b-111">**編碼**</span><span class="sxs-lookup"><span data-stu-id="41c7b-111">**Encoding**</span></span>|<span data-ttu-id="41c7b-112">.NET Framework 所支援之字元編碼方式的 Internet Assigned Numbers Authority (IANA) 名稱。</span><span class="sxs-lookup"><span data-stu-id="41c7b-112">The Internet Assigned Numbers Authority (IANA) name of a character encoding that is supported by the .NET Framework.</span></span> <span data-ttu-id="41c7b-113">預設值是 `UTF-8`。</span><span class="sxs-lookup"><span data-stu-id="41c7b-113">The default value is `UTF-8`.</span></span> <span data-ttu-id="41c7b-114">其他值的範例包括 ASCII、UTF-7 和 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="41c7b-114">Examples of other values include ASCII, UTF-7, and UTF-16.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41c7b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41c7b-115">See Also</span></span>  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 <span data-ttu-id="41c7b-116">[將裝置資訊設定傳遞至轉譯延伸模組](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="41c7b-116">[Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span></span>  
 <span data-ttu-id="41c7b-117">[在 RSReportServer.Config中自訂轉譯延伸模組參數](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="41c7b-117">[Customize Rendering Extension Parameters in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="41c7b-118">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="41c7b-118">Technical Reference &#40;SSRS&#41;</span></span>](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
