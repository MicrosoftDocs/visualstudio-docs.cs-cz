---
title: Začínáme s rozšířením ladicího programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1c616c7cf8ed90ec3d76046892167b9b742a1b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152711"
---
# <a name="getting-started-with-debugger-extensibility"></a>Začínáme s rozšiřitelností ladicího programu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]Poskytuje informace, které je třeba mít k dispozici k vytvoření a přizpůsobení komponent ladicího programu používaných pro ladění programů v rámci [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prostředí.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ladění přidalo vylepšení odvozená od rozsáhlého testování použitelnosti provedeného v předchozích [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ladicích programech. Ladění můžete použít [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ke krokování s vícejazyčnými aplikacemi nebo můžete implementovat průběžné úpravy proměnných při ladění aplikací a vícejazyčných řešení.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ladění se provádí mimo proces s laděným programem a je proto méně rušivý v prostoru procesu aplikace. V důsledku toho je snazší psát komponenty, které pracují s ladicím programem, aniž by to ovlivnilo váš ladicí program.  
  
 Abyste mohli nejlépe využít [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] , měli byste být obeznámeni s následujícím:  
  
- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Integrované vývojové prostředí (IDE)  
  
- Programovací jazyk C++  
  
- ATL COM  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Plán pro rozšíření ladicího programu](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Popisuje proces implementace ladění v produktu v závislosti na vašem kompilátoru a jeho výstupu.  
  
 [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md)  
 Poskytuje přehled [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] komponent ladění, které zahrnují modul ladění (de), vyhodnocovací filtr výrazů (EE) a popisovač symbolů (SH).  
  
 [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)  
 Popisuje hlavní koncepty architektury ladění.  
  
 [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)  
 Vysvětluje, jak ladicí stroj (DE) funguje současně v rámci kódu, dokumentace a kontextů hodnocení výrazů. Popisuje pro každý ze tří kontextů, umístění, umístění nebo hodnocení, které jsou pro něj relevantní.  
  
 [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md)  
 Obsahuje odkazy na různé úlohy ladění, jako je například spuštění programu a vyhodnocování výrazů.
