---
title: Přehled okna Vlastnosti | Dokumentace Microsoftu
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
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8b733a6845a61a71f15d8574666b345dedbf6f50
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752101"
---
# <a name="properties-window-overview"></a>Přehled okna Vlastnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Vlastnosti** okno se používá k zobrazení vlastností objektů vybraných v dva hlavní typy dostupné v systému windows [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrované vývojové prostředí (IDE). Jsou tyto dva typy systému windows:  
  
-   Okna nástrojů, jako je například Průzkumník řešení, zobrazení tříd a objektů prohlížeče  
  
-   Okna dokumentu obsahující takové editory a návrháře jako Návrháře formulářů, editoru XML a editoru HTML  
  
## <a name="using-the-properties-window"></a>Pomocí okna Vlastnosti  
 **Vlastnosti** okně zobrazí vlastnosti jednoho nebo více vybraných položek. Pokud je vybráno více položek, zobrazí se průnik všechny vlastnosti pro všechny vybrané objekty.  
  
 Události související s vybraným objektem v okně návrhu formuláře nebo editoru HTML pomocí metadat modelu COM + se zobrazují v **vlastnosti** okna. Například můžete vybrat tlačítko a zobrazit související události, jako například `OnClick` události, které lze propojit na toto tlačítko.  
  
 Události zobrazené v **vlastnosti** okno se primárně používají s objekty, které jsou vázány na kód. Pokud upravujete soubor formátu, který není nutné nic dělat s kódem, nebudete mít žádné události. Události se zobrazí pouze v **vlastnosti** okno po vytvoření vazby mezi spouštěním kódu určitých událostí spojených s konkrétní objekty. Příklad tohoto by kódu na pozadí vybraného objektu, který se spustí při aktivaci tohoto objektu.  
  
 V následující tabulce jsou uvedeny primární rozhraní používaných **vlastnosti** okna.  
  
|Název rozhraní|Popis|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Obsahuje seznam kategorií, které mají **vlastnosti** okno a jednotlivých vlastností se mapuje na kategorie.|  
|[Rozhraní IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)|Poskytuje metody a vlastnosti programovací nástroje a další aplikace, které podporují automatizaci objektu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Obsahuje tlačítko se třemi tečkami (...) tlačítka volá *tvůrci* , který otevře modální dialogové okno windows implementované samotného objektu. Použít, pokud hodnota není snadno zadaný uživatelem v textovém poli. Například se může použít k otevření barvu ovládacího prvku pro výběr, který určuje hodnotu RGB za vás.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Poskytuje přístup k objektům, které používá k aktualizaci informací zobrazených v **vlastnosti** okna. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> je implementováno rozšíření VSPackages pro každé okno, které obsahuje volitelný objekty s souvisejících vlastností, který se má zobrazit.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Poskytuje informace o typu objektu, jako jsou metody rozhraní a pole struktury.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Umožňuje rozšíření VSPackages, na které přijde upozornění výběr události a k načtení informací o aktuálním hierarchie projektu, položky, hodnota elementu a kontextu uživatelského rozhraní příkazového.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Poskytuje prostředí, které nabízí přístup k více výběrů.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Používá k poskytování lokalizované názvy na některé vlastnosti zobrazené **vlastnosti** okna.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Upozorní registrovaných rozšíření VSPackages na změny aktuálního výběru, hodnota elementu nebo příkaz kontextu uživatelského rozhraní.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Upozorní prostředí, které ke změně aktuálního výběru a poskytuje přístup k informacím o hierarchii a položky týkající se nový výběr.|  
  
 Další informace o `IDispatch`, naleznete v knihovně MSDN.  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)   
 [Pole a rozhraní okna Vlastnosti](../../extensibility/internals/properties-window-fields-and-interfaces.md)

