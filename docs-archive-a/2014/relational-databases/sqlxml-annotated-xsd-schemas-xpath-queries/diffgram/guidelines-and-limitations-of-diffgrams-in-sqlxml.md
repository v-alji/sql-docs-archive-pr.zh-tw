---
title: SQLXML 中的 Diffgram 指導方針和限制 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
author: rothja
ms.author: jroth
ms.openlocfilehash: 0f2901f02f8b4a8fc7b77dcb6c1cb166cb6af6ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596603"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a><span data-ttu-id="8d0d6-102">在 SQLXML 中的 DiffGrams 指導方針和限制</span><span class="sxs-lookup"><span data-stu-id="8d0d6-102">Guidelines and Limitations of DiffGrams in SQLXML</span></span>
  <span data-ttu-id="8d0d6-103">搭配 SQLXML 4.0 使用 DiffGrams 時，請記住以下事項：</span><span class="sxs-lookup"><span data-stu-id="8d0d6-103">Remember the following when using DiffGrams with SQLXML 4.0:</span></span>  
  
-   <span data-ttu-id="8d0d6-104">二進位大型物件 (BLOB) 類型如同 `text/ntext` 和 images，在使用 DiffGrams 時，不得用於 `<diffgr:before>` 區塊，因為這會將它們包含在並行控制中使用。</span><span class="sxs-lookup"><span data-stu-id="8d0d6-104">Binary large object (BLOB) types like `text/ntext` and images should not be used in the `<diffgr:before>` block in when working with DiffGrams, because this will include them for use in concurrency control.</span></span> <span data-ttu-id="8d0d6-105">這可能會因為 BLOB 類型的比較限制而造成 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的問題。</span><span class="sxs-lookup"><span data-stu-id="8d0d6-105">This can cause problems with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] because of the limitations on comparison for BLOB types.</span></span> <span data-ttu-id="8d0d6-106">例如，WHERE 子句中的 LIKE 關鍵字用於 `text` 資料類型之資料行間的比較，不過，如果 BLOB 類型中，資料大小大於 8K，則比較將會失敗。</span><span class="sxs-lookup"><span data-stu-id="8d0d6-106">For example, the LIKE keyword is used in the WHERE clause for comparing between columns of the `text` data type; however, comparisons will fail in the case of BLOB types where the size of the data is greater than 8K.</span></span>  
  
-   <span data-ttu-id="8d0d6-107">`ntext` 資料中的特殊字元可能會因為 BLOB 類型的比較限制而造成 SQLXML 4.0 的問題。</span><span class="sxs-lookup"><span data-stu-id="8d0d6-107">Special characters in `ntext` data can cause problems with SQLXML 4.0 because of the limitations on comparison for BLOB types.</span></span> <span data-ttu-id="8d0d6-108">例如，用於 `<diffgr:before>` 類型之資料行的並行檢查中時，在 DiffGram 的 `ntext` 區塊中使用 "[Serializable]" 將會失敗，並顯示下列 SQLOLEDB 錯誤描述：</span><span class="sxs-lookup"><span data-stu-id="8d0d6-108">For example, the use of "[Serializable]" in the `<diffgr:before>` block of a DiffGram when used in concurrency checking of a column of `ntext` type will fail with the following SQLOLEDB error description:</span></span>  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
