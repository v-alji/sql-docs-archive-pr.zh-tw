---
title: 如何：部署自訂報表項目 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, deploying
ms.assetid: 80e97b0d-e355-4240-aebd-08cbc84089ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 66519610526478caadeb41b48c9823414e88d5d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708993"
---
# <a name="how-to-deploy-a-custom-report-item"></a><span data-ttu-id="975aa-102">如何：部署自訂報表項目</span><span class="sxs-lookup"><span data-stu-id="975aa-102">How to: Deploy a Custom Report Item</span></span>
  <span data-ttu-id="975aa-103">若要在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中部署自訂報表項目，您必須修改報表伺服器組態檔，並將設計階段和執行階段元件組件複製到適當的報表設計師和報表伺服器應用程式資料夾中。</span><span class="sxs-lookup"><span data-stu-id="975aa-103">To deploy a custom report item in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must modify the report server configuration files and copy the design-time and run-time component assemblies into the appropriate application folders for both Report Designer and the report server.</span></span>  
  
### <a name="to-deploy-a-custom-report-item"></a><span data-ttu-id="975aa-104">部署自訂報表項目</span><span class="sxs-lookup"><span data-stu-id="975aa-104">To deploy a custom report item</span></span>  
  
1.  <span data-ttu-id="975aa-105">編輯 Rsreportdesigner.config 檔案，將自訂報表項目執行階段和設計階段元件設定為用於設計工具：</span><span class="sxs-lookup"><span data-stu-id="975aa-105">Edit the Rsreportdesigner.config file to configure the custom report item run-time and design-time components for use in the designer.</span></span> <span data-ttu-id="975aa-106">請注意，`ReportItemName` 項目必須符合用於 `CustomReportItemAttribute` 類別的 `CustomReportItemDesigner` 屬性。</span><span class="sxs-lookup"><span data-stu-id="975aa-106">Note that the `ReportItemName` entry must match the `CustomReportItemAttribute` attribute used in your `CustomReportItemDesigner` class.</span></span> <span data-ttu-id="975aa-107">例如：</span><span class="sxs-lookup"><span data-stu-id="975aa-107">For example:</span></span>  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    <ReportItemDesigner>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsDesigner, PolygonsDesigner" />  
    </ReportItemDesigner>  
    <ReportItemConverter>  
       <Converter Source="Chart" Target="Polygons" Type="PolygonsCRI.PolygonsConverter, PolygonsDesigner" />  
    </ReportItemConverter>  
    ```  
  
2.  <span data-ttu-id="975aa-108">編輯 Rsreportserver.config 檔案來註冊自訂表單項目執行階段元件。</span><span class="sxs-lookup"><span data-stu-id="975aa-108">Edit the Rsreportserver.config file to register the custom report item run-time component.</span></span> <span data-ttu-id="975aa-109">例如：</span><span class="sxs-lookup"><span data-stu-id="975aa-109">For example:</span></span>  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    ```  
  
3.  <span data-ttu-id="975aa-110">編輯 Rsssrvpolicy.config 檔案以加入 `CodeGroup`，將適當的權限授與自訂報表項目。</span><span class="sxs-lookup"><span data-stu-id="975aa-110">Edit the Rsssrvpolicy.config file to add a `CodeGroup` that grants the proper permissions to the custom report item.</span></span> <span data-ttu-id="975aa-111">例如：</span><span class="sxs-lookup"><span data-stu-id="975aa-111">For example:</span></span>  
  
    ```  
    <CodeGroup   
       class="UnionCodeGroup"   
       version="1"   
       PermissionSetName="FullTrust"  
       Description="This code group grants MyCustomReportItem.dll FullTrust permission. ">  
       <IMembershipCondition   
          class="UrlMembershipCondition"  
          version="1"  
       Url="C:\Program Files\Microsoft SQL Server\ MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin\MyCustomReportItem.dll" />  
    </CodeGroup>  
    ```  
  
4.  <span data-ttu-id="975aa-112">將自訂報表項目執行階段元件 DLL 複製到 %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies and \Program Files\Microsoft SQL Server\MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin 目錄。</span><span class="sxs-lookup"><span data-stu-id="975aa-112">Copy the custom report item run-time component DLL to the %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies and \Program Files\Microsoft SQL Server\MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin directories.</span></span>  
  
5.  <span data-ttu-id="975aa-113">將自訂報表項目設計階段元件 DLL 複製到 %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies 目錄。</span><span class="sxs-lookup"><span data-stu-id="975aa-113">Copy the custom report item design-time component DLL to the %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="975aa-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="975aa-114">See Also</span></span>  
 <span data-ttu-id="975aa-115">[Reporting Services 組態檔](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="975aa-115">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 [<span data-ttu-id="975aa-116">自訂報表項目類別庫</span><span class="sxs-lookup"><span data-stu-id="975aa-116">Custom Report Item Class Libraries</span></span>](custom-report-item-class-libraries.md)  
  
  
