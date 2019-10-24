---
title: Základy typu projektu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 435d3ca0e35911754cac1e37abb276939109a0b3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725409"
---
# <a name="project-type-essentials"></a>Základy typů projektů
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsahuje několik typů projektů pro jazyky, jako je například [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] nebo [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] také umožňuje vytvořit vlastní typy projektů.

 Pokud chcete pouze přidat vlastní příkazy, editory nebo okna nástrojů do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], můžete tak učinit bez vytvoření nového typu projektu. Další informace naleznete v následujících tématech:

- [Příkazy, nabídky a panely nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Editor a rozšíření služeb jazyka](../../extensibility/editor-and-language-service-extensions.md)

- [Rozšíření a přizpůsobení panelů nástrojů](../../extensibility/extending-and-customizing-tool-windows.md)

  Podobně, pokud chcete přizpůsobit chování zadaných [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] a [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] typy projektů, můžete tak učinit pomocí podtypů projektu. Další informace naleznete v tématu [podtypy projektu](../../extensibility/internals/project-subtypes.md).

  Je nutné vytvořit nový typ projektu pro projekty, které jsou založeny na jiném jazyce než [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] a [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], pokud chcete podporovat jednu nebo více následujících akcí:

- Sestavení

- Nasazení

- Více konfigurací

- Správa zdrojového kódu

- Ladění

- Položky projektu v Průzkumník řešení

- Dialogová okna **Otevřít projekt** nebo **Nový projekt**

- Vnoření projektu

- Další informace o možnostech typů projektů naleznete v následujících tématech:

- Typy projektů jsou objekty ve VSPackage, které implementují sadu rozhraní [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] očekává. Pokud používáte C# pro vývoj typu projektu, třídy projektu spravovaného balíčku implementují pro vás potřebná rozhraní a umožňují dědění této implementace. Další informace najdete v tématu [použití spravovaného balíčku balíčku k implementaci typu projektu (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).

- Pro C++ vývojáře třídy v knihovně HierUtil fungují podobným způsobem. Další informace najdete v tématu [ne v sestavení: použití tříd projektu HierUtil7 k implementaci typu projektu (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

- Typy projektů mohou podporovat jiná data než typické soubory zdrojového kódu, které sestavují do sestavení. exe nebo. dll. Například [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] databázových projektů obsahuje odkazy na soubory skriptu a dotazy uložené na disku a přidat příkazy, které **Průzkumník řešení** k provádění skriptů a dotazů pro databázi, ale projekty nepodporují chování sestavení. Další informace naleznete v tématu [otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md).

- Typ projektu nemusí vůbec používat soubory. Typ projektu může například ukládat veškerá jeho data do databáze. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje typy projektů úplnou kontrolu nad tím, jak uchovávají data pro projekty a položky projektu. Další informace naleznete v tématu [rozhodnutí o návrhu typu projektu](../../extensibility/internals/project-type-design-decisions.md).

- Typy projektů musí poskytovat objekt pro *vytváření projektu*, což je objekt, který vytváří instanci typu projektu vždy, když [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je k otevření nebo vytvoření projektu, který je založen na daném typu projektu. Další informace naleznete v tématu [vytváření instancí projektu pomocí továrnování projektu](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

- Typy projektů musí poskytovat šablony pro projekty a položky projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] používá šablony, když uživatelé vytvoří nové projekty a přidají nové položky do existujících projektů. Další informace naleznete v tématu [Přidání projektů a šablon položek projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).

- Typy projektů mohou podporovat více konfigurací, jako je například ladění a vydání. Uživatelé mohou změnit různé konfigurace projektu pomocí stránek vlastností, které zadáte. Další informace najdete v tématu [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md).

## <a name="see-also"></a>Viz také:
- [Nasazování typů projektů](../../extensibility/internals/deploying-project-types.md)