---
title: 步驟 2：將專案轉換成專案部署模型 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 80964293-f1f5-4da7-b1fb-00ab8c30c1c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a7b879b2bea4afd58a48cdfc6f0890353fe6758
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592109"
---
# <a name="step-2-converting-the-project-to-the-project-deployment-model"></a><span data-ttu-id="a67f7-102">步驟 2:將專案轉換成專案部署模型</span><span class="sxs-lookup"><span data-stu-id="a67f7-102">Step 2: Converting the Project to the Project Deployment Model</span></span>
  <span data-ttu-id="a67f7-103">在這個工作中，您將使用 Integration Services 專案轉換精靈，將專案轉換為專案部署模型。</span><span class="sxs-lookup"><span data-stu-id="a67f7-103">In this task, you will use the Integration Services Project Conversion Wizard to convert the project to the Project Deployment Model.</span></span>  
  
### <a name="converting-the-project-to-the-project-deployment-model"></a><span data-ttu-id="a67f7-104">將專案轉換成專案部署模型</span><span class="sxs-lookup"><span data-stu-id="a67f7-104">Converting the Project to the Project Deployment Model</span></span>  
  
1.  <span data-ttu-id="a67f7-105">在 [專案] 功能表上，按一下 [轉換為專案部署模型]。</span><span class="sxs-lookup"><span data-stu-id="a67f7-105">On the Project Menu, click Convert to Project Deployment Model.</span></span>  
  
2.  <span data-ttu-id="a67f7-106">在 Integration Services 專案轉換精靈簡介頁面上檢閱步驟，然後按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="a67f7-106">On the Integration Services Project Conversion Wizard Introduction page, review the steps then click Next.</span></span>  
  
3.  <span data-ttu-id="a67f7-107">在 [選取封裝] 頁面上，在封裝清單中，清除 [Lesson 6.dtsx] 以外的所有核取方塊，然後按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="a67f7-107">On the Select Packages page, in the Packages list, clear all checkboxes except Lesson 6.dtsx then click Next.</span></span>  
  
4.  <span data-ttu-id="a67f7-108">在指定專案屬性頁面上，按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="a67f7-108">On the Specify Project Properties page, click Next.</span></span>  
  
5.  <span data-ttu-id="a67f7-109">在 [更新執行封裝工作] 頁面上按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="a67f7-109">On the Update Execute Package Task page click Next.</span></span>  
  
6.  <span data-ttu-id="a67f7-110">在 [選取組態] 頁面上，確定已選取 [設定] 清單中的 Lesson 6.dtsx 封裝，然後按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="a67f7-110">On the Select Configurations page, make sure the Lesson 6.dtsx package is selected in the Configurations list, then click Next.</span></span>  
  
7.  <span data-ttu-id="a67f7-111">在 [建立參數] 頁面上確認已在 [組態屬性] 清單中選取 Lesson 6.dtsx 封裝，以及範圍會設定為封裝，然後按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="a67f7-111">On the Create Parameters page make sure the Lesson 6.dtsx package is selected, and the Scope is set to Package, in the Configuration Properties List, then Click Next.</span></span>  
  
8.  <span data-ttu-id="a67f7-112">在 [設定參數] 頁面上確認名稱和值的值同於第 5 課中指定變數值和設定值，然後按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="a67f7-112">On the Configure Parameters page verify that the values for Name and Value are the same name and value specified in Lesson 5 for the variable and configuration value, then click Next.</span></span>  
  
9. <span data-ttu-id="a67f7-113">在 [檢閱] 頁面，在 [摘要] 窗格，請注意精靈已經用從組態檔的資訊來設定轉換屬性。</span><span class="sxs-lookup"><span data-stu-id="a67f7-113">On the Review page, in the Summary pane, notice that the wizard has used the information from the configuration file to set the Properties to be converted.</span></span>  
  
10. <span data-ttu-id="a67f7-114">按一下 [轉換]。</span><span class="sxs-lookup"><span data-stu-id="a67f7-114">Click Convert.</span></span>  
  
     <span data-ttu-id="a67f7-115">當轉換完成時，會顯示訊息警告不會儲存變更，直到專案儲存在 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="a67f7-115">When the conversion completes a message is displayed warning that the changes are not saved until the project is saved in Visual Studio.</span></span> <span data-ttu-id="a67f7-116">在警告對話方塊中按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="a67f7-116">Click OK on the warning dialog.</span></span>  
  
11. <span data-ttu-id="a67f7-117">按一下 [Integration Services 專案轉換精靈] 的 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="a67f7-117">On the Integration Services Project Conversion Wizard click Close.</span></span>  
  
12. <span data-ttu-id="a67f7-118">在 SQL Server Data Tools，按一下 [檔案] 功能表，然後按一下 [儲存] 儲存轉換的封裝。</span><span class="sxs-lookup"><span data-stu-id="a67f7-118">In SQL Server Data Tools, click the File menu, then click Save to save the converted package.</span></span>  
  
13. <span data-ttu-id="a67f7-119">按一下 [參數] 索引標籤，並確認封裝現在包含 VarFolderName 參數，而值的路徑同於從第 5 課組態檔的新範例資料資料夾所指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="a67f7-119">Click the Parameters Tab and verify that the package now contains a parameter for VarFolderName and that the value is the same path specified for the New Sample Data folder from the Lesson 5 configuration file.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="a67f7-120">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="a67f7-120">Next Task in Lesson</span></span>  
 [<span data-ttu-id="a67f7-121">步驟 3：測試第 6 課的封裝</span><span class="sxs-lookup"><span data-stu-id="a67f7-121">Step 3: Testing the Lesson 6 Package</span></span>](lesson-6-3-testing-the-lesson-6-package.md)  
  
  
