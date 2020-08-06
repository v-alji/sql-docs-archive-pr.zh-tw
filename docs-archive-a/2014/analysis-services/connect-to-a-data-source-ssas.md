---
title: 連接到 (SSAS) 的資料來源 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.conndatasource.f1
ms.assetid: 1e2b17e9-092b-4af1-8a58-c52b8fe10ff1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4fe7f7d5b31118369b8ce2a855b955e44f661dbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593030"
---
# <a name="connect-to-a-data-source-ssas"></a><span data-ttu-id="84f2b-102">連接到資料來源 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="84f2b-102">Connect to a Data Source (SSAS)</span></span>
  <span data-ttu-id="84f2b-103">**[資料表匯入精靈]** 的這個頁面可讓您建立與各種資料來源之間的新資料來源連接，例如關聯式資料庫、資料摘要和檔案等資料來源。</span><span class="sxs-lookup"><span data-stu-id="84f2b-103">This page of the **Table Import Wizard** enables you to create a new data source connection to a variety of data sources, such as relational databases, data feeds, and files.</span></span> <span data-ttu-id="84f2b-104">若要從 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]存取精靈，請按一下 **[模型]** 功能表上的 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="84f2b-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="84f2b-105">若要連接至資料來源，您必須先在機器上安裝適當的提供者。</span><span class="sxs-lookup"><span data-stu-id="84f2b-105">To connect to a data source, you must have the appropriate provider installed on your machine.</span></span> <span data-ttu-id="84f2b-106">您必須將適當的提供者安裝在工作空間資料庫伺服器上。</span><span class="sxs-lookup"><span data-stu-id="84f2b-106">You must also have the appropriate provider installed on the workspace database server.</span></span> <span data-ttu-id="84f2b-107">若是 32 位元 (x86) 伺服器，必須安裝 32 位元提供者。</span><span class="sxs-lookup"><span data-stu-id="84f2b-107">For 32-bit (x86) servers, 32-bit providers must be installed.</span></span> <span data-ttu-id="84f2b-108">若是 64 位元 (x64) 伺服器，必須安裝 64 位元提供者。</span><span class="sxs-lookup"><span data-stu-id="84f2b-108">For 64-bit (x64) servers, 64-bit providers must be installed.</span></span>  
  
 <span data-ttu-id="84f2b-109">不管架構為何，[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 一律在 32 位元處理序下執行。</span><span class="sxs-lookup"><span data-stu-id="84f2b-109">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] always runs in a 32-bit process, regardless of architecture.</span></span> <span data-ttu-id="84f2b-110">在 64 位元機器上執行 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 時，如果要安裝資料提供者，您應該注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="84f2b-110">When running [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] on a 64-bit machine, you should be aware of the following when installing data providers:</span></span>  
  
-   <span data-ttu-id="84f2b-111">針對支援並行安裝 32 位元和 64 位元提供者的提供者，您必須同時安裝兩個提供者。</span><span class="sxs-lookup"><span data-stu-id="84f2b-111">For providers that support side-by-side installation of 32-bit and 64-bit providers, you should install both providers.</span></span>  
  
-   <span data-ttu-id="84f2b-112">至於 ACE 提供者，您必須安裝 64 位元版本的提供者。</span><span class="sxs-lookup"><span data-stu-id="84f2b-112">For the ACE provider, you must install the 64-bit version of the provider.</span></span> <span data-ttu-id="84f2b-113">由於 Office 會自動安裝 ACE 提供者，因此您不應該在裝載工作空間資料庫次無器的 64 位元機器上執行 32 位元版本的 Microsoft Office。</span><span class="sxs-lookup"><span data-stu-id="84f2b-113">Because Office automatically installs the ACE provider, you should not run a 32-bit version of Microsoft Office on a 64-bit machine hosting the workspace database server.</span></span>  
  
     <span data-ttu-id="84f2b-114">ACE 提供者用來從文字檔、Excel 檔和 Access 檔匯入。</span><span class="sxs-lookup"><span data-stu-id="84f2b-114">The ACE provider is used to import from Text, Excel, and Access files.</span></span> <span data-ttu-id="84f2b-115">如果不需要這些資料來源的支援，您可以在執行 64 位元工作空間資料庫伺服器的機器上，執行 32 位元版本的 Microsoft Office。</span><span class="sxs-lookup"><span data-stu-id="84f2b-115">If support for these data sources is not needed, you can then run a 32-bit version of Microsoft Office on a machine running a 64-bit workspace database server.</span></span>  
  
-   <span data-ttu-id="84f2b-116">針對不支援並行安裝 32 位元和 64 位元提供者的其他提供者，您必須安裝 32 位元提供者。</span><span class="sxs-lookup"><span data-stu-id="84f2b-116">For other providers that do not support side-by-side installation of 32-bit and 64-bit providers, you must install the 32-bit provider.</span></span> <span data-ttu-id="84f2b-117">如果只有 64 位元機器可以使用，您必須使用遠端機器，並將 64 位元提供者安裝為工作空間資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="84f2b-117">If only 64-bit machines are available, you must use a remote machine with a 64-bit provider installed as the workspace database server.</span></span>  
  
  
