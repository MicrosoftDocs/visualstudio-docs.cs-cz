---
title: Stav balíčku VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state, VSPackages
- VSPackages, managing application state
- state persistence
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
manager: jillfra
ms.openlocfilehash: f3140b527673f87b1d7c552e99584232494aed7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62979992"
---
# <a name="vspackage-state"></a>Stav VSPackage
Řada faktorů určuje sadu trvalých hodnot nebo stav [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aplikace.  
  
- Projekty mají vlastnosti projektu a konfigurace.  
  
- Řešení mají vlastnosti.  
  
- Uživatelská nastavení určují velikost a umístění oken dokumentů, oken nástrojů, stavu ukotvení a klávesových zkratek.  
  
- Aplikace mohou mít možnosti, které nastaví uživatel.  
  
- Objekty, které vytváří aplikace, mohou mít vlastní vlastnosti.  
  
  Tady je několik způsobů, jak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lze spravovat stav aplikace:  
  
- Na stránkách vlastností projektu a řešení.  
  
- Pomocí **Průvodce importem a exportem nastavení**, který umožňuje uživateli přesunout nastavení z jednoho počítače do druhého.  
  
- Pomocí dialogového okna **Možnosti** , které obsahuje možnosti související s aplikacemi.  
  
- Prostřednictvím okna **vlastnosti** , které zpřístupňuje vlastnosti objektů.  
  
- Prostřednictvím automatizace. Aplikace má přístup k vlastnostem VSPackage a objektům, které byly vystaveny pro automatizaci.  
  
  Základní stav aplikace jsou různé mechanismy trvalosti, které umožňují ukládání a obnovování stavu aplikace.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Podpora pro trvalost stavu](../misc/support-for-state-persistence.md)  
 Obsahuje seznam běžných strategií pro uložení, obnovení a resetování stavu VSPackage.  
  
 [Možnosti a stránky Možnosti](../extensibility/internals/options-and-options-pages.md)  
 Obsahuje obecné a vlastní stránky možností a vysvětluje, jak je implementovat.  
  
 [Vytvoření stránky Možnosti](../extensibility/creating-an-options-page.md)  
 Vysvětluje, jak vytvořit dvě stránky možností, jednoduchou stránku a vlastní stránku.  
  
 [Podpora pro kategorie nastavení](../misc/support-for-settings-categories.md)  
 Popisuje uživatelská nastavení a jejich vytvoření a uchování.  
  
 [Vytvoření kategorie nastavení](../extensibility/creating-a-settings-category.md)  
 Vysvětluje, jak vytvořit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kategorii nastavení a použít ji k ukládání hodnot do a obnovení hodnot ze souboru nastavení.  
  
 [Rozšíření vlastností a okno Vlastnosti](../extensibility/extending-properties-and-the-property-window.md)  
 Vysvětluje, jak zobrazit a změnit hodnotu objektu v okně **vlastnosti** .  
  
 [Vystavení vlastností v okně Vlastnosti](../extensibility/exposing-properties-to-the-properties-window.md)  
 Vysvětluje, jak zveřejnit veřejné vlastnosti objektu v okně **vlastnosti** .  
  
 [Podpora vlastností projektu a konfigurace](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 Vysvětluje, jak zobrazit a změnit vlastnosti projektu a konfigurace.  
  
 [Načtení vlastností projektu](../extensibility/getting-project-properties.md)  
 Provede vás kroky při vytváření spravovaného VSPackage, který zobrazí vlastnosti projektu v okně nástroje.  
  
 [Použití úložiště nastavení](../extensibility/using-the-settings-store.md)  
 Vysvětluje nastavení mechanismu trvalosti úložiště a jeho použití.  
  
## <a name="related-sections"></a>Související oddíly  
 [Balíčky VSPackage](../extensibility/internals/vspackages.md)  
 Poskytuje obecnou orientaci pro témata, která vysvětlují, jak vytvářet a používat sady VSPackage.