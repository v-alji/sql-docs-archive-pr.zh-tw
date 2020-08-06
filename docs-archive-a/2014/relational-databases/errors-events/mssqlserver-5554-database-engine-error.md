---
title: MSSQLSERVER_5554 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5095a50f257abafb6ebde97bb32c57bc71fc4e09
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596721"
---
# <a name="mssqlserver_5554"></a><span data-ttu-id="328c7-102">MSSQLSERVER_5554</span><span class="sxs-lookup"><span data-stu-id="328c7-102">MSSQLSERVER_5554</span></span>
    
## <a name="details"></a><span data-ttu-id="328c7-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="328c7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="328c7-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="328c7-104">Product Name</span></span>|<span data-ttu-id="328c7-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="328c7-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="328c7-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="328c7-106">Event ID</span></span>|<span data-ttu-id="328c7-107">5554</span><span class="sxs-lookup"><span data-stu-id="328c7-107">5554</span></span>|  
|<span data-ttu-id="328c7-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="328c7-108">Event Source</span></span>|<span data-ttu-id="328c7-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="328c7-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="328c7-110">元件</span><span class="sxs-lookup"><span data-stu-id="328c7-110">Component</span></span>|<span data-ttu-id="328c7-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="328c7-111">SQLEngine</span></span>|  
|<span data-ttu-id="328c7-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="328c7-112">Symbolic Name</span></span>|<span data-ttu-id="328c7-113">FS_MINIVER_OVERFLOW</span><span class="sxs-lookup"><span data-stu-id="328c7-113">FS_MINIVER_OVERFLOW</span></span>|  
|<span data-ttu-id="328c7-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="328c7-114">Message Text</span></span>|<span data-ttu-id="328c7-115">單一檔案的版本總數已到達檔案系統設定的上限。</span><span class="sxs-lookup"><span data-stu-id="328c7-115">The total number of versions for a single file has reached the maximum limit set by the file system.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="328c7-116">說明</span><span class="sxs-lookup"><span data-stu-id="328c7-116">Explanation</span></span>  
 <span data-ttu-id="328c7-117">在 Multiple Active Result Sets (MARS) 或觸發程序案例中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會使用作業系統所指定的迷你版本。</span><span class="sxs-lookup"><span data-stu-id="328c7-117">In multiple active result sets (MARS) or trigger scenarios, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses the miniversion specified by the operating system.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="328c7-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="328c7-118">User Action</span></span>  
 <span data-ttu-id="328c7-119">嘗試避免重複更新相同交易內的資料。</span><span class="sxs-lookup"><span data-stu-id="328c7-119">Try to avoid repeated updates to the data in the same transaction.</span></span>  
  
  
