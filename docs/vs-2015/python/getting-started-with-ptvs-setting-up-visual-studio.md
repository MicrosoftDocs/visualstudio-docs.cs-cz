---
title: 'Začínáme s PTVS: nastavení sady Visual Studio 2015 | Dokumentace Microsoftu'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec491c1d-bdb2-4c2b-a390-bd808cec635a
caps.latest.revision: 6
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: c48687f0c3c151b45fed4f6dc53a428faca41cd9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052916"
---
# <a name="getting-started-with-ptvs-setting-up-visual-studio"></a>Začínáme s PTVS: Nastavení Visual Studia

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Instalace PTVS a související knihovny je rychlá, pokud máte sadu Visual Studio. Pokud nemáte Visual Studio, můžete získat bezplatnou kopii verze profesionální kvality.

Můžete sledovat tyto pokyny ve velmi krátké [videa youtube](https://www.youtube.com/watch?v=_okUV47eM5c&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=1).

Obecný postup je následující: instalace sady Visual Studio, nainstalujte PTVS, nainstalujte Python a data knihovny (Anaconda, zápoje) a potom nakonec Zkontrolujte instalaci.

První věc, kterou budete potřebovat je sada Visual Studio. Pokud jste vývojář open source nebo jednotlivci, můžete použít Visual Studio [Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs), který je zdarma a funkční pro odborníky v oblasti. Za předpokladu, je pro classroom učení, vědecký výzkum nebo přispívání do open source projektů, můžete použít také edice Community v organizaci. Pro studenty a startupy by měl vypadat do DreamSpark a programů BizSpark zobrazíte, pokud nárok zdarma přístup nebo požádejte vašeho zaměstnavatele, jestli máte předplatné MSDN.

Po instalaci sady Visual Studio, budete muset [nainstalovat PTVS](http://pytools.codeplex.com/wikipage?title=PTVS%20Installation). Toto je zdarma, samostatného rozšíření, která má plně podporovaný společností Microsoft a zveřejněno byly vyvinuty v sadě příspěvky od komunity.

Teď je potřeba [nainstalujte Python](https://www.python.org/download/). Python je spravován v komunitě a jeho domovské stránky je python.org. Continuum Analytics vytvoří bezplatné sady volá Anaconda Python a mnoho užitečných knihoven (hlavně u vědy a zpracování dat) a Enthought vytváří podobně jako sada prostředků s názvem zápoje. Stačí nainstalovat některou z těchto produktů. Pokud si nejste jisti, která z nich, začněte tématem [Anaconda](https://www.continuum.io/downloads), která poskytuje nejaktuálnější Python a většina obtížné instalační balíčky.

Spusťte sadu Visual Studio a ujistěte se, že všechno funguje. V nabídce zobrazení vyberte další Windows. Uvidíte položku s názvem prostředí Pythonu. Toto okno zobrazuje všechny instalace Pythonu, PTVS zjistilo a všechny balíčky, které jste nainstalovali. V okně také řídí obnovení databáze k zobrazení dokončování při úpravě kódu. Tento proces aktualizace nějakou dobu trvá, ale po dokončení PTVS můžete zobrazit další užitečné informace o balíčcích.

Pokud chcete používat s nástroji PTVS IPython, postupujte podle těchto [pokyny](http://pytools.codeplex.com/wikipage?title=Using%20IPython%20with%20PTVS).

Můžete sledovat tyto pokyny v krátké [videa youtube](https://www.youtube.com/watch?v=_okUV47eM5c&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=1).

## <a name="see-also"></a>Viz také

[Videa můžete začít a Deep Dive PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
