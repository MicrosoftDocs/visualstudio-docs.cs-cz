---
title: Rozšíření vlastností | Microsoft Docs
description: Přečtěte si o rozhraních, která je nutné implementovat, a zavolejte k roztažení seznamu vlastností v okno Vlastnosti sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3b1006f74cd2de03b4fe74e090d7ffcd1c921e5d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069644"
---
# <a name="extend-properties"></a>Rozšířené vlastnosti
Okno [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **vlastnosti** je univerzální prohlížeč vlastností pro součásti COM a com+ a podporuje všechny [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] produkty. Okno **vlastnosti** pracuje s `ITypeInfo` informacemi o typu a metadaty modelu COM+ k vypsání vlastností doby návrhu pro aktuálně vybraný objekt v jakémkoli jiném okně v integrovaném vývojovém prostředí (IDE).

 Okno **vlastnosti** , které lze otevřít stisknutím klávesy **F4** na klávesnici nebo výběr **okna vlastnosti** v nabídce **zobrazení** , se používá k zobrazení a úpravám vlastností a událostí pro dobu návrhu, které jsou nezávislé na konfiguraci, a události vybraných objektů. Vlastnosti závislé na konfiguraci spojené s řešeními a projekty se zobrazují na [stránkách vlastností](../../extensibility/internals/property-pages.md). Další informace najdete v [možnostech správy možností konfigurace](../../extensibility/internals/managing-configuration-options.md).

 ![Přehled okno Vlastnosti](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow") okno Vlastnosti

 Tato část poskytuje podrobné informace, které se vztahují na jednotlivé oblasti okna **vlastnosti** a rozhraní, která je nutné implementovat, a volání pro naplnění okna.

## <a name="in-this-section"></a>V této části
- [Přehled okno Vlastnosti](../../extensibility/internals/properties-window-overview.md)

 Vysvětluje účel okna **vlastností** relativně k oknu nástrojů a oknu dokumentu.

- [Zásady šablony a okno Vlastnosti](../../extensibility/internals/template-policy-and-the-properties-window.md)

 Popisuje, jak je projekt obsažen v projektu šablony organizace a jak může tento projekt šablony vyhovět zásadám.

- [okno Vlastnosti polí a rozhraní](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 Vysvětluje základ pro výběr, který určuje, jaké informace se zobrazí v okně **vlastnosti** .

- [Seznam okno Vlastnosti objektů](../../extensibility/internals/properties-window-object-list.md)

 Popisuje účel seznamu objektů okna **vlastností** a popisuje, jak, když jiný objekt z tohoto seznamu aktivuje volání, prostředí je informováno o vybrání nového objektu.

- [okno Vlastnosti tlačítka](../../extensibility/internals/properties-window-buttons.md)

 Vysvětluje účel čtyř výchozích tlačítek zobrazených na panelu nástrojů okna **vlastnosti** .

- [Zobrazit mřížku vlastností](../../extensibility/internals/properties-display-grid.md)

 Vysvětluje, kde se v mřížce nacházejí pole názvů vlastností a hodnot vlastností.

## <a name="related-sections"></a>Související oddíly
- [Typy projektů](../../extensibility/internals/project-types.md)

 Popisuje projekty jako stavební kameny [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí (IDE).

- [Kompilace a sestavení](../../ide/compiling-and-building-in-visual-studio.md)

 Popisuje, jak můžete použít [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] platformu pro průběžné testování a ladění aplikací při jejich sestavování.

- [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 Popisuje `IDispatch` rozhraní, které bylo nejprve navrženo tak, aby podporovalo automatizaci, a poskytuje mechanismus s pozdní vazbou pro přístup a načtení informací o metodách a vlastnostech objektu.

- [Správa nastavení aplikace (.NET)](../../ide/managing-application-settings-dotnet.md)

 Poskytuje přehled nastavení aplikace, která umožňují konfiguraci aplikace tak, aby hodnoty vlastností byly uloženy v externím konfiguračním souboru namísto zkompilovaného kódu aplikace.

- [Řešení a projekty](../../ide/solutions-and-projects-in-visual-studio.md)

 Vysvětluje, jak efektivně spravuje položky, jako jsou například [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] odkazy, datová připojení, složky a soubory, které jsou vyžadovány vaším vývojovým úsilím prostřednictvím řešení a projektů.

- [Rozšiřování dalších částí sady Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)

 Vysvětluje, jak používat [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] služby k vytvoření prvků uživatelského rozhraní, které se shodují se zbytkem z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
