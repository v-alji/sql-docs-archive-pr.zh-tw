---
title: FTP 連線管理員編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftpconnectionmanager.f1
helpviewer_keywords:
- FTP Connection Manager Editor
ms.assetid: 874b6585-255b-4a43-8396-bb08c3e8ac2b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d14635a4d90c267801f6d372dda5c7bcc7f4869f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710726"
---
# <a name="ftp-connection-manager-editor"></a><span data-ttu-id="0db8f-102">FTP 連接管理員編輯器</span><span class="sxs-lookup"><span data-stu-id="0db8f-102">FTP Connection Manager Editor</span></span>
  <span data-ttu-id="0db8f-103">使用 [FTP 連線管理員編輯器]\*\*\*\* 對話方塊來指定連接到 FTP 伺服器的屬性。</span><span class="sxs-lookup"><span data-stu-id="0db8f-103">Use the **FTP Connection Manager Editor** dialog box to specify properties for connecting to an FTP server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0db8f-104">FTP 連接管理員僅支援匿名驗證和基本驗證，</span><span class="sxs-lookup"><span data-stu-id="0db8f-104">The FTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="0db8f-105">而不支援 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="0db8f-105">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="0db8f-106">若要深入了解 FTP 連線管理員，請參閱 [FTP 連線管理員](connection-manager/ftp-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="0db8f-106">To learn more about the FTP connection manager, see [FTP Connection Manager](connection-manager/ftp-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="0db8f-107">選項。</span><span class="sxs-lookup"><span data-stu-id="0db8f-107">Options</span></span>  
 <span data-ttu-id="0db8f-108">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="0db8f-108">**Server name**</span></span>  
 <span data-ttu-id="0db8f-109">提供 FTP 伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="0db8f-109">Provide the name of the FTP server.</span></span>  
  
 <span data-ttu-id="0db8f-110">**伺服器埠**</span><span class="sxs-lookup"><span data-stu-id="0db8f-110">**Server port**</span></span>  
 <span data-ttu-id="0db8f-111">指定 FTP 伺服器上用來連接的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="0db8f-111">Specify the port number on the FTP server to use for the connection.</span></span> <span data-ttu-id="0db8f-112">這個屬性的預設值為 **21**。</span><span class="sxs-lookup"><span data-stu-id="0db8f-112">The default value of this property is **21**.</span></span>  
  
 <span data-ttu-id="0db8f-113">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="0db8f-113">**User name**</span></span>  
 <span data-ttu-id="0db8f-114">提供存取 FTP 伺服器的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="0db8f-114">Provide a user name to access the FTP server.</span></span> <span data-ttu-id="0db8f-115">這個屬性的預設值為 **匿名**。</span><span class="sxs-lookup"><span data-stu-id="0db8f-115">The default value of this property is **anonymous**.</span></span>  
  
 <span data-ttu-id="0db8f-116">**密碼**</span><span class="sxs-lookup"><span data-stu-id="0db8f-116">**Password**</span></span>  
 <span data-ttu-id="0db8f-117">提供存取 FTP 伺服器的密碼。</span><span class="sxs-lookup"><span data-stu-id="0db8f-117">Provide the password to access the FTP server.</span></span>  
  
 <span data-ttu-id="0db8f-118">**逾時 (以秒為單位)**</span><span class="sxs-lookup"><span data-stu-id="0db8f-118">**Time-out (in seconds)**</span></span>  
 <span data-ttu-id="0db8f-119">指定工作超時前所花費的秒數。值為**0**表示無限的時間量。</span><span class="sxs-lookup"><span data-stu-id="0db8f-119">Specify the number of seconds the task takes before timing out. A value of **0** indicates an infinite amount of time.</span></span> <span data-ttu-id="0db8f-120">這個屬性的預設值為 **60**。</span><span class="sxs-lookup"><span data-stu-id="0db8f-120">The default value of this property is **60**.</span></span>  
  
 <span data-ttu-id="0db8f-121">**使用被動模式**</span><span class="sxs-lookup"><span data-stu-id="0db8f-121">**Use passive mode**</span></span>  
 <span data-ttu-id="0db8f-122">指定伺服器或用戶端是否起始連接。</span><span class="sxs-lookup"><span data-stu-id="0db8f-122">Specify whether the server or the client initiates the connection.</span></span> <span data-ttu-id="0db8f-123">伺服器會以主動模式起始連接，而用戶端則會以被動模式啟動連接。</span><span class="sxs-lookup"><span data-stu-id="0db8f-123">The server initiates the connection in active mode, and the client activates the connection in passive mode.</span></span> <span data-ttu-id="0db8f-124">此屬性的預設值為 **主動模式**。</span><span class="sxs-lookup"><span data-stu-id="0db8f-124">The default value of this property is **active mode**.</span></span>  
  
 <span data-ttu-id="0db8f-125">**重試**</span><span class="sxs-lookup"><span data-stu-id="0db8f-125">**Retries**</span></span>  
 <span data-ttu-id="0db8f-126">指定工作嘗試連接的次數。</span><span class="sxs-lookup"><span data-stu-id="0db8f-126">Specify the number of times the task attempts to make a connection.</span></span> <span data-ttu-id="0db8f-127">值為 **0** 指出不限制嘗試次數。</span><span class="sxs-lookup"><span data-stu-id="0db8f-127">A value of **0** indicates no limit to the number of attempts.</span></span>  
  
 <span data-ttu-id="0db8f-128">**區塊大小 (以 KB 為單位)**</span><span class="sxs-lookup"><span data-stu-id="0db8f-128">**Chunk size (in KB)**</span></span>  
 <span data-ttu-id="0db8f-129">提供以 KB 為單位的傳輸資料區塊大小。</span><span class="sxs-lookup"><span data-stu-id="0db8f-129">Provide a chunk size in kilobytes for transmitting data.</span></span>  
  
 <span data-ttu-id="0db8f-130">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="0db8f-130">**Test Connection**</span></span>  
 <span data-ttu-id="0db8f-131">設定 FTP 連線管理員之後，請按一下 [測試連接]\*\*\*\* 以確認連接是可行的。</span><span class="sxs-lookup"><span data-stu-id="0db8f-131">After configuring the FTP Connection Manager, confirm that the connection is viable by clicking **Test Connection**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0db8f-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0db8f-132">See Also</span></span>  
 [<span data-ttu-id="0db8f-133">Integration Services 錯誤和訊息參考</span><span class="sxs-lookup"><span data-stu-id="0db8f-133">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
