---
title: 'Začínáme s PTVS: vytváření webu v Azure | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bdbda36-14d2-4fde-ba42-d91042777ff6
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 1c4f0d0a1bf963857cde5dc0c6aa36e2aa04ca7f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282747"
---
# <a name="getting-started-with-ptvs-building-a-website-in-azure"></a>Začínáme s PTVS: Vytváření webu v Azure
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete začít rychle vytvářet webu Pythonu v Azure.  
  
 Můžete sledovat tyto pokyny ve velmi krátké [videa youtube](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6).  
  
 Začněte nový projekt... Dialogové okno a projekty v Pythonu zvolte webový projekt Bottle.  To [Bottle](http://bottlepy.org/docs/dev/index.html) šablona je první web na základě [Bootstrap framework](http://getbootstrap.com/).  Při vytváření projektu sady Visual Studio vás vyzve k instalaci závislostí (Bottle v tomto případě) do virtuálního prostředí.  Vzhledem k tomu, že nasazujete na web Azure, budete muset přidat závislosti do virtuálního prostředí za účelem nasazení nezbytné bits pro provoz vašeho webu.  Potřebujete také založit vaše prostředí na Python 2.7 nebo 3.4 32-bit.  Po vytvoření projektu, stisknutím klávesy F5 spusťte váš web spuštěn místně.  
  
 Je snadné zkuste webu v Azure.  Pokud nemáte předplatné Azure, můžete použít [try.azurewebsites.net](https://trywebsites.azurewebsites.net/).  Tento web nabízí jednoduchý způsob, jak vyzkoušet Azure Websites je hodina současně s pouze přihlášení prostřednictvím sociální sítě.  Nepotřebujete platební kartu.  Výběr šablony funkce prázdný web v rozevírací nabídce změnit jazyk a zvolte možnost vytvořit.  V části "Práce s vaší webovou aplikací" zvolte stáhnout profil publikování a uložte soubor pro použití se sadou Visual Studio.  Můžete také nasadit pomocí git ve všech operačních systémech.  
  
 Přepněte zpět do sady Visual Studio a projekt, který jste vytvořili.  Vyberte uzel projektu v Průzkumníku řešení, klikněte na tlačítko vpravo ukazatele a vyberte publikovat.  Pokud máte předplatné Azure, můžete kliknout na Microsoft Azure Websites, v dialogovém okně spravovat vaše weby odsud.  V tomto návodu zvolte Import importovat profil publikování, který jste si právě stáhli.  Vzhledem k tomu, že profil publikování obsahuje všechny potřebné informace, můžete publikovat.  Během několika sekund se otevře nové okno prohlížeče a webu je v provozu hostované v cloudu Azure.  
  
 Jednoduché weby jsou jednoduché, ale informace významnější webové aplikace v Azure najdete v tématu [podrobné informace o](https://www.youtube.com/watch?v=WG3pGmoo8nE&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=10) stejně jako ostatní videa v tomto kanálu (odkaz v pravém horním rohu získávání spuštěna nebo deep dive stránka s videi věnovanými, stejně jako níže .  
  
 Můžete sledovat tyto pokyny ve velmi krátké [videa youtube](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6).  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace ke službě Wiki](https://github.com/Microsoft/PTVS/wiki/Web-Project)   
 [Videa můžete začít a Deep Dive PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

