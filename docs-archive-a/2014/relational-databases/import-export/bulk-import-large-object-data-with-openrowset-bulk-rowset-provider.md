---
title: 使用 OPENROWSET Bulk 資料列集提供者大量匯入大型物件資料 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- SINGLE_NCLOB option
- bulk rowset providers [SQL Server]
- bulk importing [SQL Server], data formats
- OPENROWSET function, bulk importing large data
- SINGLE_CLOB option
- data formats [SQL Server], large-object data
- large data, bulk imports
- SINGLE_BLOB option
ms.assetid: 171cdd5c-1e47-4bd7-b99a-4f0fd4e10526
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0f43aa2fa5e7f7ef0b2c8f1f6e5e6ff28e02f9f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594998"
---
# <a name="bulk-import-large-object-data-by-using-the-openrowset-bulk-rowset-provider-sql-server"></a><span data-ttu-id="40e5a-102">使用 OPENROWSET BULK 資料列集提供者大量匯入大型物件資料 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="40e5a-102">Bulk Import Large-Object Data by using the OPENROWSET Bulk Rowset Provider (SQL Server)</span></span>
  <span data-ttu-id="40e5a-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OPENROWSET Bulk 資料列集提供者可讓您將資料檔案當做大型物件資料大量匯入。</span><span class="sxs-lookup"><span data-stu-id="40e5a-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OPENROWSET Bulk Rowset Provider enables you to bulk import a data file as large-object data.</span></span>  
  
 <span data-ttu-id="40e5a-104">OPENROWSET Bulk 資料列集提供者支援的大型物件資料類型包括 **varbinary**(max) 或 **image**、 **varchar**(max) 或 **text**，以及 **nvarchar**(max) 或 **ntext**。</span><span class="sxs-lookup"><span data-stu-id="40e5a-104">The large-object data types supported by OPENROWSET Bulk Rowset Provider are **varbinary**(max) or **image**, **varchar**(max) or **text**, and **nvarchar**(max) or **ntext**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="40e5a-105">**image**、 **text** 和 **ntext** 資料類型已被取代。</span><span class="sxs-lookup"><span data-stu-id="40e5a-105">The **image**, **text** and **ntext** data types are deprecated.</span></span>  
  
 <span data-ttu-id="40e5a-106">OPENROWSET BULK 子句支援三個選項，以單一資料列、單一資料行的資料列集匯入資料檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="40e5a-106">The OPENROWSET BULK clause supports three options for importing the contents of a data file as a single-row, single-column rowset.</span></span> <span data-ttu-id="40e5a-107">您可以指定其中一個大型物件選項，而不使用格式檔案。</span><span class="sxs-lookup"><span data-stu-id="40e5a-107">You can specify one of these large-object options instead of using a format file.</span></span> <span data-ttu-id="40e5a-108">這些選項如下：</span><span class="sxs-lookup"><span data-stu-id="40e5a-108">These options are as follows:</span></span>  
  
 <span data-ttu-id="40e5a-109">SINGLE_BLOB</span><span class="sxs-lookup"><span data-stu-id="40e5a-109">SINGLE_BLOB</span></span>  
 <span data-ttu-id="40e5a-110">將 *data_file* 內容讀取為單一資料列，並以 **varbinary(max)** 類型的單一資料行資料列集的形式傳回內容。</span><span class="sxs-lookup"><span data-stu-id="40e5a-110">Reads the contents of *data_file* as a single-row, returns the contents as a single-column rowset of type **varbinary(max)**.</span></span>  
  
 <span data-ttu-id="40e5a-111">SINGLE_CLOB</span><span class="sxs-lookup"><span data-stu-id="40e5a-111">SINGLE_CLOB</span></span>  
 <span data-ttu-id="40e5a-112">將指定的資料檔案內容讀取為字元，並使用目前資料庫的定序，以 **varchar(max)** 類型的單一資料列、單一資料行資料列集的形式傳回內容；例如文字或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word 文件。</span><span class="sxs-lookup"><span data-stu-id="40e5a-112">Reads the contents of the specified data file as characters, returns the contents as a single-row, single-column rowset of type **varchar(max)**, using the collation of the current database; such as a text or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word document.</span></span>  
  
 <span data-ttu-id="40e5a-113">SINGLE_NCLOB</span><span class="sxs-lookup"><span data-stu-id="40e5a-113">SINGLE_NCLOB</span></span>  
 <span data-ttu-id="40e5a-114">將指定的資料檔案內容讀取為 Unicode，並使用目前資料庫的定序，以 **nvarchar(max)** 類型的單一資料列、單一資料行資料列集的形式傳回內容。</span><span class="sxs-lookup"><span data-stu-id="40e5a-114">Reads the contents of the specified data file as Unicode, returns the contents as a single-row, single-column rowset of type **nvarchar(max)**, using the collation of the current database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40e5a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40e5a-115">See Also</span></span>  
 <span data-ttu-id="40e5a-116">[使用 BULK INSERT 或 OPENROWSET&#40;BULK...&#41; 匯入大量資料 &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="40e5a-116">[Import Bulk Data by Using BULK INSERT or OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) </span></span>  
 <span data-ttu-id="40e5a-117">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40e5a-117">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="40e5a-118">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40e5a-118">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="40e5a-119">[大量匯入期間保留 Null 或使用預設值 &#40;SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="40e5a-119">[Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md) </span></span>  
 <span data-ttu-id="40e5a-120">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="40e5a-120">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 [<span data-ttu-id="40e5a-121">BULK INSERT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="40e5a-121">BULK INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/bulk-insert-transact-sql)  
  
  
