---
title: 在 .NET Framework 更新之後升級 SQLCLR 組件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b1a008cc-7e6b-4655-a869-bd429f986400
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 45d60db413e11828f26bd03e1c8f350645838d12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596918"
---
# <a name="upgrade-sqlclr-assemblies-after-net-framework-update"></a><span data-ttu-id="079cf-102">在 .NET Framework 更新之後升級 SQLCLR 組件</span><span class="sxs-lookup"><span data-stu-id="079cf-102">Upgrade SQLCLR Assemblies After .NET Framework Update</span></span>
  [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] <span data-ttu-id="079cf-103">(DQS) 是參考 Microsoft .NET Framework 4 組件的 SQL Common Language Runtime (SQLCR) 常式集合。</span><span class="sxs-lookup"><span data-stu-id="079cf-103">(DQS) is a collection of SQL Common Language Runtime (SQLCR) routines that reference Microsoft .NET Framework 4 assemblies.</span></span> <span data-ttu-id="079cf-104">如果您在電腦上安裝任何會影響這類參考 .NET Framework 組件的 .NET Framework 更新，則會導致全域組件快取 (GAC) 中組件的模組版本 ID (MVID) 發生變更。</span><span class="sxs-lookup"><span data-stu-id="079cf-104">When you install any .NET Framework updates on your computer that affect any such referenced .NET Framework assembly, it leads to a change in the Module Version ID (MVID) of the assembly in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="079cf-105">這樣會造成 GAC 中所參考組件的 MVID 與 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中組件的 MVID 不相符。</span><span class="sxs-lookup"><span data-stu-id="079cf-105">This causes a mismatch between the MVIDs of the referenced assembly in GAC and the assembly in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="079cf-106">如果 .NET Framework 更新需要您重新啟動 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 電腦，會自動升級受影響的 SQLCLR 組件，以修正重新啟動 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 電腦時的 MVID 不相符問題。</span><span class="sxs-lookup"><span data-stu-id="079cf-106">If the .NET Framework update requires you to restart the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer, the affected SQLCLR assemblies are upgraded automatically to fix the MVID mismatch issue on restarting the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer.</span></span> <span data-ttu-id="079cf-107">不過，若是不需要您重新啟動 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 電腦的 .NET Framework 更新，則會發生錯誤，因為當您嘗試使用 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 連接至 [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]時，會造成組件的 MVID 不相符：</span><span class="sxs-lookup"><span data-stu-id="079cf-107">However, for .NET Framework updates that do not require you to restart your [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer, an error occurs due to the mismatch in the MVIDs of the assemblies when you try to connect to a [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] using a [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]:</span></span>  
  
```  
A new version of .NET was installed on this machine. In order to continue to work with DQS please run dqsinstaller.exe -upgradedlls.  
```  
  
 <span data-ttu-id="079cf-108">若要修正此問題，則必須升級 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中受影響的 SQLCLR 組件。</span><span class="sxs-lookup"><span data-stu-id="079cf-108">To fix this issue, the affected SQLCLR assemblies in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] must be upgraded.</span></span> <span data-ttu-id="079cf-109">您可以透過使用 **upgradedlls** 命令列參數執行 DQSInstaller.exe 檔的方式略過重新建立 DQS 資料庫，而只升級受影響的組件。</span><span class="sxs-lookup"><span data-stu-id="079cf-109">You can do so by running the DQSInstaller.exe file with the **upgradedlls** command line parameter to skip recreating the DQS databases, and just upgrade the affected assemblies.</span></span> <span data-ttu-id="079cf-110">這樣可確保您的知識庫、資料品質專案以及 DQS 中的任何其他資料都會保留下來。</span><span class="sxs-lookup"><span data-stu-id="079cf-110">This ensures that your knowledge bases, data quality projects, and any other data in DQS are preserved.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="079cf-111">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="079cf-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="079cf-112">您必須以 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 電腦上 Administrator 群組成員的身分登入。</span><span class="sxs-lookup"><span data-stu-id="079cf-112">You must be logged on as a member of the Administrators group on the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer.</span></span>  
  
-   <span data-ttu-id="079cf-113">您的 Windows 使用者帳戶必須是安裝 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 之 SQL Server 執行個體上系統管理員 (sysadmin) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="079cf-113">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance where [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] is installed.</span></span>  
  
### <a name="to-upgrade-sqlclr-assemblies"></a><span data-ttu-id="079cf-114">升級 SQLCLR 組件</span><span class="sxs-lookup"><span data-stu-id="079cf-114">To upgrade SQLCLR Assemblies</span></span>  
  
1.  <span data-ttu-id="079cf-115">啟動 [命令提示字元]。</span><span class="sxs-lookup"><span data-stu-id="079cf-115">Start Command Prompt.</span></span>  
  
2.  <span data-ttu-id="079cf-116">在命令提示字元中，將目錄變更為 DQSInstaller.exe 所在的位置。</span><span class="sxs-lookup"><span data-stu-id="079cf-116">At the command prompt, change your directory to the location where DQSInstaller.exe is available.</span></span> <span data-ttu-id="079cf-117">如果已經安裝了 SQL Server 的預設執行個體，DQSInstaller.exe 檔會位於 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn。</span><span class="sxs-lookup"><span data-stu-id="079cf-117">If you installed the default instance of SQL Server, the DQSInstaller.exe file will be available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn:</span></span>  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
    ```  
  
3.  <span data-ttu-id="079cf-118">在命令提示字元中輸入下列命令，然後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="079cf-118">At the command prompt, type the following command, and press ENTER:</span></span>  
  
    ```  
    dqsinstaller.exe -upgradedlls  
    ```  
  
4.  <span data-ttu-id="079cf-119">其餘步驟與 [執行 DQSInstaller.exe 完成 Data Quality Server 安裝](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#WindowsExplorer) 的 [從開始畫面、開始功能表或 Windows 檔案總管執行 DQSInstaller.exe](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)一節中的步驟 2-6 相同。</span><span class="sxs-lookup"><span data-stu-id="079cf-119">Rest of the steps are same as steps 2-6 in the [Run DQSInstaller.exe from Start Screen, Start Menu or Windows Explorer](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#WindowsExplorer) section in [Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="079cf-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="079cf-120">See Also</span></span>  
 <span data-ttu-id="079cf-121">[安裝 Data Quality Services](install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="079cf-121">[Install Data Quality Services](install-data-quality-services.md) </span></span>  
 [<span data-ttu-id="079cf-122">在安裝 SQL Server 更新之後升級 DQS 資料庫結構描述</span><span class="sxs-lookup"><span data-stu-id="079cf-122">Upgrade DQS Databases Schema After Installing SQL Server Update</span></span>](upgrade-dqs-databases-schema-after-installing-sql-server-update.md)  
  
  
