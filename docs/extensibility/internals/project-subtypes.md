---
title: Podtypy projektů | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706410"
---
# <a name="project-subtypes"></a>Podtypy projektů
Podtypy projektu umožňují přizpůsobit nebo ochucovat chování projektových systémů aplikace [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Vlastní nastavení zahrnují uložení dalších dat do souboru projektu, přidání nebo filtrování položek v dialogovém okně **Přidat novou položku,** řízení způsobu odlazení a nasazení sestavení a rozšíření dialogového **okna Stránky vlastností** projektu. VSPackages implementovat podtypy projektu pomocí agregace COM.

> [!NOTE]
> Systém projektu Visual C++ nepodporuje podtypy projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]sám používá podtypy projektu k implementaci sql serveru a inteligentních zařízení projekty.

## <a name="in-this-section"></a>V tomto oddílu
- [Návrh podtypů projektů](../../extensibility/internals/project-subtypes-design.md)

 Popisuje koncept podtypů projektu.

- [Inicializační sekvence podtypů projektů](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

 Popisuje programový projekt podtyp inicializace sekvence podle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prostředí.

- [Vlastnosti a metody rozšířené prostřednictvím podtypů projektů](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

 Obsahuje podrobné popisy funkcí a metod, které jsou nejčastěji rozšiřovány pomocí podtypů projektu.

- [Trvalá data v souboru projektu nástroje MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

 Popisuje, jak zachovat data v souboru <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> projektu a jak použít k údržbě dat v souboru projektu přes úrovně agregace podtypu projektu.

- [Uživatelské rozhraní vlastností projektu](../../extensibility/internals/project-property-user-interface.md)

 Popisuje, jak mohou podtypy projektu upravovat dialogové okno **Stránky vlastností** projektu.

- [Rozšíření objektového modelu základního projektu](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

 Obsahuje informace o tom, jak mohou podtypy projektu používat zařízení Automation Extender k rozšíření objektového modelu automatizace.

- [Přispívání do dialogového okna Přidat novou položku](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

 Popisuje, jak přidat položky do dialogového okna **Přidat novou položku.**

- [Ukládání dat v souborech projektu](../../extensibility/saving-data-in-project-files.md)

 Vysvětluje, jak podtyp projektu můžete uložit a načíst data specifické pro podtyp v souboru projektu pomocí rozhraní Spravovaného balíčku (MPF).

- [Zpracování specializovaného nasazení](../../extensibility/internals/handling-specialized-deployment.md)

 Vysvětluje, jak podtypy projektu může poskytnout specializované <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> chování nasazení implementací rozhraní.

- [Přidávání a odebírání stránek vlastností](../../extensibility/adding-and-removing-property-pages.md)

 Popisuje přidávání a odebírání stránek vlastností v Návrháři projektů.

## <a name="related-sections"></a>Související oddíly
- [Typy projektů](../../extensibility/internals/project-types.md)

 Obsahuje odkazy na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] témata popisující projekty.
