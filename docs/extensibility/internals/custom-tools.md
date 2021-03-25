---
title: Vlastní nástroje | Microsoft Docs
description: Naučte se, jak vytvořit vlastní nástroje v aplikaci Visual Studio, které přiřadí nástroj k položce v projektu a spustí tento nástroj pokaždé, když je soubor uložený.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d714822605178382ec2ef3574db617f7986cf888
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091042"
---
# <a name="custom-tools"></a>Vlastní nástroje
*Vlastní nástroje* umožňují přidružit nástroj k položce v projektu a spustit tento nástroj pokaždé, když je soubor uložený. Některé vlastní nástroje, které se někdy označují jako *generátory tvořené jedním souborem*, se často používají k implementaci překladatelů, které generují kód z dat a naopak. Například generátory s jedním souborem vytvoří [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] a [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] zdrojový kód ze souborů *. Settings* a *. resx* . Generovaný zdrojový kód poskytuje přístup silného typu k datům v souborech *. Settings* a *. resx* . [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Typy projektů a podporují vlastní nástroje; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] typy projektů ne. Vlastní typy projektů mohou také podporovat vlastní nástroje.

 Vlastní nástroje jsou registrované komponenty, které implementují `IVsSingleFileGenerator` rozhraní.

 Vlastní nástroje jsou přidruženy k `ProjectItem` objektu rozhraní a jsou jako návrháři a editory. Vlastní nástroj přebírá soubor reprezentovaný `ProjectItem` jako vstup a zapisuje nový soubor, jehož název souboru je poskytován `DefaultExtension` metodou.

## <a name="in-this-section"></a>V této části
- [Implementace generátorů tvořených jedním souborem](../../extensibility/internals/implementing-single-file-generators.md)

 Popisuje, jak použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> rozhraní k implementaci vlastního nástroje.

- [Registrovat generátory jednoho souboru](../../extensibility/internals/registering-single-file-generators.md)

 V této části najdete popis všech položek registru pro vlastní nástroj.

- [Vystavení typů pro vizuální návrháře](../../extensibility/internals/exposing-types-to-visual-designers.md)

 Vysvětluje, jak systémy projektu poskytují podporu pro vizuální návrháře pro přístup k vygenerovaným třídám a typům prostřednictvím dočasných souborů přenositelného spustitelného souboru (PE).

- [Zachovat vlastnost položky projektu](../../extensibility/persisting-the-property-of-a-project-item.md)

 Ukazuje, jak zachovat vlastnost položky projektu, například autora zdrojového souboru v souboru projektu.

## <a name="reference"></a>Reference
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Poskytuje podrobnosti o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> , který transformuje jeden vstupní soubor do jednoho výstupního souboru, který lze zkompilovat nebo přidat do projektu.

 <xref:EnvDTE.ProjectItem> Vysvětluje `ProjectItem` rozhraní, které představuje položku v projektu.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> Poskytuje podrobnosti o `DefaultExtension` metodě, která načte příponu názvu souboru, která je předána názvu výstupního souboru.

## <a name="related-sections"></a>Související oddíly
- [Roztažení projektů](../../extensibility/extending-projects.md)

 Popisuje, jak používat [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projekty a řešení k uspořádání souborů kódu a souborů prostředků a jak implementovat správu zdrojového kódu.
