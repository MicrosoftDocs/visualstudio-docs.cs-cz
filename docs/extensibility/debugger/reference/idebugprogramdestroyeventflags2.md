---
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d869304dd8b6dc82db78cc09ed9d51a54acdc3c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722502"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Umožňuje ladicímu stroji [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] při ukončení ladicí relace přepsat výchozí chování uživatelského rozhraní.

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
 Výchozím chováním [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] uživatelského rozhraní je vrátit se zpět do režimu návrhu poté, co všechny programy odesílají událost zničení programu. Toto rozhraní umožňuje ladicímu stroji změnit toto chování.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
