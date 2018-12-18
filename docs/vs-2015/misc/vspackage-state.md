---
title: Stav balíčku VSPackage | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- state, VSPackages
- VSPackages, managing application state
- state persistence
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
manager: douge
ms.openlocfilehash: 0364d7190244217bef50b50b60462d69e1fc145c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895207"
---
# <a name="vspackage-state"></a>Stav balíčku VSPackage
Řada faktorů určit sadu trvalé hodnoty nebo stav, nástroje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aplikace.  
  
- Projekty mají vlastnosti projektu a konfigurace.  
  
- Řešení mají vlastnosti.  
  
- Uživatelská nastavení určuje velikost a pozice okna dokumentů, oken nástrojů, dokovací stavu a klávesové zkratky.  
  
- Aplikace může mít možnosti, které nastaví uživatel.  
  
- Objekty, které aplikace může mít vlastní vlastnosti.  
  
  Tady jsou některé ze způsobů, který [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] stav aplikace je možné spravovat:  
  
- Na stránkách vlastností projektu a řešení.  
  
- Až **Průvodce importem a exportem nastavení**, který umožňuje uživateli přesunout nastavení z jednoho počítače do jiného.  
  
- Až **možnosti** dialogové okno, která zahrnuje možnosti týkající se aplikací.  
  
- Až **vlastnosti** okno, které zpřístupní vlastnosti objektů.  
  
- Díky automatizaci. Aplikace můžete přístup k balíčku VSPackage a objekt vlastnosti, které byly vystaveny automatizace.  
  
  Základní stavu aplikace jsou různé mechanismy trvalost, které umožňují uložit a obnovit stav aplikace.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Podpora pro trvalost stavu](../misc/support-for-state-persistence.md)  
 Zobrazí seznam běžných strategií pro ukládání, obnovení a obnovení stavu VSPackage.  
  
 [Možnosti a stránky Možnosti](../extensibility/internals/options-and-options-pages.md)  
 Představuje obecné a vlastní stránky možnosti a vysvětluje, jak je implementovat.  
  
 [Vytvoření stránky Možnosti](../extensibility/creating-an-options-page.md)  
 Vysvětluje, jak vytvořit dvě možnosti stránky, jednoduché stránky a vlastní stránky.  
  
 [Podpora pro kategorie nastavení](../misc/support-for-settings-categories.md)  
 Tento článek popisuje nastavení uživatele a jak jsou vytvořeny a trvalé.  
  
 [Vytvoření kategorie nastavení](../extensibility/creating-a-settings-category.md)  
 Vysvětluje, jak vytvořit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kategorie nastavení a použít ho k uložení hodnot a obnovení hodnoty ze souboru nastavení.  
  
 [Rozšíření vlastností a okno Vlastnosti](../extensibility/extending-properties-and-the-property-window.md)  
 Vysvětluje, jak zobrazit a změnit hodnoty objektu v **vlastnosti** okna.  
  
 [Vystavení vlastností v okně Vlastnosti](../extensibility/exposing-properties-to-the-properties-window.md)  
 Vysvětluje, jak vystavit veřejné vlastnosti objektu **vlastnosti** okna.  
  
 [Podpora vlastností projektu a konfigurace](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 Vysvětluje, jak zobrazit a změnit vlastnosti projektu a konfigurace.  
  
 [Načtení vlastností projektu](../extensibility/getting-project-properties.md)  
 Vás provede kroky k vytvoření spravovaného VSPackage, která se zobrazí v okně nástroje Vlastnosti projektu.  
  
 [Použití úložiště nastavení](../extensibility/using-the-settings-store.md)  
 Vysvětluje mechanismus trvalého nastavení Store a jak ji používat.  
  
## <a name="related-sections"></a>Související oddíly  
 [Balíčky VSPackage](../extensibility/internals/vspackages.md)  
 Poskytuje obecné orientace na témata, která popisují, jak vytvořit a používat balíčky VSPackages.