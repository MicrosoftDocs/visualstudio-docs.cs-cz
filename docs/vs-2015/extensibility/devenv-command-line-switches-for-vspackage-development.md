---
title: Přepínače příkazového řádku nástroje devenv pro vývoj VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
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
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 97ce429a7140d7b95393c2dcb8b34491b3adfefa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185282"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Přepínače příkazového řádku nástroje Devenv pro vývoj rozšíření VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] umožňuje vývojářům automatizovat úlohy z příkazového řádku při spuštění devenv.exe, souboru, který spouští integrované vývojové prostředí (IDE) sady Visual Studio.  
  
 Mezi úlohy patří:  
  
- Nasazení aplikací v předem navržených konfiguracích z vnějšku rozhraní IDE.  
  
- Automatické vytváření projektů pomocí přednastavených nastavení sestavení nebo konfigurací ladění.  
  
- Načítání integrovaného vývojového prostředí (IDE) v konkrétních konfiguracích, od vně rozhraní IDE. Kromě toho můžete prostředí IDE přizpůsobit při spuštění.  
  
## <a name="guidelines-for-switches"></a>Pokyny pro přepínače  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dokumentace popisuje přepínače příkazového řádku devenv na úrovni uživatele. Další informace najdete v tématu [přepínače příkazového řádku devenv](../ide/reference/devenv-command-line-switches.md). Devenv podporuje také další přepínače příkazového řádku, které jsou užitečné při vývoji, nasazení a ladění VSPackage.  
  
|Přepínač příkazového řádku|Popis|  
|--------------------------|-----------------|  
|/safemode|Spustí se [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v nouzovém režimu, načítají se jenom výchozí integrované vývojové prostředí (IDE) a služby. Přepínač/safemode zabraňuje načtení všech rozhraní VSPackage třetí strany při [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] spuštění, čímž zajistí stabilní spuštění.<br /><br /> Tento přepínač nepřijímá žádné argumenty.|  
|/resetskippkgs|Zruší všechny možnosti pro přeskočení načítání, které byly přidány uživateli, kteří se chtějí vyhnout načítání problematických VSPackage, a pak spustí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Přítomnost značky SkipLoading zakáže načítání VSPackage. Vymazání značky znovu povolí načítání VSPackage.<br /><br /> Tento přepínač nepřijímá žádné argumenty.|  
|/rootsuffix|Spustí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se pomocí alternativního umístění. Následující příkaz se spustí pomocí zástupce vytvořeného [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] instalačním programem:<br /><br /> /RootSuffix devenv<br /><br /> V takovém případě exp identifikuje umístění s konkrétní příponou, například 10.0 exp místo 10,0. Experimentální instance umožňuje ladit VSPackage odděleně od instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , kterou používáte k psaní kódu.<br /><br /> Tento přepínač může přijmout libovolný řetězec, který určuje umístění, které jste vytvořili pomocí VSRegEx.exe. Další informace najdete v [experimentální instanci](../extensibility/the-experimental-instance.md).|  
|/splash|Zobrazuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] úvodní obrazovku jako obvykle a pak před zobrazením hlavního integrovaného vývojového prostředí (IDE) zobrazuje okno se zprávou. Okno se zprávou vám umožní prozkoumat úvodní obrazovku, například, aby zkontrolovala ikonu produktu VSPackage.<br /><br /> Tento přepínač nepřijímá žádné argumenty.|  
  
## <a name="see-also"></a>Viz také  
 [Přidávání přepínačů příkazového řádku](../extensibility/adding-command-line-switches.md)   
 [Devenv – přepínače příkazového řádku](../ide/reference/devenv-command-line-switches.md)
