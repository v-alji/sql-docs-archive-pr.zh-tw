---
title: 建立 SQL Server Native Client OLE DB 提供者應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, application creation
- applications [SQL Server Native Client]
- OLE DB, creating applications
ms.assetid: f3ae6815-f32d-4913-a1a2-2ba2f20cfd88
author: rothja
ms.author: jroth
ms.openlocfilehash: a661f23cdacc4b581dadbe7625cb6e2ea318857f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698122"
---
# <a name="creating-a-sql-server-native-client-ole-db-provider-application"></a><span data-ttu-id="ac252-102">建立 SQL Server Native Client OLE DB 提供者應用程式</span><span class="sxs-lookup"><span data-stu-id="ac252-102">Creating a SQL Server Native Client OLE DB Provider Application</span></span>
  <span data-ttu-id="ac252-103">建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 原生用戶端 OLE DB 提供者應用程式牽涉到下列步驟：</span><span class="sxs-lookup"><span data-stu-id="ac252-103">Creating a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider application involves these steps:</span></span>  
  
1.  <span data-ttu-id="ac252-104">建立與資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="ac252-104">Establishing a connection to a data source.</span></span>  
  
2.  <span data-ttu-id="ac252-105">執行命令。</span><span class="sxs-lookup"><span data-stu-id="ac252-105">Executing a command.</span></span>  
  
3.  <span data-ttu-id="ac252-106">處理結果。</span><span class="sxs-lookup"><span data-stu-id="ac252-106">Processing the results.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac252-107">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="ac252-107">When possible, use Windows Authentication.</span></span> <span data-ttu-id="ac252-108">如果無法使用 Windows 驗證，請提示使用者在執行階段輸入認證。</span><span class="sxs-lookup"><span data-stu-id="ac252-108">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="ac252-109">請避免將認證儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="ac252-109">Avoid storing credentials in a file.</span></span> <span data-ttu-id="ac252-110">如果您必須保存認證，則應該用 [Win32 cryptoAPI](https://go.microsoft.com/fwlink/?LinkId=9504) 加密這些認證。</span><span class="sxs-lookup"><span data-stu-id="ac252-110">If you must persist credentials, you should encrypt them with [the Win32 cryptoAPI](https://go.microsoft.com/fwlink/?LinkId=9504).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac252-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="ac252-111">In This Section</span></span>  
  
-   [<span data-ttu-id="ac252-112">建立與資料來源的連接</span><span class="sxs-lookup"><span data-stu-id="ac252-112">Establishing a Connection to a Data Source</span></span>](establishing-a-connection-to-a-data-source.md)  
  
-   [<span data-ttu-id="ac252-113">執行命令</span><span class="sxs-lookup"><span data-stu-id="ac252-113">Executing a Command</span></span>](executing-a-command.md)  
  
-   [<span data-ttu-id="ac252-114">處理結果</span><span class="sxs-lookup"><span data-stu-id="ac252-114">Processing Results</span></span>](processing-results.md)  
  
-   [<span data-ttu-id="ac252-115">關於 OLE DB 屬性</span><span class="sxs-lookup"><span data-stu-id="ac252-115">About OLE DB Properties</span></span>](about-ole-db-properties.md)  
  
-   [<span data-ttu-id="ac252-116">在 SQL Server Native Client 中使用 OUTPUT 子句搭配 OLE DB</span><span class="sxs-lookup"><span data-stu-id="ac252-116">Using the OUTPUT Clause with OLE DB in SQL Server Native Client</span></span>](using-the-output-clause-with-ole-db-in-sql-server-native-client.md)  
  
## <a name="see-also"></a><span data-ttu-id="ac252-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac252-117">See Also</span></span>  
 [<span data-ttu-id="ac252-118">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="ac252-118">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
