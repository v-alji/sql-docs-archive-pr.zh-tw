---
title: 連線到 Oracle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- connOra
ms.assetid: 711ac7ff-5d3d-4533-80ca-d1fecdb3048f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e6546e3bbde666107ed7757c41d98d5b7b598924
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706669"
---
# <a name="connect-to-oracle"></a><span data-ttu-id="b17e5-102">連接到 Oracle</span><span class="sxs-lookup"><span data-stu-id="b17e5-102">Connect to Oracle</span></span>
  <span data-ttu-id="b17e5-103">當您初次加入或編輯 CDC 執行個體中使用的資料表時，系統可能會要求您連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b17e5-103">When you add or edit the tables used in the CDC instance for the first time, you may be asked to connect to the Oracle database.</span></span> <span data-ttu-id="b17e5-104">您應該輸入可以存取要擷取之資料表結構描述的 Oracle 使用者認證。</span><span class="sxs-lookup"><span data-stu-id="b17e5-104">You should enter the credentials of an Oracle user who can access the schema of the tables to be captured.</span></span> <span data-ttu-id="b17e5-105">請在此對話方塊中輸入以下資訊：</span><span class="sxs-lookup"><span data-stu-id="b17e5-105">Enter the following in this dialog box:</span></span>  
  
 <span data-ttu-id="b17e5-106">**驗證**</span><span class="sxs-lookup"><span data-stu-id="b17e5-106">**Authentication**</span></span>  
  
 <span data-ttu-id="b17e5-107">選取下列其中一個：</span><span class="sxs-lookup"><span data-stu-id="b17e5-107">Select one of the following:</span></span>  
  
-   <span data-ttu-id="b17e5-108">**Windows 驗證**：選取此選項可使用目前的 Windows 網域認證。</span><span class="sxs-lookup"><span data-stu-id="b17e5-108">**Windows Authentication**: Select this to use the current Windows domain credentials.</span></span> <span data-ttu-id="b17e5-109">只有當設定 Oracle 資料庫使用 Windows 驗證時，才可使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="b17e5-109">You can use this option only if the Oracle database is configured to work with Windows authentication.</span></span>  
  
-   <span data-ttu-id="b17e5-110">**Oracle 驗證**：如果您選取這個選項，您必須在您所連接的 Oracle 資料庫中輸入使用者的 **[使用者名稱]** 和 **[密碼]** 。</span><span class="sxs-lookup"><span data-stu-id="b17e5-110">**Oracle Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the Oracle database you are connecting to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b17e5-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b17e5-111">See Also</span></span>  
 [<span data-ttu-id="b17e5-112">將資料表新增至 CDC 執行個體</span><span class="sxs-lookup"><span data-stu-id="b17e5-112">Add Tables to a CDC Instance</span></span>](add-tables-to-a-cdc-instance.md)  
  
  
