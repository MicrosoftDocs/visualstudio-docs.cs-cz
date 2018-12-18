---
title: Základy typů projektů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b7daf114bb31019a499bc17e287df923107ee1a1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891567"
---
# <a name="project-type-essentials"></a>Základy typů projektů
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsahuje několik typů projektů pro jazyky, jako například [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] nebo [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] také umožňuje vytvořit vlastní typy projektů.  
  
 Pokud chcete přidat vlastní příkazy, editory nebo okna nástrojů do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], jde to provést bez vytvoření nového typu projektu. Další informace naleznete v následujících tématech:  
  
- [Příkazy, nabídky a panely nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
- [Editor a rozšíření služeb jazyka](../../extensibility/editor-and-language-service-extensions.md)  
  
- [Rozšíření a přizpůsobení panelů nástrojů](../../extensibility/extending-and-customizing-tool-windows.md)  
  
  Podobně pokud chcete přizpůsobit chování zadané [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] a [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] typy projektů, můžete provést pomocí podtypů projektů. Další informace najdete v tématu [podtypů projektů](../../extensibility/internals/project-subtypes.md).  
  
  Musíte vytvořit nový typ projektu pro projekty, které vycházejí z jazyka jiného než [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] a [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Pokud chcete zajistit podporu jeden nebo více z následujících akcí:  
  
- Sestavení  
  
- Nasazení  
  
- Více konfigurací  
  
- Správy zdrojového kódu  
  
- Ladění  
  
- Položky projektu v Průzkumníku řešení  
  
- **Otevřít projekt** nebo **nový projekt** dialogová okna  
  
- Vnoření projektů  
  
- Další informace o možnostech typů projektů naleznete v následujících tématech:  
  
- Typy projektů jsou objekty v sadě VSPackage, implementující sadu rozhraní [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] očekává. Pokud používáte C# na vývoj typu projektu, projektu třídy Managed Package Framework implementovat rozhraní potřebná pro vás a umožňují dědit tuto implementaci. Další informace najdete v tématu [pomocí Managed Package Framework pro implementaci typu projektu (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
- Pro vývojáře v jazyce C++ tříd v knihovně HierUtil pracovní podobným způsobem. Další informace najdete v tématu [není v sestavení: použití třídy HierUtil7 projektu k implementaci typu projektu (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
- Typy projektů může podporovat dat než typické zdrojové soubory sestavení do sestavení .exe nebo .dll. Například [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] databázové projekty obsahují odkazy na skript a dotaz soubory uložené na disku a přidání příkazů pro **Průzkumníka řešení** ke spuštění skriptů a dotazy na databázi, ale projektů nepodporují chování sestavení. Další informace najdete v tématu [otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md).  
  
- Typ projektu nemusí vůbec používat soubory. Například typ projektu může uchovávat svá data v databázi. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje typy projektů úplnou kontrolu nad jak jsou zachována i data pro projekty a položky projektu. Další informace najdete v tématu [rozhodnutí o návrhu typu projektu](../../extensibility/internals/project-type-design-decisions.md).  
  
- Musíte zadat typy projektů *objekt pro vytváření projektu*, což je objekt, který vytvoří instanci projektu zadejte vždy, když [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] některého otevřete nebo vytvořte projekt, který je založen na typu projektu. Další informace najdete v tématu [vytváření instancí podle pomocí projektu objekty pro vytváření projektů](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
- Typy projektů, musíte zadat šablon projektů a položek projektů. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] používá šablony, když uživatelé vytvářet nové projekty a přidání nových položek do existujících projektů. Další informace najdete v tématu [přidání projektů a šablon položek projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
- Typy projektů může podporovat více konfigurací, jako je ladění a vydání. Uživatelé mohou změnit další možnosti konfigurace projektu pomocí stránky vlastností, které zadáte. Další informace najdete v tématu [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Viz také  
 [Nasazování typů projektů](../../extensibility/internals/deploying-project-types.md)