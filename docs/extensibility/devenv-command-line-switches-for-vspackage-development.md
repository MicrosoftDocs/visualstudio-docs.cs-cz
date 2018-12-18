---
title: Přepínače příkazového řádku nástroje DEVENV pro vývoj rozšíření VSPackage | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- /setup command line switch
- /resetskippkgs command line switch
- /noVSIP command line switch
- /rootsuffix command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8fd305133f913877f8d4ad4808a8c4efcab52af4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847055"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Přepínače příkazového řádku nástroje DEVENV pro vývoj rozšíření VSPackage
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] umožňuje vývojářům automatizovat úlohy z příkazového řádku při provádění *devenv.exe*, soubor, který spouští integrovaného vývojového prostředí (IDE) sady Visual Studio.  

 Mezi úlohy patří:  

-   Nasazení aplikací v předem navrženými konfigurace z mimo rozhraní IDE.  

-   Vytváření projektů pomocí přednastavených automaticky nastavení sestavení nebo konfiguraci ladění.  

-   Načítání integrovaného vývojového prostředí v konkrétní konfigurace, z mimo rozhraní IDE. Kromě toho můžete přizpůsobit IDE po spuštění.  

## <a name="guidelines-for-switches"></a>Pokyny pro přepínače  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dokumentace popisuje přepínače příkazového řádku nástroje devenv uživatelské úrovni. Další informace najdete v tématu [přepínače příkazového řádku nástroje Devenv](../ide/reference/devenv-command-line-switches.md). DEVENV podporuje také další přepínače příkazového řádku, které jsou užitečné se VSPackage vývoje, nasazení a ladění.  


| Přepínač příkazového řádku | Popis |
|---------------------| - |
| / safemode | Spustí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] v nouzovém režimu, načítání výchozí integrovaného vývojového prostředí a služeb. Při načítání všech balíčků VSPackage třetích stran zabraňuje přepínač/safemode [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se spustí, čímž zajišťuje stabilní spuštění.<br /><br /> Tento přepínač nepřijímá žádné argumenty. |
| / resetskippkgs | Vymaže všechny Přeskočit načítání možnosti, které byly přidány podle uživatelů, kteří chtějí předejít problematické rozšíření VSPackages, pak spustí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Přítomnost značky SkipLoading zakáže načítání VSPackage. Vymazává se značka znovu povolí načítání sady VSPackage.<br /><br /> Tento přepínač nepřijímá žádné argumenty. |
| /rootsuffix | Spustí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pomocí alternativního umístění. Následující příkaz spustí místní vytvořené [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] instalačního programu:<br /><br /> exp /RootSuffix nástroje devenv<br /><br /> V takovém případě exp identifikuje umístění s konkrétní příponou, třeba 10.0Exp spíše než 10.0. Experimentální instanci umožňuje ladit VSPackage odděleně od instance [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , že používáte psaní kódu.<br /><br /> Tento přepínač můžete využít libovolný řetězec, který identifikuje, kterou jste vytvořili pomocí VSRegEx.exe umístění. Další informace najdete v tématu [experimentální instanci](../extensibility/the-experimental-instance.md). |
| /Splash | Ukazuje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] obvyklým úvodní obrazovka a poté zobrazí okno se zprávou před zobrazením hlavní integrovaného vývojového prostředí. Okno se zprávou umožňuje zkoumat úvodní obrazovka Hledat ikona produktu VSPackage, třeba.<br /><br /> Tento přepínač nepřijímá žádné argumenty. |

## <a name="see-also"></a>Viz také:  
 [Přidání přepínačů příkazového řádku](../extensibility/adding-command-line-switches.md)   
 [Přepínače příkazového řádku nástroje devenv](../ide/reference/devenv-command-line-switches.md)