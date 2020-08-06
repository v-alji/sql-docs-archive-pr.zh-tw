---
title: 工作1：使用主資料管理員建立供應商模型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6bbbcbff-1ecd-456c-947f-c445c8da673c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f6823c96acb7db77a3daafa895f3353b70af44dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699034"
---
# <a name="task-1-creating-suppliers-model-using-master-data-manager"></a><span data-ttu-id="5056d-102">工作 1：使用主資料管理員建立供應商模型</span><span class="sxs-lookup"><span data-stu-id="5056d-102">Task 1: Creating Suppliers Model using Master Data Manager</span></span>
  <span data-ttu-id="5056d-103">在這項工作中，您會使用**主資料管理員**在 MDS 中建立名為「**供應商**」的模型。</span><span class="sxs-lookup"><span data-stu-id="5056d-103">In this task, you create a model named **Suppliers** in MDS using **Master Data Manager**.</span></span>  
  
1.  <span data-ttu-id="5056d-104">流覽至 `http://localhost/MDS` 以啟動**主資料管理員**。</span><span class="sxs-lookup"><span data-stu-id="5056d-104">Navigate to `http://localhost/MDS` to launch **Master Data Manager**.</span></span> <span data-ttu-id="5056d-105">如果您已經使用不同的名稱或在不同網站上設定 Web 應用程式，請替換此 URL。</span><span class="sxs-lookup"><span data-stu-id="5056d-105">Replace the URL if you have configured Web Application with a different name or on a different a web site.</span></span>  
  
     <span data-ttu-id="5056d-106">![主資料管理員 - 系統管理](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-01.jpg "主資料管理員 - 系統管理")</span><span class="sxs-lookup"><span data-stu-id="5056d-106">![Master Data Manager - System Administation](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-01.jpg "Master Data Manager - System Administation")</span></span>  
  
2.  <span data-ttu-id="5056d-107">按一下 [**管理**工作] 區段中的 [**系統管理**]。</span><span class="sxs-lookup"><span data-stu-id="5056d-107">Click **System Administration** in the **Administrative Tasks** section.</span></span>  
  
3.  <span data-ttu-id="5056d-108">如果您看不到 [**加入模型**] 頁面，請在功能表列上將滑鼠停留在 [**管理**] 上，按一下 [**模型**]，然後按一下 [\*\*加入模型 (+) \*\*工具列] 按鈕來建立模型。</span><span class="sxs-lookup"><span data-stu-id="5056d-108">If you do not see the **Add Model** page, hover mouse over **Manage** on the menu bar, click **Models**, and then click **Add Model (+)** toolbar button to create a model.</span></span>  
  
     <span data-ttu-id="5056d-109">![管理 - [模型] 功能表](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-02.jpg "管理 - [模型] 功能表")</span><span class="sxs-lookup"><span data-stu-id="5056d-109">![Manage - Models Menu](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-02.jpg "Manage - Models Menu")</span></span>  
  
     <span data-ttu-id="5056d-110">![[加入模型] 工具列按鈕](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-03.jpg "[加入模型] 工具列按鈕")</span><span class="sxs-lookup"><span data-stu-id="5056d-110">![Add Model Toolbat Button](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-03.jpg "Add Model Toolbat Button")</span></span>  
  
4.  <span data-ttu-id="5056d-111">輸入**供應商**作為 [**型號名稱**]。</span><span class="sxs-lookup"><span data-stu-id="5056d-111">Enter **Suppliers** for **Model name**.</span></span>  
  
5.  <span data-ttu-id="5056d-112">清除 [**建立與模型同名的實體**] 選項。</span><span class="sxs-lookup"><span data-stu-id="5056d-112">Clear **Create entity with same name as model** option.</span></span> <span data-ttu-id="5056d-113">您稍後會使用**適用于 Excel 的 MDS 增益集**來建立實體。</span><span class="sxs-lookup"><span data-stu-id="5056d-113">You will create an entity later using the **MDS Add-in for Excel**.</span></span>  
  
     <span data-ttu-id="5056d-114">![加入模型頁面](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-04.jpg "加入模型頁面")</span><span class="sxs-lookup"><span data-stu-id="5056d-114">![Add Model Page](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-04.jpg "Add Model Page")</span></span>  
  
6.  <span data-ttu-id="5056d-115">按一下工具列上的 [**儲存模型**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5056d-115">Click **Save Model** button on the toolbar.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="5056d-116">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5056d-116">Next Step</span></span>  
 [<span data-ttu-id="5056d-117">工作 2：使用適用於 Excel 的 MDS 增益集將供應商資料上傳到 MDS</span><span class="sxs-lookup"><span data-stu-id="5056d-117">Task 2: Uploading Supplier Data to MDS using MDS Add-in for Excel</span></span>](../../2014/tutorials/task-2-uploading-supplier-data-to-mds-using-mds-add-in-for-excel.md)  
  
  
