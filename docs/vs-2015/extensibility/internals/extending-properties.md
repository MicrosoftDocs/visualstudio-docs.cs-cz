---
title: Rozšíření vlastností | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b5d2e7d15f7b479941c3186d8cd694c92f762bbf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690995"
---
# <a name="extending-properties"></a>Rozšíření vlastností
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Okno [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **vlastnosti** je univerzální prohlížeč vlastností pro součásti COM a com+ a podporuje všechny [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] produkty. Okno **vlastnosti** pracuje s `ITypeInfo` informacemi o typu a metadaty modelu COM+ k vypsání vlastností doby návrhu pro aktuálně vybraný objekt v jakémkoli jiném okně v integrovaném vývojovém prostředí (IDE).  
  
 Okno **vlastnosti** , které lze otevřít stisknutím klávesy F4 na klávesnici nebo výběr **okna vlastnosti** v nabídce **zobrazení** , se používá k zobrazení a úpravám vlastností a událostí pro dobu návrhu, které jsou nezávislé na konfiguraci, a události vybraných objektů. Vlastnosti závislé na konfiguraci spojené s řešeními a projekty se zobrazují na [stránkách vlastností](../../extensibility/internals/property-pages.md). Další informace najdete v tématu [NIB: vlastnosti projektu](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)a [NIB: Správa položek v projektech](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Přehled okna Vlastnosti](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Vlastnosti – okno  
  
 Tato část poskytuje podrobné informace, které se vztahují na jednotlivé oblasti okna **vlastnosti** a rozhraní, která je nutné implementovat, a volání pro naplnění okna.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled okna Vlastnosti](../../extensibility/internals/properties-window-overview.md)  
 Vysvětluje účel okna **vlastností** relativně k oknu nástrojů a oknu dokumentu.  
  
 [Zásady šablon a okno Vlastnosti](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Popisuje, jak je projekt obsažen v projektu šablony organizace a jak může tento projekt šablony vyhovět zásadám.  
  
 [Pole a rozhraní okna Vlastnosti](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Vysvětluje základ pro výběr, který určuje, jaké informace se zobrazí v okně **vlastnosti** .  
  
 [Seznam objektů okna Vlastnosti](../../extensibility/internals/properties-window-object-list.md)  
 Popisuje účel seznamu objektů okna **vlastností** a popisuje, jak, když jiný objekt z tohoto seznamu aktivuje volání, prostředí je informováno o vybrání nového objektu.  
  
 [Tlačítka okna Vlastnosti](../../extensibility/internals/properties-window-buttons.md)  
 Vysvětluje účel čtyř výchozích tlačítek zobrazených na panelu nástrojů okna **vlastnosti** .  
  
 [Zobrazení mřížky okna Vlastnosti](../../extensibility/internals/properties-display-grid.md)  
 Vysvětluje, kde se v mřížce nacházejí pole názvů vlastností a hodnot vlastností.  
  
 [Oznamuje se sledování výběru okna vlastností.](../../misc/announcing-property-window-selection-tracking.md)  
 Popisuje sledování výběru pro okno **vlastnosti** .  
  
 [Skrytí vlastností s podřízenými vlastnostmi](../../misc/hiding-properties-that-have-child-properties.md)  
 Vysvětluje, jak skrýt vlastnosti, které mají podřízené vlastnosti implementující <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> rozhraní.  
  
 [Poskytnutí okna vlastních vlastností](../../misc/providing-a-custom-properties-window.md)  
 Podrobně popisuje postup poskytnutí vlastního prohlížeče vlastností.  
  
 [Získání popisů polí z okna vlastností](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Vysvětluje, kde najít oblast s popisem, která zobrazuje informace související s polem vybrané vlastnosti.  
  
 [Aktualizace hodnot vlastností v okně Vlastnosti](../../misc/updating-property-values-in-the-properties-window.md)  
 Obsahuje podrobné pokyny, které znázorňují dva způsoby, jak zachovat okno **vlastností** synchronizované se změnami hodnoty vlastností.  
  
## <a name="related-sections"></a>Související oddíly  
 [Typy projektů](../../extensibility/internals/project-types.md)  
 Popisuje projekty jako stavební kameny [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaného vývojového prostředí (IDE).  
  
 [Kompilace a sestavení](../../ide/compiling-and-building-in-visual-studio.md)  
 Popisuje, jak můžete použít [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] platformu pro průběžné testování a ladění aplikací při jejich sestavování.  
  
 [Vlastnosti dokumentu HTML, okno vlastností](https://msdn.microsoft.com/library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Poskytuje pokyny pro úpravu dokumentu HTML přímo z okno Vlastnosti a poskytuje tabulku s podrobnostmi o polích v dokumentu HTML v okno Vlastnosti.  
  
 [IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 Popisuje `IDispatch` rozhraní, které bylo nejprve navrženo tak, aby podporovalo automatizaci, a poskytuje mechanismus s pozdní vazbou pro přístup a načtení informací o metodách a vlastnostech objektu.  
  
 [NIB: Úvod do dynamických vlastností (Visual Studio)](https://msdn.microsoft.com/f5102027-1431-4195-ae40-9b991de46d3a)  
 Poskytuje přehled dynamických vlastností, které umožňují konfiguraci aplikace tak, aby hodnoty vlastností byly uloženy v externím konfiguračním souboru namísto zkompilovaného kódu aplikace.  
  
 [NIB: projekty jako kontejnery](https://msdn.microsoft.com/87d40f63-f487-4767-8963-64beec27ba1b)  
 Popisuje roli projektu jako kontejner v řešení pro logickou správu, sestavování a ladění položek, které tvoří vaši aplikaci.  
  
 [NIB: vlastnosti projektu](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Popisuje, jak projekt spravuje nastavení, která umožňují řízení vlastností, které platí pro celý projekt a také vlastnosti, které jsou omezeny na určité konfigurace sestavení projektu.  
  
 [Řešení a projekty](../../ide/solutions-and-projects-in-visual-studio.md)  
 Vysvětluje, jak efektivně spravuje položky, jako jsou například [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] odkazy, datová připojení, složky a soubory, které jsou vyžadovány vaším vývojovým úsilím prostřednictvím řešení a projektů.  
  
 [Rozšíření dalších částí sady Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Vysvětluje, jak používat [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] služby k vytvoření prvků uživatelského rozhraní, které se shodují se zbytkem z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .
