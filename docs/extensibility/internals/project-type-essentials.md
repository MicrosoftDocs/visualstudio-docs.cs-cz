---
title: Základy typů projektů | Microsoft Docs
description: Přečtěte si, kdy je nutné vytvořit typ projektu a kdy můžete rozšířit existující typ projektu pomocí podtypů projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 051e7b76edd4559914307459fdcbdf1b7c0b600e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903552"
---
# <a name="project-type-essentials"></a>Základy typů projektů
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsahuje několik typů projektů pro jazyky, jako je [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] nebo [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] také umožňuje vytvářet vlastní typy projektů.

 Pokud chcete do přidat vlastní příkazy, editory nebo okna nástrojů, můžete to udělat bez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vytvoření nového typu projektu. Další informace najdete v následujících tématech:

- [Příkazy, nabídky a panely nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Editor a rozšíření služeb jazyka](../../extensibility/editor-and-language-service-extensions.md)

- [Rozšíření a přizpůsobení panelů nástrojů](../../extensibility/extending-and-customizing-tool-windows.md)

  Podobně pokud chcete přizpůsobit chování zadaných typů a typů projektu, můžete to [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] provést pomocí podtypů projektu. Další informace najdete v tématu [Podtypy projektů.](../../extensibility/internals/project-subtypes.md)

  Je nutné vytvořit nový typ projektu pro projekty, které jsou založené na jiném jazyce než a pokud chcete podporovat [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] jeden nebo více z [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] následujících:

- Sestavení

- Nasazení

- Více konfigurací

- Správa zdrojového kódu

- Ladění

- Položky projektu v Průzkumník řešení

- Dialogová **okna Otevřít** projekt **nebo** Nový projekt

- Vnořování projektů

- Další informace o možnostech typů projektů najdete v následujících informacích:

- Typy projektů jsou objekty v balíčku VSPackage, které implementují sadu rozhraní, která [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] očekává. Pokud k vývoji typu projektu používáte jazyk C#, implementují třídy projektu Managed Package Framework potřebná rozhraní za vás a umožňují dědit tuto implementaci. Další informace najdete v tématu Implementace typu projektu pomocí rozhraní spravovaného balíčku [(C#).](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)

- Pro vývojáře v jazyce C++ fungují třídy v knihovně HierUtil podobným způsobem. Další informace naleznete v části [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type (C++)](/previous-versions/bb166212(v=vs.100)).

- Typy projektů mohou podporovat jiná data než typické soubory zdrojového kódu, které jsou součástí .exe nebo .dll sestavení. Databázové projekty například obsahují odkazy na skriptovací a dotazovací soubory uložené na disku a přidávají příkazy do Průzkumník řešení ke spouštění skriptů a dotazů na databázi, ale projekty nepodporují chování [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sestavení.  Další informace najdete v tématu [Otevírání a ukládání položek projektu.](../../extensibility/internals/opening-and-saving-project-items.md)

- Typ projektu nemusí vůbec používat soubory. Například typ projektu může ukládat všechna data do databáze. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje typům projektů úplnou kontrolu nad způsobem, jakým uchová data pro projekty a položky projektu. Další informace najdete v tématu [Rozhodnutí o návrhu typů projektů.](../../extensibility/internals/project-type-design-decisions.md)

- Typy projektů musí poskytovat objekt pro *vytváření* projektu , což je objekt, který vytvoří instanci typu projektu vždy, když je volána k otevření nebo vytvoření projektu založeného na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tomto typu projektu. Další informace najdete v tématu [Vytváření instancí projektu pomocí projektových továren.](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

- Typy projektů musí dodávat šablony pro projekty a položky projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] používá šablony, když uživatelé vytvářejí nové projekty a přidávají nové položky do existujících projektů. Další informace najdete v tématu [Přidání šablon projektů a položek projektu.](../../extensibility/internals/adding-project-and-project-item-templates.md)

- Typy projektů mohou podporovat více konfigurací, například ladění a vydání. Uživatelé mohou změnit různé konfigurace projektu pomocí stránek vlastností, které zadáte. Další informace najdete v tématu [Správa možností konfigurace.](../../extensibility/internals/managing-configuration-options.md)

## <a name="see-also"></a>Viz také
- [Nasazování typů projektů](../../extensibility/internals/deploying-project-types.md)