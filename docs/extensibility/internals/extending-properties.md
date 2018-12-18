---
title: Rozšíření vlastností | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 77b5861dd084098e561f3642b5738dd0279d4b52
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512106"
---
# <a name="extend-properties"></a>Rozšíření vlastností
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Vlastnosti** okno je univerzální vlastnost prohlížeče pro komponenty COM a modelu COM + a podporuje všechny [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] produktů. **Vlastnosti** okno funguje s `ITypeInfo` zadejte informace a metadata COM +. Chcete-li vypsat vlastnosti doby návrhu pro aktuálně vybraného objektu v druhém okně v integrovaném vývojovém prostředí (IDE).  
  
 **Vlastnosti** okna, která se dá otevřít stisknutím kombinace kláves **F4** na klávesnici, nebo výběrem **okno vlastností** na **zobrazení** nabídce Umožňuje zobrazit a upravit vlastnosti nezávislé na konfiguraci, návrhu a událostí vybraných objektů. Vlastnosti závislé na konfiguraci, přidružené k řešení a projekty jsou zobrazeny v [stránky vlastností](../../extensibility/internals/property-pages.md). Další informace najdete [spravovat možnosti konfigurace](../../extensibility/internals/managing-configuration-options.md).  
  
 ![Přehled okna vlastnosti](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Vlastnosti – okno  
  
 Tato část obsahuje podrobné informace, které se týkají jednotlivých oblastí **vlastnosti** okno a rozhraní, které je nutné implementovat a volání k naplnění okna.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled okna Vlastnosti](../../extensibility/internals/properties-window-overview.md)  
 Vysvětluje účel **vlastnosti** okno vzhledem k okna nástrojů a dokumentu.  
  
 [Zásady šablon a okno Vlastnosti](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Tento článek popisuje, jak je projekt obsažené v šabloně projektu organizace, a jak této šablony projektu organizace můžete vynutit zásady.  
  
 [Vlastnosti pole a rozhraní okna](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Vysvětluje základ pro výběr, který určuje, jaké informace se zobrazí v **vlastnosti** okna.  
  
 [Seznam objektů okna Vlastnosti](../../extensibility/internals/properties-window-object-list.md)  
 Popisuje účel **vlastnosti** seznam objektů okna, který popisuje, jak při jiný objekt z tohoto seznamu aktivuje volání dané, prostředí je informován, že byl vybraný nový objekt.  
  
 [Tlačítka okna Vlastnosti](../../extensibility/internals/properties-window-buttons.md)  
 Vysvětluje účel čtyři výchozí tlačítka zobrazená na **vlastnosti** okno nástrojů.  
  
 [Zobrazení mřížky okna Vlastnosti](../../extensibility/internals/properties-display-grid.md)  
 Popisuje, kde se nacházejí názvy vlastností a polí hodnot vlastností v mřížce.  
  
## <a name="related-sections"></a>Související oddíly  
 [Typy projektů](../../extensibility/internals/project-types.md)  
 Tento článek popisuje projekty jako stavební bloky [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí.  
  
 [Kompilace a sestavení](../../ide/compiling-and-building-in-visual-studio.md)  
 Popisuje, jak můžete použít [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] platformu pro průběžné testování a ladění aplikací, jako je sestavení.  
  
 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)  
 Popisuje `IDispatch` rozhraní, který byl původně navržený pro podporu automatizace, poskytuje mechanismus s pozdní vazbou a přístup k načtení informací o metod a vlastností objektu.  
  
 [Správa nastavení aplikace (.NET)](../../ide/managing-application-settings-dotnet.md)  
 Poskytuje přehled nastavení aplikace, které umožňují nakonfigurovat aplikaci tak, aby hodnoty vlastností jsou uložené v externích konfiguračním souboru místo zkompilovaný kód aplikace.  
  
 [Řešení a projekty](../../ide/solutions-and-projects-in-visual-studio.md)  
 Vysvětluje, jak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] efektivně spravuje položky jako odkazy, datová připojení, složky a soubory, které vyžaduje úsilí vývoje prostřednictvím řešení a projekty.  
  
 [Rozšíření dalších částí sady Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Vysvětluje způsob používání [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] služeb vytvořil prvky uživatelského rozhraní, které odpovídají zbytek [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].