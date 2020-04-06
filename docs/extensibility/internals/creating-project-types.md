---
title: Vytváření typů projektů | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: d2398b63b8cd52784252cfc764bb6c6a30e1accc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709072"
---
# <a name="create-project-types"></a>Vytvořit typy projektů
Můžete rozšířit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vytvořením nového typu projektu. Chcete-li vytvořit nový typ projektu, musíte pochopit několik konceptů a provést několik kroků. Následující témata poskytují přehled o tom, jak vytvořit typy projektů.

## <a name="in-this-section"></a>V tomto oddílu
- [Rozhodnutí o návrhu typu projektu](../../extensibility/internals/project-type-design-decisions.md)

 Popisuje položku, trvalost souboru projektu a rozhodnutí o návrhu mechaniky závazku, která je třeba provést před vytvořením nového typu projektu.

- [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)

 Obsahuje přehled kroků, které je nutné postupovat k vytvoření nového typu projektu, který podporuje takové programovací úlohy, jako je úprava kódu a kompilace, vytváření, ladění a nasazování aplikací v projektu.

- [Vytvoření instancí projektu pomocí továren projektu](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Obsahuje informace o tom, jak poskytnout a použít továrnu projektu k vytvoření instancí nového projektu.

- [Registrace typu projektu](../../extensibility/internals/registering-a-project-type.md)

 Poskytuje ukázky kódu příkazů z registru, které poskytují výchozí cesty a data, a tabulku, která obsahuje položky ze skriptu registru pro každý příkaz.

- [Trvalosti projektu](../../extensibility/internals/project-persistence.md)

 Popisuje použití `IPersistFileFormat` zachovat soubor i nezaložené na souboru objekty projektu.

- [Použití nástroje MSBuild](../../extensibility/internals/using-msbuild.md)

 Popisuje, jak typ projektu [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] můžete použít modul sestavení, aby uživatelé stavět z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a na příkazovém řádku.

## <a name="related-sections"></a>Související oddíly
- [Podpora nástrojů pro procházení symbolů](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Vysvětluje architekturu nástrojů pro zobrazení kódu, jako je prohlížeč **objektů** a okno **Zobrazení tříd.** Popisuje rozhraní a metody, které se používají k implementaci procházení objektů v Balíčku VSPackage.

- [Přidání šablon položek projektu a projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Popisuje význam, který projekty hrají při určování, který editor se používá při otevření položky projektu a jak lze manipulovat s prostředky projektu.

- [Instalace balíčků VSPackages pomocí Instalační služby systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 Ukazuje, jak dát vspackage vlastní jedinečnou identitu a jak zabalit knihovny DLL balíčku VSPackage a další informace v balíčku Instalační služby systému Windows (*. msi)* pro nasazení pro vaše zákazníky.

- [Hierarchie v sadě Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Popisuje způsob [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zobrazení a adres hierarchií.

- [Balíčky VSPackage](../../extensibility/internals/vspackages.md)

 Obsahuje přehled VSPackage, instalovatelný objekt COM, který [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozšiřuje prostředí a popisuje, jak implementovat vlastní VSPackage.

- [Typy projektů](../../extensibility/internals/project-types.md)

 Popisuje, jak pomocí projektů upravit kód, kompilovat a sestavit kód a spustit a ladit kód a poskytuje odkazy na podrobná témata o tom, jak vytvořit typy projektů.
