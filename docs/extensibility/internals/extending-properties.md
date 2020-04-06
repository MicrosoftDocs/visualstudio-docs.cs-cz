---
title: Rozšíření vlastností | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7064128c54434b0a7bb8799e62b751e765511c48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708421"
---
# <a name="extend-properties"></a>Rozšířit vlastnosti
Okno [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Vlastnosti** je univerzální prohlížeč vlastností pro komponenty [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modelu COM a COM+ a podporuje všechny produkty. Okno **Vlastnosti** `ITypeInfo` pracuje s informacemi o typu a metadaty modelu COM+ a zobrazí vlastnosti aktuálně vybraného objektu v libovolném jiném okně v integrovaném vývojovém prostředí (IDE).

 Okno **Vlastnosti,** které lze otevřít stisknutím **klávesy F4** na klávesnici nebo výběrem **okna Vlastnosti** v nabídce **Zobrazení,** slouží k zobrazení a úpravám vlastností a událostí vybraných objektů nezávislých na konfiguraci. Vlastnosti závislé na konfiguraci přidružené k řešením a projektům jsou zobrazeny na [stránkách vlastností](../../extensibility/internals/property-pages.md). Další informace naleznete v [části Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md).

 ![Přehled okna Vlastnosti](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesOkno") Okno Vlastnosti

 Tato část obsahuje podrobné informace, které se vztahují k jednotlivým oblastem okna **Vlastnosti** a rozhraní, které je nutné implementovat a volat k naplnění okna.

## <a name="in-this-section"></a>V tomto oddílu
- [Přehled okna Vlastnosti](../../extensibility/internals/properties-window-overview.md)

 Vysvětluje účel okna **Vlastnosti** vzhledem k okně nástroje a okno dokumentu.

- [Zásady šablony a okno Vlastnosti](../../extensibility/internals/template-policy-and-the-properties-window.md)

 Popisuje, jak je projekt obsažen v projektu šablony organizace a jak může tento projekt šablony organizace vynutit zásady.

- [Vlastnosti okenních polí a rozhraní](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 Vysvětluje základ pro výběr, který určuje, jaké informace se zobrazí v okně **Vlastnosti.**

- [Seznam objektů okna Vlastnosti](../../extensibility/internals/properties-window-object-list.md)

 Popisuje účel seznamu objektů okna **Vlastnosti,** popisující, jak, když jiný objekt z tohoto seznamu aktivuje volání, prostředí je informován, že byl vybrán nový objekt.

- [Tlačítka oken Vlastnosti](../../extensibility/internals/properties-window-buttons.md)

 Vysvětluje účel čtyř výchozích tlačítek zobrazených na panelu nástrojů okna **Vlastnosti.**

- [Mřížka zobrazení vlastností](../../extensibility/internals/properties-display-grid.md)

 Vysvětluje, kde se v mřížce nacházejí pole názvů vlastností a hodnot vlastností.

## <a name="related-sections"></a>Související oddíly
- [Typy projektů](../../extensibility/internals/project-types.md)

 Popisuje projekty jako stavební [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bloky ide.

- [Kompilace a sestavení](../../ide/compiling-and-building-in-visual-studio.md)

 Popisuje, jak můžete [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] použít platformu pro průběžné testování a ladění aplikací při jejich vytváření.

- [Idispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 Popisuje `IDispatch` rozhraní, které bylo nejprve navrženo pro podporu automatizace, poskytující mechanismus s pozdní vazbou pro přístup a načítání informací o metodách a vlastnostech objektu.

- [Správa nastavení aplikace (.NET)](../../ide/managing-application-settings-dotnet.md)

 Obsahuje přehled nastavení aplikace, které umožňují konfigurovat aplikaci tak, aby hodnoty vlastností byly uloženy v externím konfiguračním souboru namísto kompilovaného kódu aplikace.

- [Řešení a projekty](../../ide/solutions-and-projects-in-visual-studio.md)

 Vysvětluje, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jak efektivně spravuje položky, jako jsou odkazy, datová připojení, složky a soubory, které jsou vyžadovány úsilím o vývoj prostřednictvím řešení a projektů.

- [Rozšíření dalších částí sady Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)

 Vysvětluje, jak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] používat služby k vytvoření prvků [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]uživatelského rozhraní, které odpovídají zbytku aplikace .
