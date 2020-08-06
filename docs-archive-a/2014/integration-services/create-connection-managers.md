---
title: 建立連線管理員 |Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.connectionmanager.f1
helpviewer_keywords:
- Integration Services packages, connections
- SSIS packages, connections
- packages [Integration Services], connections
- connection managers [Integration Services], creating
- SQL Server Integration Services packages, connections
ms.assetid: 6ca317b8-0061-4d9d-b830-ee8c21268345
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7661d165ea606af880fd00e4638ec43e9bfcc890
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594610"
---
# <a name="create-connection-managers"></a><span data-ttu-id="01f54-102">建立連接管理員</span><span class="sxs-lookup"><span data-stu-id="01f54-102">Create Connection Managers</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="01f54-103">包含各種連接管理員，以符合連接到不同類型伺服器和資料來源之工作的需要。</span><span class="sxs-lookup"><span data-stu-id="01f54-103">includes a variety of connection managers to suit the needs of tasks that connect to different types of servers and data sources.</span></span> <span data-ttu-id="01f54-104">連接管理員可由在不同類型資料儲存區中擷取和載入之資料的資料流程元件使用，也可由將記錄寫入伺服器、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料表或檔案的記錄提供者使用。</span><span class="sxs-lookup"><span data-stu-id="01f54-104">Connection managers are used by the data flow components that extract and load data in different types of data stores, and by the log providers that write logs to a server, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table, or file.</span></span> <span data-ttu-id="01f54-105">例如，具有傳送郵件工作的封裝使用 SMTP 連接管理員類型，來連接到 Simple Mail Transfer Protocol (SMTP) 伺服器。</span><span class="sxs-lookup"><span data-stu-id="01f54-105">For example, a package with a Send Mail task uses an SMTP connection manager type to connect to a Simple Mail Transfer Protocol (SMTP) server.</span></span> <span data-ttu-id="01f54-106">具有執行 SQL 工作的封裝，可以使用 OLE DB 連線管理員來連接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="01f54-106">A package with an Execute SQL task can use an OLE DB connection manager to connect to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="01f54-107">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 連接](connection-manager/integration-services-ssis-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="01f54-107">For more information, see [Integration Services &#40;SSIS&#41; Connections](connection-manager/integration-services-ssis-connections.md).</span></span>

 <span data-ttu-id="01f54-108">若要在您建立新的封裝時自動建立及設定連線管理員，您可以使用 [[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 匯入和匯出精靈]。</span><span class="sxs-lookup"><span data-stu-id="01f54-108">To automatically create and configure connection managers when you create a new package, you can use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard.</span></span> <span data-ttu-id="01f54-109">精靈也可以幫助您建立及設定使用連線管理員的來源和目的地。</span><span class="sxs-lookup"><span data-stu-id="01f54-109">The wizard also helps you create and configure the sources and destinations that use the connection managers.</span></span> <span data-ttu-id="01f54-110">如需詳細資訊，請參閱 [在 SQL Server 資料工具中建立封裝](create-packages-in-sql-server-data-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="01f54-110">For more information, see [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md).</span></span>

 <span data-ttu-id="01f54-111">若要手動建立新的連線管理員，並將其加入至現有的封裝，請使用  **設計師之 [控制流程]** **、[資料流程]** **和 [事件處理常式]** **索引標籤上所出現的 [連線管理員]** [!INCLUDE[ssIS](../includes/ssis-md.md)] 區域。</span><span class="sxs-lookup"><span data-stu-id="01f54-111">To manually create a new connection manager and add it to an existing package, you use the **Connection Managers** area that appears on the **Control Flow**, **Data Flow**, and **Event Handlers** tabs of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="01f54-112">從 [連線管理員]  區域，您可以使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師所提供的對話方塊，來選擇要建立的連線管理員類型，然後再設定連線管理員的屬性。</span><span class="sxs-lookup"><span data-stu-id="01f54-112">From the **Connection Manager** area, you choose the type of connection manager to create, and then set the properties of the connection manager by using a dialog box that [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer provides.</span></span> <span data-ttu-id="01f54-113">如需詳細資訊，請參閱本主題稍後的「使用連線管理員區域」一節。</span><span class="sxs-lookup"><span data-stu-id="01f54-113">For more information, see the section, "Using the Connection Managers Area," later in this topic.</span></span>

 <span data-ttu-id="01f54-114">將連接管理員加入封裝之後，您就可以在工作、「Foreach 迴圈」容器、來源、轉換和目的地中使用它。</span><span class="sxs-lookup"><span data-stu-id="01f54-114">After the connection manager is added to a package, you can use it in tasks, Foreach Loop containers, sources, transformations, and destinations.</span></span> <span data-ttu-id="01f54-115">如需詳細資訊，請參閱 [Integration Services 工作](control-flow/integration-services-tasks.md)、[Foreach 迴圈容器](control-flow/foreach-loop-container.md)和[資料流程](data-flow/data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="01f54-115">For more information, see [Integration Services Tasks](control-flow/integration-services-tasks.md), [Foreach Loop Container](control-flow/foreach-loop-container.md), and [Data Flow](data-flow/data-flow.md).</span></span>

## <a name="using-the-connection-managers-area"></a><span data-ttu-id="01f54-116">使用連接管理員區域</span><span class="sxs-lookup"><span data-stu-id="01f54-116">Using the Connection Managers Area</span></span>
 <span data-ttu-id="01f54-117">當  **設計師的 [控制流程]** **、[資料流程]** **或 [事件處理常式]** [!INCLUDE[ssIS](../includes/ssis-md.md)] 索引標籤處於作用中時，您可以建立連線管理員。</span><span class="sxs-lookup"><span data-stu-id="01f54-117">You can create connection managers while the **Control Flow**, **Data Flow**, or **Event Handlers** tab of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer is active.</span></span>

 <span data-ttu-id="01f54-118">下圖顯示  **設計師之 [控制流程]** **索引標籤上的 [連線管理員]** [!INCLUDE[ssIS](../includes/ssis-md.md)] 區域。</span><span class="sxs-lookup"><span data-stu-id="01f54-118">The following diagram shows the **Connection Managers** area on the **Control Flow** tab of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>

 <span data-ttu-id="01f54-119">![具有套件的控制流程設計師螢幕擷取畫面](media/samplecontrolflow.gif "具有套件的控制流程設計師螢幕擷取畫面")</span><span class="sxs-lookup"><span data-stu-id="01f54-119">![Screenshot of control flow designer with package](media/samplecontrolflow.gif "Screenshot of control flow designer with package")</span></span>

#### <a name="to-add-configure-or-delete-a-connection-manager-in-ssis-designer"></a><span data-ttu-id="01f54-120">在 SSIS 設計師中加入、設定或刪除連線管理員</span><span class="sxs-lookup"><span data-stu-id="01f54-120">To add, configure, or delete a connection manager in SSIS Designer</span></span>

-   [<span data-ttu-id="01f54-121">加入、刪除或共用封裝中的連接管理員</span><span class="sxs-lookup"><span data-stu-id="01f54-121">Add, Delete, or Share a Connection Manager in a Package</span></span>](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md)

-   [<span data-ttu-id="01f54-122">設定連線管理員的屬性</span><span class="sxs-lookup"><span data-stu-id="01f54-122">Set the Properties of a Connection Manager</span></span>](../../2014/integration-services/set-the-properties-of-a-connection-manager.md)

## <a name="32-bit-and-64-bit-providers-for-connection-managers"></a><span data-ttu-id="01f54-123">連接管理員的 32 位元和 64 位元提供者</span><span class="sxs-lookup"><span data-stu-id="01f54-123">32-Bit and 64-Bit Providers for Connection Managers</span></span>
 <span data-ttu-id="01f54-124">連接管理員使用的許多提供者都有 32 位元和 64 位元兩種版本。</span><span class="sxs-lookup"><span data-stu-id="01f54-124">Many of the providers that connection managers use are available in 32-bit and 64-bit versions.</span></span> <span data-ttu-id="01f54-125">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 設計環境是 32 位元的環境；設計封裝時，您只會看到 32 位元的提供者。</span><span class="sxs-lookup"><span data-stu-id="01f54-125">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] design environment is a 32-bit environment and you see only 32-bit providers while you are designing a package.</span></span> <span data-ttu-id="01f54-126">因此，如果要將連接管理員設定成使用特定的 64 位元提供者，您必須同時安裝 32 位元版本的同一個提供者。</span><span class="sxs-lookup"><span data-stu-id="01f54-126">Therefore, you can only configure a connection manager to use a specific 64-bit provider if the 32-bit version of the same provider is also installed.</span></span>

 <span data-ttu-id="01f54-127">執行階段中會使用正確的版本，而且就算您在設計階段中指定了 32 位元版本的提供者也沒有關係。</span><span class="sxs-lookup"><span data-stu-id="01f54-127">At run time, the correct version is used, and it does not matter that you specified the 32-bit version of the provider at design time.</span></span> <span data-ttu-id="01f54-128">即使封裝是在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中執行，還是可以執行 64 位元版本的提供者。</span><span class="sxs-lookup"><span data-stu-id="01f54-128">The 64-bit version of the provider can be run even if the package is run in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>

 <span data-ttu-id="01f54-129">兩個版本的提供者具有相同的識別碼。</span><span class="sxs-lookup"><span data-stu-id="01f54-129">Both versions of the provider have the same ID.</span></span> <span data-ttu-id="01f54-130">若要指定 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 執行階段是否使用可用的 64 位元版本提供者，請設定 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案的 Run64BitRuntime 屬性。</span><span class="sxs-lookup"><span data-stu-id="01f54-130">To specify whether the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] runtime uses an available 64-bit version of the provider, you set the Run64BitRuntime property of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="01f54-131">如果 Run64BitRuntime 屬性設定為 `true` ，執行時間會尋找並使用64位提供者; 如果 Run64BitRuntime 為 `false` ，執行時間會尋找並使用32位提供者。</span><span class="sxs-lookup"><span data-stu-id="01f54-131">If the Run64BitRuntime property is set to `true`, the runtime finds and uses the 64-bit provider; if Run64BitRuntime is `false`, the runtime finds and uses the 32-bit provider.</span></span> <span data-ttu-id="01f54-132">如需可在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案上設定之屬性的詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 和 Studio 環境](integration-services-ssis-development-and-management-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="01f54-132">For more information about properties you can set on [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects, see [Integration Services &#40;SSIS&#41; and Studio Environments](integration-services-ssis-development-and-management-tools.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="01f54-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01f54-133">See Also</span></span>
 <span data-ttu-id="01f54-134">[&#40;SSIS&#41; 事件處理常式](integration-services-ssis-event-handlers.md)的[控制流程](control-flow/control-flow.md)[資料流程](data-flow/data-flow.md)Integration Services</span><span class="sxs-lookup"><span data-stu-id="01f54-134">[Control Flow](control-flow/control-flow.md) [Data Flow](data-flow/data-flow.md) [Integration Services &#40;SSIS&#41; Event Handlers](integration-services-ssis-event-handlers.md)</span></span>


