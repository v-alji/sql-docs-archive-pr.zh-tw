---
title: SAP BW 連線管理員編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ec970319-e749-4753-8675-9cf76ed99669
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 527af979fc9c92062f24e1fe161b93e88ed4ab4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698434"
---
# <a name="sap-bw-connection-manager-editor"></a><span data-ttu-id="60019-102">SAP BW 連接管理員編輯器</span><span class="sxs-lookup"><span data-stu-id="60019-102">SAP BW Connection Manager Editor</span></span>
  <span data-ttu-id="60019-103">使用 [SAP BW 連線管理員編輯器]\*\*\*\* 可以指定要用來連接到 SAP Netweaver BW 版本 7 系統的屬性。</span><span class="sxs-lookup"><span data-stu-id="60019-103">Use the **SAP BW Connection Manager Editor** to specify the properties to use to connect to an SAP Netweaver BW version 7 system.</span></span>  
  
 <span data-ttu-id="60019-104">SAP BW 連接管理員會提供 SAP Netweaver BW 7 系統的連接，供 SAP BW 來源或目的地使用。</span><span class="sxs-lookup"><span data-stu-id="60019-104">The SAP BW connection manager provides connectivity to an SAP Netweaver BW 7 system for use by the SAP BW source or destination.</span></span> <span data-ttu-id="60019-105">若要深入了解 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW 之 SAP BW 連線管理員的詳細資訊，請參閱 [SAP BW 連線管理員](connection-manager/sap-bw-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="60019-105">To learn more about the SAP BW connection manager of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Connection Manager](connection-manager/sap-bw-connection-manager.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="60019-106">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="60019-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="60019-107">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="60019-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="60019-108">**若要開啟 SAP BW 連接管理員編輯器**</span><span class="sxs-lookup"><span data-stu-id="60019-108">**To open the SAP BW Connection Manager Editor**</span></span>  
  
1.  <span data-ttu-id="60019-109">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 連線管理員的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="60019-109">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that contains the SAP BW connection manager.</span></span>  
  
2.  <span data-ttu-id="60019-110">在 [控制流程]\*\*\*\* 索引標籤上的 [連線管理員] 區域中，執行下列其中一個步驟：</span><span class="sxs-lookup"><span data-stu-id="60019-110">In the Connection Managers area on the **Control Flow** tab, do one of the following steps:</span></span>  
  
    -   <span data-ttu-id="60019-111">按兩下 SAP BW 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="60019-111">Double-click the SAP BW connection manager.</span></span>  
  
         <span data-ttu-id="60019-112">-或-</span><span class="sxs-lookup"><span data-stu-id="60019-112">-or-</span></span>  
  
    -   <span data-ttu-id="60019-113">以滑鼠右鍵按一下 SAP BW 連線管理員，然後選取 [編輯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="60019-113">Right-click the SAP BW connection manager, and then select **Edit**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="60019-114">選項</span><span class="sxs-lookup"><span data-stu-id="60019-114">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60019-115">如果您不知道設定連接管理員的所有必要值，可能必須詢問 SAP 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="60019-115">If you do not know all the values that are required to configure the connection manager, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="60019-116">**用戶端**</span><span class="sxs-lookup"><span data-stu-id="60019-116">**Client**</span></span>  
 <span data-ttu-id="60019-117">指定系統的用戶端編號。</span><span class="sxs-lookup"><span data-stu-id="60019-117">Specify the client number of the system.</span></span>  
  
 <span data-ttu-id="60019-118">**語言**</span><span class="sxs-lookup"><span data-stu-id="60019-118">**Language**</span></span>  
 <span data-ttu-id="60019-119">指定系統所使用的語言。</span><span class="sxs-lookup"><span data-stu-id="60019-119">Specify the language that the system uses.</span></span> <span data-ttu-id="60019-120">例如，指定 [EN]\*\*\*\* 代表英文。</span><span class="sxs-lookup"><span data-stu-id="60019-120">For example, specify **EN** for English.</span></span>  
  
 <span data-ttu-id="60019-121">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="60019-121">**User name**</span></span>  
 <span data-ttu-id="60019-122">指定將用來連接到系統的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="60019-122">Specify the user name that will be used to connect to the system.</span></span>  
  
 <span data-ttu-id="60019-123">**密碼**</span><span class="sxs-lookup"><span data-stu-id="60019-123">**Password**</span></span>  
 <span data-ttu-id="60019-124">指定將搭配使用者名稱使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="60019-124">Specify the password that will be used with the user name.</span></span>  
  
 <span data-ttu-id="60019-125">**使用單一應用程式伺服器**</span><span class="sxs-lookup"><span data-stu-id="60019-125">**Use single application server**</span></span>  
 <span data-ttu-id="60019-126">連接到單一應用程式伺服器。</span><span class="sxs-lookup"><span data-stu-id="60019-126">Connect to a single application server.</span></span>  
  
 <span data-ttu-id="60019-127">若要連接到負載平衡的伺服器群組，請改用 [使用負載平衡]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="60019-127">To connect to a group of load-balanced servers, use the **Use load balancing** option instead.</span></span>  
  
 <span data-ttu-id="60019-128">**主控件**</span><span class="sxs-lookup"><span data-stu-id="60019-128">**Host**</span></span>  
 <span data-ttu-id="60019-129">如果要連接到單一應用程式伺服器，請指定主機名稱。</span><span class="sxs-lookup"><span data-stu-id="60019-129">If connecting to a single application server, specify the host name.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60019-130">只有當您已選取 [使用單一應用程式伺服器]\*\*\*\* 選項時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="60019-130">This option is only available if you have selected the **Use single application server** option.</span></span>  
  
 <span data-ttu-id="60019-131">**系統編號**</span><span class="sxs-lookup"><span data-stu-id="60019-131">**System number**</span></span>  
 <span data-ttu-id="60019-132">如果要連接到單一應用程式伺服器，請指定系統編號。</span><span class="sxs-lookup"><span data-stu-id="60019-132">If connecting to a single application server, specify the system number.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60019-133">只有當您已選取 [使用單一應用程式伺服器]\*\*\*\* 選項時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="60019-133">This option is only available if you have selected the **Use single application server** option.</span></span>  
  
 <span data-ttu-id="60019-134">**使用負載平衡**</span><span class="sxs-lookup"><span data-stu-id="60019-134">**Use load balancing**</span></span>  
 <span data-ttu-id="60019-135">連接到負載平衡的伺服器群組。</span><span class="sxs-lookup"><span data-stu-id="60019-135">Connect to a group of load-balanced servers.</span></span>  
  
 <span data-ttu-id="60019-136">若要連接到單一應用程式伺服器，請改用 [使用單一應用程式伺服器]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="60019-136">To connect to a single application server, use the **Use single application server** option instead.</span></span>  
  
 <span data-ttu-id="60019-137">**訊息伺服器**</span><span class="sxs-lookup"><span data-stu-id="60019-137">**Message server**</span></span>  
 <span data-ttu-id="60019-138">如果要連接到負載平衡的伺服器群組，請指定訊息伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="60019-138">If connecting to a group of load-balanced servers, specify the name of the message server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60019-139">只有當您已選取 [使用負載平衡]\*\*\*\* 選項時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="60019-139">This option is only available if you have selected the **Use load balancing** option.</span></span>  
  
 <span data-ttu-id="60019-140">**群組**</span><span class="sxs-lookup"><span data-stu-id="60019-140">**Group**</span></span>  
 <span data-ttu-id="60019-141">如果要連接到負載平衡的伺服器群組，請指定伺服器群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="60019-141">If connecting to a group of load-balanced servers, specify the name of the server group name.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60019-142">只有當您已選取 [使用負載平衡]\*\*\*\* 選項時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="60019-142">This option is only available if you have selected the **Use load balancing** option.</span></span>  
  
 <span data-ttu-id="60019-143">**SID**</span><span class="sxs-lookup"><span data-stu-id="60019-143">**SID**</span></span>  
 <span data-ttu-id="60019-144">如果要連接到負載平衡的伺服器群組，請指定連接的系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="60019-144">If connecting to a group of load-balanced servers, specify the System ID for the connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60019-145">只有當您已選取 [使用負載平衡]\*\*\*\* 選項時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="60019-145">This option is only available if you have selected the **Use load balancing** option.</span></span>  
  
 <span data-ttu-id="60019-146">**記錄目錄**</span><span class="sxs-lookup"><span data-stu-id="60019-146">**Log directory**</span></span>  
 <span data-ttu-id="60019-147">針對 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW 的元件啟用記錄。</span><span class="sxs-lookup"><span data-stu-id="60019-147">Enable logging for the components of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span>  
  
 <span data-ttu-id="60019-148">若要啟用記錄，請針對每個 RFC 函數呼叫前後建立的記錄檔指定目錄</span><span class="sxs-lookup"><span data-stu-id="60019-148">To enable logging, specify a directory for the log files that are created before and after each RFC function call.</span></span> <span data-ttu-id="60019-149">(這項記錄功能會使用 XML 格式來建立許多記錄檔。</span><span class="sxs-lookup"><span data-stu-id="60019-149">(This logging feature creates many log files in XML format.</span></span> <span data-ttu-id="60019-150">因為這些記錄檔也包含所有傳輸的資料列，所以這些記錄檔可能會耗用大量磁碟空間)。</span><span class="sxs-lookup"><span data-stu-id="60019-150">As these log files also contain all the rows of data that are transferred, these log files may consume a large amount of disk space.)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="60019-151">如果傳輸的資料包含機密資訊，這些記錄檔也會包含該項機密資訊。</span><span class="sxs-lookup"><span data-stu-id="60019-151">If the data that is transferred contains sensitive information, the log files will also contain that sensitive information.</span></span>  
  
 <span data-ttu-id="60019-152">若要指定記錄目錄，您可以手動輸入目錄路徑，也可以按一下 [瀏覽]\*\*\*\* 並瀏覽到記錄目錄。</span><span class="sxs-lookup"><span data-stu-id="60019-152">To specify the log directory, you can either enter the directory path manually, or click **Browse** and browse to the log directory.</span></span>  
  
 <span data-ttu-id="60019-153">如果您沒有選取記錄目錄，就不會啟用記錄功能。</span><span class="sxs-lookup"><span data-stu-id="60019-153">If you do not select a log directory, logging is not enabled.</span></span>  
  
 <span data-ttu-id="60019-154">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="60019-154">**Browse**</span></span>  
 <span data-ttu-id="60019-155">瀏覽並選取資料夾做為記錄目錄。</span><span class="sxs-lookup"><span data-stu-id="60019-155">Browse to select a folder for the log directory.</span></span>  
  
 <span data-ttu-id="60019-156">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="60019-156">**Test Connection**</span></span>  
 <span data-ttu-id="60019-157">使用您已提供的值來測試連接。</span><span class="sxs-lookup"><span data-stu-id="60019-157">Test the connection using the values that you have provided.</span></span> <span data-ttu-id="60019-158">按一下 [測試連接]\*\*\*\* 之後，就會出現一個訊息方塊，指出連接成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="60019-158">After clicking **Test Connection**, a message box appears and indicates whether the connection succeeded or failed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60019-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60019-159">See Also</span></span>  
 [<span data-ttu-id="60019-160">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="60019-160">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](microsoft-connector-for-sap-bw-f1-help.md)  
  
  
