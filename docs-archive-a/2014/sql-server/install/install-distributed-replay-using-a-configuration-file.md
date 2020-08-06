---
title: 使用設定檔安裝 Distributed Replay |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3259232c-6963-4c9c-9d10-ae42aa262eef
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7757cce29c2e6b3ce4f1e91fc97cbf8be02ae521
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704729"
---
# <a name="install-distributed-replay-using-a-configuration-file"></a><span data-ttu-id="ffba0-102">使用組態檔安裝 Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="ffba0-102">Install Distributed Replay Using a Configuration File</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ffba0-103">安裝程式可讓您根據使用者輸入和系統預設值產生組態檔。</span><span class="sxs-lookup"><span data-stu-id="ffba0-103">Setup provides the ability to generate a configuration file based on user input and system defaults.</span></span> <span data-ttu-id="ffba0-104">如指定要安裝管理工具，即可使用組態檔部署管理工具、Distributed Replay Controller 及 Distributed Replay Client 三項 Distributed Replay 元件。</span><span class="sxs-lookup"><span data-stu-id="ffba0-104">If you specify that you want the Management tools installed, you can use the configuration file to deploy the three Distributed Replay components (administration tool, Distributed Replay controller, and the Distributed Replay client).</span></span> <span data-ttu-id="ffba0-105">這個組態檔支援安裝、修復和解除安裝 Distributed Replay 元件。</span><span class="sxs-lookup"><span data-stu-id="ffba0-105">It supports Installing, repairing, and uninstalling of the Distributed Replay components.</span></span>  
  
 <span data-ttu-id="ffba0-106">安裝程式僅支援透過命令列使用組態檔。</span><span class="sxs-lookup"><span data-stu-id="ffba0-106">Setup supports the use of the configuration file only through the command-line.</span></span> <span data-ttu-id="ffba0-107">使用組態檔時，參數的處理順序如下所述：</span><span class="sxs-lookup"><span data-stu-id="ffba0-107">The processing order of the parameters while using the configuration file is outlined below:</span></span>  
  
-   <span data-ttu-id="ffba0-108">組態檔會覆寫封裝中的預設值</span><span class="sxs-lookup"><span data-stu-id="ffba0-108">The configuration file overwrites the defaults in a package</span></span>  
  
-   <span data-ttu-id="ffba0-109">命令列的值會覆寫組態檔中的值</span><span class="sxs-lookup"><span data-stu-id="ffba0-109">Command-line values overwrite the values in the configuration file</span></span>  
  
 <span data-ttu-id="ffba0-110">如需如何使用設定檔的詳細資訊，請參閱[使用設定檔安裝 SQL Server 2014](../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="ffba0-110">For more information about how to use a configuration file, see [Install SQL Server 2014 Using a Configuration File](../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ffba0-111">安裝 Distributed Replay 之後，您必須在控制器電腦與用戶端電腦上建立防火牆規則，並為目標伺服器上的每個用戶端電腦授與權限。</span><span class="sxs-lookup"><span data-stu-id="ffba0-111">After you install Distributed Replay you must create firewall rules on the controller and client computers, and grant each client computer permissions on the target server.</span></span> <span data-ttu-id="ffba0-112">如需詳細資訊，請參閱 [完成安裝後步驟](../../tools/distributed-replay/complete-the-post-installation-steps.md)。</span><span class="sxs-lookup"><span data-stu-id="ffba0-112">For more information, see [Complete the Post-Installation Steps](../../tools/distributed-replay/complete-the-post-installation-steps.md).</span></span>  
  
### <a name="to-generate-a-configuration-file"></a><span data-ttu-id="ffba0-113">若要產生組態檔</span><span class="sxs-lookup"><span data-stu-id="ffba0-113">To generate a configuration file</span></span>  
  
1.  <span data-ttu-id="ffba0-114">遵循安裝精靈的指示，直到 [準備安裝]  頁面。</span><span class="sxs-lookup"><span data-stu-id="ffba0-114">Follow the Setup wizard through to the **Ready to Install** page.</span></span> <span data-ttu-id="ffba0-115">組態檔的路徑已指定於 **[準備安裝]** 頁面的 [組態檔路徑] 區段中。</span><span class="sxs-lookup"><span data-stu-id="ffba0-115">The path to the configuration file is specified in the **Ready to Install** page in the configuration file path section.</span></span>  
  
2.  <span data-ttu-id="ffba0-116">取消安裝程式而不實際完成安裝，即可產生 INI 檔案。</span><span class="sxs-lookup"><span data-stu-id="ffba0-116">Cancel the setup without actually completing the installation, to generate the INI file.</span></span>  
  
### <a name="to-install-distributed-replay-using-the-configuration-file"></a><span data-ttu-id="ffba0-117">使用組態檔安裝 Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="ffba0-117">To Install Distributed Replay Using the Configuration File</span></span>  
  
-   <span data-ttu-id="ffba0-118">透過命令提示字元執行安裝，並且使用 ConfigurationFile 參數來提供 ConfigurationFile.ini。</span><span class="sxs-lookup"><span data-stu-id="ffba0-118">Run the installation through the command prompt and supply the ConfigurationFile.ini using the ConfigurationFile parameter.</span></span>  
  
 <span data-ttu-id="ffba0-119">**範例語法**</span><span class="sxs-lookup"><span data-stu-id="ffba0-119">**Sample Syntax**</span></span>  
  
 <span data-ttu-id="ffba0-120">下面是有關如何在命令提示字元中指定組態檔的範例：</span><span class="sxs-lookup"><span data-stu-id="ffba0-120">Following is an example on how to specify the configuration file at the command prompt:</span></span>  
  
```  
Setup.exe /CTLRSVCPASSWORD="ctlrsvcpswd" /CLTSVCPASSWORD="cltsvcpswd" / ConfigurationFile=ConfigurationFile.INI\  
```  
  
> [!NOTE]  
>  <span data-ttu-id="ffba0-121">您必須在命令列中指定這兩個密碼，因為您無法在組態檔中設定它們。</span><span class="sxs-lookup"><span data-stu-id="ffba0-121">You must specify both passwords in the command line because you cannot configure them in the configuration file.</span></span>  
  
  
