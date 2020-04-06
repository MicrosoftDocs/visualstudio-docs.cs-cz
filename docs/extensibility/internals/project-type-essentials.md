---
title: Typ projektu Essentials | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b44da532207668d9526aec0ccdcab027b94184e6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706385"
---
# <a name="project-type-essentials"></a>Základy typů projektů
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]obsahuje několik typů projektů [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] pro [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]jazyky, jako je například nebo . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]také umožňuje vytvářet vlastní typy projektů.

 Pokud chcete do aplikace přidat pouze vlastní příkazy, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]editory nebo okna nástrojů , můžete tak učinit bez vytvoření nového typu projektu. Další informace najdete v následujících tématech:

- [Příkazy, nabídky a panely nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Editor a rozšíření služeb jazyka](../../extensibility/editor-and-language-service-extensions.md)

- [Rozšíření a přizpůsobení panelů nástrojů](../../extensibility/extending-and-customizing-tool-windows.md)

  Podobně pokud chcete přizpůsobit chování dodaných [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] a [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] typů projektů, můžete tak učinit pomocí podtypů projektu. Další informace naleznete [v tématu Podtypy projektu](../../extensibility/internals/project-subtypes.md).

  Je nutné vytvořit nový typ projektu pro projekty, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] které jsou založeny na jiném jazyce než a pokud chcete podporovat jednu nebo více z následujících možností:

- Sestavení

- Nasazení

- Více konfigurací

- Správa zdrojového kódu

- Ladění

- Položky projektu v Průzkumníku řešení

- Dialogová okna **Otevřít projekt** nebo **Nový projekt**

- Vnoření projektu

- Další informace o možnostech typů projektů naleznete v následujících tématech:

- Typy projektů jsou objekty v Balíčku VSPackage, které implementují sadu rozhraní [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] očekává. Pokud používáte C# k vývoji typu projektu, třídy projektu Spravované ho balíček framework implementovat potřebná rozhraní pro vás a umožňují dědit tuto implementaci. Další informace naleznete [v tématu Použití rozhraní spravovaného balíčku k implementaci typu projektu (C#).](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)

- Pro vývojáře jazyka C++ třídy v knihovně HierUtil pracovat podobným způsobem. Další informace naleznete [v tématu Not in Build: Using HierUtil7 Project Classes to Implement a Project Type (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

- Typy projektů mohou podporovat jiná data než typické soubory zdrojového kódu, které se vytvářejí do sestavení .exe nebo DLL. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Databázové projekty například obsahují odkazy na soubory skriptů a dotazů uložené na disku a přidávají příkazy do **Průzkumníka řešení** ke spuštění skriptů a dotazů proti databázi, ale projekty nepodporují chování sestavení. Další informace naleznete v [tématu Otevírání a ukládání položek projektu](../../extensibility/internals/opening-and-saving-project-items.md).

- Typ projektu nemusí používat soubory vůbec. Například typ projektu může ukládat všechna svá data v databázi. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]poskytuje typům projektů úplnou kontrolu nad tím, jak uchovávají data pro projekty a položky projektu. Další informace naleznete v [tématu Project Type Design Decisions](../../extensibility/internals/project-type-design-decisions.md).

- Typy projektů musí poskytnout *továrnu projektu*, což je objekt, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] který vytvoří instanci typu projektu vždy, když je řečeno, otevřít nebo vytvořit projekt, který je založen na tomto typu projektu. Další informace naleznete [v tématu Vytváření instancí projektu pomocí továren projektu](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

- Typy projektů musí dodávat šablony pro projekty a položky projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]používá šablony, když uživatelé vytvářejí nové projekty a přidávají nové položky do existujících projektů. Další informace naleznete [v tématu Přidání šablon položek projektu a projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).

- Typy projektů může podporovat více konfigurací, jako je například ladění a vydání. Uživatelé mohou změnit různé konfigurace projektu pomocí stránek vlastností, které zadáte. Další informace naleznete v [tématu Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md).

## <a name="see-also"></a>Viz také
- [Nasazování typů projektů](../../extensibility/internals/deploying-project-types.md)
