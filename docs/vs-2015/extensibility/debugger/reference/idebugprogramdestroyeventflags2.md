---
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 86f7e211c742e4d95f3459d058139854874e7d85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182212"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Umožňuje ladicímu stroji [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] při ukončení ladicí relace přepsat výchozí chování uživatelského rozhraní.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Toto rozhraní je implementováno pomocí ladicích modulů. Je užitečné pro hostitele, kteří můžou vytvořit a zničit více programů během doby života procesu.  
  
## <a name="methods"></a>Metody  
 V následující tabulce jsou uvedeny metody `IDebugProgramDestroyEventFlags2` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Načte program zničení příznaků.|  
  
## <a name="remarks"></a>Poznámky  
 Výchozím chováním [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] uživatelského rozhraní je vrátit se zpět do režimu návrhu poté, co všechny programy odesílají událost zničení programu. Toto rozhraní umožňuje ladicímu stroji změnit toto chování.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
