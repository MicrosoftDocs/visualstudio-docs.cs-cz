---
title: Začínáme s Pythonem | Dokumenty společnosti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 97d60fe31f838c4cc497701f4560dc426ebc1cc9
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543976"
---
# <a name="getting-started-with-python"></a>Začínáme s Pythonem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Python Tools for Visual Studio (PTVS) je bezplatný modul plug-in s [otevřeným zdrojovým kódem](https://github.com/Microsoft/ptvs) pro Visual Studio, který je výkonným prostředím pro vývoj Pythonu.  
  
## <a name="python-the-language"></a>Jazyk Pythonu
  
Python je populární programovací jazyk, který používá mnoho univerzit, vědců, skriptovacích aplikací, příležitostných vývojářů a profesionálních vývojářů, kteří pracují na aplikacích, webových stránkách a cloudových službách.

Jako programovací jazyk je Python:
  
- Spolehlivé.
- Obecně užitečné pro skriptování rychlých programů, skriptování aplikací, aplikací klasické pracovní plochy, webových serverů, webových služeb a vědeckých výpočtů.
- Snadno se učí a má dobrý design na podporu dobré kódování (mnoho univerzit používat pro úvodní programovací kurzy).
- Flexibilní, podporující imperativní, funkční a objektově orientované programovací styly.
- Volný a open source.
- Běží dobře na všech hlavních operačních systémech.  
- Podporováno mnoha bezplatnými, užitečnými a dobře navrženými knihovnami.  
- Podporováno spoustou dokumentace, ukázky a silná komunita vývojářů.  

Chcete-li se dozvědět více o jazyce, začněte s [Pythonem pro začátečníky](https://www.python.org/about/gettingstarted/) na python.org.

Chcete-li nainstalovat [https://www.python.org/download/](https://www.python.org/download/)Python sám, navštivte .

## <a name="python-tools-for-visual-studio"></a>Python Tools for Visual Studio
  
Nástroje Pythonu pro Visual Studio, které můžete nainstalovat ze [visualstudio.com](https://www.visualstudio.com/explore/python-vs), poskytují následující funkce:  
  
- Podpora více interpretů: různé verze CPython, IronPython a IPython  
- Projektový systém, který implicitně vyzvedne strukturu složek kódu Pythonu a také umožňuje explicitní řízení, takže můžete identifikovat kód aplikace, testovací kód, webové stránky, JavaScript, vytvářet skripty a tak dále.  
- Šablony projektů pro konzolu, web, Azure, datové vědy a další typy projektů.    
- Sada Azure SDK pro Python (viz níže)    
- Bohaté funkce pro úpravy a porozumění kódu, včetně vybarvení syntaxe, automatického dokončování ve všech kódech a knihovnách, nápovědy k podpisu, zobrazení tříd, přechodu na definici, hledání všech odkazů, refaktoringu a dalších.    
- Interaktivní (REPL) Okno
- IPython s vizualizacemi dat.
- Podpora ironpythona a rozhraní .NET/WPF.    
- Bohaté ladění bez projektu sady Visual Studio, možnost existujícího spustitelného ladění ve smíšeném režimu, vzdálené ladění systému Windows/Linux/Mac a ladění v interaktivním okně.   
- Nástroje pro profilování.  
- Testovací nástroje.  
  
Následující zdroje vám pomohou začít:

- [Průvodce instalací](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)    
- [Začínáme a hluboký ponor krátká videa](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)  
- Instalace a funkce demo (27 min)](https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Dokumentace](https://github.com/Microsoft/PTVS/wiki)  

Všimněte si, že Visual Studio v současné době neposkytuje prostředky k vytvoření samostatného spustitelného souboru pomocí Pythonu, což v podstatě znamená program s vloženým překladačem Pythonu. Existují však různé prostředky v rámci komunity Pythonu, jak je popsáno na [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython také podporuje vkládání do nativní aplikace, jak je popsáno v [blogu, pomocí CPython je vložitelný zip soubor](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/).
  
## <a name="building-ui-with-python"></a>Vytváření ui s Pythonem  

Hlavní nabídkou pro vytváření ui s Pythonem je [Projekt Qt](https://www.qt.io/qt-for-application-development/), s vazbami pro Python známý jako [PySide (oficiální vazba)](https://wiki.qt.io/PySide) (viz také [PySide ke stažení](https://download.qt.io/official_releases/pyside/.))a [PyQt](https://wiki.python.org/moin/PyQt). V současné době podpora Pythonu v sadě Visual Studio neobsahuje žádné konkrétní nástroje pro vývoj ui.

## <a name="azure-sdk-for-python"></a>Azure SDK pro Python
  
Azure SDK pro Python, který podporuje Windows, Mac a Linux, usnadňuje využití a správu služeb Microsoft Azure. Podrobnosti naleznete v následujících zdrojích: 

- Chcete-li nainstalovat sadu SDK, použijte [index balíčků Pythonu](https://pypi.python.org/pypi/azure) nebo postupujte podle [instalace Pythonu a sady SDK](/azure/developer/python/azure-sdk-install) v dokumentaci k Azure. 
- [Azure SDK pro Python Developer Center](https://azure.microsoft.com/develop/python/) má spoustu nápovědy od instalace do dokumentace s kurzy.  Některé zdůrazňuje následovat:  
- Praktičtí průvodci:
  - [Objekt blob úložiště](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [Fronta úložiště](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Tabulka úložiště](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Fronty služby Service Bus](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Témata/odběry služby Service Bus](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Správa služeb](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>Vědecká výpočetní technika

Kromě všech knihoven datových vědců pythonu podporují nástroje Pythonu pro Visual Studio poznámkové bloky IPython a IPython, které můžou být hostované v Azure.

Doporučujeme získat IPython a vědecké výpočetní knihovny (matplotlib, scipy, numpy, atd.) z [University of California, Irvine](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).  
  
## <a name="see-also"></a>Viz také  

[Začínáme s PTVS: Nastavení Visual Studia](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[Začínáme s PTVS: Začínáme s kódováním (Projekty)](../python/getting-started-with-ptvs-start-coding-projects.md)
[Začínáme s PTVS: Úpravy kódu](../python/getting-started-with-ptvs-editing-code.md)
[Začínáme s PTVS: Ladění Začínáme](../python/getting-started-with-ptvs-debugging.md)
s[PTVS: Interaktivní Python](../python/getting-started-with-ptvs-interactive-python.md)
[Začínáme s PTVS: Vytváření webu v Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
