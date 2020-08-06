---
title: " (XMLA) 鎖定和解除鎖定資料庫 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- locking [XML for Analysis]
- XML for Analysis, locking
- XMLA, locking
- unlocking objects
ms.assetid: 451afa58-ce03-4ecc-8dd3-9e7e8559b5f1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 96afa94f7c9c20072ae88b09a436d079ce0478ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704386"
---
# <a name="locking-and-unlocking-databases-xmla"></a><span data-ttu-id="3f7ac-102">鎖定和解除鎖定資料庫 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="3f7ac-102">Locking and Unlocking Databases (XMLA)</span></span>
  <span data-ttu-id="3f7ac-103">您可以使用 XML for Analysis (XMLA) 中的 [[鎖定](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)] 和 [[解除鎖定](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)] 命令，分別鎖定和解除鎖定資料庫。</span><span class="sxs-lookup"><span data-stu-id="3f7ac-103">You can lock and unlock databases using, respectively, the [Lock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) and [Unlock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) commands in XML for Analysis (XMLA).</span></span> <span data-ttu-id="3f7ac-104">一般而言，其他 XMLA 命令會視需要自動鎖定和解除鎖定物件，以便在執行期間完成命令。</span><span class="sxs-lookup"><span data-stu-id="3f7ac-104">Typically, other XMLA commands automatically lock and unlock objects as needed to complete the command during execution.</span></span> <span data-ttu-id="3f7ac-105">您可以明確地鎖定或解除鎖定資料庫，以便在單一交易中執行多個命令，例如[批次](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla)命令，同時防止其他應用程式將寫入交易認可到資料庫。</span><span class="sxs-lookup"><span data-stu-id="3f7ac-105">You can explicitly lock or unlock a database to perform multiple commands within a single transaction, such as a [Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) command, while preventing other applications from committing a write transaction to the database.</span></span>  
  
## <a name="locking-databases"></a><span data-ttu-id="3f7ac-106">鎖定資料庫</span><span class="sxs-lookup"><span data-stu-id="3f7ac-106">Locking Databases</span></span>  
 <span data-ttu-id="3f7ac-107">`Lock` 命令會在目前使用中交易的內容中鎖定某個物件，以便共用或獨佔使用。</span><span class="sxs-lookup"><span data-stu-id="3f7ac-107">The `Lock` command locks an object, either for shared or exclusive use, within the context of the currently active transaction.</span></span> <span data-ttu-id="3f7ac-108">鎖定物件會防止認可交易，直到移除鎖定為止。</span><span class="sxs-lookup"><span data-stu-id="3f7ac-108">A lock on an object prevents transactions from committing until the lock is removed.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="3f7ac-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 支援兩種鎖定類型：共用鎖定和獨佔鎖定。</span><span class="sxs-lookup"><span data-stu-id="3f7ac-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supports two types of locks, shared locks and exclusive locks.</span></span> <span data-ttu-id="3f7ac-110">如需所支援之鎖定類型的詳細資訊 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，請參閱[Mode 元素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/mode-element-xmla)。</span><span class="sxs-lookup"><span data-stu-id="3f7ac-110">For more information about the lock types supported by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], see [Mode Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/mode-element-xmla).</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="3f7ac-111">僅允許鎖定資料庫。</span><span class="sxs-lookup"><span data-stu-id="3f7ac-111">allows only databases to be locked.</span></span> <span data-ttu-id="3f7ac-112">[Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)元素必須包含資料庫的物件參考 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3f7ac-112">The [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) element must contain an object reference to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="3f7ac-113">如果您沒有指定 `Object` 元素或者 `Object` 元素參考資料庫以外的物件，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="3f7ac-113">If the `Object` element is not specified or if the `Object` element refers to an object other than a database, an error occurs.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3f7ac-114">只有資料庫管理員或伺服器管理員可以明確發出 `Lock` 命令。</span><span class="sxs-lookup"><span data-stu-id="3f7ac-114">Only database administrators or server administrators can explicitly issue a `Lock` command.</span></span>  
  
 <span data-ttu-id="3f7ac-115">其他命令會隱含地針對 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫發出 `Lock` 命令。</span><span class="sxs-lookup"><span data-stu-id="3f7ac-115">Other commands implicitly issue a `Lock` command on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="3f7ac-116">任何從資料庫讀取資料或中繼資料的作業（例如任何[探索](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)方法或執行[語句](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla)命令的[Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)方法）都會隱含地發出資料庫的共用鎖定。</span><span class="sxs-lookup"><span data-stu-id="3f7ac-116">Any operation that reads data or metadata from a database, such as any [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) method or an [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method running a [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) command, implicitly issues a shared lock on the database.</span></span> <span data-ttu-id="3f7ac-117">任何將資料或中繼資料變更認可至資料庫上之物件的交易（ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 例如，執行 `Execute` [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)命令的方法）都會隱含地發出資料庫的獨佔鎖定。</span><span class="sxs-lookup"><span data-stu-id="3f7ac-117">Any transaction that commits changes in data or metadata to an object on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, such as an `Execute` method running an [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) command, implicitly issues an exclusive lock on the database.</span></span>  
  
## <a name="unlocking-objects"></a><span data-ttu-id="3f7ac-118">解除鎖定物件</span><span class="sxs-lookup"><span data-stu-id="3f7ac-118">Unlocking Objects</span></span>  
 <span data-ttu-id="3f7ac-119">`Unlock` 命令會移除在目前使用中交易內容內部建立的鎖定。</span><span class="sxs-lookup"><span data-stu-id="3f7ac-119">The `Unlock` command removes a lock established within the context of the currently active transaction.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3f7ac-120">只有資料庫管理員或伺服器管理員可以明確發出 `Unlock` 命令。</span><span class="sxs-lookup"><span data-stu-id="3f7ac-120">Only database administrators or server administrators can explicitly issue an `Unlock` command.</span></span>  
  
 <span data-ttu-id="3f7ac-121">所有鎖定都會保存在目前交易的內容中。</span><span class="sxs-lookup"><span data-stu-id="3f7ac-121">All locks are held in the context of the current transaction.</span></span> <span data-ttu-id="3f7ac-122">當目前的交易經過認可或回復時，就會自動釋放在交易內部定義的所有鎖定。</span><span class="sxs-lookup"><span data-stu-id="3f7ac-122">When the current transaction is committed or rolled back, all locks defined within the transaction are automatically released.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f7ac-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f7ac-123">See Also</span></span>  
 <span data-ttu-id="3f7ac-124">[&#40;XMLA&#41;的 Lock 元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="3f7ac-124">[Lock Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) </span></span>  
 <span data-ttu-id="3f7ac-125">[&#40;XMLA&#41;解除鎖定元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="3f7ac-125">[Unlock Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) </span></span>  
 [<span data-ttu-id="3f7ac-126">在 Analysis Services 中使用 XMLA 進行開發</span><span class="sxs-lookup"><span data-stu-id="3f7ac-126">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
