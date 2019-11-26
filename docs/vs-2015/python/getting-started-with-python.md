---
title: Začínáme pomocí Pythonu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 21e724e585f2a5bf0e1fe2a6b70f89c1bd5f5eec
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298189"
---
# <a name="getting-started-with-python"></a>Začínáme s Pythonem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Python Tools for Visual Studio (PTVS) je bezplatný [Open Source](https://github.com/Microsoft/ptvs) modul plug-in pro Visual Studio, který představuje výkonné prostředí pro vývoj v Pythonu.  
  
## <a name="python-the-language"></a>Jazyk Pythonu
  
Python je oblíbený programovací jazyk, který používá spousta vysokých škol, vědců, skriptovacích skriptů, příležitostného vývojáře a profesionálních vývojářů, kteří pracují s aplikacemi, weby a Cloud Services.

V programovacím jazyce je Python:
  
- Spolehlivosti.
- Obecně užitečné pro skriptování rychlých programů, skriptování aplikací, desktopových aplikací, webových serverů, webových služeb a vědeckých výpočtů.
- Snadno se naučíte a má dobrý návrh na podporu správného kódování (spousta vysokých škol ho využívají pro úvodní programovací kurzy).
- Flexibilní a podporující imperativní, funkční a objektově orientované programovací styly.
- Bezplatný a open source.
- Funguje i na všech hlavních operačních systémech.  
- Podporováno spoustou volných, užitečných a dobře navržených knihoven.  
- Podporuje spoustu dokumentace, ukázek a výkonné komunity vývojářů.  

Pokud chcete získat další informace o jazyce, začněte v [Pythonu pro začátečníky](https://www.python.org/about/gettingstarted/) na Python.org.

Pokud chcete nainstalovat samotný Python, navštivte [https://www.python.org/download/](https://www.python.org/download/).

## <a name="python-tools-for-visual-studio"></a>Python Tools for Visual Studio
  
Python Tools for Visual Studio, které můžete nainstalovat z [VisualStudio.com](https://www.visualstudio.com/explore/python-vs), poskytují následující funkce:  
  
- Podpora pro více překladačů: různé verze CPython, Ironpythonu a IPython  
- Systém projektu, který implicitně vybere strukturu složek kódu Pythonu a umožňuje také explicitní řízení, abyste mohli identifikovat kód aplikace, testovací kód, webové stránky, JavaScript, skripty sestavení atd.  
- Šablony projektů pro konzolu, web, Azure, datové vědy a další typy projektů.    
- Sada Azure SDK for Python (viz níže)    
- Bohatě upravené funkce pro úpravy a porozumění kódu, včetně barevného zvýraznění syntaxe, automatického dokončování všech vašich kódů a knihoven, nápovědě k podpisu, zobrazení tříd, přechodu na definici, hledání všech odkazů, refaktoringu a dalších.    
- Interaktivní okno (REPL)
- IPython pomocí vizualizací dat.
- Podpora pro Ironpythonu a .NET/WPF.    
- Bohatá ladit bez projektu sady Visual Studio, schopnost existující spustitelný soubor, ladění ve smíšeném režimu, vzdálené ladění na Windows/Linux/Mac a ladění v interaktivním okně.   
- Nástroje pro profilaci.  
- Testovací nástroje.  
  
Následující materiály vám pomůžou začít:

- [Průvodce instalací](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)    
- [Začínáme a rozsáhlá podrobně krátká videa](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)  
- Ukázka instalace a funkcí (27 min)] (https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Dokumentace](https://github.com/Microsoft/PTVS/wiki)  

Všimněte si, že Visual Studio v současné době neposkytuje způsob vytvoření samostatného spustitelného souboru pomocí Pythonu, což v podstatě znamená program s vloženým překladačem Pythonu. V komunitě Pythonu ale existují různé způsoby, jak je popsáno v [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython podporuje také vkládání do nativní aplikace, jak je popsáno v blogovém příspěvku [pomocí souboru ZIP](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/)s možnou vloženou do CPython.
  
## <a name="building-ui-with-python"></a>Sestavování uživatelského rozhraní pomocí Pythonu  

Hlavní nabídka pro vytváření uživatelského rozhraní s Pythonem je [projekt QT](https://www.qt.io/qt-for-application-development/)s vazbami pro Python označované jako [PySide (oficiální vazba)](https://wiki.qt.io/PySide) (viz také [soubory PySide ke stažení](https://download.qt.io/official_releases/pyside/.)) a [PyQt](https://wiki.python.org/moin/PyQt). V současné době podpora Pythonu v sadě Visual Studio neobsahuje žádné konkrétní nástroje pro vývoj uživatelského rozhraní.

## <a name="azure-sdk-for-python"></a>Azure SDK pro Python
  
Sada Azure SDK pro Python, která podporuje Windows, Mac a Linux, usnadňuje využívání a správu Microsoft Azure služeb. Podrobnosti najdete v následujících zdrojích informací: 

- Chcete-li nainstalovat sadu SDK, použijte [index balíčku Python](https://pypi.python.org/pypi/azure) nebo proveďte [instalaci PYTHONU a sadu SDK](https://docs.microsoft.com/azure/python/python-sdk-azure-install) v dokumentaci k Azure. 
- [Sada Azure SDK for Python Developer Center](https://azure.microsoft.com/develop/python/) obsahuje spoustu lepších ustanovení o instalaci v dokumentaci s kurzy.  Některé nejdůležitější kroky:  
- Praktičtí průvodci:
  - [Objekt BLOB úložiště](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [Fronta úložiště](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Tabulka úložiště](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Fronty Service Bus](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Service Bus témata/předplatná](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Správa služeb](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>Vědecký výpočetní výkon

Kromě všech knihoven dat Pythonu pro odborníky na data, Python Tools for Visual Studio podporují poznámkové bloky IPython a IPython, které můžou být hostované v Azure.

Doporučujeme, abyste získali IPython a vědecké výpočetní knihovny (matplotlib, scipy, numpy atd.) z [University of California, Irvine](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).  
  
## <a name="see-also"></a>Viz také  

[Začínáme s PTVS: nastavení sady Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[Začínáme s PTVS: začátek kódování (projekty)](../python/getting-started-with-ptvs-start-coding-projects.md)
[Začínáme s PTVS: Úprava kódu](../python/getting-started-with-ptvs-editing-code.md)
[Začínáme pomocí PTVS: ladění](../python/getting-started-with-ptvs-debugging.md)
[Začínáme pomocí PTVS: interaktivní Python](../python/getting-started-with-ptvs-interactive-python.md)
[Začínáme with PTVS: vytvoření webu v Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
