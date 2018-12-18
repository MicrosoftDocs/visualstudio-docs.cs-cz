---
title: Rozšíření vlastností | Dokumentace Microsoftu
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
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 919b5a08f003d6e6c320edef4c1321af35f17388
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777874"
---
# <a name="extending-properties"></a>Rozšíření vlastností
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Vlastnosti** okno je univerzální vlastnost prohlížeče pro komponenty COM a modelu COM + a podporuje všechny [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] produktů. **Vlastnosti** okno funguje s `ITypeInfo` zadejte informace a metadata COM +. Chcete-li vypsat vlastnosti doby návrhu pro aktuálně vybraného objektu v druhém okně v integrovaném vývojovém prostředí (IDE).  
  
 **Vlastnosti** okna, která se dá otevřít stisknutím klávesy F4 nebo výběrem **okno vlastností** na **zobrazení** nabídky, se používá k zobrazení a úpravy Vlastnosti nezávislé na konfiguraci, návrhu a události vybraných objektů. Vlastnosti závislé na konfiguraci, přidružené k řešení a projekty jsou zobrazeny v [stránky vlastností](../../extensibility/internals/property-pages.md). Další informace najdete v tématu [vlastnosti NIB: projektu](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md), a [správu NIB: položka v projektech](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Přehled okna vlastnosti](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Vlastnosti – okno  
  
 Tato část obsahuje podrobné informace, které se týkají jednotlivých oblastí **vlastnosti** okno a rozhraní, které je nutné implementovat a volání k naplnění okna.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled okna Vlastnosti](../../extensibility/internals/properties-window-overview.md)  
 Vysvětluje účel **vlastnosti** okno vzhledem k okna nástrojů a dokumentu.  
  
 [Zásady šablon a okno Vlastnosti](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Tento článek popisuje, jak je projekt obsažené v šabloně projektu organizace, a jak této šablony projektu organizace můžete vynutit zásady.  
  
 [Pole a rozhraní okna Vlastnosti](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Vysvětluje základ pro výběr, který určuje, jaké informace se zobrazí v **vlastnosti** okna.  
  
 [Seznam objektů okna Vlastnosti](../../extensibility/internals/properties-window-object-list.md)  
 Popisuje účel **vlastnosti** seznam objektů okna, který popisuje, jak při jiný objekt z tohoto seznamu aktivuje volání dané, prostředí je informován, že byl vybraný nový objekt.  
  
 [Tlačítka okna Vlastnosti](../../extensibility/internals/properties-window-buttons.md)  
 Vysvětluje účel čtyři výchozí tlačítka zobrazená na **vlastnosti** okno nástrojů.  
  
 [Zobrazení mřížky okna Vlastnosti](../../extensibility/internals/properties-display-grid.md)  
 Popisuje, kde se nacházejí názvy vlastností a polí hodnot vlastností v mřížce.  
  
 [Oznamujeme vydání výběr vlastností okna Sledování](../../misc/announcing-property-window-selection-tracking.md)  
 Popisuje sledování pro výběr **vlastnosti** okna.  
  
 [Skrývání vlastností, které mají podřízené vlastnosti](../../misc/hiding-properties-that-have-child-properties.md)  
 Vysvětluje, jak skrýt vlastnosti, které mají podřízené vlastnosti implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> rozhraní.  
  
 [Poskytování vlastních vlastností okna](../../misc/providing-a-custom-properties-window.md)  
 Podrobně popisuje kroky k zajištění prohlížeči vlastností.  
  
 [Získávání popisy pole z okna Vlastnosti](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Vysvětluje, kde najdete popis oblast, která obsahuje informace související s vybranou vlastnost pole.  
  
 [Aktualizuje hodnoty vlastností v okně Vlastnosti](../../misc/updating-property-values-in-the-properties-window.md)  
 Obsahuje podrobné pokyny, které ukazují dva způsoby, jak zachovat **vlastnosti** okno synchronizovat se službou změně hodnoty vlastnosti.  
  
## <a name="related-sections"></a>Související oddíly  
 [Typy projektů](../../extensibility/internals/project-types.md)  
 Tento článek popisuje projekty jako stavební bloky [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaného vývojového prostředí.  
  
 [Kompilace a sestavení](../../ide/compiling-and-building-in-visual-studio.md)  
 Popisuje, jak můžete použít [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] platformu pro průběžné testování a ladění aplikací, jako je sestavení.  
  
 [Vlastnosti dokumentu HTML, okna Vlastnosti](http://msdn.microsoft.com/library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Poskytuje pokyny pro úpravy dokument HTML přímo z okna Vlastnosti a tabulka s podrobnostmi o pole v dokumentu HTML v okně Vlastnosti.  
  
 [IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 Popisuje `IDispatch` rozhraní, který byl původně navržený pro podporu automatizace, poskytuje mechanismus s pozdní vazbou a přístup k načtení informací o metod a vlastností objektu.  
  
 [NIB: Úvod k dynamické vlastnosti (Visual Studio)](http://msdn.microsoft.com/en-us/f5102027-1431-4195-ae40-9b991de46d3a)  
 Poskytuje základní informace o dynamické vlastnosti, které umožňují nakonfigurovat aplikaci tak, aby hodnoty vlastností jsou uložené v externích konfiguračním souboru místo zkompilovaný kód aplikace.  
  
 [NIB: projekty jako kontejnery](http://msdn.microsoft.com/en-us/87d40f63-f487-4767-8963-64beec27ba1b)  
 Popisuje roli projektu jako kontejner v řešení, které logicky spravovat, vytvářet a ladit položky, které tvoří vaši aplikaci.  
  
 [Vlastnosti NIB: projektu](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Popisuje, jak projekt spravuje nastavení, která umožňují vlastnosti ovládacích prvků, které platí pro celý projekt a také vlastnosti, které jsou omezené na určité konfigurace sestavení projektu.  
  
 [Řešení a projekty](../../ide/solutions-and-projects-in-visual-studio.md)  
 Vysvětluje, jak [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] efektivně spravuje položky jako odkazy, datová připojení, složky a soubory, které vyžaduje úsilí vývoje prostřednictvím řešení a projekty.  
  
 [Rozšíření dalších částí sady Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Vysvětluje způsob používání [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] služeb vytvořil prvky uživatelského rozhraní, které odpovídají zbytek [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

