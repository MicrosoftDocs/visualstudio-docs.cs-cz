---
title: Přispívání do modelu automatizace | Microsoft Docs
description: Naučte se přispívat do modelu automatizace sady Visual Studio pomocí sady pokynů při navrhování sady VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 44da0c91eb425cbd558aea4335447f9293684b90
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057036"
---
# <a name="contribute-to-the-automation-model"></a>Přispívání do modelu automatizace
Sada Visual Studio poskytuje sadu automatizačních rozhraní pro přizpůsobení prostředí. Model automatizace je objektový model, který koncovým uživatelům umožňuje vytvářet doplňky a rozšíření sady Visual Studio.

 Kromě toho je vhodné, jako vývojář VSPackage, pro přispívání do modelu automatizace; Díky tomu můžete koncovým uživatelům vaší VSPackage povolit vytváření doplňků a obecně poskytovat konzistentní prostředí uživatelského modelu při použití VSPackage v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Pro zajištění konzistence prostředí koncových uživatelů můžete při navrhování VSPackage použít sadu pokynů, takže model automatizace pro sadu VSPackage bude odpovídat nápadům v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>V této části
- [Přehled modelu automatizace](../../extensibility/internals/automation-model-overview.md)

 Definuje model automatizace jako související skupiny objektů, které řídí hlavní charakteristiky společného prostředí. Tato sada objektů je naformátovaná v diagramu modelu automatizace.

- [Zajištění automatizace pro VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md)

 Popisuje dva hlavní způsoby, jak zajistit automatizaci pro VSPackage.

- [Vystavení objektů projektu](../../extensibility/internals/exposing-project-objects.md)

 Poskytuje podrobné pokyny pro vytváření objektů specifických pro VSPackage.

- [Modelování projektu](../../extensibility/internals/project-modeling.md)

 Vysvětluje standardní objekty projektu, které jsou požadovány pro vytvoření automatizace pro nový typ projektu a ilustruje cestu, kterou automatizace projektu sleduje. Toto téma také poskytuje výpisy deklarací a implementaci tříd.

- [Vystavení událostí](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Poskytuje podrobné pokyny pro vytváření událostí pro model automatizace.

- [Podpora automatizace pro stránky možností](../../extensibility/internals/automation-support-for-options-pages.md)

 Popisuje, jak vrátit objekt automatizace pro podporu vlastností dialogového okna vlastních **možností** sady VSPackage v nabídce **nástroje** rozšířením `DTE.Properties` objektu.

- [Poskytnutí automatizace pro kód](../../extensibility/internals/providing-automation-for-code.md)

 Vysvětluje, že vytvoření modelu automatizace pro váš kód není vyžadováno. Odkaz je však k dispozici v tomto tématu, které poskytuje přehledné informace do modelů kódu.

- [Postupy: poskytnutí automatizace pro Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Vysvětluje, že poskytnutí automatizace je dobrý nápad vždy, když chcete objekty automatizace zpřístupnit v okně a prostředí již neposkytuje předem připravený automatizační objekt. Popisuje automatizaci pro okna nástrojů a okna dokumentů.

- [Použití modelu automatizace](../../extensibility/internals/using-the-automation-model.md)

 Obsahuje dva příklady kódu, které ukazují, jak spotřebitel automatizace získává počáteční objekty automatizace projektu.

- [Automatizace pro objekty Configuration a SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Poskytuje informace o automatizaci pro objekty Configuration a SelectedItems.

## <a name="reference"></a>Reference
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Obsahuje ukázku kódu, který ukazuje, jak se VSPackage účastní modelu automatizačních objektů DTE. Zobrazí seznam parametrů, vrácených hodnot a vybraných poznámek.
