---
title: IDebugProgramDestroyEventFlags2 | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722502"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Umožňuje ladicí modul přepsat výchozí chování [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] hlavního nastavení při ukončení relace ladění.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno ladicími moduly. Je užitečné pro hostitele, kteří mohou vytvořit a zničit více programů po celou dobu životnosti procesu.

## <a name="methods"></a>Metody
 V následující tabulce jsou `IDebugProgramDestroyEventFlags2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Načte příznaky zničení programu.|

## <a name="remarks"></a>Poznámky
 Výchozí chování [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] uI je vrátit se do režimu návrhu poté, co všechny programy odeslali událost zničení programu. Toto rozhraní umožňuje ladicí modul změnit toto chování.

## <a name="requirements"></a>Požadavky
 Záhlaví: Msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
