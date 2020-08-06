---
title: OData 連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3caa4372-aff3-4c0f-9ecd-97870948b8d0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 46eedaa008b284661fd1d364d2e2bc87c373a9f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597268"
---
# <a name="odata-connection-manager"></a><span data-ttu-id="ec265-102">OData 連接管理員</span><span class="sxs-lookup"><span data-stu-id="ec265-102">OData Connection Manager</span></span>
  <span data-ttu-id="ec265-103">OData 連接管理員可讓封裝連接到 OData 來源。</span><span class="sxs-lookup"><span data-stu-id="ec265-103">An OData connection manager enables a package to connect to an OData source.</span></span> <span data-ttu-id="ec265-104">OData 來源元件會使用 OData 連接管理員連接到 OData 來源，並取用此服務中的資料。</span><span class="sxs-lookup"><span data-stu-id="ec265-104">An OData Source component connects to an OData source using an OData connection manager and consumes data from the service.</span></span> <span data-ttu-id="ec265-105">如需詳細資訊（包括這些元件的安裝指示），請參閱[OData 來源](../data-flow/odata-source.md)一節。</span><span class="sxs-lookup"><span data-stu-id="ec265-105">See [OData Source](../data-flow/odata-source.md)section for detailed information including the installation instructions for these components.</span></span>  
  
## <a name="adding-connection-manager-to-an-ssis-package"></a><span data-ttu-id="ec265-106">將連接管理員加入至 SSIS 封裝</span><span class="sxs-lookup"><span data-stu-id="ec265-106">Adding Connection Manager to an SSIS Package</span></span>  
 <span data-ttu-id="ec265-107">您可以使用三種方式，將新的 OData 連接管理員加入至 SSIS 封裝：</span><span class="sxs-lookup"><span data-stu-id="ec265-107">You can add a new OData Connection Manager to an SSIS package in three ways:</span></span>  
  
-   <span data-ttu-id="ec265-108">按一下 [OData 來源編輯器] 中的 [新增...] 按鈕</span><span class="sxs-lookup"><span data-stu-id="ec265-108">Click the **New...** button in the **OData Source Editor**</span></span>  
  
-   <span data-ttu-id="ec265-109">以滑鼠右鍵按一下**方案總管**中的 [**連接管理**器] 資料夾，然後按一下 [**新增連接管理員**]。</span><span class="sxs-lookup"><span data-stu-id="ec265-109">Right-click **Connection Managers** folder in the **Solution Explorer** and click **New Connection Manager**.</span></span> <span data-ttu-id="ec265-110">針對 [連線管理員類型]  選取 [ODATA]  。</span><span class="sxs-lookup"><span data-stu-id="ec265-110">Select **ODATA** for **Connection manager type**.</span></span>  
  
-   <span data-ttu-id="ec265-111">以滑鼠右鍵按一下封裝設計師底部的 [**連線管理員**] 窗格，然後選取 [**新增連接 ...**]。針對 [**連線管理員類型**] 選取 [ **ODATA** ]。</span><span class="sxs-lookup"><span data-stu-id="ec265-111">Right-click in the **Connection Managers** pane at the bottom of the package designer, and select **New Connection...**. Select **ODATA** for **Connection manager type**.</span></span>  
  
## <a name="connection-manager-authentication"></a><span data-ttu-id="ec265-112">連接管理員驗證</span><span class="sxs-lookup"><span data-stu-id="ec265-112">Connection Manager Authentication</span></span>  
 <span data-ttu-id="ec265-113">OData 連接管理員支援兩種模式的驗證。</span><span class="sxs-lookup"><span data-stu-id="ec265-113">The OData Connection Manager supports two modes of authentication.</span></span>  
  
-   <span data-ttu-id="ec265-114">Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="ec265-114">Windows Authentication</span></span>  
  
-   <span data-ttu-id="ec265-115">基本驗證 (使用者名稱/密碼)</span><span class="sxs-lookup"><span data-stu-id="ec265-115">Basic Authentication (username/password)</span></span>  
  
 <span data-ttu-id="ec265-116">如果是匿名存取，請選取 [Windows 驗證] 選項</span><span class="sxs-lookup"><span data-stu-id="ec265-116">For anonymous access, select the Windows Authentication option</span></span>  
  
### <a name="specifying-and-securing-credentials"></a><span data-ttu-id="ec265-117">指定認證及維護認證安全</span><span class="sxs-lookup"><span data-stu-id="ec265-117">Specifying and Securing Credentials</span></span>  
 <span data-ttu-id="ec265-118">如果您的 OData 服務需要基本驗證，您可以在[Odata 連線管理員編輯器](../odata-connection-manager-editor.md)中指定使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="ec265-118">If your OData service requires basic authentication, you can specify a username and password in the [OData Connection Manager Editor](../odata-connection-manager-editor.md).</span></span> <span data-ttu-id="ec265-119">您在編輯器中輸入的值會保存在封裝中。</span><span class="sxs-lookup"><span data-stu-id="ec265-119">The values you enter in the editor are persisted in the package.</span></span> <span data-ttu-id="ec265-120">密碼值會根據封裝保護等級進行加密。</span><span class="sxs-lookup"><span data-stu-id="ec265-120">The password value is encrypted according to the package protection level.</span></span>  
  
 <span data-ttu-id="ec265-121">有多個方式可將使用者名稱和密碼值外部化/參數化。</span><span class="sxs-lookup"><span data-stu-id="ec265-121">There are multiple ways to externalize/parameterize the username and password values.</span></span> <span data-ttu-id="ec265-122">當您使用 SQL Server Management Studio 執行封裝時，在 [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] 中執行這項處理的兩個主要方式是藉由使用參數或是直接設定連接管理員屬性。</span><span class="sxs-lookup"><span data-stu-id="ec265-122">The two primary ways of doing this in [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] are by using parameters, or by setting the connection manager properties directly when you run the package using SQL Server Management Studio.</span></span>  
  
## <a name="odata-connection-manager-properties"></a><span data-ttu-id="ec265-123">OData 連接管理員屬性</span><span class="sxs-lookup"><span data-stu-id="ec265-123">OData Connection Manager Properties</span></span>  
 <span data-ttu-id="ec265-124">下列清單描述您可能想要變更的一些 OData 連接管理員屬性。</span><span class="sxs-lookup"><span data-stu-id="ec265-124">The following list describes some of the OData Connection Manager properties that you may want to change.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ec265-125">屬性</span><span class="sxs-lookup"><span data-stu-id="ec265-125">Property</span></span>|<span data-ttu-id="ec265-126">描述</span><span class="sxs-lookup"><span data-stu-id="ec265-126">Description</span></span>|  
|<span data-ttu-id="ec265-127">Url</span><span class="sxs-lookup"><span data-stu-id="ec265-127">Url</span></span>|<span data-ttu-id="ec265-128">服務文件的 URL。</span><span class="sxs-lookup"><span data-stu-id="ec265-128">URL to the service document.</span></span>|  
|<span data-ttu-id="ec265-129">UserName</span><span class="sxs-lookup"><span data-stu-id="ec265-129">UserName</span></span>|<span data-ttu-id="ec265-130">基本驗證所使用的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="ec265-130">Username to use for Basic Authentication.</span></span>|  
|<span data-ttu-id="ec265-131">密碼</span><span class="sxs-lookup"><span data-stu-id="ec265-131">Password</span></span>|<span data-ttu-id="ec265-132">基本驗證所使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="ec265-132">Password to use for Basic Authentication.</span></span>|  
|<span data-ttu-id="ec265-133">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="ec265-133">ConnectionString</span></span>|<span data-ttu-id="ec265-134">反映連接管理員的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="ec265-134">Reflects other properties of the connection manager.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec265-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec265-135">See Also</span></span>  
 [<span data-ttu-id="ec265-136">OData 連線管理員編輯器</span><span class="sxs-lookup"><span data-stu-id="ec265-136">OData Connection Manager Editor</span></span>](../odata-connection-manager-editor.md)  
  
  
