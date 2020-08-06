---
title: 大量複製文字和影像資料 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
author: rothja
ms.author: jroth
ms.openlocfilehash: 9240fd0eb8c32ed39613824ea5a07764e277160c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606827"
---
# <a name="bulk-copying-text-and-image-data"></a><span data-ttu-id="93d77-102">大量複製 Text 與 Image 資料</span><span class="sxs-lookup"><span data-stu-id="93d77-102">Bulk Copying Text and Image Data</span></span>
  <span data-ttu-id="93d77-103">大型**text**、 **Ntext**和**image**值會使用[bcp_moretext](../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)函數進行大量複製。</span><span class="sxs-lookup"><span data-stu-id="93d77-103">Large **text**, **ntext**, and **image** values are bulk copied using the [bcp_moretext](../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) function.</span></span> <span data-ttu-id="93d77-104">您會將**text**、 **Ntext**或**image**資料行的程式碼[bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) ，並將*pData*指標設定為 Null，表示將會提供**bcp_moretext**的資料。</span><span class="sxs-lookup"><span data-stu-id="93d77-104">You code [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) for the **text**, **ntext**, or **image** column with a *pData* pointer set to NULL indicating the data will be provided with **bcp_moretext**.</span></span> <span data-ttu-id="93d77-105">請務必指定為每個大量複製資料列中的每個**text**、 **Ntext**或**image**資料行所提供的確切資料長度。</span><span class="sxs-lookup"><span data-stu-id="93d77-105">It is important to specify the exact length of data supplied for each **text**, **ntext**,or **image** column in each bulk-copied row.</span></span> <span data-ttu-id="93d77-106">如果資料行的資料長度與[bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)中指定的資料行長度不同，請使用[bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)將長度設定為適當的值。</span><span class="sxs-lookup"><span data-stu-id="93d77-106">If the length of the data for a column is different from the column length specified in [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md), use [bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) to set the length to the proper value.</span></span> <span data-ttu-id="93d77-107">[Bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)傳送所有非**文字**、非**Ntext**和非**影像**的資料;接著，您可以呼叫**bcp_moretext** ，以不同的單位傳送**text**、 **Ntext**或**image**資料。</span><span class="sxs-lookup"><span data-stu-id="93d77-107">A [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) sends all the non-**text**, non-**ntext**, and non-**image** data; you then call **bcp_moretext** to send the **text**, **ntext**, or **image** data in separate units.</span></span> <span data-ttu-id="93d77-108">大量複製函數會在透過**bcp_moretext**傳送的資料長度總和等於最新**bcp_collen**或**bcp_bind**中指定的長度時，判斷所有資料都已傳送給目前的**text**、 **Ntext**或**image**資料行。</span><span class="sxs-lookup"><span data-stu-id="93d77-108">Bulk copy functions determine that all data has been sent for the current **text**, **ntext**, or **image** column when the sum of the lengths of data sent through **bcp_moretext** equals the length specified in the latest **bcp_collen** or **bcp_bind**.</span></span>  
  
 <span data-ttu-id="93d77-109">**bcp_moretext**沒有用來識別資料行的參數。</span><span class="sxs-lookup"><span data-stu-id="93d77-109">**bcp_moretext** has no parameter to identify a column.</span></span> <span data-ttu-id="93d77-110">當資料列中有多個**text**、 **Ntext**或**image**資料行時， **bcp_moretext**會在**text**、 **Ntext**或**image**資料行上操作，並以具有最低序數的資料行為開頭，並繼續進行序號最高的資料行。</span><span class="sxs-lookup"><span data-stu-id="93d77-110">When there are multiple **text**, **ntext**, or **image** columns in a row, **bcp_moretext** operates on the **text**, **ntext**, or **image** columns starting with the column having the lowest ordinal number and proceeding to the column with the highest ordinal number.</span></span> <span data-ttu-id="93d77-111">當所傳送資料的長度總和等於最新**bcp_collen**或目前資料行**bcp_bind**中指定的長度時， **bcp_moretext**會從一個資料行移到下一個。</span><span class="sxs-lookup"><span data-stu-id="93d77-111">**bcp_moretext** goes from one column to the next when the sum of the lengths of data sent equals the length specified in the latest **bcp_collen** or **bcp_bind** for the current column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93d77-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93d77-112">See Also</span></span>  
 [<span data-ttu-id="93d77-113">&#40;ODBC&#41;執行大量複製作業</span><span class="sxs-lookup"><span data-stu-id="93d77-113">Performing Bulk Copy Operations &#40;ODBC&#41;</span></span>](performing-bulk-copy-operations-odbc.md)  
  
  
