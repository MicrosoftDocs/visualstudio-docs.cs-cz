---
title: GETNAME_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 648f84b106dab7aa6e38cc3e45e59162a216a875
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160142"
---
# <a name="getname_type"></a>GETNAME_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje název typu souborů, které se mají načíst.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
typedef DWORD GETNAME_TYPE;  
```  
  
```csharp  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## <a name="members"></a>Členové  
 GN_NAME  
 Určuje popisný název dokumentu nebo kontextu.  
  
 GN_FILENAME  
 Určuje úplnou cestu dokumentu nebo kontextu.  
  
 GN_BASENAME  
 Určuje základní název souboru místo úplné cesty dokumentu nebo kontextu.  
  
 GN_MONIKERNAME  
 Určuje jedinečný název dokumentu nebo kontextu ve formě monikeru.  
  
 GN_URL  
 Určuje název adresy URL dokumentu nebo kontextu.  
  
 GN_TITLE  
 Určuje název dokumentu, pokud existuje.  
  
 GN_STARTPAGEURL  
 Získá úvodní adresu URL stránky pro procesy.  
  
## <a name="remarks"></a>Poznámky  
 Tyto hodnoty jsou předány jako parametry metodám [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)a [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) , aby určily, jaký typ názvu se má vrátit.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
