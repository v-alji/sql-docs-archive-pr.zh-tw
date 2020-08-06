---
title: " (表格式) 的連接標記法 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 4b410b16-d36e-4185-bb20-922e66e5e2b7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 60f3fdc10baf5dc3be9cd1b0ee6196d2a8da3d2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594233"
---
# <a name="connection-representation-tabular"></a><span data-ttu-id="d3228-102">連接表示法 (表格式)</span><span class="sxs-lookup"><span data-stu-id="d3228-102">Connection Representation (Tabular)</span></span>
  <span data-ttu-id="d3228-103">定義填入表格式模型之資料來源的連接物件。</span><span class="sxs-lookup"><span data-stu-id="d3228-103">The connection object defines the source of the data that populates the tabular model.</span></span>  
  
## <a name="connection-representation"></a><span data-ttu-id="d3228-104">連接表示法</span><span class="sxs-lookup"><span data-stu-id="d3228-104">Connection Representation</span></span>  
 <span data-ttu-id="d3228-105">連接物件的規格遵循 OLE DB 提供者的規則。</span><span class="sxs-lookup"><span data-stu-id="d3228-105">The specification for the connection object follows the rules of OLE DB providers.</span></span>  
  
### <a name="connection-in-amo"></a><span data-ttu-id="d3228-106">AMO 中的連接</span><span class="sxs-lookup"><span data-stu-id="d3228-106">Connection in AMO</span></span>  
 <span data-ttu-id="d3228-107">當您使用 AMO 管理表格式模型資料庫時，AMO 中的 <xref:Microsoft.AnalysisServices.DataSource> 物件與連接邏輯物件會有一對一的相符關係。</span><span class="sxs-lookup"><span data-stu-id="d3228-107">When using AMO to manage a tabular model database, the <xref:Microsoft.AnalysisServices.DataSource> object in AMO matches one-to-one to the connection logical object.</span></span>  
  
 <span data-ttu-id="d3228-108">下列程式碼片段示範如何在表格式模型中建立 AMO 資料來源或連接物件。</span><span class="sxs-lookup"><span data-stu-id="d3228-108">The following code snippet shows how to create an AMO data source, or Connection object in a tabular model.</span></span>  
  
```  
  
//Create an OLEDB connection string  
StringBuilder SqlCnxStr = new StringBuilder();  
SqlCnxStr.Append(String.Format("Data Source={0};" ,SQLServer.Text));  
SqlCnxStr.Append(String.Format("Initial Catalog={0};", SQLDatabase.Text));  
SqlCnxStr.Append(String.Format("Persist Security Info={0};", false));  
SqlCnxStr.Append(String.Format("Integrated Security={0};", "SSPI"));  
SqlCnxStr.Append(String.Format("Provider={0}", "SQLNCLI11"));  
String DatasourceCnxString = SqlCnxStr.ToString();  
  
//Verify connection string and connectivity  
System.Data.OleDb.OleDbConnection OleDbCnx = new System.Data.OleDb.OleDbConnection(DatasourceCnxString);  
try  
{  
    OleDbCnx.Open();  
}  
catch ()  
{  
    throw;  
}  
String newDataSourceName = (string.IsNullOrEmpty(DataSourceName.Text) || string.IsNullOrWhiteSpace(DataSourceName.Text)) ? SQLDatabase.Text : DataSourceName.Text;  
AMO.DataSource newDatasource = newDatabase.DataSources.Add(newDataSourceName, newDataSourceName);  
newDatasource.ConnectionString = DatasourceCnxString.Text;  
if (impersonateServiceAccount.Checked)  
    newDatasource.ImpersonationInfo = new AMO.ImpersonationInfo(AMO.ImpersonationMode.ImpersonateServiceAccount);  
else  
{  
    if (String.IsNullOrEmpty(impersonateAccountUserName.Text))  
    {  
        MessageBox.Show(String.Format("Account User Name cannot be blank when using 'ImpersonateAccount' mode"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
        return;  
    }  
    newDatasource.ImpersonationInfo = new AMO.ImpersonationInfo(AMO.ImpersonationMode.ImpersonateAccount, impersonateAccountUserName.Text, impersonateAccountPassword.Text);  
}  
newDatasource.Update();  
  
```  
  
## <a name="tabular-amo-2012-sample"></a><span data-ttu-id="d3228-109">表格式 AMO 2012 範例</span><span class="sxs-lookup"><span data-stu-id="d3228-109">Tabular AMO 2012 sample</span></span>  
 <span data-ttu-id="d3228-110">若要更了解如何使用 AMO 建立及操作連接表示法，請參閱「表格式 AMO 2012」範例的原始程式碼，特別要檢查以下的原始程式檔：Database.cs。</span><span class="sxs-lookup"><span data-stu-id="d3228-110">To have a better understanding on how to use AMO to create and manipulate connection representations, see source code in the Tabular AMO 2012 sample; specifically check in the following source file: Database.cs.</span></span> <span data-ttu-id="d3228-111">您可以在 Codeplex 上取得範例。</span><span class="sxs-lookup"><span data-stu-id="d3228-111">The sample is available at Codeplex.</span></span> <span data-ttu-id="d3228-112">提供此範例程式碼的用意只是為了支援這裡所說明的邏輯概念，您不應將其用於生產環境。</span><span class="sxs-lookup"><span data-stu-id="d3228-112">Sample code is provided only as a support to the logical concepts explained here, and should not be used in a production environment.</span></span>  
  
  
