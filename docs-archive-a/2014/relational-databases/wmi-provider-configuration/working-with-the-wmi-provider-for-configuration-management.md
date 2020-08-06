---
title: 使用設定管理的 WMI 提供者 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- permissions [WMI]
- connection strings [WMI]
- security [WMI]
- WMI Provider for Configuration Management, connection strings
- WMI Provider for Configuration Management, security
- late binding [WMI]
- WMI Provider for Configuration Management, late binding
- binding [WMI]
ms.assetid: 34daa922-7074-41d0-9077-042bb18c222a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 80f311fb0abae2337f6ea4a5d5d85aaa0d320b94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595841"
---
# <a name="working-with-the-wmi-provider-for-configuration-management"></a><span data-ttu-id="05f3e-102">針對組態管理使用 WMI 提供者</span><span class="sxs-lookup"><span data-stu-id="05f3e-102">Working with the WMI Provider for Configuration Management</span></span>
  <span data-ttu-id="05f3e-103">在使用電腦管理的 WMI 提供者進行程式設計之前，請考慮下列事項：</span><span class="sxs-lookup"><span data-stu-id="05f3e-103">Consider the following before programming with the WMI Provider for Computer Management:</span></span>  
  
## <a name="binding"></a><span data-ttu-id="05f3e-104">繫結</span><span class="sxs-lookup"><span data-stu-id="05f3e-104">Binding</span></span>  
 <span data-ttu-id="05f3e-105">組態管理的 WMI 提供者是 COM 物件模型，而且可支援早期和晚期繫結。</span><span class="sxs-lookup"><span data-stu-id="05f3e-105">The WMI Provider for Configuration Management is a COM object model and it supports early and late binding.</span></span> <span data-ttu-id="05f3e-106">藉由晚期繫結，您可以使用指令碼語言 (例如 VBScript) 透過程式設計的方式來操作 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務、網路設定和別名。</span><span class="sxs-lookup"><span data-stu-id="05f3e-106">With late binding you can use script languages, such as VBScript, to manipulate the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, network settings, and aliases programmatically.</span></span>  
  
 <span data-ttu-id="05f3e-107">如需使用指令碼語言設計 WMI 提供者的詳細資訊，請參閱 [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN[網站](https://go.microsoft.com/fwlink/?linkid=15426)。</span><span class="sxs-lookup"><span data-stu-id="05f3e-107">For further information about programming WMI Provider implementations using scripting languages, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [Web site](https://go.microsoft.com/fwlink/?linkid=15426).</span></span>  
  
## <a name="specifying-a-connection-string"></a><span data-ttu-id="05f3e-108">指定連接字串</span><span class="sxs-lookup"><span data-stu-id="05f3e-108">Specifying a Connection String</span></span>  
 <span data-ttu-id="05f3e-109">應用程式會藉由連接到組態管理的 WMI 提供者所定義的 WMI 命名空間，將該提供者導向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="05f3e-109">Applications direct the WMI Provider for Configuration Management to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by connecting to a WMI namespace defined by the provider.</span></span> <span data-ttu-id="05f3e-110">Windows WMI 服務會將此命名空間對應至提供者 DLL 並將其載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="05f3e-110">The Windows WMI service maps this namespace to the provider DLL and loads it into memory.</span></span> <span data-ttu-id="05f3e-111">所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體都會以單一的 WMI 命名空間代表。</span><span class="sxs-lookup"><span data-stu-id="05f3e-111">All instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are represented with a single WMI namespace.</span></span> <span data-ttu-id="05f3e-112">命名空間預設為</span><span class="sxs-lookup"><span data-stu-id="05f3e-112">The namespace defaults to</span></span>  
  
```  
\\.\root\Microsoft\SqlServer\ComputerManagement12\instance_name  
```  
  
 <span data-ttu-id="05f3e-113">其中 `instance_name` 預設為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預設安裝中的 `MSSQLSERVER`。</span><span class="sxs-lookup"><span data-stu-id="05f3e-113">where `instance_name` defaults to `MSSQLSERVER` in a default installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="05f3e-114">**注意：** 如果您是透過 Windows 防火牆進行連線，則必須確定您的電腦已正確設定。</span><span class="sxs-lookup"><span data-stu-id="05f3e-114">**Note:** If you are connecting through Windows Firewall you will need to make sure your computers are configured appropriately.</span></span> <span data-ttu-id="05f3e-115">請參閱 MSDN 網站上 Windows Management Instrumentation 檔中的「透過 Windows 防火牆連線」文章 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。 [Web site](https://go.microsoft.com/fwlink/?linkid=15426)</span><span class="sxs-lookup"><span data-stu-id="05f3e-115">See the "Connecting Through Windows Firewall" article in the Windows Management Instrumentation documentation on [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [Web site](https://go.microsoft.com/fwlink/?linkid=15426).</span></span>  
  
## <a name="permissions-and-server-authentication"></a><span data-ttu-id="05f3e-116">權限和伺服器驗證</span><span class="sxs-lookup"><span data-stu-id="05f3e-116">Permissions and Server Authentication</span></span>  
 <span data-ttu-id="05f3e-117">若要存取組態管理的 WMI 提供者，用戶端 WMI 管理指令碼必須在目標電腦的管理員內容中執行。</span><span class="sxs-lookup"><span data-stu-id="05f3e-117">To access the WMI Provider for Configuration Management, the client WMI management script must be running in the context of an administrator on the target computer.</span></span> <span data-ttu-id="05f3e-118">您在要管理的電腦上必須是本機 Windows 管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="05f3e-118">You need to be a member of the local Windows administrators group on the computer you want to manage.</span></span>  
  
 <span data-ttu-id="05f3e-119">管理員可以設定群組原則，以控制使用者對 WMI 提供者的存取。</span><span class="sxs-lookup"><span data-stu-id="05f3e-119">The administrator can set group policies to control user access to WMI providers.</span></span> <span data-ttu-id="05f3e-120">如需有關設定群組原則的詳細資訊，請參閱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員說明中的＜群組原則和 MMC＞。</span><span class="sxs-lookup"><span data-stu-id="05f3e-120">For more information about setting group policies see "Group Policy and MMC" in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager Help.</span></span>  
  
 <span data-ttu-id="05f3e-121">WMI 管理指令碼可用來更新用來執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的帳戶。</span><span class="sxs-lookup"><span data-stu-id="05f3e-121">The WMI management script can be used to update the account under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services run.</span></span>  
  
 <span data-ttu-id="05f3e-122">安全性憑證受到組態管理的 WMI 提供者支援。</span><span class="sxs-lookup"><span data-stu-id="05f3e-122">Security certificates are supported by the WMI Provider for Configuration Management.</span></span> <span data-ttu-id="05f3e-123">如需憑證的詳細資訊，請參閱[加密](../security/encryption/encryption-hierarchy.md)階層。</span><span class="sxs-lookup"><span data-stu-id="05f3e-123">For more information about certificates, see [Encryption Hierarchy](../security/encryption/encryption-hierarchy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05f3e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05f3e-124">See Also</span></span>  
 [<span data-ttu-id="05f3e-125">SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="05f3e-125">SQL Server Configuration Manager</span></span>](../sql-server-configuration-manager.md)  
  
  
