---
title: Vlastní nástroje | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 594d564cf4a18eb0b673abd9b45b7d70e20381b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196919"
---
# <a name="custom-tools"></a>Vlastní nástroje
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

*Vlastní nástroje* umožňují přidružit nástroj k položce v projektu a spustit tento nástroj pokaždé, když je soubor uložený. Některé vlastní nástroje, které se někdy označují jako *generátory tvořené jedním souborem*, se často používají k implementaci překladatelů, které generují kód z dat a naopak. Například generátory s jedním souborem vytvoří [!INCLUDE[csprcs](../../includes/csprcs-md.md)] a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] zdrojový kód ze souborů. Settings a. resx. Generovaný zdrojový kód poskytuje přístup silného typu k datům v souborech. Settings a. resx. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Typy projektů a podporují vlastní nástroje; [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] typy projektů ne. Vlastní typy projektů mohou také podporovat vlastní nástroje.  
  
 Vlastní nástroje jsou registrované komponenty, které implementují `IVsSingleFileGenerator` rozhraní.  
  
 Vlastní nástroje jsou přidruženy k `ProjectItem` objektu rozhraní a jsou jako návrháři a editory. Vlastní nástroj přebírá soubor reprezentovaný `ProjectItem` jako vstup a zapisuje nový soubor, jehož název souboru je poskytován `DefaultExtension` metodou.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Implementace generátorů tvořených jedním souborem](../../extensibility/internals/implementing-single-file-generators.md)  
 Popisuje, jak použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> rozhraní k implementaci vlastního nástroje.  
  
 [Určení výchozího oboru názvů projektu](../../misc/determining-the-default-namespace-of-a-project.md)  
 Popisuje, jak určit správný obor názvů na základě používaného jazyka.  
  
 [Registrace generátorů tvořených jedním souborem](../../extensibility/internals/registering-single-file-generators.md)  
 V této části najdete popis všech položek registru pro vlastní nástroj.  
  
 [Zveřejnění typů pro vizuální návrháře](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Vysvětluje, jak systémy projektu poskytují podporu pro vizuální návrháře pro přístup k vygenerovaným třídám a typům prostřednictvím dočasných souborů přenositelného spustitelného souboru (PE).  
  
 [Trvalé uložení vlastnosti položky projektu](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Ukazuje, jak zachovat vlastnost položky projektu, například autora zdrojového souboru v souboru projektu.  
  
## <a name="reference"></a>Referenční informace  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Poskytuje podrobnosti o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> , který transformuje jeden vstupní soubor do jednoho výstupního souboru, který lze zkompilovat nebo přidat do projektu.  
  
 <xref:EnvDTE.ProjectItem>  
 Vysvětluje `ProjectItem` rozhraní, které představuje položku v projektu.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Poskytuje podrobnosti o `DefaultExtension` metodě, která načte příponu názvu souboru, která je předána názvu výstupního souboru.  
  
## <a name="related-sections"></a>Související oddíly  
 [Rozšíření projektů](../../extensibility/extending-projects.md)  
 Popisuje, jak používat [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projekty a řešení k uspořádání souborů kódu a souborů prostředků a jak implementovat správu zdrojového kódu.
