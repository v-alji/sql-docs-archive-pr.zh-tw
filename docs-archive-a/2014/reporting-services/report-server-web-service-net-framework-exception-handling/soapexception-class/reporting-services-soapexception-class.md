---
title: Reporting Services SoapException 類別 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], SoapException class
- SoapException class
ms.assetid: 2cec49ee-20b1-40eb-a75b-0908d9c05b34
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6f6efdfac89014116957990ef2db21cf52e76a4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699310"
---
# <a name="reporting-services-soapexception-class"></a><span data-ttu-id="ecb2f-102">Reporting Services SoapException 類別</span><span class="sxs-lookup"><span data-stu-id="ecb2f-102">Reporting Services SoapException Class</span></span>
  <span data-ttu-id="ecb2f-103">您應該處理可能會發生的特定 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 錯誤。</span><span class="sxs-lookup"><span data-stu-id="ecb2f-103">You should address specific [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] errors that you know might happen.</span></span> <span data-ttu-id="ecb2f-104">例如，在您詢問使用者是否建立資料夾的應用程式中，使用者或許會嘗試建立已經存在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ecb2f-104">For example, in an application where you ask the user to create a folder, it might be possible for the user to try to create a folder that already exists.</span></span> <span data-ttu-id="ecb2f-105">身為開發人員，您無法控制使用者在應用程式的資料夾名稱與路徑欄位中輸入的內容，但是，您卻可以控制使用者在試圖建立已經存在的項目時所得到的體驗。</span><span class="sxs-lookup"><span data-stu-id="ecb2f-105">As the developer, you do not have control over what the user enters in the folder name and path fields of your application, but you do have control over what the user experience is when someone incidentally tries to create an item that already exists.</span></span>  
  
 <span data-ttu-id="ecb2f-106">為了使您更易於捕捉特定的錯誤狀況，[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 會對例外狀況的錯誤碼進行分類，並使用 **SoapException** 類別的屬性傳回錯誤的分類。</span><span class="sxs-lookup"><span data-stu-id="ecb2f-106">To make it easier for you to catch specific error conditions, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] classifies an error code for the exception and returns the classification of the error using properties from the **SoapException** class.</span></span> <span data-ttu-id="ecb2f-107">如需詳細資訊，請參閱 SDK 檔中的「SoapException 類別」 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ecb2f-107">For more information, see "SoapException Class" in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
 <span data-ttu-id="ecb2f-108">下表列出 **SoapException** 類別的公用屬性。</span><span class="sxs-lookup"><span data-stu-id="ecb2f-108">The following table lists the public properties of the **SoapException** class.</span></span>  
  
|<span data-ttu-id="ecb2f-109">公用屬性</span><span class="sxs-lookup"><span data-stu-id="ecb2f-109">Public property</span></span>|<span data-ttu-id="ecb2f-110">描述</span><span class="sxs-lookup"><span data-stu-id="ecb2f-110">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="ecb2f-111">**演員**</span><span class="sxs-lookup"><span data-stu-id="ecb2f-111">**Actor**</span></span>|<span data-ttu-id="ecb2f-112">造成例外狀況的程式碼，</span><span class="sxs-lookup"><span data-stu-id="ecb2f-112">The code that caused the exception.</span></span> <span data-ttu-id="ecb2f-113">這個值是 Web 服務方法的 URL。</span><span class="sxs-lookup"><span data-stu-id="ecb2f-113">The value is the URL to the Web service method.</span></span>|  
|<span data-ttu-id="ecb2f-114">**詳細資料**</span><span class="sxs-lookup"><span data-stu-id="ecb2f-114">**Detail**</span></span>|<span data-ttu-id="ecb2f-115">應用程式特定的錯誤資訊，</span><span class="sxs-lookup"><span data-stu-id="ecb2f-115">Application-specific error information.</span></span> <span data-ttu-id="ecb2f-116">這個值是由報表伺服器所設定，且格式為 XML。</span><span class="sxs-lookup"><span data-stu-id="ecb2f-116">The value is set by the report server and is in XML format.</span></span> <span data-ttu-id="ecb2f-117">如需詳細資訊，請參閱 [Detail 屬性](detail-property.md)和[使用 Detail 屬性處理特定的錯誤](../best-practices/using-the-detail-property-to-handle-specific-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="ecb2f-117">For more information, see [Detail Property](detail-property.md) and [Using the Detail Property to Handle Specific Errors](../best-practices/using-the-detail-property-to-handle-specific-errors.md).</span></span>|  
|<span data-ttu-id="ecb2f-118">**HelpLink**</span><span class="sxs-lookup"><span data-stu-id="ecb2f-118">**HelpLink**</span></span>|<span data-ttu-id="ecb2f-119">與該錯誤相關聯的說明檔之 URL 或 URN。</span><span class="sxs-lookup"><span data-stu-id="ecb2f-119">A URL or URN to a Help file associated with the error.</span></span> <span data-ttu-id="ecb2f-120">這個值通常是由 Web 服務所設定，而且它會將 URL 設定為 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 說明與支援。</span><span class="sxs-lookup"><span data-stu-id="ecb2f-120">The value is usually set by the Web service and it sets a URL to [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Help and Support.</span></span> <span data-ttu-id="ecb2f-121">因為 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 對於所發生的錯誤支援多個說明連結，所以報表伺服器會將說明連結資訊設定為 **Detail** 屬性的一部分。</span><span class="sxs-lookup"><span data-stu-id="ecb2f-121">Because [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] supports multiple help links for errors that occur, the report server sets help link information as part of the **Detail** property.</span></span> <span data-ttu-id="ecb2f-122">如需詳細資訊，請參閱 [HelpLink 項目](helplink-element.md)。</span><span class="sxs-lookup"><span data-stu-id="ecb2f-122">For more information, see [HelpLink Element](helplink-element.md).</span></span>|  
|<span data-ttu-id="ecb2f-123">**Message**</span><span class="sxs-lookup"><span data-stu-id="ecb2f-123">**Message**</span></span>|<span data-ttu-id="ecb2f-124">描述錯誤的當地語系化描述性訊息。</span><span class="sxs-lookup"><span data-stu-id="ecb2f-124">A descriptive, localized message that describes the error.</span></span> <span data-ttu-id="ecb2f-125">此文字可能會出現在應用程式 UI 中。</span><span class="sxs-lookup"><span data-stu-id="ecb2f-125">This text might appear in the application UI.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ecb2f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecb2f-126">See Also</span></span>  
 <span data-ttu-id="ecb2f-127">[Reporting Services 中的例外狀況處理簡介](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="ecb2f-127">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="ecb2f-128">SoapException 錯誤資料表</span><span class="sxs-lookup"><span data-stu-id="ecb2f-128">SoapException Errors Table</span></span>](soapexception-errors-table.md)  
  
  
