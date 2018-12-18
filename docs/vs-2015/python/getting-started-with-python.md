---
title: Začínáme s Pythonem | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 5cb04bb01aaa6eb06c5e3c50aa13ab51c136678c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49275285"
---
# <a name="getting-started-with-python"></a>Začínáme s Pythonem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroje Pythonu pro Visual Studio (PTVS) je bezplatná, [open source](https://github.com/Microsoft/ptvs) modulu plug-in pro Visual Studio, která prostředí výkonné vývoj v jazyce Python.  
  
## <a name="python-the-language"></a>Jazyk Python
  
Python je oblíbený programovací jazyk, který používá mnoho univerzity, odborníky, autory skriptů aplikace, příležitostné vývojáři a profesionální vývojáři pracující na aplikace, weby a cloudové služby.

Jako programovací jazyk Python je:
  
- Spolehlivé.
- Obecně užitečná pro skriptování rychlé programy, skriptování aplikací, aplikací klasické pracovní plochy, webové servery, webové služby a vědecké výpočty.
- Snadno učí a má dobrý návrh podporovat dobré psaní kódu (mnoha vysokých školách použije pro úvodní kurzy programovací).
- Flexibilní a podporuje styly imperativní, funkční a objektově orientované programování.
- Zdarma a open source.
- Spustí se také všechny hlavní operační systémy.  
- Podporuje mnoho zdarma, užitečné a přehledné knihoven.  
- Podporuje spoustu dokumentace, ukázky a silné vývojářské komunity.  

Další informace o jazyku, začněte s [Python pro začátečníky](https://www.python.org/about/gettingstarted/) na webu python.org.

K instalaci Pythonu, sama, navštivte [ https://www.python.org/download/ ](https://www.python.org/download/).
 
  
## <a name="python-tools-for-visual-studio"></a>Python Tools for Visual Studio
  
Nástroje Pythonu pro Visual Studio, které si můžete nainstalovat z [visualstudio.com](https://www.visualstudio.com/en-us/explore/python-vs), poskytují následující funkce:  
  
- Podpora pro více interpretů: různé verze CPython, IronPython a IPython  
- Systém projektu, který implicitně vybere strukturu složek kódu v Pythonu a také umožňuje explicitní kontrolu, abyste mohli identifikovat kód aplikace, kód testu, webové stránky, JavaScript, skripty sestavení a tak dále.  
- Šablony projektů pro konzolu, web, Azure, datové vědy a jiné typy projektů.    
- Sada Azure SDK pro Python (viz níže)    
- Bohaté možnosti úpravy kódu porozumění funkcí a včetně barevné zvýrazňování, automatické dokončování váš kód a knihoven, signaturám, zobrazení tříd, přejít k definici, najít všechny odkazy, refaktoring a více syntaxe.    
- Okno aplikace interaktivní (REPL)
- IPython pomocí datových vizualizací.
- Podpora pro IronPython a .NET/WPF.    
- Bohatá podpora ladění bez projektu sady Visual Studio, možnost do existujícího spustitelného souboru, ve smíšeném režimu ladění, vzdálené ladění na Windows/Linux/Mac a ladění v interaktivním okně.   
- Nástroje pro profilaci.  
- Testovací nástroje.  
  
Následující prostředky vám pomůže začít pracovat:

- [Průvodce instalací](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)    
- [Získání krátkých videích Začínáme a deep dive](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)  
- Instalace a funkce ukázka (27 min)])https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Dokumentace](https://github.com/Microsoft/PTVS/wiki)  


Všimněte si, že Visual Studio v současné době neposkytuje způsob, jak vytvořit samostatný spustitelný soubor pomocí Pythonu, která v podstatě znamená, že program s vložený interpret Pythonu. Existují však různými prostředky v rámci komunity Python k tomu, jak je popsáno na [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython také podporuje se vložený do nativní aplikace, jak je popsáno v blogovém příspěvku [pomocí CPython Vložitelný soubor Zip](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/).
  
## <a name="building-ui-with-python"></a>Vytváření uživatelského rozhraní pomocí Pythonu  

Hlavní nabídky pro vytváření uživatelského rozhraní pomocí Pythonu, je [Qt projektu](https://www.qt.io/qt-for-application-development/), s vazbami pro Python, označované jako [PySide (oficiální vazby)](http://wiki.qt.io/PySide) (viz také [PySide soubory ke stažení](https://download.qt.io/official_releases/pyside/.)) a [PyQt](https://wiki.python.org/moin/PyQt). V současné době podpora Pythonu v sadě Visual Studio neobsahuje žádné konkrétní nástroje pro vývoj uživatelského rozhraní.

## <a name="azure-sdk-for-python"></a>Azure SDK pro Python
  
Sada Azure SDK pro Python, která podporuje Windows, Mac a Linux, usnadňuje používání a správu služeb Microsoft Azure. Podívejte se na následujících odkazech podrobnosti: 

- Chcete-li nainstalovat sadu SDK, použijte [indexu balíčků Pythonu](https://pypi.python.org/pypi/azure) nebo postupujte podle [instalace Pythonu a sady SDK](https://azure.microsoft.com/documentation/articles/python-how-to-install/) v dokumentaci k Azure. 
- [Azure SDK pro Centrum pro vývojáře Python](https://azure.microsoft.com/develop/python/) obsahuje velké množství nápovědy z instalace dokumentaci k kurzy.  Mezi nejdůležitější funkce následujícím:  
- Návody:
  - [Úložiště objektů Blob](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [Fronta úložiště](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Storage Table](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Fronty služby Service Bus](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Předplatná služby Service Bus](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Správa služeb](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>Vědecké výpočty

Kromě všech mezi odborníky přes data knihoven Pythonu nástroje Pythonu pro Visual Studio podporují IPython a IPython notebook, které je možné hostovat v Azure.

Doporučujeme, abyste získání IPython a vědecké výpočetní knihovny (matplotlib, scipy, numpy, atd.) z [University of California, Irvine](http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).  
  
## <a name="see-also"></a>Viz také  

[Začínáme s PTVS: nastavení Visual Studia](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[Začínáme s PTVS: začít kódovat (projekty)](../python/getting-started-with-ptvs-start-coding-projects.md)
[Začínáme s PTVS: úpravy kódu](../python/getting-started-with-ptvs-editing-code.md) 
 [Začínáme s PTVS: ladění](../python/getting-started-with-ptvs-debugging.md)
[Začínáme s PTVS: interaktivní Python](../python/getting-started-with-ptvs-interactive-python.md)
[Začínáme Práce s PTVS: vytváření webu v Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)

