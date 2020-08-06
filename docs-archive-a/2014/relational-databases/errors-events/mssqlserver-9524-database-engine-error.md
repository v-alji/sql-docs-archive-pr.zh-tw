---
title: MSSQLSERVER_9524 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9524 (Database Engine error)
ms.assetid: 12da7931-e124-4466-889c-046f1b7b7bfd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e6c46ee0ef0bd1be299614e2cb04a3d6cd99d92e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595039"
---
# <a name="mssqlserver_9524"></a><span data-ttu-id="6e9b8-102">MSSQLSERVER_9524</span><span class="sxs-lookup"><span data-stu-id="6e9b8-102">MSSQLSERVER_9524</span></span>
    
## <a name="details"></a><span data-ttu-id="6e9b8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6e9b8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6e9b8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6e9b8-104">Product Name</span></span>|<span data-ttu-id="6e9b8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6e9b8-105">SQL Server</span></span>|  
|<span data-ttu-id="6e9b8-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6e9b8-106">Event ID</span></span>|<span data-ttu-id="6e9b8-107">9254</span><span class="sxs-lookup"><span data-stu-id="6e9b8-107">9254</span></span>|  
|<span data-ttu-id="6e9b8-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="6e9b8-108">Event Source</span></span>|<span data-ttu-id="6e9b8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6e9b8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6e9b8-110">元件</span><span class="sxs-lookup"><span data-stu-id="6e9b8-110">Component</span></span>|<span data-ttu-id="6e9b8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6e9b8-111">SQLEngine</span></span>|  
|<span data-ttu-id="6e9b8-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6e9b8-112">Symbolic Name</span></span>|<span data-ttu-id="6e9b8-113">XMLERR_INVALID_COLUMNSET_XML</span><span class="sxs-lookup"><span data-stu-id="6e9b8-113">XMLERR_INVALID_COLUMNSET_XML</span></span>|  
|<span data-ttu-id="6e9b8-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6e9b8-114">Message Text</span></span>|<span data-ttu-id="6e9b8-115">提供的 XML 內容不符合疏鬆資料行集所需的 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="6e9b8-115">The XML content provided does not conform to the required XML format for sparse column sets.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6e9b8-116">說明</span><span class="sxs-lookup"><span data-stu-id="6e9b8-116">Explanation</span></span>  
 <span data-ttu-id="6e9b8-117">嘗試修改資料行集。</span><span class="sxs-lookup"><span data-stu-id="6e9b8-117">An attempt was made to modify a column set.</span></span> <span data-ttu-id="6e9b8-118">資料行集的 XML 內容必須符合資料行集的格式限制。</span><span class="sxs-lookup"><span data-stu-id="6e9b8-118">The XML content of a column set must meet the format restrictions of a column set.</span></span> <span data-ttu-id="6e9b8-119">資料行集的一般格式如下：</span><span class="sxs-lookup"><span data-stu-id="6e9b8-119">The general format of a column set is as follows:</span></span>  
  
 `<column_name_1>value1</column_name_1><column_name_2>value2</column_name_2>...`  
  
 <span data-ttu-id="6e9b8-120">如需有關資料行集的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜使用資料行集＞主題。</span><span class="sxs-lookup"><span data-stu-id="6e9b8-120">For more information about column sets, see the topic "Using Column Sets" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6e9b8-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6e9b8-121">User Action</span></span>  
 <span data-ttu-id="6e9b8-122">更正陳述式內資料行集的 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="6e9b8-122">Correct the format of the XML for the column set in the statement.</span></span>  
  
  
