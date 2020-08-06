---
title: TRUSTWORTHY 資料庫屬性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database property
ms.assetid: 64b2a53d-4416-4a19-acc0-664a61b45348
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 23391fe48037d4cd7f69aef7df6649949301a0f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688698"
---
# <a name="trustworthy-database-property"></a><span data-ttu-id="bce26-102">TRUSTWORTHY 資料庫屬性</span><span class="sxs-lookup"><span data-stu-id="bce26-102">TRUSTWORTHY Database Property</span></span>
  <span data-ttu-id="bce26-103">TRUSTWORTHY 資料庫屬性是用來指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體是否信任資料庫及其中的內容。</span><span class="sxs-lookup"><span data-stu-id="bce26-103">The TRUSTWORTHY database property is used to indicate whether the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trusts the database and the contents within it.</span></span> <span data-ttu-id="bce26-104">依預設，此設定為 OFF，但可使用 ALTER DATABASE 陳述式來將它設為 ON。</span><span class="sxs-lookup"><span data-stu-id="bce26-104">By default, this setting is OFF, but can be set to ON by using the ALTER DATABASE statement.</span></span> <span data-ttu-id="bce26-105">例如： `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;` 。</span><span class="sxs-lookup"><span data-stu-id="bce26-105">For example, `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bce26-106">您必須是 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能設定此選項。</span><span class="sxs-lookup"><span data-stu-id="bce26-106">To set this option, you must be a member of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="bce26-107">此屬性可用來減少因附加含有下列任一物件之資料庫而帶來的威脅：</span><span class="sxs-lookup"><span data-stu-id="bce26-107">This property can be used to reduce certain threats that can exist as a result of attaching a database that contains one of the following objects:</span></span>  
  
-   <span data-ttu-id="bce26-108">含有 EXTERNAL_ACCESS 或 UNSAFE 權限設定的惡意組件。</span><span class="sxs-lookup"><span data-stu-id="bce26-108">Malicious assemblies with an EXTERNAL_ACCESS or UNSAFE permission setting.</span></span> <span data-ttu-id="bce26-109">如需相關資訊，請參閱 [CLR Integration Security](../clr-integration/security/clr-integration-security.md)。</span><span class="sxs-lookup"><span data-stu-id="bce26-109">For more information, see [CLR Integration Security](../clr-integration/security/clr-integration-security.md).</span></span>  
  
-   <span data-ttu-id="bce26-110">定義為以高階權限使用者身分來執行的惡意模組。</span><span class="sxs-lookup"><span data-stu-id="bce26-110">Malicious modules that are defined to execute as high privileged users.</span></span> <span data-ttu-id="bce26-111">如需詳細資訊，請參閱 [EXECUTE AS 子句 &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="bce26-111">For more information, see [EXECUTE AS Clause &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql).</span></span>  
  
 <span data-ttu-id="bce26-112">這兩種情況都需要有特定程度的權限，而且在已附加至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的資料庫內容中使用時，都會受到適當的機制保護。</span><span class="sxs-lookup"><span data-stu-id="bce26-112">Both of these situations require a specific degree of privileges and are protected against by appropriate mechanisms when they are used in the context of a database that is already attached to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bce26-113">然而，如果資料庫離線了，具有資料庫檔案存取權的使用者可能會將其附加至所選取的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，並將具有惡意的內容加入資料庫。</span><span class="sxs-lookup"><span data-stu-id="bce26-113">However, if the database is taken offline, a user that has access to the database file can potentially attach it to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] of his or her choice and add malicious content to the database.</span></span> <span data-ttu-id="bce26-114">當在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中卸離和附加資料庫時，會對資料和記錄檔設定某些權限，以限制對資料庫檔案的存取權。</span><span class="sxs-lookup"><span data-stu-id="bce26-114">When databases are detached and attached in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], certain permissions are set on the data and log files that restrict access to the database files.</span></span>  
  
 <span data-ttu-id="bce26-115">因為附加至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的資料庫無法馬上獲得信任，所以該資料庫在被明確地標示為值得信任之前，將無法存取資料庫範圍以外的資源。</span><span class="sxs-lookup"><span data-stu-id="bce26-115">Because a database that is attached to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be immediately trusted, the database is not allowed to access resources beyond the scope of the database until the database is explicitly marked trustworthy.</span></span> <span data-ttu-id="bce26-116">此外，專為存取資料庫外部資源而設計的模組，以及具有 EXTERNAL_ACCESS 和 UNSAFE 權限設定的組件，都有額外的必備條件，才能順利地執行。</span><span class="sxs-lookup"><span data-stu-id="bce26-116">Also, modules that are designed to access resources outside the database, and assemblies with either the EXTERNAL_ACCESS and UNSAFE permission setting, have additional requirements in order to run successfully.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="bce26-117">相關內容</span><span class="sxs-lookup"><span data-stu-id="bce26-117">Related Content</span></span>  
 [<span data-ttu-id="bce26-118">SQL Server Database Engine 和 Azure SQL Database 的資訊安全中心</span><span class="sxs-lookup"><span data-stu-id="bce26-118">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [<span data-ttu-id="bce26-119">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bce26-119">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
