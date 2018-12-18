---
title: Vytváření typů projektů | Dokumentace Microsoftu
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
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 58b31e363d78af7902e6174c9683b7e794031263
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756209"
---
# <a name="creating-project-types"></a>Vytváření typů projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Můžete rozšířit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tak, že vytvoříte nový typ projektu. Pokud chcete vytvořit nový typ projektu, musíte porozumět několika konceptům a dokončit několik kroků. Následující témata poskytují přehled o tom, jak vytvořit typy projektů.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Rozhodnutí týkající se návrhu typu projektu](../../extensibility/internals/project-type-design-decisions.md)  
 Tento článek popisuje položky, trvalost souborů projektu a závazku mechanik rozhodnutí, které je nutné provést před vytvořením nového typu projektu.  
  
 [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Poskytuje přehled kroků, které musíte provést, chcete-li vytvořit nový typ projektu, který podporuje programovacích úkolů jako úpravy kódu a kompilaci, sestavování, ladění a nasazování aplikací ve vašem projektu.  
  
 [Vytváření instancí projektu pomocí objektů pro vytváření projektů](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Poskytuje informace o tom, jak zadat a použít objekt pro vytváření projektu k vytvoření instance nového projektu.  
  
 [Registrace typu projektu](../../extensibility/internals/registering-a-project-type.md)  
 Poskytuje příklady příkazů z registru, které poskytují výchozí cesty a data a tabulky, které obsahují položky z registru skriptu příkazu for each.  
  
 [Trvalost projektu](../../extensibility/internals/project-persistence.md)  
 Popisuje způsob používání `IPersistFileFormat` zachování souborů a objektů nezaložené souboru projektu.  
  
 [Použití nástroje MSBuild](../../extensibility/internals/using-msbuild.md)  
 Popisuje, jak můžete pomocí typu projektu [!INCLUDE[vstecmsbuild](../../includes/vstecmsbuild-md.md)] modul umožňuje uživatelům sestavení ze sestavení [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a na příkazovém řádku.  
  
## <a name="related-sections"></a>Související oddíly  
 [Podpůrné nástroje procházení symbolů](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Popisuje architekturu kódu zobrazení nástroje, jako **prohlížeče objektů** a **zobrazení tříd** okna. Popisuje rozhraní a metody, které se používají k implementaci procházet objekty v sadě VSPackage.  
  
 [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Tento článek popisuje význam, které projekty hrají při určování, které editor se používá při otevření položky projektu a jak lze ovládat prostředky projektu.  
  
 [Instalace balíčků VSPackage pomocí Instalační služby systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Ukazuje, jak poskytnout vašeho balíčku VSPackage svou vlastní jedinečnou identitu a postup při zabalení vaší knihovny DLL balíčku VSPackage a další informace v balíčku Instalační služby systému Windows (. Soubor MSI) pro nasazení tak, aby vaši zákazníci.  
  
 [Hierarchie v sadě Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Popisuje, jak [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zobrazení a adresy hierarchie.  
  
 [Balíčky VSPackage](../../extensibility/internals/vspackages.md)  
 Obsahuje základní informace o balíčku VSPackage Instalovatelné objekt modelu COM, který rozšiřuje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prostředí a popisuje, jak implementovat vlastní VSPackage.  
  
 [Typy projektů](../../extensibility/internals/project-types.md)  
 Popisuje, jak pomocí projektů Úprava kódu, kompilaci a vytváření kódu a spuštění a ladění kódu a poskytuje odkazy na témata podrobné informace o tom, jak vytvořit typy projektů.

