---
title: 教學課程：Database Engine 使用者入門 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tutorials [connecting]
- tutorials [Database Engine]
- unable to connect [SQL Server]
- failure to connect [SQL Server]
- connecting tutorial [SQL Server]
ms.assetid: 655e709b-346b-469c-bddc-a5a0238d07e0
author: rothja
ms.author: jroth
ms.openlocfilehash: aaa1fb21c026d064c2b14db73aadc2b82e9c15d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606113"
---
# <a name="tutorial-getting-started-with-the-database-engine"></a><span data-ttu-id="854c8-102">教學課程：Database Engine 使用者入門</span><span class="sxs-lookup"><span data-stu-id="854c8-102">Tutorial: Getting Started with the Database Engine</span></span>
  <span data-ttu-id="854c8-103">歡迎使用 [!INCLUDE[ssDE](../includes/ssde-md.md)] 使用者入門教學課程。</span><span class="sxs-lookup"><span data-stu-id="854c8-103">Welcome to the Getting Started with the [!INCLUDE[ssDE](../includes/ssde-md.md)] tutorial.</span></span> <span data-ttu-id="854c8-104">本教學課程的主要對象是剛接觸 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 且已安裝 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]的使用者。</span><span class="sxs-lookup"><span data-stu-id="854c8-104">This tutorial is intended for users who are new to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and who have installed [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or [!INCLUDE[ssExpress](../includes/ssexpress-md.md)].</span></span> <span data-ttu-id="854c8-105">這個簡短的教學課程可幫助您開始使用 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="854c8-105">This brief tutorial helps you get started using the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="854c8-106">學習內容</span><span class="sxs-lookup"><span data-stu-id="854c8-106">What You Will Learn</span></span>  
 <span data-ttu-id="854c8-107">本教學課程示範如何在本機電腦以及從另一部電腦上使用 [!INCLUDE[ssDE](../includes/ssde-md.md)] 連接到 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="854c8-107">This tutorial shows you how to connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] on both the local computer and from another computer.</span></span>  
  
 <span data-ttu-id="854c8-108">這個教學課程分成兩個課程：</span><span class="sxs-lookup"><span data-stu-id="854c8-108">This tutorial is divided into two lessons:</span></span>  
  
 [<span data-ttu-id="854c8-109">第 1 課：連接到資料庫引擎</span><span class="sxs-lookup"><span data-stu-id="854c8-109">Lesson 1: Connecting to the Database Engine</span></span>](lesson-1-connecting-to-the-database-engine.md)  
 <span data-ttu-id="854c8-110">在這一課，您將學會如何連接到 [!INCLUDE[ssDE](../includes/ssde-md.md)] 並讓其他人可以連接。</span><span class="sxs-lookup"><span data-stu-id="854c8-110">In this lesson, you will learn how to connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] and enable additional people to connect.</span></span>  
  
 [<span data-ttu-id="854c8-111">第 2 課：從另一部電腦連接</span><span class="sxs-lookup"><span data-stu-id="854c8-111">Lesson 2: Connecting from Another Computer</span></span>](lesson-2-connecting-from-another-computer.md)  
 <span data-ttu-id="854c8-112">在這一課，您將學會如何從第二部電腦連接到 [!INCLUDE[ssDE](../includes/ssde-md.md)] ，包括啟用通訊協定、設定通訊埠及設定防火牆設定。</span><span class="sxs-lookup"><span data-stu-id="854c8-112">In this lesson, you will learn how to connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] from a second computer, including enabling protocols, configuring ports, and configuring firewall settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="854c8-113">需求</span><span class="sxs-lookup"><span data-stu-id="854c8-113">Requirements</span></span>  
 <span data-ttu-id="854c8-114">本教學課程沒有知識方面的必要條件。</span><span class="sxs-lookup"><span data-stu-id="854c8-114">This tutorial has no knowledge prerequisites.</span></span>  
  
 <span data-ttu-id="854c8-115">您的系統必須已經安裝下列項目，才能使用這個教學課程：</span><span class="sxs-lookup"><span data-stu-id="854c8-115">Your system must have the following installed to use this tutorial:</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]<span data-ttu-id="854c8-116">第 1 課：建立 Windows Azure 儲存體物件[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="854c8-116">.</span></span> [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] <span data-ttu-id="854c8-117">的安裝方式是執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安裝程式或從 [Microsoft 下載中心](https://go.microsoft.com/fwlink/?LinkId=144346)下載並安裝。</span><span class="sxs-lookup"><span data-stu-id="854c8-117">can be installed by running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] setup or by downloading and installing from [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=144346).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="854c8-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="854c8-118">See Also</span></span>  
 [<span data-ttu-id="854c8-119">教學課程：SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="854c8-119">Tutorial: SQL Server Management Studio</span></span>](../ssms/tutorials/tutorial-sql-server-management-studio.md)  
  
  
