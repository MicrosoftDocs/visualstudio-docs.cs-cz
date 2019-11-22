---
title: 'Začínáme s PTVS: vytváření webů v Azure | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 3bdbda36-14d2-4fde-ba42-d91042777ff6
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 288fb24c9c1c4ddee1cb59a968e717531e274af1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300593"
---
# <a name="getting-started-with-ptvs-building-a-website-in-azure"></a>Začínáme s PTVS: Vytváření webu v Azure
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete rychle začít vytvářet weby v Pythonu v Azure.  
  
 Můžete sledovat tyto pokyny ve velmi krátké [videa youtube](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6).  
  
 Začněte s novým projektem... dialog a v části projekty Pythonu vyberte webový projekt láhve.  Tato šablona [láhve](http://bottlepy.org/docs/dev/index.html) je počáteční web založený na [spouštěcí architektuře](https://getbootstrap.com/).  Při vytváření projektu aplikace Visual Studio zobrazí výzvu k instalaci závislostí (v tomto případě láhev) do virtuálního prostředí.  Vzhledem k tomu, že nasazujete na web Azure, musíte přidat závislosti do virtuálního prostředí, aby bylo možné nasadit nezbytné bity pro operaci vaší lokality.  Je také nutné založit prostředí v Pythonu 2,7 nebo 3,4 32-bit.  Po vytvoření projektu stiskněte klávesu F5, aby se váš web spustil místně.  
  
 Vyzkoušení webu v Azure je snadné.  Pokud nemáte předplatné Azure, můžete použít [Try.azurewebsites.NET](https://trywebsites.azurewebsites.net/).  Tento web nabízí jednoduchý způsob, jak si můžete vyzkoušet Azure websites po celou hodinu, a to jenom pomocí sociálního přihlášení.  Nepotřebujete platební kartu.  Vyberte prázdnou šablonu webu v rozevíracím seznamu změnit jazyk a klikněte na tlačítko vytvořit.  V části práce s webovou aplikací vyberte Stáhnout profil publikování a uložte soubor pro použití se sadou Visual Studio.  Pomocí Gitu můžete nasadit i z libovolného operačního systému.  
  
 Přepněte zpět do sady Visual Studio a projektu, který jste vytvořili.  V Průzkumník řešení vyberte uzel projektu, klikněte na tlačítko pravý ukazatel a zvolte publikovat.  Pokud máte předplatné Azure, můžete v dialogovém okně kliknout na Microsoft Azure Websites a spravovat své weby odsud.  Pro tento návod vyberte Importovat a importujte publikační profil, který jste právě stáhli.  Vzhledem k tomu, že profil publikování obsahuje všechny nezbytné informace, můžete zvolit publikovat.  Během několika sekund se otevře nové okno prohlížeče a váš web je hostovaný v cloudu Azure.  
  
 Jednoduché weby jsou jednoduché, ale informace o důležitějších webových aplikacích v Azure najdete v části [podrobně](https://www.youtube.com/watch?v=WG3pGmoo8nE&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=10) video a také ostatní v tomto kanálu (odkaz v pravém horním rohu stránky Začínáme nebo hluboko podrobně video), a taky dál.  
  
 Můžete sledovat tyto pokyny ve velmi krátké [videa youtube](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6).  
  
## <a name="see-also"></a>Viz také  
   [dokumentaci k wiki](https://github.com/Microsoft/PTVS/wiki/Web-Project)  
 [Videa můžete začít a Deep Dive PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
