---
title: '[模擬資訊] 對話方塊 (資料表匯入 Wizard) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.impersonationinfo.f1
ms.assetid: bee7eee5-0650-41f1-a372-5076ae97a58c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5300f8b6106a7f29f51018b4e039c2a8c28aa729
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687329"
---
# <a name="impersonation-information-dialog-box-table-import-wizard"></a><span data-ttu-id="9848d-102">模擬資訊對話方塊 (資料表匯入精靈)</span><span class="sxs-lookup"><span data-stu-id="9848d-102">Impersonation Information Dialog Box (Table Import Wizard)</span></span>
  <span data-ttu-id="9848d-103">使用 **[模擬資訊]** 頁面可指定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 將用來連接資料來源的認證。</span><span class="sxs-lookup"><span data-stu-id="9848d-103">Use the **Impersonation Information** page to specify the credentials that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] will use to connect to the data source.</span></span> <span data-ttu-id="9848d-104">如需有關認證模擬的詳細資訊，請參閱[&#40;SSAS 表格式&#41;](tabular-models/impersonation-ssas-tabular.md)的模擬。</span><span class="sxs-lookup"><span data-stu-id="9848d-104">For more information about credentials impersonation, see [Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="9848d-105">選項</span><span class="sxs-lookup"><span data-stu-id="9848d-105">Options</span></span>  
 <span data-ttu-id="9848d-106">**特定的 Windows 使用者名稱和密碼**</span><span class="sxs-lookup"><span data-stu-id="9848d-106">**Specific Windows user name and password**</span></span>  
 <span data-ttu-id="9848d-107">選取此選項，可讓表格式模型使用指定之 Windows 使用者帳戶的安全性認證。</span><span class="sxs-lookup"><span data-stu-id="9848d-107">Select this option to have the tabular model use the security credentials of a specified Windows user account.</span></span>  
  
 <span data-ttu-id="9848d-108">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="9848d-108">**User name**</span></span>  
 <span data-ttu-id="9848d-109">輸入要使用之使用者帳戶的網域和名稱。</span><span class="sxs-lookup"><span data-stu-id="9848d-109">Type the domain and name of the user account to be used.</span></span> <span data-ttu-id="9848d-110">請使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="9848d-110">Use the following format:</span></span>  
  
 <span data-ttu-id="9848d-111">*\<Domain name>* **\\** *\<User account name>*</span><span class="sxs-lookup"><span data-stu-id="9848d-111">*\<Domain name>* **\\** *\<User account name>*</span></span>  
  
 <span data-ttu-id="9848d-112">唯有選取 **[使用特定的使用者名稱和密碼]** 之後，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="9848d-112">This option is enabled only if **Use a specific name and password** is selected.</span></span>  
  
 <span data-ttu-id="9848d-113">**密碼**</span><span class="sxs-lookup"><span data-stu-id="9848d-113">**Password**</span></span>  
 <span data-ttu-id="9848d-114">輸入表格式模型所要使用之使用者帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="9848d-114">Type the password of the user account to be used by the Tabular model.</span></span>  
  
 <span data-ttu-id="9848d-115">唯有選取 **[使用特定的使用者名稱和密碼]** 之後，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="9848d-115">This option is enabled only if **Use a specific name and password** is selected.</span></span>  
  
 <span data-ttu-id="9848d-116">**服務帳戶**</span><span class="sxs-lookup"><span data-stu-id="9848d-116">**Service account**</span></span>  
 <span data-ttu-id="9848d-117">選取此選項，可使用與管理模型之 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服務相關聯的安全性認證。</span><span class="sxs-lookup"><span data-stu-id="9848d-117">Select this option to use the security credentials associated with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] service that manages the model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9848d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9848d-118">See Also</span></span>  
 [<span data-ttu-id="9848d-119">模擬 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="9848d-119">Impersonation &#40;SSAS Tabular&#41;</span></span>](tabular-models/impersonation-ssas-tabular.md)  
  
  
