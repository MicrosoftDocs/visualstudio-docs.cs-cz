---
title: Základy typů projektů | Dokumentace Microsoftu
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
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a719ea26473874cb0d771b46ee05ea15092fb17
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51746459"
---
# <a name="project-type-essentials"></a>Základy typů projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obsahuje několik typů projektů pro jazyky, jako například [!INCLUDE[csprcs](../../includes/csprcs-md.md)] nebo [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] také umožňuje vytvořit vlastní typy projektů.  
  
 Pokud chcete přidat vlastní příkazy, editory nebo okna nástrojů do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], jde to provést bez vytvoření nového typu projektu. Další informace naleznete v následujících tématech:  
  
- [Příkazy, nabídky a panely nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
- [Editor a rozšíření služeb jazyka](../../extensibility/editor-and-language-service-extensions.md)  
  
- [Rozšíření a přizpůsobení panelů nástrojů](../../extensibility/extending-and-customizing-tool-windows.md)  
  
  Podobně pokud chcete přizpůsobit chování zadané [!INCLUDE[csprcs](../../includes/csprcs-md.md)] a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] typy projektů, můžete provést pomocí podtypů projektů. Další informace najdete v tématu [podtypů projektů](../../extensibility/internals/project-subtypes.md).  
  
  Musíte vytvořit nový typ projektu pro projekty, které vycházejí z jazyka jiného než [!INCLUDE[csprcs](../../includes/csprcs-md.md)] a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Pokud chcete zajistit podporu jeden nebo více z následujících akcí:  
  
- Sestavení  
  
- Nasazení  
  
- Více konfigurací  
  
- Správy zdrojového kódu  
  
- Ladění  
  
- Položky projektu v Průzkumníku řešení  
  
- **Otevřít projekt** nebo **nový projekt** dialogová okna  
  
- Vnoření projektů  
  
- Další informace o možnostech typů projektů naleznete v následujících tématech:  
  
- Typy projektů jsou objekty v sadě VSPackage, implementující sadu rozhraní [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] očekává. Pokud používáte C# na vývoj typu projektu, projektu třídy Managed Package Framework implementovat rozhraní potřebná pro vás a umožňují dědit tuto implementaci. Další informace najdete v tématu [pomocí Managed Package Framework pro implementaci typu projektu (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
- Pro vývojáře v jazyce C++ tříd v knihovně HierUtil pracovní podobným způsobem. Další informace najdete v tématu [není v sestavení: použití třídy HierUtil7 projektu k implementaci typu projektu (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
- Typy projektů může podporovat dat než typické zdrojové soubory sestavení do sestavení .exe nebo .dll. Například [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] databázové projekty obsahují odkazy na skript a dotaz soubory uložené na disku a přidání příkazů pro **Průzkumníka řešení** ke spuštění skriptů a dotazy na databázi, ale projektů nepodporují chování sestavení. Další informace najdete v tématu [otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md).  
  
- Typ projektu nemusí vůbec používat soubory. Například typ projektu může uchovávat svá data v databázi. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] poskytuje typy projektů úplnou kontrolu nad jak jsou zachována i data pro projekty a položky projektu. Další informace najdete v tématu [rozhodnutí o návrhu typu projektu](../../extensibility/internals/project-type-design-decisions.md).  
  
- Musíte zadat typy projektů *objekt pro vytváření projektu*, což je objekt, který vytvoří instanci projektu zadejte vždy, když [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] některého otevřete nebo vytvořte projekt, který je založen na typu projektu. Další informace najdete v tématu [vytváření instancí podle pomocí projektu objekty pro vytváření projektů](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
- Typy projektů, musíte zadat šablon projektů a položek projektů. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] používá šablony, když uživatelé vytvářet nové projekty a přidání nových položek do existujících projektů. Další informace najdete v tématu [přidání projektů a šablon položek projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
- Typy projektů může podporovat více konfigurací, jako je ladění a vydání. Uživatelé mohou změnit další možnosti konfigurace projektu pomocí stránky vlastností, které zadáte. Další informace najdete v tématu [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Viz také  
 [Nasazování typů projektů](../../extensibility/internals/deploying-project-types.md)

