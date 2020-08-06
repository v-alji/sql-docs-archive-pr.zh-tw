---
title: 建立資料庫主要金鑰 | Microsoft 文件
ms.custom: ''
ms.date: 09/12/2019
ms.prod: sql-server-2014
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], creating
ms.assetid: 8cb24263-e97d-4e4d-9429-6cf494a4d5eb
author: jaszymas
ms.author: jaszymas
ms.reviewer: carlrab
ms.openlocfilehash: cb8305d9d5a3c72e6dffafd231f21110a5abdd14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709077"
---
# <a name="create-a-database-master-key"></a><span data-ttu-id="23f5d-102">建立資料庫主要金鑰</span><span class="sxs-lookup"><span data-stu-id="23f5d-102">Create a Database Master Key</span></span>

<span data-ttu-id="23f5d-103">本主題描述如何使用，在中建立資料庫的資料庫主要金鑰 `master` [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [!INCLUDE[tsql](../../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="23f5d-103">This topic describes how to create a database master key in the `master` database in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>

<span data-ttu-id="23f5d-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="23f5d-104">**In This Topic**</span></span>

- <span data-ttu-id="23f5d-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="23f5d-105">**Before you begin:**</span></span>

  [<span data-ttu-id="23f5d-106">安全性</span><span class="sxs-lookup"><span data-stu-id="23f5d-106">Security</span></span>](#Security)

- [<span data-ttu-id="23f5d-107">若要使用 Transact-SQL 建立資料庫主要金鑰</span><span class="sxs-lookup"><span data-stu-id="23f5d-107">To create a database master key using Transact-SQL</span></span>](#TsqlProcedure)

## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="23f5d-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="23f5d-108">Before You Begin</span></span>

### <a name="security"></a><a name="Security"></a> <span data-ttu-id="23f5d-109">Security</span><span class="sxs-lookup"><span data-stu-id="23f5d-109">Security</span></span>

#### <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="23f5d-110">權限</span><span class="sxs-lookup"><span data-stu-id="23f5d-110">Permissions</span></span>

<span data-ttu-id="23f5d-111">需要資料庫的 CONTROL 權限。</span><span class="sxs-lookup"><span data-stu-id="23f5d-111">Requires CONTROL permission on the database.</span></span>

## <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="23f5d-112">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="23f5d-112">Using Transact-SQL</span></span>

### <a name="to-create-a-database-master-key"></a><span data-ttu-id="23f5d-113">若要建立資料庫主要金鑰</span><span class="sxs-lookup"><span data-stu-id="23f5d-113">To create a database master key</span></span>

1. <span data-ttu-id="23f5d-114">選擇密碼以加密即將儲存於資料庫的主要金鑰副本。</span><span class="sxs-lookup"><span data-stu-id="23f5d-114">Choose a password for encrypting the copy of the master key that will be stored in the database.</span></span>
2. <span data-ttu-id="23f5d-115">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="23f5d-115">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>
3. <span data-ttu-id="23f5d-116">展開 [系統資料庫]，以滑鼠右鍵按一下 `master`，然後按一下 [新增查詢]。</span><span class="sxs-lookup"><span data-stu-id="23f5d-116">Expand **System Databases**, right-click `master` and then click **New Query**.</span></span>
4. <span data-ttu-id="23f5d-117">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="23f5d-117">Copy and paste the following example into the query window and click **Execute**.</span></span>

  ```sql
  -- Creates the master key.
  -- The key is encrypted using the password "23987hxJ#KL95234nl0zBe."
  CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';
```

<span data-ttu-id="23f5d-118">如需詳細資訊，請參閱 [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="23f5d-118">For more information, see [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql).</span></span>
