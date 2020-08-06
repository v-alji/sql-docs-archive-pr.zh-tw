---
title: 工作4：使用 SQL Server Data Tools 建立 SSIS 專案 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 8603ea91-2ec4-40b6-8070-4f824332f5d3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 07976dbd2c84b1385d79ce3f4ce4f616e0f706b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702174"
---
# <a name="task-4-creating-an-ssis-project-using-sql-server-data-tools"></a><span data-ttu-id="1294b-102">工作 4：使用 SQL Server Data Tools 建立 SSIS 專案</span><span class="sxs-lookup"><span data-stu-id="1294b-102">Task 4: Creating an SSIS Project using SQL Server Data Tools</span></span>
  <span data-ttu-id="1294b-103">在這項工作中，您會使用**SQL Server Data Tools**來建立 SSIS 專案，以自動化清理和比對供應商資料。</span><span class="sxs-lookup"><span data-stu-id="1294b-103">In this task, you create an SSIS project by using **SQL Server Data Tools** to automate cleansing and matching supplier data.</span></span>

1.  <span data-ttu-id="1294b-104">啟動 **SQL Server Data Tools**。</span><span class="sxs-lookup"><span data-stu-id="1294b-104">Launch **SQL Server Data Tools**.</span></span> <span data-ttu-id="1294b-105">按一下 [開始]，指向 [**所有程式**]，展開 [ **Microsoft SQL Server 2012**]，然後按一下 [ **SQL Server Data Tools**]。</span><span class="sxs-lookup"><span data-stu-id="1294b-105">Click Start, point to **All Programs**, expand **Microsoft SQL Server 2012**, and click **SQL Server Data Tools**.</span></span>

2.  <span data-ttu-id="1294b-106">在 [ **檔案** ] 功能表中，指向 [ **新增**]，然後按一下 [ **專案**]。</span><span class="sxs-lookup"><span data-stu-id="1294b-106">On the **File** menu, point to **New**, and click **Project**.</span></span>

3.  <span data-ttu-id="1294b-107">展開 [**已安裝的範本**] 窗格中的 [**商業智慧**]，然後選取 [ **Integration Services**]。</span><span class="sxs-lookup"><span data-stu-id="1294b-107">Expand **Business Intelligence** in the **Installed Templates** pane, and select **Integration Services**.</span></span>

     <span data-ttu-id="1294b-108">![Visual Studio - [新增專案] 對話方塊](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-01.jpg "Visual Studio - [新增專案] 對話方塊")</span><span class="sxs-lookup"><span data-stu-id="1294b-108">![Visual Studio - New Project Dialog Box](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-01.jpg "Visual Studio - New Project Dialog Box")</span></span>

4.  <span data-ttu-id="1294b-109">在**專案類型清單**中，選取 [ **Integration Services 專案**]。</span><span class="sxs-lookup"><span data-stu-id="1294b-109">Select **Integration Services Project** in the **list of project types**.</span></span>

5.  <span data-ttu-id="1294b-110">針對 [**名稱**] 輸入**CleanseAndCurateSuppliers** ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="1294b-110">Type **CleanseAndCurateSuppliers** for **Name** and click **OK**.</span></span>

6.  <span data-ttu-id="1294b-111">在**方案總管**] 視窗中，以滑鼠右鍵按一下 **.dtsx** ，然後選取 [**重新命名**]。</span><span class="sxs-lookup"><span data-stu-id="1294b-111">In **Solution Explorer** window, right-click **Package.dtsx** and select **Rename**.</span></span> <span data-ttu-id="1294b-112">如果您沒有看到 [**方案總管**] 視窗，請按一下功能表列上的 [**查看**]，然後按一下 [**方案總管**]。</span><span class="sxs-lookup"><span data-stu-id="1294b-112">If you don't see **Solution Explorer** window, click **View** on the menu bar and click **Solution Explorer**.</span></span>

     <span data-ttu-id="1294b-113">![Package.dtsx - [重新命名] 功能表](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-02.jpg "Package.dtsx - [重新命名] 功能表")</span><span class="sxs-lookup"><span data-stu-id="1294b-113">![Package.dtsx - Rename Menu](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-02.jpg "Package.dtsx - Rename Menu")</span></span>

7.  <span data-ttu-id="1294b-114">輸入**cleanseandcurate.cleanse supplier data.guid. .dtsx** ，然後按**enter**。</span><span class="sxs-lookup"><span data-stu-id="1294b-114">Type **CleanseAndCurate.dtsx** and press **ENTER**.</span></span> <span data-ttu-id="1294b-115">請確定**擴充**功能保持不變 **。 .dtsx**。</span><span class="sxs-lookup"><span data-stu-id="1294b-115">Make sure that the **extension** remains **.dtsx**.</span></span>

## <a name="next-step"></a><span data-ttu-id="1294b-116">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1294b-116">Next Step</span></span>
 [<span data-ttu-id="1294b-117">工作 5：新增資料流程工作</span><span class="sxs-lookup"><span data-stu-id="1294b-117">Task 5: Adding Data Flow Task</span></span>](task-5-adding-data-flow-task.md)


