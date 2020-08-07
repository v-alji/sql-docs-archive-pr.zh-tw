---
title: 認證 (Database Engine) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- principals [SQL Server], credentials
- schemas [SQL Server], credentials
- permissions [SQL Server], credentials
- groups [SQL Server], credentials
- ALTER ANY CREDENTIAL permission
- security [SQL Server], credentials
- authentication [SQL Server], credentials
- users [SQL Server], credentials
- credentials [SQL Server], about credentials
- credentials [SQL Server]
ms.assetid: c8df6022-e0b4-46b8-9670-3f86938d3177
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: faa2b5be7cf6918b5d5232763a96ed4dbbc89e51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598779"
---
# <a name="credentials-database-engine"></a><span data-ttu-id="b3f60-102">認證 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="b3f60-102">Credentials (Database Engine)</span></span>
  <span data-ttu-id="b3f60-103">認證是包含驗證資訊 (認證) 的記錄，該項資訊是連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]外部資源時所需的資訊，</span><span class="sxs-lookup"><span data-stu-id="b3f60-103">A credential is a record that contains the authentication information (credentials) required to connect to a resource outside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b3f60-104">此資訊會由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]用於內部。</span><span class="sxs-lookup"><span data-stu-id="b3f60-104">This information is used internally by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b3f60-105">大部份認證都包含 Windows 使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="b3f60-105">Most credentials contain a Windows user name and password.</span></span>  
  
 <span data-ttu-id="b3f60-106">儲存在認證中的資訊可讓透過 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的使用者，可以存取在伺服器執行個體外部的資源。</span><span class="sxs-lookup"><span data-stu-id="b3f60-106">The information stored in a credential enables a user who has connected to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by way of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication to access resources outside the server instance.</span></span> <span data-ttu-id="b3f60-107">如果外部資源為 Windows，則使用者會驗證為認證中指定的 Windows 使用者。</span><span class="sxs-lookup"><span data-stu-id="b3f60-107">When the external resource is Windows, the user is authenticated as the Windows user specified in the credential.</span></span> <span data-ttu-id="b3f60-108">單一認證可對應至多個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="b3f60-108">A single credential can be mapped to multiple [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins.</span></span> <span data-ttu-id="b3f60-109">但是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入只能對應至一個認證。</span><span class="sxs-lookup"><span data-stu-id="b3f60-109">However, a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login can be mapped to only one credential.</span></span>  
  
 <span data-ttu-id="b3f60-110">系統認證會自動建立並與特定端點關聯。</span><span class="sxs-lookup"><span data-stu-id="b3f60-110">System credentials are created automatically and are associated with specific endpoints.</span></span> <span data-ttu-id="b3f60-111">系統認證的名稱是以兩個雜湊符號 (##) 開頭。</span><span class="sxs-lookup"><span data-stu-id="b3f60-111">Names for system credentials start with two hash signs (##).</span></span>  
  
 <span data-ttu-id="b3f60-112">如需認證的詳細資訊，請參閱[sys. 認證](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql)目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="b3f60-112">For more information about credentials, see the [sys.credentials](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) catalog view.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="b3f60-113">相關內容</span><span class="sxs-lookup"><span data-stu-id="b3f60-113">Related Content</span></span>  
 <span data-ttu-id="b3f60-114">[建立認證](../authentication-access/create-a-credential.md)[建立認證 &#40;transact-sql&#41;](/sql/t-sql/statements/create-credential-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="b3f60-114">[Create a Credential](../authentication-access/create-a-credential.md) [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)</span></span>  
  
 [<span data-ttu-id="b3f60-115">保護 SQL Server 的安全</span><span class="sxs-lookup"><span data-stu-id="b3f60-115">Securing SQL Server</span></span>](../securing-sql-server.md)  
  
  
