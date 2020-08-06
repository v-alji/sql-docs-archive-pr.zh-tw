---
title: 資料來源名稱和64位作業系統 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
author: rothja
ms.author: jroth
ms.openlocfilehash: ae31584ca3c076919f688d1ef9bdef80706c6940
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593360"
---
# <a name="data-source-names-and-64-bit-operating-systems"></a><span data-ttu-id="7281a-102">資料來源名稱和 64 位元作業系統</span><span class="sxs-lookup"><span data-stu-id="7281a-102">Data Source Names and 64-Bit Operating Systems</span></span>
  <span data-ttu-id="7281a-103">若要建立並執行應用程式，當做 64 位元作業系統上的 32 位元應用程式，您必須利用 %windir%\SysWOW64\odbcad32.exe，以 ODBC 管理員身分建立 ODBC 資料來源。</span><span class="sxs-lookup"><span data-stu-id="7281a-103">To build and run an application as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7281a-104">備註</span><span class="sxs-lookup"><span data-stu-id="7281a-104">Remarks</span></span>  
 <span data-ttu-id="7281a-105">64 位元的 Windows 作業系統有兩個 odbcad32.exe 檔案：</span><span class="sxs-lookup"><span data-stu-id="7281a-105">A 64-bit Windows operating system has two odbcad32.exe files:</span></span>  
  
-   <span data-ttu-id="7281a-106">%SystemRoot%\system32\odbcad32.exe 用於建立與維持 64 位元應用程式的資料來源名稱。</span><span class="sxs-lookup"><span data-stu-id="7281a-106">%SystemRoot%\system32\odbcad32.exe is used to create and maintain data source names for 64-bit applications.</span></span>  
  
-   <span data-ttu-id="7281a-107">%SystemRoot%\SysWOW64\odbcad32.exe 用於建立與維持 32 位元應用程式的資料來源名稱，包括在 64 位元作業系統上執行的 32 位元應用程式。</span><span class="sxs-lookup"><span data-stu-id="7281a-107">%SystemRoot%\SysWOW64\odbcad32.exe is used to create and maintain data source names for 32-bit applications, including 32-bit applications that run on 64-bit operating systems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7281a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7281a-108">See Also</span></span>  
 [<span data-ttu-id="7281a-109">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="7281a-109">SQL Server Native Client &#40;ODBC&#41;</span></span>](sql-server-native-client-odbc.md)  
  
  
