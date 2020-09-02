---
title: IDebugPrimitiveTypeField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugPrimitiveTypeField interface
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad9ff38ae4533f7999b9966c1de32ac77105fcc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188110"
---
# <a name="idebugprimitivetypefield"></a>IDebugPrimitiveTypeField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Představuje hodnotu výčtu primitivního typu z rozhraní [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPrimitiveTypeField : IDebugField  
```  
  
## <a name="methods"></a>Metody  
 Kromě metod v rozhraní [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) implementuje toto rozhraní následující metodu:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|Načte primitivní typ přidružený k tomuto poli.|  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: SH. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
