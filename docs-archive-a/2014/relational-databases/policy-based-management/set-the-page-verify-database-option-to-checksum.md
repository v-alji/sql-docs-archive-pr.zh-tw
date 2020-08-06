---
title: 將 PAGE_VERIFY 資料庫選項設定為 CHECKSUM | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 13296a976722390668b8ca6d901cf0dd080e5cc3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708197"
---
# <a name="set-the-page_verify-database-option-to-checksum"></a><span data-ttu-id="ee237-102">將 PAGE_VERIFY 資料庫選項設定為 CHECKSUM</span><span class="sxs-lookup"><span data-stu-id="ee237-102">Set the PAGE_VERIFY Database Option to CHECKSUM</span></span>
  <span data-ttu-id="ee237-103">這個規則會檢查 PAGE_VERIFY 資料庫選項是否設定為 CHECKSUM。</span><span class="sxs-lookup"><span data-stu-id="ee237-103">This rule checks whether PAGE_VERIFY database option is set to CHECKSUM.</span></span> <span data-ttu-id="ee237-104">當針對 PAGE_VERIFY 資料庫選項啟用 CHECKSUM 時， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 會針對整頁的內容計算總和檢查碼，並在將頁面寫入磁碟時，於頁首中儲存值。</span><span class="sxs-lookup"><span data-stu-id="ee237-104">When CHECKSUM is enabled for the PAGE_VERIFY database option, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] calculates a checksum over the contents of the whole page, and stores the value in the page header when a page is written to disk.</span></span> <span data-ttu-id="ee237-105">從磁碟讀取頁面時，會重新計算總和檢查碼，並與頁首所儲存的總和檢查碼值作比較。</span><span class="sxs-lookup"><span data-stu-id="ee237-105">When the page is read from disk, the checksum is recomputed and compared to the checksum value that is stored in the page header.</span></span> <span data-ttu-id="ee237-106">如此有助於提供高層級的資料檔完整性。</span><span class="sxs-lookup"><span data-stu-id="ee237-106">This helps provide a high level of data-file integrity.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="ee237-107">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="ee237-107">Best Practices Recommendations</span></span>  
 <span data-ttu-id="ee237-108">將 PAGE_VERIFY 資料庫選項設定為 CHECKSUM。</span><span class="sxs-lookup"><span data-stu-id="ee237-108">Set the PAGE_VERIFY database option to CHECKSUM.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="ee237-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="ee237-109">For More Information</span></span>  
 [<span data-ttu-id="ee237-110">ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ee237-110">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  
