---
title: Začínáme s rozšiřitelností ladicího programu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bafdd45b57a9fe660e97127c2c99c333ead0e60a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721161"
---
# <a name="getting-started-with-debugger-extensibility"></a>Začínáme s rozšiřitelností ladicího programu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Poskytuje informace, které potřebujete k vytváření a přizpůsobování umožňuje ladit programy v rámci komponenty ladicího programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prostředí.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ladění bylo přidáno vylepšení se odvozené z rozsáhlé použitelnost testů na předchozí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ladicí programy. Můžete použít [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ladění krokovat vícejazyčné aplikace, nebo můžete implementovat na průběžné úpravy proměnných při ladění aplikací a řešení pro více jazyků.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ladění je provedeno out-of-process program, který se právě ladí a proto je teď míň obtěžující do procesního prostoru aplikace. V důsledku toho je usnadňuje psaní součásti, které pracují s ladicím programem, aniž by to ovlivnilo ladicí program.  
  
 Na co nejlíp využít [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], měli byste se seznámit s následující:  
  
-   [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Integrované vývojové prostředí (IDE)  
  
-   Programovací jazyk C++  
  
-   KNIHOVNY ATL MODELU COM  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Plán pro rozšíření ladicího programu](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Popisuje proces implementace produktu, v závislosti na vaší kompilátoru a její výstup ladění.  
  
 [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md)  
 Najdete zde přehled [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ladění komponenty, které zahrnují ladicího stroje (DE), Chyba při vyhodnocování výrazu (EE) a obslužné rutiny symbolů (SH).  
  
 [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)  
 Popisuje hlavní koncepty ladění architektury.  
  
 [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)  
 Vysvětluje, jak funguje ladicího stroje (DE) současně v kódu, dokumentace a kontexty vyhodnocení výrazu. Popisuje všech třech kontextech, umístění, pozice nebo vyhodnocení relevantní k němu.  
  
 [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md)  
 Obsahuje odkazy na různé úlohy ladění, jako je například spuštění programu a vyhodnocení výrazů.

