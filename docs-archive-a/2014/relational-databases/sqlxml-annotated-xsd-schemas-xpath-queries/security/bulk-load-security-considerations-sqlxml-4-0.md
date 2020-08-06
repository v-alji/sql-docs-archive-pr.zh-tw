---
title: 大量載入安全性考慮 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, XML Bulk Load
- bulk load [SQLXML], security
- security [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], security
ms.assetid: 192fc6d4-ecbc-4a4d-a5cb-55e1f64af318
author: rothja
ms.author: jroth
ms.openlocfilehash: 21c1cbe7f94ef42327aa7b81f75fa521d9f7c0e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607372"
---
# <a name="bulk-load-security-considerations-sqlxml-40"></a><span data-ttu-id="308ca-102">大量載入安全性考量 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="308ca-102">Bulk Load Security Considerations (SQLXML 4.0)</span></span>
  <span data-ttu-id="308ca-103">下面是使用 XML 大量載入的安全性指導方針：</span><span class="sxs-lookup"><span data-stu-id="308ca-103">The following are security guidelines for using XML Bulk Load:</span></span>  
  
-   <span data-ttu-id="308ca-104">當您指定要將大量載入作業當做交易執行時，可以使用 `TempFilePath` 屬性來指定要在其中建立暫存檔的資料夾。</span><span class="sxs-lookup"><span data-stu-id="308ca-104">When you specify that the Bulk Load operation is to be performed as a transaction, you use the `TempFilePath` property to specify a folder in which to create the temporary files.</span></span>  
  
     <span data-ttu-id="308ca-105">大量載入處理序會使用下列權限來建立這些暫存檔：</span><span class="sxs-lookup"><span data-stu-id="308ca-105">The Bulk Load process creates these temporary files with the following permissions:</span></span>  
  
    -   <span data-ttu-id="308ca-106">讀取/寫入/刪除存取權會授與大量載入處理序。</span><span class="sxs-lookup"><span data-stu-id="308ca-106">Read/Write/Delete access is granted to the Bulk Load process.</span></span>  
  
    -   <span data-ttu-id="308ca-107">讀取權限會授與所有使用者，因為 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用來存取這些檔案的帳戶是未知的。</span><span class="sxs-lookup"><span data-stu-id="308ca-107">Read permission is granted to all users, because the account under which Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] will access these files is unknown.</span></span> <span data-ttu-id="308ca-108">您可以針對包含這些暫存檔的資料夾設定適當的權限，藉以限制它們的存取權。</span><span class="sxs-lookup"><span data-stu-id="308ca-108">You can restrict the access to these temporary files by setting the appropriate permissions on the folder that contains them.</span></span>  
  
-   <span data-ttu-id="308ca-109">XML 大量載入本身沒有任何權限設定。</span><span class="sxs-lookup"><span data-stu-id="308ca-109">XML Bulk Load does not itself have any permissions settings.</span></span> <span data-ttu-id="308ca-110">系統會假設資料庫已正確設定，而且使用者內容 (亦即，設定要使用大量載入的登入) 已設定適當的權限。</span><span class="sxs-lookup"><span data-stu-id="308ca-110">It is assumed that the database is set up correctly and that the user context (that is, the login that Bulk Load is set use) has appropriate permissions set.</span></span>  
  
-   <span data-ttu-id="308ca-111">在非交易式模式中，如果大量載入處理序期間發生錯誤，資料可能會維持部分載入的狀態。</span><span class="sxs-lookup"><span data-stu-id="308ca-111">In non-transactional mode, if an error occurs during the Bulk Load process, data may be left in a partially loaded state.</span></span> <span data-ttu-id="308ca-112">大量載入只會在發生錯誤的時間點停止。</span><span class="sxs-lookup"><span data-stu-id="308ca-112">Bulk Load will simply stop at the point where it is when this happens.</span></span> <span data-ttu-id="308ca-113">交易式模式可用來減少這個問題。</span><span class="sxs-lookup"><span data-stu-id="308ca-113">Transactional mode can be used to alleviate this issue.</span></span>  
  
-   <span data-ttu-id="308ca-114">發生大量載入錯誤時，它們可能會包含資料庫的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="308ca-114">When Bulk Load errors occur, they may include information about the database.</span></span> <span data-ttu-id="308ca-115">例如，它們可能會包含資料表或資料行的名稱，或資料行類型資訊。</span><span class="sxs-lookup"><span data-stu-id="308ca-115">For example, they may include the name of a table or column, or column type information.</span></span> <span data-ttu-id="308ca-116">當您使用大量載入時，就應該謹慎地捕捉來自大量載入處理序的錯誤並且傳回一般錯誤訊息，而非直接將錯誤公開給使用者。</span><span class="sxs-lookup"><span data-stu-id="308ca-116">When you use Bulk Load, you should take care to catch errors from the Bulk Load process and return a generic error message, rather than exposing errors directly to users.</span></span>  
  
-   <span data-ttu-id="308ca-117">大量載入不會對它所處理的資料量設定任何限制。</span><span class="sxs-lookup"><span data-stu-id="308ca-117">Bulk Load sets no limit on the amount of data it works over.</span></span> <span data-ttu-id="308ca-118">大量載入不會針對要載入的資料大小進行任何檢查。</span><span class="sxs-lookup"><span data-stu-id="308ca-118">Bulk Load does not do any checking on the size of the data to be loaded.</span></span> <span data-ttu-id="308ca-119">執行大量載入的使用者必須負責確保系統有足夠的記憶體可處理指定的檔案，而且資料庫有足夠的空間可儲存所載入的資料。</span><span class="sxs-lookup"><span data-stu-id="308ca-119">It is the responsibility of the user executing Bulk Load to ensure that there is enough memory to process the specified file, and that there is enough room in the database to store the data being loaded.</span></span>  
  
-   <span data-ttu-id="308ca-120">大量載入不會嘗試使用以程式碼方式提供的資料。</span><span class="sxs-lookup"><span data-stu-id="308ca-120">Bulk Load does not make an attempt to use the data it is given as code.</span></span> <span data-ttu-id="308ca-121">系統絕對不會以任何方式執行資料輸入。</span><span class="sxs-lookup"><span data-stu-id="308ca-121">The data input is never executed in any fashion.</span></span> <span data-ttu-id="308ca-122">輸入資料中的任何程式碼或命令會都被視為一般資料，不會加以執行。</span><span class="sxs-lookup"><span data-stu-id="308ca-122">Any code or commands in the input data are treated as normal data and will not be executed.</span></span>  
  
-   <span data-ttu-id="308ca-123">大量載入可能會根據 XML 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料模型之間的差異，對給定資料進行格式上的變更。</span><span class="sxs-lookup"><span data-stu-id="308ca-123">Bulk Load may make formatting changes to the given data based on differences between the XML and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data models.</span></span> <span data-ttu-id="308ca-124">例如，指定時間的格式是不同的。</span><span class="sxs-lookup"><span data-stu-id="308ca-124">For example, the format for specifying a time is different.</span></span> <span data-ttu-id="308ca-125">大量載入會嘗試解決這些差異。</span><span class="sxs-lookup"><span data-stu-id="308ca-125">Bulk Load will attempt to resolve these differences.</span></span> <span data-ttu-id="308ca-126">結果是某些精確度的資訊可能會遺失。</span><span class="sxs-lookup"><span data-stu-id="308ca-126">As a result, some precision information may be lost.</span></span>  
  
-   <span data-ttu-id="308ca-127">大量載入不會對其用來處理資料的時間量設定限制。</span><span class="sxs-lookup"><span data-stu-id="308ca-127">Bulk Load sets no limit on the amount of time it takes to process the data.</span></span> <span data-ttu-id="308ca-128">在處理完成或發生錯誤之前，都會繼續進行處理。</span><span class="sxs-lookup"><span data-stu-id="308ca-128">Processing will continue until processing is complete or an error occurs.</span></span>  
  
-   <span data-ttu-id="308ca-129">大量載入可以在資料庫內部建立和刪除暫存資料表，而且需要權限才能這樣做。</span><span class="sxs-lookup"><span data-stu-id="308ca-129">Bulk Load can create and delete temporary tables within the database, and needs permissions to do so.</span></span> <span data-ttu-id="308ca-130">這些資料表的權限將提供給連接至資料庫的相同使用者，以便進行大量載入處理序。</span><span class="sxs-lookup"><span data-stu-id="308ca-130">Permissions to these tables will be given to the same user who is connecting to the database for the Bulk Load process.</span></span>  
  
-   <span data-ttu-id="308ca-131">大量載入可以建立和刪除在交易式模式處理期間使用的暫存檔，而且需要權限才能這樣做。</span><span class="sxs-lookup"><span data-stu-id="308ca-131">Bulk Load can create and delete temporary files used during transactional mode processing, and needs permissions to do so.</span></span> <span data-ttu-id="308ca-132">建立這些檔案所使用的權限與執行大量載入之執行緒的目前使用者相同。</span><span class="sxs-lookup"><span data-stu-id="308ca-132">These files are created with the same permissions as the current user of the thread within which Bulk Load is running.</span></span>  
  
-   <span data-ttu-id="308ca-133">如果使用者設定了讓 SQLXML 寫入錯誤的錯誤記錄檔，每次執行大量載入時，系統都會使用上一個大量載入處理序的資料來覆寫該檔案。</span><span class="sxs-lookup"><span data-stu-id="308ca-133">If the user sets an error Log file for SQLXML to write errors into, then each time Bulk Load is executed the file will be overwritten with data from the last Bulk Load process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="308ca-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="308ca-134">See Also</span></span>  
 [<span data-ttu-id="308ca-135">執行 XML 資料的大量載入 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="308ca-135">Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;</span></span>](../bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)  
  
  
