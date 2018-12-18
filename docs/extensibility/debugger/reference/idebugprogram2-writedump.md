---
title: IDebugProgram2::WriteDump | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3d2953b3f30a0d485b58afc04e8ce42158a7537e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905258"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Výpis zapíše do souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```csharp  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `DumpType`  
 [in] Hodnota z [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) výčet, který určuje typ s výpisem paměti, například řečeno nebo long.  
  
 `pszDumpUrl`  
 [in] Adresa URL s výpisem paměti pro zápis. Obvykle je to ve formě `file://c:\path\filename.ext`, ale mohou být jakákoliv platná adresa URL.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Výpis program obvykle zahrnuje aktuální rámec zásobníku, zásobník samotný seznam vlákna spuštěná v programu a pravděpodobně paměti, která vlastní program.  
  
## <a name="see-also"></a>Viz také  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)