---
title: Podtypy projektů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71dab4767c806b44cbd1f9638738b4a13d6b2bcb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706410"
---
# <a name="project-subtypes"></a>Podtypy projektů
Podtypy projektů umožňují přizpůsobit nebo určit chování systémů projektu v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Vlastní nastavení zahrnuje ukládání dalších dat do souboru projektu, přidávání nebo filtrování položek v dialogovém okně **Přidat novou položku** , řízení způsobu ladění a nasazení sestavení a rozšíření dialogového okna **stránky vlastností** projektu. Rozhraní VSPackage implementují podtypy projektu pomocí agregace modelu COM.

> [!NOTE]
> Projektový systém Visual C++ nepodporuje podtypy projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] k implementaci SQL Server a inteligentních projektů zařízení používá sám sebe podtypy projektu.

## <a name="in-this-section"></a>V tomto oddílu
- [Návrh podtypů projektů](../../extensibility/internals/project-subtypes-design.md)

 Popisuje koncept podtypů projektu.

- [Inicializační sekvence podtypů projektů](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

 Popisuje sekvenci inicializace podtypu programového projektu podle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prostředí.

- [Vlastnosti a metody rozšířené prostřednictvím podtypů projektů](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

 Poskytuje podrobný popis funkcí a metod, které jsou nejčastěji rozšířeny pomocí podtypů projektu.

- [Trvalá data v souboru projektu nástroje MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

 Popisuje, jak zachovat data v souboru projektu a jak použít <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> k údržbě dat v souboru projektu napříč úrovněmi agregace podtypu projektu.

- [Uživatelské rozhraní vlastností projektu](../../extensibility/internals/project-property-user-interface.md)

 Popisuje způsob, jakým mohou podtypy projektů upravovat dialogové okno **stránky vlastností** projektu.

- [Rozšíření objektového modelu základního projektu](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

 Poskytuje informace o způsobu, jakým podtypy projektů mohou pomocí rozšířených objektů automatizace Rozšířený objektový model.

- [Přispívání do dialogového okna Přidat novou položku](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

 Popisuje, jak přidat položky do dialogového okna **Přidat novou položku** .

- [Ukládání dat v souborech projektu](../../extensibility/saving-data-in-project-files.md)

 Vysvětluje způsob, jakým podtyp projektu může uložit a načíst data specifická pro podtypy v souboru projektu pomocí rozhraní Managed Package Framework (MPF).

- [Zpracování specializovaného nasazení](../../extensibility/internals/handling-specialized-deployment.md)

 Vysvětluje způsob, jakým podtypy projektů mohou poskytovat specializované chování nasazení implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> rozhraní.

- [Přidávání a odebírání stránek vlastností](../../extensibility/adding-and-removing-property-pages.md)

 Popisuje přidávání a odebírání stránek vlastností v Návrháři projektu.

## <a name="related-sections"></a>Související oddíly
- [Typy projektů](../../extensibility/internals/project-types.md)

 Obsahuje odkazy na témata s podrobnostmi o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektech.
