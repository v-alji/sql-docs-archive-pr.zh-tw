---
title: 尋找報表定義結構描述版本 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- XML schemas [Reporting Services]
- Report Definition Language, XML schema
- schemas [Reporting Services]
ms.assetid: 67954419-1b61-4481-a3b9-23b4ba7a5624
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 413a270a3722ddda1f418c748fa5b7fba50dfeea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700783"
---
# <a name="find-the-report-definition-schema-version-ssrs"></a><span data-ttu-id="7dfd7-102">尋找報表定義結構描述版本 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="7dfd7-102">Find the Report Definition Schema Version (SSRS)</span></span>
  <span data-ttu-id="7dfd7-103">報表定義檔案會針對用來驗證 rdl 檔的報表定義結構描述版本指定 RDL 命名空間。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-103">A report definition file specifies the RDL namespace for the version of the report definition schema that is used to validate the rdl file.</span></span> <span data-ttu-id="7dfd7-104">當您在報表撰寫環境 (例如 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的報表設計師或報表產生器) 中開啟 .rdl 檔案時，如果此報表是針對先前的命名空間所建立，系統就會自動建立備份檔案，而且此報表會升級為目前的命名空間。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-104">When you open an .rdl file in a report authoring environment such as Report Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or Report Builder, if the report was created for a previous namespace, a backup file is automatically created, and the report is upgraded to the current namespace.</span></span> <span data-ttu-id="7dfd7-105">如果您儲存了升級的報表定義，就會儲存轉換的 .rdl 檔。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-105">If you save the upgraded report definition, you have saved the converted .rdl file.</span></span> <span data-ttu-id="7dfd7-106">這是升級報表定義的唯一方式。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-106">This is the only way to upgrade a report definition.</span></span> <span data-ttu-id="7dfd7-107">報表定義本身不會在報表伺服器上升級。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-107">The report definition itself is not upgraded on a report server.</span></span> <span data-ttu-id="7dfd7-108">不過，已編譯的報表會在報表伺服器上升級。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-108">The compiled report is upgraded on a report server.</span></span> <span data-ttu-id="7dfd7-109">如需詳細資訊，請參閱 [Upgrade Reports](../install-windows/upgrade-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-109">For more information, see [Upgrade Reports](../install-windows/upgrade-reports.md).</span></span>  
  
### <a name="how-to-identify-the-rdl-schema-version-of-a-report"></a><span data-ttu-id="7dfd7-110">如何：識別報表的 RDL 結構描述版本</span><span class="sxs-lookup"><span data-stu-id="7dfd7-110">How to: Identify the RDL Schema Version of a Report</span></span>  
  
1.  <span data-ttu-id="7dfd7-111">在可以檢視 xml 的應用程式 (例如 [記事本] 或 XML Notepad 2007) 中開啟 .rdl 檔案。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-111">Open the report .rdl file in an application such as Notepad or XML Notepad 2007 in which you can view the xml.</span></span>  
  
     <span data-ttu-id="7dfd7-112">XML 報表元素會指定結構描述命名空間。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-112">The XML Report element specifies the schema namespace.</span></span> <span data-ttu-id="7dfd7-113">例如，下列報表元素會指定報表設計師的命名空間以及報表定義的命名空間。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-113">For example, the following Report element specifies the namespace for Report Designer and the namespace for the report definition.</span></span>  
  
    ```  
    <Report xmlns:rd=https://schemas.microsoft.com/SQLServer/reporting/reportdesigner   
    xmlns="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition">  
    ```  
  
     <span data-ttu-id="7dfd7-114">報表定義命名空間是由下列 URL 指定： `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-114">The report definition namespace is specified by the following URL: `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`.</span></span>  
  
### <a name="how-to-identify-the-rdl-schema-version-of-report-designer"></a><span data-ttu-id="7dfd7-115">如何：識別報表設計師的 RDL 結構描述版本</span><span class="sxs-lookup"><span data-stu-id="7dfd7-115">How to: Identify the RDL Schema Version of Report Designer</span></span>  
  
1.  <span data-ttu-id="7dfd7-116">開啟新的專案。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-116">Open a new project.</span></span> <span data-ttu-id="7dfd7-117">您所選擇的專案版本會決定 RDL 結構描述的版本。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-117">The version of the project that you choose determines the version of the RDL schema.</span></span> <span data-ttu-id="7dfd7-118">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中支援多個結構描述版本。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-118">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], more than one schema version is supported.</span></span> <span data-ttu-id="7dfd7-119">如需詳細資訊，請參閱 [Deployment and Version Support in SQL Server Data Tools &#40;SSRS&#41;](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-119">For more information, see [Deployment and Version Support in SQL Server Data Tools &#40;SSRS&#41;](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="7dfd7-120">在 [專案]\*\*\*\* 功能表上，按一下 [加入新項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-120">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="7dfd7-121">[新增項目]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-121">The **Add New Item** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="7dfd7-122">在 [範本]\*\*\*\* 窗格中，按一下 [報表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-122">In the **Templates** pane, click **Report**.</span></span>  
  
4.  <span data-ttu-id="7dfd7-123">在 [名稱]\*\*\*\* 中，鍵入報表名稱或接受預設值。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-123">In **Name**, type a report name or accept the default.</span></span>  
  
5.  <span data-ttu-id="7dfd7-124">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-124">Click **Add**.</span></span> <span data-ttu-id="7dfd7-125">報表設計師就會在 [設計] 檢視中開啟新的空白報表。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-125">Report Designer opens a new blank report in Design view.</span></span>  
  
6.  <span data-ttu-id="7dfd7-126">在 [檢視]\*\*\*\* 功能表中，按一下 [程式碼]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-126">On the **View** menu, click **Code**.</span></span> <span data-ttu-id="7dfd7-127">報表定義就會顯示成 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-127">The report definition is displayed as an XML file.</span></span>  
  
     <span data-ttu-id="7dfd7-128">XML 報表元素會指定結構描述命名空間。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-128">The XML Report element specifies the schema namespace.</span></span> <span data-ttu-id="7dfd7-129">例如，下列報表元素會指定報表設計師的命名空間以及報表定義的命名空間。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-129">For example, the following Report element specifies the namespace for Report Designer and the namespace for the report definition.</span></span>  
  
    ```  
    <Report xmlns:rd=https://schemas.microsoft.com/SQLServer/reporting/reportdesigner  
    xmlns="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition">  
    ```  
  
     <span data-ttu-id="7dfd7-130">報表定義命名空間是由下列 URL 指定： `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`</span><span class="sxs-lookup"><span data-stu-id="7dfd7-130">The report definition namespace is specified by the following URL: `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`</span></span>  
  
### <a name="how-to-identify-the-rdl-schema-version-on-the-report-server"></a><span data-ttu-id="7dfd7-131">如何：識別報表伺服器的 RDL 結構描述版本</span><span class="sxs-lookup"><span data-stu-id="7dfd7-131">How to: Identify the RDL Schema Version on the Report Server</span></span>  
  
-   <span data-ttu-id="7dfd7-132">在報表管理員中，輸入報表伺服器的 URL。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-132">In Report Manager, type the URL for the report server.</span></span> <span data-ttu-id="7dfd7-133">例如，下列 URL 會指定本機電腦上的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-133">For example, the following URL specifies a report server on the local computer:</span></span>  
  
     `http://localhost/reportserver/reportdefinition.xsd`  
  
     <span data-ttu-id="7dfd7-134">.xsd 檔就會在瀏覽器中開啟。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-134">The .xsd file opens in the browser.</span></span>  
  
     <span data-ttu-id="7dfd7-135">XML 結構描述元素會指定結構描述命名空間。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-135">The XML schema element specifies the schema namespace.</span></span> <span data-ttu-id="7dfd7-136">例如，下列結構描述元素會指定三個命名空間： [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]在內部使用的 targetNamespace 參考、結構描述本身 (xsd) 的 xsd 參考，以及報表定義參考。</span><span class="sxs-lookup"><span data-stu-id="7dfd7-136">For example, the following schema element specifies three namespaces: the targetNamespace reference that is used internally by [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], the xsd reference for the schema itself (xsd), and the report definition reference.</span></span>  
  
    ```  
    <xsd:schema   
    targetNamespace="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition"   
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
    xmlns="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition"   
    elementFormDefault="qualified">  
    ```  
  
     <span data-ttu-id="7dfd7-137">報表定義命名空間是由下列 URL 指定： `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`</span><span class="sxs-lookup"><span data-stu-id="7dfd7-137">The report definition namespace is specified by the following URL: `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dfd7-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7dfd7-138">See Also</span></span>  
 <span data-ttu-id="7dfd7-139">[升級報表](../install-windows/upgrade-reports.md) </span><span class="sxs-lookup"><span data-stu-id="7dfd7-139">[Upgrade Reports](../install-windows/upgrade-reports.md) </span></span>  
 [<span data-ttu-id="7dfd7-140">報表定義語言 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7dfd7-140">Report Definition Language &#40;SSRS&#41;</span></span>](report-definition-language-ssrs.md)  
  
  
