---
title: 開啟物件伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- open objects option
ms.assetid: c8424d3c-86ba-4cc5-bf0c-be4ce44bdd04
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6d22a3d6dd358afe9cf921376664c2d25705a6a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687143"
---
# <a name="open-objects-server-configuration-option"></a><span data-ttu-id="8ff52-102">開啟物件伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="8ff52-102">open objects Server Configuration Option</span></span>
  <span data-ttu-id="8ff52-103">雖然在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中已停用此選項的功能，但此選項仍存在於 **sp_configure** 中。</span><span class="sxs-lookup"><span data-stu-id="8ff52-103">This option is still present in **sp_configure**, although its functionality has been disabled in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8ff52-104">(此設定無效)。在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，已開啟之資料庫物件的數目會受到動態管理，而且只受可用記憶體的限制。</span><span class="sxs-lookup"><span data-stu-id="8ff52-104">(The setting has no effect.) In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the number of open database objects is managed dynamically and is limited only by the available memory.</span></span> <span data-ttu-id="8ff52-105">**open objects** 選項可在 **sp_configure** 中使用，以保有與現有指令碼之間的回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="8ff52-105">The **open objects** option available in **sp_configure** for backward compatibility with existing scripts.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8ff52-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ff52-106">See Also</span></span>  
 [<span data-ttu-id="8ff52-107">伺服器組態選項 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8ff52-107">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
