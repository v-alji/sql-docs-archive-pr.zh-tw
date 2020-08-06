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
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a>將結果集傳送到伺服器 (擴充預存程序 API)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 請改用 CLR 整合。  
  
 將結果集傳送至時 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，擴充預存程式應該呼叫適當的 API，如下所示：  
  
-   **Srv_sendmsg**函數可以在所有資料列之前或之後的任何順序中呼叫， (是否已有任何) 與**srv_sendrow**一起傳送。 在以**srv_senddone**傳送完成狀態之前，所有訊息都必須傳送至用戶端。  
  
-   系統會針對傳送到用戶端的每個資料列，呼叫 **srv_sendrow** 函式一次。 所有的資料列都必須先傳送給用戶端，才會使用**srv_sendmsg**、 **srv_pfield**的**srv_status**引數或**srv_senddone**來傳送任何訊息、狀態值或完成狀態。  
  
-   傳送尚未以**srv_describe**定義之所有資料行的資料列，會導致應用程式引發參考用錯誤訊息，並將失敗傳回給用戶端。 在此情況下，不會傳送資料列。  
  
## <a name="see-also"></a>另請參閱  
 [建立擴充預存程序](creating-extended-stored-procedures.md)  
  
  
