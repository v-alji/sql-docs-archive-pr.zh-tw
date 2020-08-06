---
title: 使用自訂字典自訂斷詞工具行為 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9fb02a47da20134925d9b2486ea0c08091af4aa6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700987"
---
# <a name="customize-the-behavior-of-word-breakers-with-a-custom-dictionary"></a><span data-ttu-id="473bf-102">使用自訂字典自訂斷詞工具行為</span><span class="sxs-lookup"><span data-stu-id="473bf-102">Customize the Behavior of Word Breakers with a Custom Dictionary</span></span>
  <span data-ttu-id="473bf-103">您可以建立語言特有自訂字典檔案，以自訂特定語言之斷詞工具的行為。</span><span class="sxs-lookup"><span data-stu-id="473bf-103">You can customize the behavior of the word breaker for a particular language by creating a language-specific custom dictionary file.</span></span> <span data-ttu-id="473bf-104">例如，您可以防止斷詞工具中斷特定詞彙或模式。</span><span class="sxs-lookup"><span data-stu-id="473bf-104">For example, you can prevent the word breaker from breaking certain terms or patterns.</span></span>  
  
 <span data-ttu-id="473bf-105">如需詳細資訊，請參閱下列 SharePoint 文章：</span><span class="sxs-lookup"><span data-stu-id="473bf-105">For more information, see the following SharePoint article:</span></span>  
  
 [<span data-ttu-id="473bf-106">建立自訂字典 (SharePoint Server 2010)</span><span class="sxs-lookup"><span data-stu-id="473bf-106">Create a custom dictionary (SharePoint Server 2010)</span></span>](https://go.microsoft.com/fwlink/?LinkId=215011)  
  
 <span data-ttu-id="473bf-107">針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，將自訂字典檔案放入下列資料夾中：</span><span class="sxs-lookup"><span data-stu-id="473bf-107">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], place custom dictionary files in the following folder:</span></span>  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 <span data-ttu-id="473bf-108">建立或變更自訂字典檔案之後，請使用下列命令重新啟動 SQL 全文檢索背景程式啟動器：</span><span class="sxs-lookup"><span data-stu-id="473bf-108">After creating or changing custom dictionary files, restart the SQL Full-text Daemon Launcher with the following command:</span></span>  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
  
