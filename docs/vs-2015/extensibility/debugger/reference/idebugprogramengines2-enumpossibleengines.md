---
title: 'IDebugProgramEngines2:: EnumPossibleEngines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a417fd4f0d90ffebd291179dee28a0e81f92cce9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182191"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vrátí identifikátory GUID pro všechny možné moduly ladění (DE), které mohou ladit tento program.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```csharp  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celtBuffer`  
 pro Počet identifikátorů DE GUID, které se mají vrátit. To také určuje maximální velikost `rgguidEngines` pole.  
  
 `rgguidEngines`  
 [in, out] Pole identifikátoru GUID, které se mají vyplnit.  
  
 `pceltEngines`  
 mimo Vrátí skutečný počet identifikátorů DE GUID, které jsou vráceny.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. Vrátí [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` nebo [C#] 0x8007007A, pokud vyrovnávací paměť není dostatečně velká.  
  
## <a name="remarks"></a>Poznámky  
 Aby bylo možné zjistit, kolik modulů existuje, zavolejte tuto metodu jednou s `celtBuffer` parametrem nastaveným na hodnotu 0 a `rgguidEngines` parametr nastavte na hodnotu null. Vrátí `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A pro C#) a `pceltEngines` parametr vrátí potřebnou velikost vyrovnávací paměti.  
  
## <a name="see-also"></a>Viz také  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
