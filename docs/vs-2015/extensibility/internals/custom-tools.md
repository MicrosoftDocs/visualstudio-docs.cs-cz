---
title: Vlastní nástroje | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 98dce865af4dd1f8498dcd697b53abdb8608abed
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793422"
---
# <a name="custom-tools"></a>Vlastní nástroje
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

*Vlastní nástroje* vám umožní přidružit nástroj položky v projektu a spusťte tento nástroj pokaždé, když je soubor uložen. Některé vlastní nástroje, někdy označovány jako *generátorů tvořených jedním souborem*, jsou často používána k implementaci překladače, které generují kód z dat a naopak. Například vytvořit generátorů tvořených jedním souborem [!INCLUDE[csprcs](../../includes/csprcs-md.md)] a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] zdrojový kód mimo soubor .settings a resx. Generovaný zdrojový kód poskytuje silného typu přístup k datům v souborech .settings a resx. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] typy projektů podpory vlastního nástroje. [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] typy projektů nejsou. Vlastní typy projektů může také podporovat vlastních nástrojů.  
  
 Jsou registrované součásti, které implementují vlastní nástroje `IVsSingleFileGenerator` rozhraní.  
  
 Jsou přidružené k vlastní nástroje `ProjectItem` rozhraní objektu a jsou podobné návrháři a editory. Vlastní nástroj přebírá souboru reprezentována `ProjectItem` jako vstup a zapíše nový soubor, jehož název souboru poskytuje `DefaultExtension` metoda.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Implementace generátorů tvořených jedním souborem](../../extensibility/internals/implementing-single-file-generators.md)  
 Popisuje způsob použití <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> rozhraní za účelem implementace vlastní nástroj.  
  
 [Určení výchozí Namespace projektu](../../misc/determining-the-default-namespace-of-a-project.md)  
 Popisuje, jak určit správný obor názvů založený na používaný jazyk.  
  
 [Registrace generátorů tvořených jedním souborem](../../extensibility/internals/registering-single-file-generators.md)  
 Obsahuje popis pro všechny položky registru pro vlastní nástroj.  
  
 [Zveřejnění typů pro vizuální návrháře](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Vysvětluje, jak systémů projektů poskytovat podporu pro vizuální návrhářské nástroje a typy tříd pro přístup k vygenerované pomocí souborů dočasné (PE portable executable).  
  
 [Trvalé uložení vlastnosti položky projektu](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Ukazuje, jak zachovat vlastnosti položky projektu, jako je například autor zdrojového souboru, v souboru projektu.  
  
## <a name="reference"></a>Odkaz  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Poskytuje podrobnosti o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, který transformuje jeden vstupní soubor do jednoho výstupního souboru, který má zkompilovat nebo přidat do projektu.  
  
 <xref:EnvDTE.ProjectItem>  
 Vysvětluje, `ProjectItem` rozhraní, která představuje položku v projektu.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Poskytuje podrobnosti o `DefaultExtension` metodu, která načte příponu názvu souboru, který je uveden název výstupního souboru.  
  
## <a name="related-sections"></a>Související oddíly  
 [Rozšíření projektů](../../extensibility/extending-projects.md)  
 Popisuje způsob použití [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projekty a řešení pro uspořádání souborů s kódem a soubory prostředků a jak implementovat správy zdrojového kódu.

