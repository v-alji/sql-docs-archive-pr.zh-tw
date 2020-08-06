---
title: 完成安裝後步驟 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 0a788a2a-9b4f-4bfc-b1b5-83eeb1ea9ab2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1e9aae3dccaa409bcebc473213286f3edf19e7f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596958"
---
# <a name="complete-the-post-installation-steps"></a><span data-ttu-id="d9c22-102">完成安裝後步驟</span><span class="sxs-lookup"><span data-stu-id="d9c22-102">Complete the Post-Installation Steps</span></span>
  <span data-ttu-id="d9c22-103">安裝 Distributed Replay 之後，必須修改 Distributed Replay 控制器及用戶端服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="d9c22-103">After you install Distributed Replay you must modify the Distributed Replay controller and client services accounts.</span></span>  
  
### <a name="to-complete-the-post-installation-steps"></a><span data-ttu-id="d9c22-104">若要完成後續安裝步驟</span><span class="sxs-lookup"><span data-stu-id="d9c22-104">To complete the post-installation steps</span></span>  
  
1.  <span data-ttu-id="d9c22-105">**建立防火牆規則**：在控制器和用戶端電腦上，您必須允許輸入流量通過對應服務的防火牆。</span><span class="sxs-lookup"><span data-stu-id="d9c22-105">**Create firewall rules**: On the controller and client computers, you must allow inbound traffic through the firewall for the corresponding service.</span></span> <span data-ttu-id="d9c22-106">請針對服務可執行檔 (位於安裝資料夾中) 指定防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="d9c22-106">Specify the firewall rules for the service executables, located in the installation folders.</span></span>  
  
    1.  <span data-ttu-id="d9c22-107">對於控制器服務，請為安裝資料夾中的 **DReplayController.exe**建立規則。</span><span class="sxs-lookup"><span data-stu-id="d9c22-107">For the controller service, create a rule for **DReplayController.exe**, located in the installation folder.</span></span> <span data-ttu-id="d9c22-108">例如，下列命令會啟用這項規則，其中 `%InstallPath%` 是服務的安裝資料夾：</span><span class="sxs-lookup"><span data-stu-id="d9c22-108">For example, the following command enables this rule, where `%InstallPath%` is the installation folder of the service:</span></span>  
  
         `netsh advfirewall firewall add rule name="allow dreplay controller" dir=in program="%InstallPath%\DReplayController\DReplayController.exe" action=allow`  
  
    2.  <span data-ttu-id="d9c22-109">對於每部用戶端電腦上的用戶端服務，請為安裝資料夾中的 **DReplayClient.exe**建立規則。</span><span class="sxs-lookup"><span data-stu-id="d9c22-109">For the client service, on each client computer, create a rule for **DReplayClient.exe**, located in the installation folder.</span></span> <span data-ttu-id="d9c22-110">例如，下列命令會啟用這項規則，其中 `%InstallPath%` 是服務的安裝資料夾：</span><span class="sxs-lookup"><span data-stu-id="d9c22-110">For example, the following command enables this rule, where `%InstallPath%` is the installation folder of the service:</span></span>  
  
         `netsh advfirewall firewall add rule name="allow dreplay client" dir=in program="%InstallPath%\DReplayClient\DReplayClient.exe" action=allow`  
  
2.  <span data-ttu-id="d9c22-111">**將目標伺服器的權限授與每個用戶端**：當您已經完成在用戶端電腦上安裝用戶端服務的作業之後，就必須手動將用戶端服務帳戶加入目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的系統管理員角色。</span><span class="sxs-lookup"><span data-stu-id="d9c22-111">**Grant each client permissions on the target server**: After you have completed installing the client service on the client computers, you must manually add the client service accounts to the sysadmin role on the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d9c22-112">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="d9c22-112">.NET Framework Security</span></span>  
 <span data-ttu-id="d9c22-113">您必須具備管理權限，才可安裝各種 Distributed Replay 功能。</span><span class="sxs-lookup"><span data-stu-id="d9c22-113">You must have administrative permissions in order to install any of the Distributed Replay features.</span></span> <span data-ttu-id="d9c22-114">只有擁有系統管理員權限的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入能夠將用戶端服務帳戶加入測試伺服器的系統管理員伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="d9c22-114">Only a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login having sysadmin permissions can add the client service accounts to the sysadmin server role of the test server.</span></span> <span data-ttu-id="d9c22-115">如需 Distributed Replay 安全性考量的詳細資訊，請參閱 [Distributed Replay 安全性](distributed-replay-security.md)。</span><span class="sxs-lookup"><span data-stu-id="d9c22-115">For more information about Distributed Replay security considerations, see [Distributed Replay Security](distributed-replay-security.md).</span></span>  
  
  
