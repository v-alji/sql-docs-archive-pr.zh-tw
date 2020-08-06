---
title: SqlToolsVSNativeHelpers | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: d33cb556-0380-490a-9220-b74062dbd6d9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 84f8a3a3408b68cb8c389b05b417f391a1f86c93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710493"
---
# <a name="sqltoolsvsnativehelpers"></a><span data-ttu-id="d1656-102">SqlToolsVSNativeHelpers</span><span class="sxs-lookup"><span data-stu-id="d1656-102">SqlToolsVSNativeHelpers</span></span>
  <span data-ttu-id="d1656-103">在 Visual Studio 中支援 SQL Server 功能的程式庫。</span><span class="sxs-lookup"><span data-stu-id="d1656-103">Library that supports SQL Server functionality in Visual Studio.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1656-104">語法</span><span class="sxs-lookup"><span data-stu-id="d1656-104">Syntax</span></span>  
  
```  
  
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID /*lpReserved*/)  
```  
  
## <a name="return-value"></a><span data-ttu-id="d1656-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="d1656-105">Return Value</span></span>  
 <span data-ttu-id="d1656-106">如果 DLL 進入點正確初始化，則為布林值 `True`，否則為 `False`。</span><span class="sxs-lookup"><span data-stu-id="d1656-106">A Boolean value, `True` if the DLL entry point initialized properly, otherwise `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1656-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1656-107">See Also</span></span>  
 [<span data-ttu-id="d1656-108">FrameWindowVisible</span><span class="sxs-lookup"><span data-stu-id="d1656-108">FrameWindowVisible</span></span>](sqltoolsvsnativehelpers-framewindowvisible.md)  
  
  
