---
title: 將結果集傳送到伺服器 (擴充預存程式 API) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
author: rothja
ms.author: jroth
ms.openlocfilehash: 82984440f96416189eb18f900764ee7bdaf05a01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584518"
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a><span data-ttu-id="28a0a-102">將結果集傳送到伺服器 (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="28a0a-102">Sending Result Sets to the Server (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="28a0a-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="28a0a-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="28a0a-104">將結果集傳送至時 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，擴充預存程式應該呼叫適當的 API，如下所示：</span><span class="sxs-lookup"><span data-stu-id="28a0a-104">When sending a result set to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the extended stored procedure should call the appropriate API as follows:</span></span>  
  
-   <span data-ttu-id="28a0a-105">**Srv_sendmsg**函數可以在所有資料列之前或之後的任何順序中呼叫， (是否已有任何) 與**srv_sendrow**一起傳送。</span><span class="sxs-lookup"><span data-stu-id="28a0a-105">The **srv_sendmsg** function may be called in any order before or after all rows (if any) have been sent with **srv_sendrow**.</span></span> <span data-ttu-id="28a0a-106">在以**srv_senddone**傳送完成狀態之前，所有訊息都必須傳送至用戶端。</span><span class="sxs-lookup"><span data-stu-id="28a0a-106">All messages must be sent to the client before the completion status is sent with **srv_senddone**.</span></span>  
  
-   <span data-ttu-id="28a0a-107">系統會針對傳送到用戶端的每個資料列，呼叫 **srv_sendrow** 函式一次。</span><span class="sxs-lookup"><span data-stu-id="28a0a-107">The **srv_sendrow** function is called once for each row sent to the client.</span></span> <span data-ttu-id="28a0a-108">所有的資料列都必須先傳送給用戶端，才會使用**srv_sendmsg**、 **srv_pfield**的**srv_status**引數或**srv_senddone**來傳送任何訊息、狀態值或完成狀態。</span><span class="sxs-lookup"><span data-stu-id="28a0a-108">All rows must be sent to the client before any messages, status values, or completion statuses are sent with **srv_sendmsg**, the **srv_status** argument of **srv_pfield**, or **srv_senddone**.</span></span>  
  
-   <span data-ttu-id="28a0a-109">傳送尚未以**srv_describe**定義之所有資料行的資料列，會導致應用程式引發參考用錯誤訊息，並將失敗傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="28a0a-109">Sending a row that has not had all its columns defined with **srv_describe** causes the application to raise an informational error message and return FAIL to the client.</span></span> <span data-ttu-id="28a0a-110">在此情況下，不會傳送資料列。</span><span class="sxs-lookup"><span data-stu-id="28a0a-110">In this case, the row is not sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28a0a-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28a0a-111">See Also</span></span>  
 [<span data-ttu-id="28a0a-112">建立擴充預存程序</span><span class="sxs-lookup"><span data-stu-id="28a0a-112">Creating Extended Stored Procedures</span></span>](creating-extended-stored-procedures.md)  
  
  
