---
title: Unicode 資料和伺服器字碼頁 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- metadata [SQL Server], stored procedures
- Unicode [SQL Server], extended stored procedures
- extended stored procedures [SQL Server], metadata
ms.assetid: 52310260-a892-4b27-ad2e-bf164b98ee80
author: rothja
ms.author: jroth
ms.openlocfilehash: e88a43ee242e9fa84ac3a5573c7d3ca3dc0369d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584515"
---
# <a name="unicode-data-and-server-code-pages"></a><span data-ttu-id="3fe54-102">Unicode 資料和伺服器字碼頁</span><span class="sxs-lookup"><span data-stu-id="3fe54-102">Unicode Data and Server Code Pages</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="3fe54-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="3fe54-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="3fe54-104">擴充預存程序 API 會針對 Unicode 資料而啟用，但不會針對 Unicode 中繼資料啟用。</span><span class="sxs-lookup"><span data-stu-id="3fe54-104">The Extended Stored Procedure API is enabled for Unicode data; however, it is not enabled for Unicode metadata.</span></span> <span data-ttu-id="3fe54-105">#define Unicode 指示詞在擴充預存程序 API 上沒有任何效果。</span><span class="sxs-lookup"><span data-stu-id="3fe54-105">The #define Unicode directive does not have any effect on the Extended Stored Procedure API.</span></span>  
  
 <span data-ttu-id="3fe54-106">所有由擴充預存程序 API 所傳回的或藉由擴充預存程序應用程式而提供給擴充預存程序 API 的中繼資料，都假設位在伺服器多位元組字碼頁中。</span><span class="sxs-lookup"><span data-stu-id="3fe54-106">All metadata returned by, or provided to the Extended Stored Procedure API by your extended stored procedure application is assumed to be in the multibyte code page of the server.</span></span> <span data-ttu-id="3fe54-107">擴充預存程式 API 伺服器應用程式的預設字碼頁是執行應用程式之電腦的 ANSI 字碼頁，可以藉由呼叫**srv_pfield**並將 field 參數設定為 SRV_SPROC_CODEPAGE 來取得。</span><span class="sxs-lookup"><span data-stu-id="3fe54-107">The default code page of an Extended Stored Procedure API server application is the ANSI code page of the computer on which the application is running, which can be obtained by calling **srv_pfield** with the field parameter set to SRV_SPROC_CODEPAGE.</span></span>  
  
 <span data-ttu-id="3fe54-108">如果擴充預存程序 API 應用程式已啟用 Unicode，則您必須先將 Unicode 中繼資料的資料行名稱、錯誤訊息等等轉換為多位元組資料，才能將此資料傳遞給擴充預存程序 API。</span><span class="sxs-lookup"><span data-stu-id="3fe54-108">If your Extended Stored Procedure API application is Unicode-enabled, you must convert your Unicode metadata column names, error messages, and so on, to multibyte data before passing this data to the Extended Stored Procedure API.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fe54-109">範例</span><span class="sxs-lookup"><span data-stu-id="3fe54-109">Example</span></span>  
 <span data-ttu-id="3fe54-110">下列擴充預存程序提供所討論的 Unicode 轉換的範例。</span><span class="sxs-lookup"><span data-stu-id="3fe54-110">The following extended stored procedure provides an example of the Unicode conversions discussed.</span></span> <span data-ttu-id="3fe54-111">請注意：</span><span class="sxs-lookup"><span data-stu-id="3fe54-111">Note that:</span></span>  
  
-   <span data-ttu-id="3fe54-112">資料行會以 Unicode 資料的形式傳遞至**srv_describe** ，因為 SRVNVARCHAR 描述該資料行。</span><span class="sxs-lookup"><span data-stu-id="3fe54-112">Column data is passed as Unicode data to **srv_describe** because the column is described to be SRVNVARCHAR.</span></span>  
  
-   <span data-ttu-id="3fe54-113">資料行名稱中繼資料會傳遞至**srv_describe**做為多位元組資料。</span><span class="sxs-lookup"><span data-stu-id="3fe54-113">Column name metadata is passed to **srv_describe** as multibyte data.</span></span>  
  
     <span data-ttu-id="3fe54-114">擴充預存程式會呼叫**srv_pfield**並將 field 參數設定為 SRV_SPROC_CODEPAGE，以取得的多位元組字碼頁 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3fe54-114">The extended stored procedure calls **srv_pfield** with the field parameter set to SRV_SPROC_CODEPAGE to obtain the multibyte code page of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="3fe54-115">錯誤訊息會以多位元組資料的形式傳遞至**srv_sendmsg** 。</span><span class="sxs-lookup"><span data-stu-id="3fe54-115">Error messages are passed to **srv_sendmsg** as multibyte data.</span></span>  
  
    ```  
    __declspec(dllexport) RETCODE proc1 (SRV_PROC *srvproc)  
    {  
        #define MAX_COL_NAME_LEN 25  
        #define MAX_COL_DATA_LEN 50  
        #define MAX_ERR_MSG_LEN 250  
        #define MAX_SERVER_ERROR 20000  
        #define XP_ERROR_NUMBER MAX_SERVER_ERROR+1  
  
        int retval;  
        UINT serverCodePage;  
        CHAR *szServerCodePage;  
  
        WCHAR unicodeColumnName[MAX_COL_NAME_LEN];  
        CHAR multibyteColumnName[MAX_COL_NAME_LEN];  
  
        WCHAR unicodeColumnData[MAX_COL_DATA_LEN];  
  
        WCHAR unicodeErrorMessage[MAX_ERR_MSG_LEN];  
        CHAR  multibyteErrorMessage[MAX_ERR_MSG_LEN];  
  
        lstrcpyW (unicodeColumnName, L"column1");  
        lstrcpyW (unicodeColumnData, L"column1 data");  
        lstrcpyW (unicodeErrorMessage, L"No Error!");  
  
        // Obtain server code page.  
        //  
        szServerCodePage = srv_pfield (srvproc, SRV_SPROC_CODEPAGE, NULL);      
        if (NULL != szServerCodePage)  
            serverCodePage = atol(szServerCodePage);  
        else   
        {   // Problem situation exists.  
            srv_senddone(srvproc, (SRV_DONE_ERROR | SRV_DONE_MORE), 0, 0);  
            return 1;  
        }  
  
        // Convert column name for Unicode to multibyte using the   
        // server code page.  
        //  
        retval = WideCharToMultiByte(    
            serverCodePage,                 // code page  
            0,                              // default  
            unicodeColumnName,              // wide-character string  
            -1,                             // string is null terminated  
            multibyteColumnName,            // address of buffer for new  
                                            //   string  
            sizeof (multibyteColumnName),   // size of buffer  
            NULL, NULL);  
  
        if (0 == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"Conversion to multibyte  
            failed.");  
            goto Error;  
        }  
  
        retval = srv_describe (srvproc, 1, multibyteColumnName,  
        SRV_NULLTERM,   
          SRVNVARCHAR, MAX_COL_DATA_LEN*sizeof(WCHAR), // destination  
            SRVNVARCHAR, lstrlenW(unicodeColumnData)*sizeof(WCHAR),  
            unicodeColumnData); //source  
        if (FAIL == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"srv_describe failed.");  
            goto Error;  
        }  
  
       retval = srv_sendrow(srvproc);  
        if (FAIL == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"srv_sendrow failed.");  
            goto Error;  
        }  
  
        retval = srv_senddone (srvproc, SRV_DONE_MORE|SRV_DONE_COUNT, 0, 1);  
        if (FAIL == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"srv_senddone failed.");  
            goto Error;  
        }  
  
        return 0;  
    Error:  
        // convert error message from Unicode to multibyte.  
        retval = WideCharToMultiByte(    
            serverCodePage,                 // code page  
            0,                              // default  
            unicodeErrorMessage,            // wide-character string  
            -1,                             // string is null terminated  
            multibyteErrorMessage,          // address of buffer for new  
                                            //   string  
            sizeof (multibyteErrorMessage), // size of buffer  
            NULL, NULL);  
  
    srv_sendmsg(srvproc, SRV_MSG_ERROR, XP_ERROR_NUMBER, SRV_INFO, 1,  
                NULL, 0, __LINE__,   
                multibyteErrorMessage,  
                SRV_NULLTERM);  
  
        srv_senddone(srvproc, (SRV_DONE_ERROR | SRV_DONE_MORE), 0, 0);  
  
        return 1;  
    }  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3fe54-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fe54-116">See Also</span></span>  
 [<span data-ttu-id="3fe54-117">srv_wsendmsg &#40;擴充預存程式 API&#41;</span><span class="sxs-lookup"><span data-stu-id="3fe54-117">srv_wsendmsg &#40;Extended Stored Procedure API&#41;</span></span>](../extended-stored-procedures-reference/srv-wsendmsg-extended-stored-procedure-api.md)  
  
  
