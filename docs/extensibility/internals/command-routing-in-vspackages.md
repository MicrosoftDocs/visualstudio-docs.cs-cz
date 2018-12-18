---
title: Příkaz směrování v balíčcích VSPackage | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5a5f884873e714c12708780a0e52f5f5574727fb
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512932"
---
# <a name="command-routing-in-vspackages"></a>Směrování příkazů v balíčcích VSPackage
Příkaz se směruje do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] na základě kontextu, ve kterém je spuštěn. Z pasivního počáteční kontextu se směruje do globální kontext.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Algoritmus směrování příkazů](../../extensibility/internals/command-routing-algorithm.md)  
 Popisuje pořadí řešení směrování příkazu.  
  
 [Dostupnost příkazu](../../extensibility/internals/command-availability.md)  
 Tento článek popisuje směrování příkazů.  
  
 [Příkazy a nabídky, které používají spolupracující sestavení](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Tento článek popisuje důležité informace o směrování příkazů mezi spravovaným kódem a modelu COM.  
  
## <a name="related-sections"></a>Související oddíly  
 [Kontextové objekty výběru](../../extensibility/internals/selection-context-objects.md)  
 Tento článek popisuje model pro určení uživatele výběr kontextu fokus na okno.  
  
 [Příkazy, nabídky a panely nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Vysvětluje, jak vytvářet uživatelské rozhraní, která zahrnuje nabídky, panely nástrojů a příkaz pole se seznamem.