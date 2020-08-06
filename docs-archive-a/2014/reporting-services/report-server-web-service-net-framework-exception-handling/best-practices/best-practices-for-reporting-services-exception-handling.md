---
title: Reporting Services 例外處理的最佳做法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], best practices
ms.assetid: 72fecf28-f02e-4338-b50f-0b21f520302d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2e0561c19fbd3e709a0440a55f023f938eabf692
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594937"
---
# <a name="best-practices-for-reporting-services-exception-handling"></a><span data-ttu-id="3243b-102">Reporting Services 例外處理的最佳作法</span><span class="sxs-lookup"><span data-stu-id="3243b-102">Best Practices for Reporting Services Exception Handling</span></span>
  <span data-ttu-id="3243b-103">當開發 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 應用程式時，您可以使用幾個方法來消除或是減少例外狀況的發生次數。</span><span class="sxs-lookup"><span data-stu-id="3243b-103">When developing [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] applications, there are several methodologies you can use to eliminate or reduce the occurrence of exceptions.</span></span> <span data-ttu-id="3243b-104">當例外狀況真的發生時，提供明確且精簡的錯誤訊息給使用者，並加入適當的例外狀況處理，以防止應用程式非預期地結束。</span><span class="sxs-lookup"><span data-stu-id="3243b-104">When exceptions do occur, provide clear and concise error messages to the user, and add adequate exception handling to prevent your applications from ending unexpectedly.</span></span>  
  
 <span data-ttu-id="3243b-105">將要求傳送給報表伺服器 Web 服務的應用程式應該執行下列項目：</span><span class="sxs-lookup"><span data-stu-id="3243b-105">An application that sends requests to the Report Server Web service should do the following:</span></span>  
  
-   <span data-ttu-id="3243b-106">透過盡可能防止無效的要求以避免造成例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3243b-106">Avoid causing exceptions by preventing as many invalid requests as possible.</span></span>  
  
-   <span data-ttu-id="3243b-107">盡可能快取例外狀況並提供特定的錯誤處理程式碼。</span><span class="sxs-lookup"><span data-stu-id="3243b-107">Catch exceptions and provide specific error-handling code whenever possible.</span></span>  
  
-   <span data-ttu-id="3243b-108">處理未擲回例外狀況的錯誤案例。</span><span class="sxs-lookup"><span data-stu-id="3243b-108">Deal with error cases that do not throw exceptions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3243b-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="3243b-109">In This Section</span></span>  
  
|<span data-ttu-id="3243b-110">主題</span><span class="sxs-lookup"><span data-stu-id="3243b-110">Topic</span></span>|<span data-ttu-id="3243b-111">描述</span><span class="sxs-lookup"><span data-stu-id="3243b-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3243b-112">防止無效的要求</span><span class="sxs-lookup"><span data-stu-id="3243b-112">Preventing Invalid Requests</span></span>](preventing-invalid-requests.md)|<span data-ttu-id="3243b-113">描述可用以防止將無效的要求傳送到報表伺服器的技術。</span><span class="sxs-lookup"><span data-stu-id="3243b-113">Describes techniques for preventing requests that are not valid from being sent to the report server.</span></span>|  
|[<span data-ttu-id="3243b-114">使用 Try 和 Catch 區塊</span><span class="sxs-lookup"><span data-stu-id="3243b-114">Using Try and Catch Blocks</span></span>](using-try-and-catch-blocks.md)|<span data-ttu-id="3243b-115">描述如何進一步使用 Try/Catch 區塊來增強應用程式的可靠性。</span><span class="sxs-lookup"><span data-stu-id="3243b-115">Describes how to further enhance the reliability of your application with try/catch blocks.</span></span>|  
|[<span data-ttu-id="3243b-116">處理未造成例外狀況的警告與案例</span><span class="sxs-lookup"><span data-stu-id="3243b-116">Handling Warnings and Cases That Do Not Cause Exceptions</span></span>](handling-warnings-and-cases-that-do-not-cause-exceptions.md)|<span data-ttu-id="3243b-117">說明如何處理錯誤才不會造成 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3243b-117">Explains how to handle errors that do not result in an exception being thrown by [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="3243b-118">使用詳細資料屬性來處理特定的錯誤</span><span class="sxs-lookup"><span data-stu-id="3243b-118">Using the Detail Property to Handle Specific Errors</span></span>](using-the-detail-property-to-handle-specific-errors.md)|<span data-ttu-id="3243b-119">說明如何使用 **SoapException** 物件的 **Detail** 屬性，以程式設計的方式處理特定錯誤。</span><span class="sxs-lookup"><span data-stu-id="3243b-119">Explains how to programmatically handle specific errors by using the **Detail** property of the **SoapException** object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3243b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3243b-120">See Also</span></span>  
 <span data-ttu-id="3243b-121">[Detail 屬性](../soapexception-class/detail-property.md) </span><span class="sxs-lookup"><span data-stu-id="3243b-121">[Detail Property](../soapexception-class/detail-property.md) </span></span>  
 <span data-ttu-id="3243b-122">[Reporting Services 中的例外狀況處理簡介](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="3243b-122">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="3243b-123">Reporting Services SoapException 類別</span><span class="sxs-lookup"><span data-stu-id="3243b-123">Reporting Services SoapException Class</span></span>](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
