---
title: rsModelGenerationError - Reporting Services 錯誤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsModelGenerationError
ms.assetid: 3a0ad63f-87f9-4ca1-b0c2-c85fa991634a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 713de57f0f2957983966f8ef0345bb374c311781
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596459"
---
# <a name="rsmodelgenerationerror---reporting-services-error"></a><span data-ttu-id="ac15b-102">rsModelGenerationError - Reporting Services 錯誤</span><span class="sxs-lookup"><span data-stu-id="ac15b-102">rsModelGenerationError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="ac15b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ac15b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ac15b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ac15b-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="ac15b-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ac15b-105">Event ID</span></span>|<span data-ttu-id="ac15b-106">rsRenderingError</span><span class="sxs-lookup"><span data-stu-id="ac15b-106">rsRenderingError</span></span>|  
|<span data-ttu-id="ac15b-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="ac15b-107">Event Source</span></span>|<span data-ttu-id="ac15b-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span><span class="sxs-lookup"><span data-stu-id="ac15b-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span></span>|  
|<span data-ttu-id="ac15b-109">元件</span><span class="sxs-lookup"><span data-stu-id="ac15b-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="ac15b-110">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ac15b-110">Message Text</span></span>|<span data-ttu-id="ac15b-111">產生模型時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="ac15b-111">An error occurred while generating model.</span></span> <span data-ttu-id="ac15b-112">(rsModelGenerationError) (ReportingServicesLibrary) %1</span><span class="sxs-lookup"><span data-stu-id="ac15b-112">(rsModelGenerationError) (ReportingServicesLibrary) %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ac15b-113">說明</span><span class="sxs-lookup"><span data-stu-id="ac15b-113">Explanation</span></span>  
 <span data-ttu-id="ac15b-114">無法產生報表模型。</span><span class="sxs-lookup"><span data-stu-id="ac15b-114">The report model could not be generated.</span></span> <span data-ttu-id="ac15b-115">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 SP1 及更舊版本中，當 System.Data.DataSet 物件無法處理資料庫結構描述中的資料表或關聯性時 (例如在資料表內的同一個資料行中定義兩個外部索引鍵時)，很可能就會出現這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="ac15b-115">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 SP1 and earlier versions, this error is most likely displayed when the System.Data.DataSet object cannot handle a table or relationship within the database schema, such as when, for example, two foreign keys are defined on the same column within a table.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ac15b-116">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ac15b-116">User Action</span></span>  
 <span data-ttu-id="ac15b-117">若要判斷導致這個訊息出現的明確原因，請檢閱位於 \Microsoft SQL Server\\<SQL Server 執行個體\>\Reporting Services\LogFiles 的報表伺服器記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ac15b-117">To determine the specific reason that caused this message to appear, review the report server log files, which are located at \Microsoft SQL Server\\<SQL Server Instance\>\Reporting Services\LogFiles.</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="ac15b-118">僅供內部使用</span><span class="sxs-lookup"><span data-stu-id="ac15b-118">Internal-Only</span></span>  
  
