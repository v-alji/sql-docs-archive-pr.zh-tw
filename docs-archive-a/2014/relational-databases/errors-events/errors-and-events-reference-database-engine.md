---
title: 錯誤和事件參考 (Database Engine) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server Database Engine]
- Database Engine [SQL Server], errors
- events [SQL Server Database Engine]
ms.assetid: ea928535-6fd1-4738-a8ed-ffb602f3825e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e991accfd0e6fdd4fa25746499308455eff85ce3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704125"
---
# <a name="errors-and-events-reference-database-engine"></a><span data-ttu-id="5962d-102">錯誤和事件參考 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="5962d-102">Errors and Events Reference (Database Engine)</span></span>

<span data-ttu-id="5962d-103">本節包含所選資料庫引擎錯誤訊息，需要進一步說明。</span><span class="sxs-lookup"><span data-stu-id="5962d-103">This section contains selected Database Engine error messages that need further explanation.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="5962d-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="5962d-104">In This Section</span></span>  
 <span data-ttu-id="5962d-105">[資料庫引擎事件和錯誤](database-engine-events-and-errors.md)描述 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 錯誤訊息的格式，並說明如何查看錯誤訊息，並將錯誤訊息傳回給應用程式。</span><span class="sxs-lookup"><span data-stu-id="5962d-105">[Database Engine Events and Errors](database-engine-events-and-errors.md) Describes the format of [!INCLUDE[ssDE](../../includes/ssde-md.md)] error messages and explains how to view error messages and return error messages to applications.</span></span>  
  
 <span data-ttu-id="5962d-106">提供 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 錯誤訊息、可能原因以及任何可以更正問題之動作的說明。</span><span class="sxs-lookup"><span data-stu-id="5962d-106">Provides an explanation of [!INCLUDE[ssDE](../../includes/ssde-md.md)] error messages, possible causes, and any actions you can take to correct the problem.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="5962d-107">外部資源</span><span class="sxs-lookup"><span data-stu-id="5962d-107">External Resources</span></span>  
 <span data-ttu-id="5962d-108">如果還沒有在產品文件集或網站上找到您所搜尋的資訊，您可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 社群中提出問題，或是向 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援尋求協助。</span><span class="sxs-lookup"><span data-stu-id="5962d-108">If you have not found the information you are looking for in the product documentation or on the Web, you can either ask a question in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] community or request help from [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="5962d-109">下表會連結到這些資源並提供說明。</span><span class="sxs-lookup"><span data-stu-id="5962d-109">The following table links to and describes these resources.</span></span>  
  
|<span data-ttu-id="5962d-110">資源</span><span class="sxs-lookup"><span data-stu-id="5962d-110">Resource</span></span>|<span data-ttu-id="5962d-111">描述</span><span class="sxs-lookup"><span data-stu-id="5962d-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="5962d-112">SQL Server 社群</span><span class="sxs-lookup"><span data-stu-id="5962d-112">SQL Server Community</span></span>](https://go.microsoft.com/fwlink/?LinkId=42455)|<span data-ttu-id="5962d-113">這個網站包含由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 社群所監控之新聞群組和論壇的連結。</span><span class="sxs-lookup"><span data-stu-id="5962d-113">This site has links to newsgroups and forums monitored by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] community.</span></span> <span data-ttu-id="5962d-114">它還會列出社群資訊來源，例如網誌或網站。</span><span class="sxs-lookup"><span data-stu-id="5962d-114">It also lists community information sources, such as blogs and Web sites.</span></span> <span data-ttu-id="5962d-115">雖然不保證一定有答案，不過 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 社群對於解答問題有很大的幫助。</span><span class="sxs-lookup"><span data-stu-id="5962d-115">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] community is very helpful in answering questions, although an answer cannot be guaranteed.</span></span>|  
|[<span data-ttu-id="5962d-116">SQL Server 程式開發人員中心社群</span><span class="sxs-lookup"><span data-stu-id="5962d-116">SQL Server Developer Center Community</span></span>](https://go.microsoft.com/fwlink/?LinkId=42456)|<span data-ttu-id="5962d-117">此網站著重在新聞群組、論壇及其他社群資源，這些資訊對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 開發人員很有用。</span><span class="sxs-lookup"><span data-stu-id="5962d-117">This site focuses on the newsgroups, forums, and other community resources that are useful to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] developers.</span></span>|  
|[<span data-ttu-id="5962d-118">Microsoft 說明及支援</span><span class="sxs-lookup"><span data-stu-id="5962d-118">Microsoft Help and Support</span></span>](https://go.microsoft.com/fwlink/?linkid=16419)|<span data-ttu-id="5962d-119">您可以使用這個網站向 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援人員提交案件。</span><span class="sxs-lookup"><span data-stu-id="5962d-119">You can use this Web site to open a case with a [!INCLUDE[msCoName](../../includes/msconame-md.md)] support professional.</span></span>|  
  
  
