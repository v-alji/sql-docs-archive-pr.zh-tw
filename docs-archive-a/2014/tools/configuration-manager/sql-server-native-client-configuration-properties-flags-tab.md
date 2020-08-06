---
title: SQL Server Native Client 設定屬性 ([旗標] 索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 59af121d-c8b9-4faa-91a1-b664f2c9b441
author: stevestein
ms.author: sstein
ms.openlocfilehash: b3ca7b87963fc3848bbb933a5c21f9d608d37d18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605955"
---
# <a name="sql-server-native-client-configuration-properties-flags-tab"></a><span data-ttu-id="e2b2c-102">SQL Server Native Client 組態屬性 (旗標索引標籤)</span><span class="sxs-lookup"><span data-stu-id="e2b2c-102">SQL Server Native Client Configuration Properties (Flags Tab)</span></span>
  <span data-ttu-id="e2b2c-103">這部電腦上的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端會使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 程式庫檔案中提供的通訊協定，來與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 伺服器通訊。</span><span class="sxs-lookup"><span data-stu-id="e2b2c-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] clients on this machine, communicate with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servers using the protocols provided in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client library file.</span></span> <span data-ttu-id="e2b2c-104">此頁面提供用戶端電腦的設定，要求使用安全通訊端層 (SSL) 來建立加密的連接。</span><span class="sxs-lookup"><span data-stu-id="e2b2c-104">This page provides configures the client computer to request an encrypted connection using Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="e2b2c-105">若無法建立加密的連接，則連接會失敗。</span><span class="sxs-lookup"><span data-stu-id="e2b2c-105">If an encrypted connection cannot be established, the connection will fail.</span></span>  
  
 <span data-ttu-id="e2b2c-106">登入過程一律加密。</span><span class="sxs-lookup"><span data-stu-id="e2b2c-106">The login process is always encrypted.</span></span> <span data-ttu-id="e2b2c-107">下列選項只適用於加密資料。</span><span class="sxs-lookup"><span data-stu-id="e2b2c-107">The options below apply only to encrypting data.</span></span> <span data-ttu-id="e2b2c-108">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如何加密通訊的詳細資訊，以及如何將用戶端設定為信任伺服器憑證之根授權單位的指示，請參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]線上叢書》中的＜加密 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的連接＞以及＜如何：啟用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的加密連接 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員)＞。</span><span class="sxs-lookup"><span data-stu-id="e2b2c-108">For more information about how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] encrypts communication and for instructions on how to configure the client to trust the root authority of the server certificate, see "Encrypting Connections to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]" and "How to: Enable Encrypted Connections to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e2b2c-109">選項。</span><span class="sxs-lookup"><span data-stu-id="e2b2c-109">Options</span></span>  
 <span data-ttu-id="e2b2c-110">**強制通訊協定加密**</span><span class="sxs-lookup"><span data-stu-id="e2b2c-110">**Force protocol encryption**</span></span>  
 <span data-ttu-id="e2b2c-111">使用 SSL 來要求連接。</span><span class="sxs-lookup"><span data-stu-id="e2b2c-111">Request a connection using SSL.</span></span>  
  
 <span data-ttu-id="e2b2c-112">**信任伺服器憑證**</span><span class="sxs-lookup"><span data-stu-id="e2b2c-112">**Trust Server Certificate**</span></span>  
 <span data-ttu-id="e2b2c-113">當設定為 **[否]** 時，用戶端處理序會嘗試驗證伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="e2b2c-113">When set to **No**, the client process attempts to validate the server certificate.</span></span> <span data-ttu-id="e2b2c-114">用戶端和伺服器各需擁有公開憑證授權單位所發行的憑證。</span><span class="sxs-lookup"><span data-stu-id="e2b2c-114">The client and server must have each have a certificate issues from a public certification authority.</span></span> <span data-ttu-id="e2b2c-115">若用戶端電腦沒有憑證，或憑證驗證失敗，則會結束連接。</span><span class="sxs-lookup"><span data-stu-id="e2b2c-115">If the certificate is not present on the client computer, or if the validation of the certificate fails, the connection is terminated.</span></span>  
  
 <span data-ttu-id="e2b2c-116">當設定為 **[是]** 時，用戶端不會驗證伺服器憑證，因此會啟用自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="e2b2c-116">When set to **Yes**, the client does not validate the server certificate, thereby enabling the use of a self-signed certificate.</span></span>  
  
 <span data-ttu-id="e2b2c-117">只有在 **[強制通訊協定加密]** 設定為 **[是]** 時，才能使用 **[信任伺服器憑證]** 。</span><span class="sxs-lookup"><span data-stu-id="e2b2c-117">**Trust Server Certificate** is only available if **Force protocol encryption** is set to **Yes**.</span></span>  
  
  
