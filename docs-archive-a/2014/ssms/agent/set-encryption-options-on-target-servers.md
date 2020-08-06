---
title: 在目標伺服器上設定加密選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, encryption
- target servers [SQL Server], encryption
- multiserver environments [SQL Server], setting encryption options on target servers
ms.assetid: 1a9fd539-e166-4ea8-9f21-ac400ca74dee
author: stevestein
ms.author: sstein
ms.openlocfilehash: cd10d2e05e59015542f41cc123de993e6128f9f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599321"
---
# <a name="set-encryption-options-on-target-servers"></a><span data-ttu-id="54672-102">在目標伺服器上設定加密選項</span><span class="sxs-lookup"><span data-stu-id="54672-102">Set Encryption Options on Target Servers</span></span>
  <span data-ttu-id="54672-103">如果您無法在主要伺服器與部分或全部的目標伺服器之間，使用安全通訊端層 (SSL) 加密通訊的憑證，但是您想要加密它們之間的通道，請將目標伺服器設定為使用所需的安全性層級。</span><span class="sxs-lookup"><span data-stu-id="54672-103">If you cannot use a certificate for Secure Sockets Layer (SSL) encrypted communications between master servers and some or all of your target servers, but you want to encrypt the channel between them, configure the target server to use the level of security required.</span></span>  
  
 <span data-ttu-id="54672-104">若要設定特定主伺服器/目標伺服器通道所需的適當安全性層級，請將目標伺服器上的 Agent 登錄子機碼 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \*\*\ HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server \\ \*\* \<*instance_name*> \*\*\SQLServerAgent\MsxEncryptChannelOptions (REG_DWORD) \*\*設為下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="54672-104">To configure the appropriate level of security required for a specific master server/target server communication channel, set the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent registry subkey **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\**\<*instance_name*>**\SQLServerAgent\MsxEncryptChannelOptions(REG_DWORD)** on the target server to one of the following values.</span></span> <span data-ttu-id="54672-105">的值 \<*instance_name*> 是**MSSQL。**_n_。</span><span class="sxs-lookup"><span data-stu-id="54672-105">The value of \<*instance_name*> is **MSSQL.**_n_.</span></span> <span data-ttu-id="54672-106">例如， **MSSQL.1** 或 **MSSQL.3**。</span><span class="sxs-lookup"><span data-stu-id="54672-106">For example, **MSSQL.1** or **MSSQL.3**.</span></span>  
  
|<span data-ttu-id="54672-107">值</span><span class="sxs-lookup"><span data-stu-id="54672-107">Value</span></span>|<span data-ttu-id="54672-108">描述</span><span class="sxs-lookup"><span data-stu-id="54672-108">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="54672-109">**0**</span><span class="sxs-lookup"><span data-stu-id="54672-109">**0**</span></span>|<span data-ttu-id="54672-110">停用此目標伺服器與主要伺服器之間的加密。</span><span class="sxs-lookup"><span data-stu-id="54672-110">Disables encryption between this target server and the master server.</span></span> <span data-ttu-id="54672-111">只有在透過其他方法保護目標伺服器與主要伺服器間通道的安全之後，才能選擇這個選項。</span><span class="sxs-lookup"><span data-stu-id="54672-111">Choose this option only when the channel between the target server and master server is secured by another means.</span></span>|  
|<span data-ttu-id="54672-112">**1**</span><span class="sxs-lookup"><span data-stu-id="54672-112">**1**</span></span>|<span data-ttu-id="54672-113">僅啟用此目標伺服器與主要伺服器之間的加密，但是不需要憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="54672-113">Enables encryption only between this target server and the master server, but no certificate validation is required.</span></span>|  
|<span data-ttu-id="54672-114">**2**</span><span class="sxs-lookup"><span data-stu-id="54672-114">**2**</span></span>|<span data-ttu-id="54672-115">啟用此目標伺服器與主要伺服器之間完整的 SSL 加密與憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="54672-115">Enables full SSL encryption and certificate validation between this target server and the master server.</span></span> <span data-ttu-id="54672-116">這項設定是預設值。</span><span class="sxs-lookup"><span data-stu-id="54672-116">This setting is the default.</span></span> <span data-ttu-id="54672-117">除非您有特殊的理由要選擇不同的值，否則最好不要變更它。</span><span class="sxs-lookup"><span data-stu-id="54672-117">Unless you have specific reason to choose a different value, we recommend not changing it.</span></span>|  
  
 <span data-ttu-id="54672-118">如果指定了 **1** 或 **2** ，則必須在主要和目標伺服器上都啟用 SSL。</span><span class="sxs-lookup"><span data-stu-id="54672-118">If **1** or **2** is specified, you must have SSL enabled on both the master and target servers.</span></span> <span data-ttu-id="54672-119">而且如果指定了 **2** ，在主要伺服器上必須有已正確簽署的憑證。</span><span class="sxs-lookup"><span data-stu-id="54672-119">If **2** is specified, you must also have a properly signed certificate present on the master server.</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="54672-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54672-120">See Also</span></span>  
 [<span data-ttu-id="54672-121">啟用 Database Engine 的加密連接 &#40;SQL Server 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="54672-121">Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;</span></span>](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
  
