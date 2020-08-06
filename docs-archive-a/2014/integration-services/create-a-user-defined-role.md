---
title: 建立使用者定義的角色 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c4128993-2333-48c7-84b1-e51cdcea393d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a0ee905c2636e20315c2180a6be8f8e40f76d5f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594614"
---
# <a name="create-a-user-defined-role"></a><span data-ttu-id="c35e7-102">建立使用者定義角色</span><span class="sxs-lookup"><span data-stu-id="c35e7-102">Create a User-Defined Role</span></span>
    
### <a name="to-create-a-user-defined-role"></a><span data-ttu-id="c35e7-103">建立使用者定義角色</span><span class="sxs-lookup"><span data-stu-id="c35e7-103">To create a user-defined role</span></span>  
  
1.  <span data-ttu-id="c35e7-104">開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c35e7-104">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="c35e7-105">在 **[檢視]** 功能表上，按一下 **[物件總管]** 。</span><span class="sxs-lookup"><span data-stu-id="c35e7-105">Click **Object Explorer** on the **View** menu.</span></span>  
  
3.  <span data-ttu-id="c35e7-106">在 [物件總管] 工具列上，按一下 **[連接]** ，再按一下 **[Database Engine]** 。</span><span class="sxs-lookup"><span data-stu-id="c35e7-106">On the Object Explorer toolbar, click **Connect**, and then click **Database Engine**.</span></span>  
  
4.  <span data-ttu-id="c35e7-107">在 [連接到伺服器]  對話方塊中，提供伺服器名稱並選取驗證模式。</span><span class="sxs-lookup"><span data-stu-id="c35e7-107">In the **Connect to Server** dialog box, provide a server name and select an authentication mode.</span></span> <span data-ttu-id="c35e7-108">您可以使用句號 (.)、(local) 或 `localhost` 表示本機伺服器。</span><span class="sxs-lookup"><span data-stu-id="c35e7-108">You can use a period (.), (local), or `localhost` to indicate the local server.</span></span>  
  
5.  <span data-ttu-id="c35e7-109">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="c35e7-109">Click **Connect**.</span></span>  
  
6.  <span data-ttu-id="c35e7-110">展開 [資料庫]、[系統資料庫]、[msdb]、[安全性] 和 [角色]。</span><span class="sxs-lookup"><span data-stu-id="c35e7-110">Expand Databases, System Databases, msdb, Security, and Roles.</span></span>  
  
7.  <span data-ttu-id="c35e7-111">在 [角色] 節點中，以滑鼠右鍵按一下 [資料庫角色]，並按一下 [新增資料庫角色]  。</span><span class="sxs-lookup"><span data-stu-id="c35e7-111">In the Roles node, right-click Database Roles, and click **New Database Role**.</span></span>  
  
8.  <span data-ttu-id="c35e7-112">在 [一般] 頁面上提供名稱，選擇性地指定擁有者和擁有的結構描述，並加入角色成員。</span><span class="sxs-lookup"><span data-stu-id="c35e7-112">On the General page, provide a name and optionally, specify an owner and owned schemas and add role members.</span></span>  
  
9. <span data-ttu-id="c35e7-113">選擇性地按一下 [權限]  ，並設定物件權限。</span><span class="sxs-lookup"><span data-stu-id="c35e7-113">Optionally, click **Permissions** and configure object permissions.</span></span>  
  
10. <span data-ttu-id="c35e7-114">選擇性地按一下 [擴充屬性]  ，並設定任何擴充屬性。</span><span class="sxs-lookup"><span data-stu-id="c35e7-114">Optionally, click **Extended Properties** and configure any extended properties.</span></span>  
  
11. <span data-ttu-id="c35e7-115">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="c35e7-115">Click **OK**.</span></span>  
  
  
