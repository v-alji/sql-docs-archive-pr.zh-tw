---
title: 伺服器設定-定序 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- collation configuration, SQL Server
- collation configuration, Setup
- collation configuration
ms.assetid: e3986870-5be4-458b-b671-5ff12a27b022
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d06735590d23da6e91151202dd421639ea433b97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598131"
---
# <a name="server-configuration---collation"></a><span data-ttu-id="29667-102">伺服器組態 - 定序</span><span class="sxs-lookup"><span data-stu-id="29667-102">Server Configuration - Collation</span></span>
  <span data-ttu-id="29667-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝精靈的 [伺服器組態 - 定序] 頁面上，您可以修改 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 用於排序的定序設定。</span><span class="sxs-lookup"><span data-stu-id="29667-103">On the Server Configuration - Collation page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard, you can modify collation settings that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] use for sorting purposes.</span></span> <span data-ttu-id="29667-104">選取選項來比對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或另一部電腦之不同安裝的定序設定。</span><span class="sxs-lookup"><span data-stu-id="29667-104">Select the option to match collation settings of different installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or of another computer.</span></span>  
  
## <a name="options"></a><span data-ttu-id="29667-105">選項</span><span class="sxs-lookup"><span data-stu-id="29667-105">Options</span></span>  
 <span data-ttu-id="29667-106">針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 而自訂</span><span class="sxs-lookup"><span data-stu-id="29667-106">Customize for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="29667-107">提供了兩組定序：Windows 定序和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 定序。</span><span class="sxs-lookup"><span data-stu-id="29667-107">provides two groups of collations: Windows collations and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] collations.</span></span> <span data-ttu-id="29667-108">您可以對 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]指定個別的定序設定，也可以對這兩者指定相同的定序。</span><span class="sxs-lookup"><span data-stu-id="29667-108">You can specify separate collation settings for the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], or you can specify the same collation for both.</span></span>  
  
 <span data-ttu-id="29667-109">根據預設，系統會針對 US-English 系統地區設定選取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 定序。</span><span class="sxs-lookup"><span data-stu-id="29667-109">By default, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] collation is selected for US-English system locales.</span></span> <span data-ttu-id="29667-110">當地語系化 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本的預設定序是由電腦的 Windows 系統地區設定所決定。</span><span class="sxs-lookup"><span data-stu-id="29667-110">The default collation for localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is determined by the Windows system locale setting for your computer.</span></span>  
  
 <span data-ttu-id="29667-111">只有當這個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝的定序設定必須符合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的另一個執行個體所使用的定序設定，或是定序設定必須符合另一部電腦的 Windows 系統地區設定時，您才應該變更預設設定。</span><span class="sxs-lookup"><span data-stu-id="29667-111">The default settings should be changed only if the collation setting for this installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must match the collation settings used by another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or if it must match the Windows system locale of another computer.</span></span>  
  
 <span data-ttu-id="29667-112">**注意** [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 只會使用 Windows 定序。</span><span class="sxs-lookup"><span data-stu-id="29667-112">**Note** [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses Windows collations only.</span></span> <span data-ttu-id="29667-113">如果您打算安裝 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]，請在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝期間選取 Windows 定序，以便確保 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 與 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]之間產生一致的結果。</span><span class="sxs-lookup"><span data-stu-id="29667-113">If you plan to install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], select a Windows collation during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to ensure consistent results between the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="29667-114">如需詳細資訊，請參閱＜ [安裝程式中的定序設定](https://go.microsoft.com/fwlink/?LinkId=190977)＞。</span><span class="sxs-lookup"><span data-stu-id="29667-114">For more information, see [Collation Settings in Setup](https://go.microsoft.com/fwlink/?LinkId=190977).</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="29667-115">最佳做法</span><span class="sxs-lookup"><span data-stu-id="29667-115">Best Practices</span></span>  
 <span data-ttu-id="29667-116">如需 Windows 系統地區設定和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式所使用之對應預設定序的資料表的詳細資訊，請參閱 [安裝程式中的定序設定](https://go.microsoft.com/fwlink/?LinkId=190977)。</span><span class="sxs-lookup"><span data-stu-id="29667-116">For more information about a table of Windows System locales and the corresponding default collations used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup, see [Collation Settings in Setup](https://go.microsoft.com/fwlink/?LinkId=190977).</span></span>  
  
 <span data-ttu-id="29667-117">如果可能的話，請針對組織使用單一定序。</span><span class="sxs-lookup"><span data-stu-id="29667-117">If it is possible, use a single collation for your organization.</span></span> <span data-ttu-id="29667-118">這樣您就不需要針對每個資料庫、資料行、運算式或識別碼明確指定定序。</span><span class="sxs-lookup"><span data-stu-id="29667-118">This way, you do not have to explicitly specify the collation for every database, column, expression, or identifier.</span></span> <span data-ttu-id="29667-119">如果您必須使用多重定序和字碼頁設定，則在編寫查詢程式碼時，必須考量定序優先順序的規則。</span><span class="sxs-lookup"><span data-stu-id="29667-119">If you must work with multiple collations and code page settings, code your queries to consider the rules of collation precedence.</span></span> <span data-ttu-id="29667-120">如需詳細資訊，請參閱[定序優先順序 &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql) 的線上叢書主題。</span><span class="sxs-lookup"><span data-stu-id="29667-120">For more information, see the Books Online topic for [Collation Precedence &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql).</span></span>  
  
 <span data-ttu-id="29667-121">當您選取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的定序時，請考慮下列建議：</span><span class="sxs-lookup"><span data-stu-id="29667-121">When you select a collation for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consider the following recommendations:</span></span>  
  
-   <span data-ttu-id="29667-122">如果可接受以二進位字碼指標為基礎的排序，請選取 BINARY2 定序。</span><span class="sxs-lookup"><span data-stu-id="29667-122">Select a BINARY2 collation if binary code point based ordering is acceptable.</span></span>  
  
-   <span data-ttu-id="29667-123">選取 Windows 定序以便跨資料類型進行一致的比較。</span><span class="sxs-lookup"><span data-stu-id="29667-123">Select a Windows collation for consistent comparison across data types.</span></span>  
  
-   <span data-ttu-id="29667-124">為獲得更好的語言排序支援，請使用新的 100 層級定序。</span><span class="sxs-lookup"><span data-stu-id="29667-124">Use a new 100-level collation for better linguistic sorting support.</span></span> <span data-ttu-id="29667-125">如需詳細資訊，請參閱 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)。</span><span class="sxs-lookup"><span data-stu-id="29667-125">For more information, see [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).</span></span>  
  
-   <span data-ttu-id="29667-126">如果您計畫將資料庫移轉到升級的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體，請選取符合您現有資料庫定序的定序。</span><span class="sxs-lookup"><span data-stu-id="29667-126">If you plan to migrate a database to the upgraded instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], select the collation that matches your existing collation of the database.</span></span>  
  
  
