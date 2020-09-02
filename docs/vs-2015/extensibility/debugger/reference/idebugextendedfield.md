---
title: IDebugExtendedField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8001ced3ba2116ec8ff76ecdac2d0789304335e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547244"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Rozšiřuje typy polí, která jsou k dispozici pro podporu obecných kódů spravovaného kódu.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugExtendedField : IDebugField  
```  
  
## <a name="methods"></a>Metody  
 Kromě metod v rozhraní [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) toto rozhraní implementuje následující metody:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Načte zadaný rozšířený typ pole.|  
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|Určuje, zda pole představuje uzavřený typ.|  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: SH. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
