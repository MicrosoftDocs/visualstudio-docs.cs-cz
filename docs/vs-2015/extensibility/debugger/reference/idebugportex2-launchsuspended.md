---
title: 'IDebugPortEx2:: LaunchSuspended | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3c5e57c003257650f5ca60d4a7c3d9becea3e776
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188458"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spustí spustitelný soubor.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT LaunchSuspended(   
   LPCOLESTR        pszExe,  
   LPCOLESTR        pszArgs,  
   LPCOLESTR        pszDir,  
   BSTR             bstrEnv,  
   DWORD            hStdInput,  
   DWORD            hStdOutput,  
   DWORD            hStdError,  
   IDebugProcess2** ppPortProcess  
);  
```  
  
```csharp  
int LaunchSuspended(   
   string             pszExe,  
   string             pszArgs,  
   string             pszDir,  
   string             bstrEnv,  
   uint               hStdInput,  
   uint               hStdOutput,  
   uint               hStdError,  
   out IDebugProcess2 ppPortProcess  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszExe`  
 pro Název spustitelného souboru, který se má spustit. Může to být úplná cesta nebo relativní vzhledem k pracovnímu adresáři zadanému v `pszDir` parametru.  
  
 `pszArgs`  
 pro Argumenty, které se mají předat spustitelnému souboru. Může být hodnota null, pokud nejsou žádné argumenty.  
  
 `pszDir`  
 pro Název pracovního adresáře používaného spustitelným souborem. Může být hodnota null, pokud není potřeba žádný pracovní adresář.  
  
 `bstrEnv`  
 pro Blok prostředí řetězců zakončených hodnotou null následovaný dodatečným ukončovacím znakem NULL.  
  
 `hStdInput`  
 pro Zpracování alternativního vstupního datového proudu. Může být 0, pokud není vyžadováno přesměrování.  
  
 `hStdOutput`  
 pro Zpracování alternativního výstupního datového proudu. Může být 0, pokud není vyžadováno přesměrování.  
  
 `hStdError`  
 pro Zpracování alternativního výstupního datového proudu chyb. Může být 0, pokud není vyžadováno přesměrování.  
  
 `ppPortProcess`  
 mimo Vrátí objekt [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) , který představuje spuštěný proces.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda by měla spustit proces, aby byla pozastavena a nespouštěla žádný kód. Metoda [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) je volána pro pokračování procesu.  
  
 Program lze také spustit z ladicího stroje. Podrobnosti najdete v tématu [spuštění programu](../../../extensibility/debugger/launching-a-program.md).  
  
## <a name="see-also"></a>Viz také  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [Spuštění programu](../../../extensibility/debugger/launching-a-program.md)
