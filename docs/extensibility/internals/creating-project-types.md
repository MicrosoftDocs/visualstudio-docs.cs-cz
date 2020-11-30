---
title: Vytváření typů projektů | Microsoft Docs
description: Naučte se, jak roztáhnout Visual Studio návrhem, vytvořením a registrací nového typu projektu, který podporuje úlohy programování.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4038a122c6d2ec5f6ed29df6e529b2bff2e2bb71
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329923"
---
# <a name="create-project-types"></a>Vytváření typů projektů
Můžete ho zvětšit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vytvořením nového typu projektu. Chcete-li vytvořit nový typ projektu, je nutné pochopit několik konceptů a provést několik kroků. Následující témata poskytují přehled o tom, jak vytvořit typy projektů.

## <a name="in-this-section"></a>V této části
- [Rozhodnutí o návrhu typu projektu](../../extensibility/internals/project-type-design-decisions.md)

 Popisuje položku, trvalost souborů projektu a rozhodnutí o návrhu nástroje pro rozhodování, která je nutné provést před vytvořením nového typu projektu.

- [Kontrolní seznam: vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)

 Poskytuje přehled kroků, které je nutné provést, chcete-li vytvořit nový typ projektu, který podporuje takové úkoly programování jako úpravy kódu a kompilování, sestavování, ladění a nasazování aplikací v projektu.

- [Vytváření instancí projektu pomocí továrnování projektu](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Obsahuje informace o tom, jak poskytnout a použít objekt pro vytváření projektu k vytvoření instancí nového projektu.

- [Registrace typu projektu](../../extensibility/internals/registering-a-project-type.md)

 Poskytuje ukázky kódu příkazů z registru, které poskytují výchozí cesty a data, a tabulku, která obsahuje položky ze skriptu registru pro každý příkaz.

- [Trvalost projektu](../../extensibility/internals/project-persistence.md)

 Popisuje použití `IPersistFileFormat` pro uchování souborů a objektů projektu založených na souborech.

- [Použití nástroje MSBuild](../../extensibility/internals/using-msbuild.md)

 Popisuje, jak může typ projektu použít [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] modul sestavení a umožnit tak uživatelům vytvářet z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] příkazového řádku a z něj.

## <a name="related-sections"></a>Související oddíly
- [Podpora nástrojů pro procházení symbolů](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Vysvětluje architekturu nástrojů pro zobrazování kódu, jako je **Prohlížeč objektů** a **zobrazení tříd** okno. Popisuje rozhraní a metody, které slouží k implementaci procházení objektů v VSPackage.

- [Přidat šablony projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Popisuje význam, který projekty hrají při určování, který Editor se používá, když je otevřená položka projektu a jak se dají manipulovat s prostředky projektu.

- [Instalace VSPackage pomocí Instalační služba systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 Ukazuje, jak poskytnout VSPackage svou vlastní jedinečnou identitu a jak zabalit knihovny VSPackage dll a další informace v balíčku Instalační služba systému Windows (*. Soubor MSI* ) pro nasazení pro vaše zákazníky.

- [Hierarchie v sadě Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Popisuje způsob [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zobrazení a adresování hierarchií.

- [Balíčky VSPackage](../../extensibility/internals/vspackages.md)

 Poskytuje přehled o VSPackage, instalovatelný objekt COM, který rozšiřuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prostředí a popisuje, jak implementovat vlastní VSPackage.

- [Typy projektů](../../extensibility/internals/project-types.md)

 Popisuje, jak používat projekty pro úpravu kódu, kompilování a sestavení kódu a spuštění a ladění kódu a obsahuje odkazy na podrobná témata týkající se vytváření typů projektů.
