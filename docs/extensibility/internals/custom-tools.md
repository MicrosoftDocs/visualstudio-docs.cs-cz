---
title: Vlastní nástroje | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e60f1d8cb8b25ed50b0b20c5ebb538286687ad72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708949"
---
# <a name="custom-tools"></a>Vlastní nástroje
*Vlastní nástroje* umožňují přidružit nástroj k položce v projektu a spustit tento nástroj při každém uložení souboru. Některé vlastní nástroje, někdy označované jako *generátory s jedním souborem*, se často používají k implementaci překladatelů, které generují kód z dat a naopak. Například generátory s jedním [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] souborem vytvářejí a zdrojový kód vytvářejí ze souborů *.settings* a *.resx.* Generovaný zdrojový kód poskytuje silný přístup k datům v souborech *.settings* a *.resx.* Typy [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] a projekt podporují vlastní nástroje; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] typy projektů ne. Vlastní typy projektů mohou také podporovat vlastní nástroje.

 Vlastní nástroje jsou registrované součásti, které implementují `IVsSingleFileGenerator` rozhraní.

 Vlastní nástroje jsou `ProjectItem` přidruženy k objektu rozhraní a jsou jako návrháři a editory. Vlastní nástroj převezme soubor reprezentovaný `ProjectItem` jako vstup a zapíše nový `DefaultExtension` soubor, jehož název souboru je poskytován metodou.

## <a name="in-this-section"></a>V tomto oddílu
- [Implementace jednosouborových generátorů](../../extensibility/internals/implementing-single-file-generators.md)

 Popisuje, jak používat <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> rozhraní k implementaci vlastního nástroje.

- [Registrace generátorů jednotlivých souborů](../../extensibility/internals/registering-single-file-generators.md)

 Obsahuje popisy všech položek registru pro vlastní nástroj.

- [Vystavit typy vizuálním návrhářům](../../extensibility/internals/exposing-types-to-visual-designers.md)

 Vysvětluje, jak projektové systémy poskytují podporu vizuálním návrhářům pro přístup k generovaným třídám a typům prostřednictvím dočasných přenosných spustitelných souborů (PE).

- [Zachovat vlastnost položky projektu](../../extensibility/persisting-the-property-of-a-project-item.md)

 Ukazuje, jak zachovat vlastnost položky projektu, například autor zdrojového souboru, v souboru projektu.

## <a name="reference"></a>Referenční informace
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>Obsahuje podrobnosti <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>o aplikaci , která transformuje jeden vstupní soubor do jednoho výstupního souboru, který lze zkompilovat nebo přidat do projektu.

 <xref:EnvDTE.ProjectItem>Vysvětluje `ProjectItem` rozhraní, které představuje položku v projektu.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>Obsahuje podrobnosti `DefaultExtension` o metodě, která načte příponu názvu souboru, která je dána názvu výstupního souboru.

## <a name="related-sections"></a>Související oddíly
- [Rozšířit projekty](../../extensibility/extending-projects.md)

 Popisuje použití [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektů a řešení k uspořádání souborů kódu a souborů prostředků a jak implementovat správu zdrojového kódu.
