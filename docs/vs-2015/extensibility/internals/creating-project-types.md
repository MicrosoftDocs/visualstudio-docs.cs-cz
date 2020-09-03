---
title: Vytváření typů projektů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bbe65d1615603e4dc7546dbfe3530093c62528e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155029"
---
# <a name="creating-project-types"></a>Vytváření typů projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Můžete ho zvětšit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] vytvořením nového typu projektu. Chcete-li vytvořit nový typ projektu, je nutné pochopit několik konceptů a provést několik kroků. Následující témata poskytují přehled o tom, jak vytvořit typy projektů.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Rozhodnutí týkající se návrhu typu projektu](../../extensibility/internals/project-type-design-decisions.md)  
 Popisuje položku, trvalost souborů projektu a rozhodnutí o návrhu nástroje pro rozhodování, která je nutné provést před vytvořením nového typu projektu.  
  
 [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Poskytuje přehled kroků, které je nutné provést, chcete-li vytvořit nový typ projektu, který podporuje programovací úkoly jako úpravy kódu a kompilování, sestavování, ladění a nasazování aplikací v projektu.  
  
 [Vytváření instancí projektu pomocí objektů pro vytváření projektů](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Obsahuje informace o tom, jak poskytnout a použít objekt pro vytváření projektu k vytvoření instancí nového projektu.  
  
 [Registrace typu projektu](../../extensibility/internals/registering-a-project-type.md)  
 Poskytuje ukázky kódu příkazů z registru, které poskytují výchozí cesty a data, a tabulku, která obsahuje položky ze skriptu registru pro každý příkaz.  
  
 [Trvalost projektu](../../extensibility/internals/project-persistence.md)  
 Popisuje použití `IPersistFileFormat` pro uchování souborů a objektů projektu založených na souborech.  
  
 [Použití nástroje MSBuild](../../extensibility/internals/using-msbuild.md)  
 Popisuje, jak může typ projektu použít [!INCLUDE[vstecmsbuild](../../includes/vstecmsbuild-md.md)] modul sestavení a umožnit tak uživatelům vytvářet z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] příkazového řádku a z něj.  
  
## <a name="related-sections"></a>Související oddíly  
 [Podpůrné nástroje procházení symbolů](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Vysvětluje architekturu nástrojů pro zobrazování kódu, jako je **Prohlížeč objektů** a **zobrazení tříd** okno. Popisuje rozhraní a metody, které slouží k implementaci procházení objektů v VSPackage.  
  
 [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Popisuje význam, který projekty hrají při určování, který Editor se používá, když je otevřená položka projektu a jak se dají manipulovat s prostředky projektu.  
  
 [Instalace balíčků VSPackage pomocí Instalační služby systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Ukazuje, jak poskytnout VSPackage svou vlastní jedinečnou identitu a jak zabalit knihovny VSPackage dll a další informace v balíčku Instalační služba systému Windows (. Soubor MSI) pro nasazení pro vaše zákazníky.  
  
 [Hierarchie v sadě Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Popisuje způsob [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zobrazení a adresování hierarchií.  
  
 [Balíčky VSPackage](../../extensibility/internals/vspackages.md)  
 Poskytuje přehled o VSPackage, instalovatelný objekt COM, který rozšiřuje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prostředí a popisuje, jak implementovat vlastní VSPackage.  
  
 [Typy projektů](../../extensibility/internals/project-types.md)  
 Popisuje, jak používat projekty pro úpravu kódu, kompilování a sestavení kódu a spuštění a ladění kódu a obsahuje odkazy na podrobná témata týkající se vytváření typů projektů.
