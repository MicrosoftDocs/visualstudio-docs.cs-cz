---
title: Směrování příkazů v VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 954d3f25a425652d8adcb31bd36fab06de0d04d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195092"
---
# <a name="command-routing-in-vspackages"></a>Směrování příkazů v balíčcích VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Příkaz je směrován v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] závislosti na kontextu, ve kterém je proveden. Je směrován z počátečního kontextu směrem ven do globálního kontextu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Algoritmus směrování](../../extensibility/internals/command-routing-algorithm.md)  
 Popisuje pořadí řešení směrování příkazů.  
  
 [Dostupnost](../../extensibility/internals/command-availability.md)  
 Popisuje směrování příkazů.  
  
 [Příkazy a nabídky, které používají definiční sestavení](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Popisuje okolnosti při směrování příkazů mezi spravovaným kódem a COM.  
  
## <a name="related-sections"></a>Související oddíly  
 [Kontextové objekty výběru](../../extensibility/internals/selection-context-objects.md)  
 Popisuje model, jak lze určit fokus kontextu výběru uživatele v okně.  
  
 [Příkazy, nabídky a panely nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Vysvětluje, jak vytvořit uživatelské rozhraní, které obsahuje nabídky, panely nástrojů a pole se seznamem příkazů.
