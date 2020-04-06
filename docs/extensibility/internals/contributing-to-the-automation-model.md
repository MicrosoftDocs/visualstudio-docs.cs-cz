---
title: Přispívání k modelu automatizace | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d660edc740229c3e91b99e1f59eb37b4e9312098
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709272"
---
# <a name="contribute-to-the-automation-model"></a>Přispějte k modelu automatizace
Visual Studio poskytuje sadu rozhraní automatizace pro přizpůsobení prostředí. Model automatizace je objektový model, který umožňuje koncovým uživatelům vytvářet doplňky a rozšíření sady Visual Studio.

 Kromě toho je vhodné, abyste jako vývojář VSPackage přispívali k modelu automatizace; Tímto způsobem povolíte koncovým uživatelům vašeho balíčku VSPackage vytvářet doplňky a obecně poskytují konzistentní uživatelské [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]modelové prostředí při použití vašeho balíčku VSPackage v aplikaci .

 Chcete-li, aby prostředí pro koncové uživatele bylo konzistentní, můžete při navrhování balíčku VSPackage postupovat podle sady [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]pokynů tak, aby model automatizace pro váš balíček VSPackage sledoval nápady v aplikaci .

## <a name="in-this-section"></a>V tomto oddílu
- [Přehled modelu automatizace](../../extensibility/internals/automation-model-overview.md)

 Definuje model automatizace jako související skupiny objektů, které řídí hlavní aspekty společného prostředí. Tato sada objektů je zobrazena v diagramu modelu automatizace.

- [Zajištění automatizace pro balíčky VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)

 Popisuje dva hlavní způsoby, jak zajistit automatizaci pro váš VSPackage.

- [Vystavit objekty projektu](../../extensibility/internals/exposing-project-objects.md)

 Obsahuje podrobné pokyny pro vytváření objektů specifických pro vspackage.

- [Modelování projektů](../../extensibility/internals/project-modeling.md)

 Vysvětluje standardní objekty projektu, které jsou nutné k vytvoření automatizace pro nový typ projektu a ilustruje cestu, která následuje automatizace projektu. Toto téma také obsahuje výpisy deklarací a implementace pro třídy.

- [Vystavit události](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Obsahuje podrobné pokyny pro vytváření událostí pro váš model automatizace.

- [Podpora automatizace pro stránky možností](../../extensibility/internals/automation-support-for-options-pages.md)

 Popisuje, jak vrátit objekt automatizace pro podporu vlastností dialogového okna vlastní **volby** VSPackage v nabídce **Nástroj** rozšířením objektu. `DTE.Properties`

- [Zajištění automatizace pro kód](../../extensibility/internals/providing-automation-for-code.md)

 Vysvětluje, že vytvoření modelu automatizace pro váš kód není vyžadováno. Odkaz je však k dispozici v tomto tématu, který poskytuje podrobné informace o modelech kódu.

- [Postup: Zajištění automatizace pro Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Vysvětluje, že poskytování automatizace je vhodné vždy, když chcete zpřístupnit objekty automatizace v okně a prostředí již neposkytuje objekt připravené automatizace. Popisuje automatizaci pro okna nástrojů a okna dokumentů.

- [Použití modelu automatizace](../../extensibility/internals/using-the-automation-model.md)

 Obsahuje dva příklady kódu, které ukazují, jak spotřebitel automatizace získá počáteční objekty automatizace projektu.

- [Automatizace pro objekty Konfigurace a SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Obsahuje informace o automatizaci objektů Configuration a SelectedItems.

## <a name="reference"></a>Referenční informace
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>Poskytuje ukázku kódu, která ukazuje, jak se VSPackage účastní objektového modelu automatizace DTE. Uvádí parametry, vrácené hodnoty a vybrané poznámky.
