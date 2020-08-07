---
title: 詳細資料屬性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Detail property
- SoapException class
ms.assetid: c1ddaeb6-c540-49fa-b06e-b6359d377ee8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 060fbaba2b8d4f5a5171e8aa7995432622ba2ba0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703830"
---
# <a name="detail-property"></a><span data-ttu-id="4992b-102">詳細資料屬性</span><span class="sxs-lookup"><span data-stu-id="4992b-102">Detail Property</span></span>
  <span data-ttu-id="4992b-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] **SoapException** 類別的 **Detail** 屬性具有下列 XML 結構：</span><span class="sxs-lookup"><span data-stu-id="4992b-103">The **Detail** property of the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] **SoapException** class has the following XML structure:</span></span>  
  
## <a name="elements"></a><span data-ttu-id="4992b-104">元素</span><span class="sxs-lookup"><span data-stu-id="4992b-104">Elements</span></span>  
 <span data-ttu-id="4992b-105">**詳細資料**</span><span class="sxs-lookup"><span data-stu-id="4992b-105">**Detail**</span></span>  
 <span data-ttu-id="4992b-106">包含所有其他錯誤詳細資料元素的上層元素。</span><span class="sxs-lookup"><span data-stu-id="4992b-106">The top-level element that contains all other error detail elements.</span></span>  
  
 <span data-ttu-id="4992b-107">**ErrorCode**</span><span class="sxs-lookup"><span data-stu-id="4992b-107">**ErrorCode**</span></span>  
 <span data-ttu-id="4992b-108">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 特定的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="4992b-108">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-specific error code.</span></span>  
  
 <span data-ttu-id="4992b-109">**HttpStatus**</span><span class="sxs-lookup"><span data-stu-id="4992b-109">**HttpStatus**</span></span>  
 <span data-ttu-id="4992b-110">HTTP 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="4992b-110">The HTTP status code.</span></span>  
  
 <span data-ttu-id="4992b-111">**Message**</span><span class="sxs-lookup"><span data-stu-id="4992b-111">**Message**</span></span>  
 <span data-ttu-id="4992b-112">報表伺服器指派的錯誤訊息與錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="4992b-112">The error message and the error code assigned by the report server.</span></span>  
  
 <span data-ttu-id="4992b-113">**HelpLink**</span><span class="sxs-lookup"><span data-stu-id="4992b-113">**HelpLink**</span></span>  
 <span data-ttu-id="4992b-114">網站的說明連結 URL，在此可以找到有關錯誤的進一步資訊。</span><span class="sxs-lookup"><span data-stu-id="4992b-114">The Help link URL to a Web site at which further information about the error can be found.</span></span> <span data-ttu-id="4992b-115">如需詳細資訊，請參閱 [HelpLink 項目](helplink-element.md)。</span><span class="sxs-lookup"><span data-stu-id="4992b-115">For more information, see [HelpLink Element](helplink-element.md).</span></span>  
  
 <span data-ttu-id="4992b-116">**LinkID**</span><span class="sxs-lookup"><span data-stu-id="4992b-116">**LinkID**</span></span>  
 <span data-ttu-id="4992b-117">指派給該連結的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4992b-117">The ID assigned to the link.</span></span>  
  
 <span data-ttu-id="4992b-118">**ProductName**</span><span class="sxs-lookup"><span data-stu-id="4992b-118">**ProductName**</span></span>  
 <span data-ttu-id="4992b-119">產品的名稱。</span><span class="sxs-lookup"><span data-stu-id="4992b-119">The name of the product.</span></span> <span data-ttu-id="4992b-120">預設值是 **Microsoft SQL Server Reporting Services**。</span><span class="sxs-lookup"><span data-stu-id="4992b-120">The default value is **Microsoft SQL Server Reporting Services**.</span></span>  
  
 <span data-ttu-id="4992b-121">**ProductVersion**</span><span class="sxs-lookup"><span data-stu-id="4992b-121">**ProductVersion**</span></span>  
 <span data-ttu-id="4992b-122">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 的版本。</span><span class="sxs-lookup"><span data-stu-id="4992b-122">The version of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="4992b-123">最大長度是 15 個字元。</span><span class="sxs-lookup"><span data-stu-id="4992b-123">The maximum length is 15 characters.</span></span> <span data-ttu-id="4992b-124">版本號碼的格式應該會如下所示：8.00.0xxx.00。</span><span class="sxs-lookup"><span data-stu-id="4992b-124">The format of the version number should be as follows: 8.00.0xxx.00.</span></span>  
  
 <span data-ttu-id="4992b-125">**ProductLocaleId**</span><span class="sxs-lookup"><span data-stu-id="4992b-125">**ProductLocaleId**</span></span>  
 <span data-ttu-id="4992b-126">應用程式的 INTL DLL 之地區設定識別碼或語言識別碼 (例如，0x41A)。</span><span class="sxs-lookup"><span data-stu-id="4992b-126">The locale ID or language ID of the application's INTL DLL (for example, 0x41A).</span></span>  
  
 <span data-ttu-id="4992b-127">**OperatingSystem**</span><span class="sxs-lookup"><span data-stu-id="4992b-127">**OperatingSystem**</span></span>  
 <span data-ttu-id="4992b-128">已安裝 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 的作業系統。</span><span class="sxs-lookup"><span data-stu-id="4992b-128">The operating system [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is installed on.</span></span> <span data-ttu-id="4992b-129">與作業系統無關時，有效值為 **0**，[!INCLUDE[win2kfamily](../../../includes/win2kfamily-md.md)] 為 **1**，而 Windows XP 則為 **16**。</span><span class="sxs-lookup"><span data-stu-id="4992b-129">Valid values include **0** for operating system independent, **1** for [!INCLUDE[win2kfamily](../../../includes/win2kfamily-md.md)], and **16** for Windows XP.</span></span>  
  
 <span data-ttu-id="4992b-130">**CountryLocaleId**</span><span class="sxs-lookup"><span data-stu-id="4992b-130">**CountryLocaleId**</span></span>  
 <span data-ttu-id="4992b-131">作業系統的地區設定識別碼或是語言識別碼。</span><span class="sxs-lookup"><span data-stu-id="4992b-131">The locale ID or language ID of the operating system.</span></span> <span data-ttu-id="4992b-132">例如，Windows 法文版本的值為 0x040c。</span><span class="sxs-lookup"><span data-stu-id="4992b-132">For example, the value for the French version of Windows is 0x040c.</span></span>  
  
 <span data-ttu-id="4992b-133">**MoreInformation**</span><span class="sxs-lookup"><span data-stu-id="4992b-133">**MoreInformation**</span></span>  
 <span data-ttu-id="4992b-134">包含執行方法時所發生之巢狀運算式的 XML 字串。</span><span class="sxs-lookup"><span data-stu-id="4992b-134">An XML string that contains nested exceptions that occurred while the method ran.</span></span>  
  
 <span data-ttu-id="4992b-135">**Source**</span><span class="sxs-lookup"><span data-stu-id="4992b-135">**Source**</span></span>  
 <span data-ttu-id="4992b-136">**MoreInformation** 的子項目。</span><span class="sxs-lookup"><span data-stu-id="4992b-136">A child element of **MoreInformation**.</span></span> <span data-ttu-id="4992b-137">錯誤的來源。</span><span class="sxs-lookup"><span data-stu-id="4992b-137">The source of the error.</span></span>  
  
 <span data-ttu-id="4992b-138">**Message**</span><span class="sxs-lookup"><span data-stu-id="4992b-138">**Message**</span></span>  
 <span data-ttu-id="4992b-139">**MoreInformation** 的子項目。</span><span class="sxs-lookup"><span data-stu-id="4992b-139">A child element of **MoreInformation**.</span></span> <span data-ttu-id="4992b-140">巢狀例外狀況的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="4992b-140">The error message of a nested exception.</span></span> <span data-ttu-id="4992b-141">這個項目包括 **ErrorCode** 與 **HelpLink** 的 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="4992b-141">This element includes XML attributes for **ErrorCode** and **HelpLink**.</span></span>  
  
 <span data-ttu-id="4992b-142">**警告**</span><span class="sxs-lookup"><span data-stu-id="4992b-142">**Warnings**</span></span>  
 <span data-ttu-id="4992b-143">包含從報表處理傳回之警告的 XML 字串。</span><span class="sxs-lookup"><span data-stu-id="4992b-143">An XML string that contains the warnings returned from report processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4992b-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4992b-144">See Also</span></span>  
 <span data-ttu-id="4992b-145">[Reporting Services 中的例外狀況處理簡介](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="4992b-145">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 <span data-ttu-id="4992b-146">[Reporting Services SoapException 類別](reporting-services-soapexception-class.md) </span><span class="sxs-lookup"><span data-stu-id="4992b-146">[Reporting Services SoapException Class](reporting-services-soapexception-class.md) </span></span>  
 [<span data-ttu-id="4992b-147">使用詳細資料屬性來處理特定的錯誤</span><span class="sxs-lookup"><span data-stu-id="4992b-147">Using the Detail Property to Handle Specific Errors</span></span>](../best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
