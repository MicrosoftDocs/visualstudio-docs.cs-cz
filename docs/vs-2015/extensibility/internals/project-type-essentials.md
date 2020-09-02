---
title: Základy typu projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e45d5f252deaf1788ae5093048ef8afb900fbe4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704063"
---
# <a name="project-type-essentials"></a>Základy typů projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obsahuje několik typů projektů pro jazyky, jako jsou [!INCLUDE[csprcs](../../includes/csprcs-md.md)] nebo [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] . [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] také umožňuje vytvořit vlastní typy projektů.  
  
 Pokud chcete pouze přidat vlastní příkazy, editory nebo okna nástrojů do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , můžete tak učinit bez vytvoření nového typu projektu. Další informace najdete v následujících tématech:  
  
- [Příkazy, nabídky a panely nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
- [Editor a rozšíření služeb jazyka](../../extensibility/editor-and-language-service-extensions.md)  
  
- [Rozšíření a přizpůsobení panelů nástrojů](../../extensibility/extending-and-customizing-tool-windows.md)  
  
  Podobně pokud chcete přizpůsobit chování dodaných [!INCLUDE[csprcs](../../includes/csprcs-md.md)] a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projektových typů, můžete tak učinit pomocí podtypů projektu. Další informace naleznete v tématu [podtypy projektu](../../extensibility/internals/project-subtypes.md).  
  
  Je nutné vytvořit nový typ projektu pro projekty, které jsou založeny na jiném jazyku, než [!INCLUDE[csprcs](../../includes/csprcs-md.md)] a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Pokud chcete podporovat jednu nebo více následujících možností:  
  
- Sestavení  
  
- Nasazení  
  
- Více konfigurací  
  
- Správa zdrojového kódu  
  
- Ladění  
  
- Položky projektu v Průzkumník řešení  
  
- Dialogová okna **Otevřít projekt** nebo **Nový projekt**  
  
- Vnoření projektu  
  
- Další informace o možnostech typů projektů naleznete v následujících tématech:  
  
- Typy projektů jsou objekty ve VSPackage, které implementují sadu rozhraní, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] očekává. Pokud používáte jazyk C# pro vývoj typu projektu, třídy projektu spravovaného balíčku implementují pro vás potřebná rozhraní a umožňují dědění této implementace. Další informace najdete v tématu [použití spravovaného balíčku balíčku k implementaci typu projektu (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
- Pro vývojáře v jazyce C++ fungují třídy v knihovně HierUtil podobným způsobem. Další informace najdete v tématu [není v sestavení: použití tříd projektu HierUtil7 k implementaci typu projektu (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
- Typy projektů mohou podporovat jiná data než typické soubory zdrojového kódu, které sestavují do sestavení. exe nebo. dll. Například [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] databázové projekty obsahují odkazy na soubory skriptu a dotazy, které jsou uloženy na disku, a přidávají příkazy pro **Průzkumník řešení** ke spouštění skriptů a dotazů na databázi, ale projekty nepodporují chování sestavení. Další informace naleznete v tématu [otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md).  
  
- Typ projektu nemusí vůbec používat soubory. Typ projektu může například ukládat veškerá jeho data do databáze. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] poskytuje typům projektů úplnou kontrolu nad tím, jak uchovávají data pro projekty a položky projektu. Další informace naleznete v tématu [rozhodnutí o návrhu typu projektu](../../extensibility/internals/project-type-design-decisions.md).  
  
- Typy projektů musí poskytovat objekt pro *vytváření projektu*, což je objekt, který vytváří instanci typu projektu, kdykoli [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] je k otevření nebo vytvoření projektu, který je založen na daném typu projektu. Další informace naleznete v tématu [vytváření instancí projektu pomocí továrnování projektu](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
- Typy projektů musí poskytovat šablony pro projekty a položky projektu. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] používá šablony, když uživatelé vytvářejí nové projekty a přidávají nové položky do existujících projektů. Další informace naleznete v tématu [Přidání projektů a šablon položek projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
- Typy projektů mohou podporovat více konfigurací, jako je například ladění a vydání. Uživatelé mohou změnit různé konfigurace projektu pomocí stránek vlastností, které zadáte. Další informace najdete v tématu [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Viz také  
 [Nasazování typů projektů](../../extensibility/internals/deploying-project-types.md)
