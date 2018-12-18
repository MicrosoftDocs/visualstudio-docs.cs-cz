---
title: PROCESS_INFO_FLAGS | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 453c976ec4dd1c0c0b1c1e67592f840c17a9ac9e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726790"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Popisuje nebo určuje vlastnosti procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```csharp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## <a name="members"></a>Členové  
 PIFLAG_SYSTEM_PROCESS  
 Označuje, že proces je systémový proces.  
  
 PIFLAG_DEBUGGER_ATTACHED  
 Označuje, že proces je laděn ladicím programem. Může se jednat [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ladicího programu, nebo mohou být některé další ladicího programu, například WinDbg.  
  
 PIFLAG_PROCESS_STOPPED  
 Označuje, že proces se ukončí. Platí, pouze pokud `PIFLAG_DEBUGGER_ATTACHED` taky. K dispozici v [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] a novější.  
  
 PIFLAG_PROCESS_RUNNING  
 Označuje, že je proces spuštěn. Platí, pouze pokud `PIFLAG_DEBUGGER_ATTACHED` taky. K dispozici v [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] a novější.  
  
## <a name="remarks"></a>Poznámky  
 Používá pro `Flags` člena [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struktury.  
  
 Tyto příznaky lze kombinovat pomocí logické bitové `OR`.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)

