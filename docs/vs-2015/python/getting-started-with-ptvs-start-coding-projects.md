---
title: 'Začínáme s PTVS: Začínáme kódovat (projekty) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 14b85e70-b9a8-415c-a307-8c8c316a0495
caps.latest.revision: 7
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: a8e0bd339d8e7b6d145cc9a916dafc2be9fc975e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845781"
---
# <a name="getting-started-with-ptvs-start-coding-projects"></a>Začínáme s PTVS: Začínáme kódovat (projekty)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroje Python Tools pro Visual Studio (PTVS) pomáhá spravovat váš kód. 
 
 Můžete sledovat tyto pokyny ve velmi krátké [videa youtube](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2). 
 
 Pokud jste používali před Pythonu, víte, že váš projekt je definován způsob rozložení soubory na disku. Tento postup funguje skvěle pro prostý projektů v Pythonu, ale když máte víc souborů (webové stránky JavaScript, testy částí a skripty sestavení), systémy souborů může začít se trochu omezující. Projekty Visual Studio používá k dosažení tři věci. 
 
- Identifikujte kritické soubory. Důležité soubory jsou ty, které jste vrácení se změnami do systému správy verzí (zdrojové soubory, zdroje atd.), ale ne soubory, které jsou generovány jako výstup sestavení. Důležité soubory jsou také ty, které budou zkopírovány do jiného počítače tak, aby někdo jiný může pracovat ve vaší aplikaci. 
 
- Zadejte, jak se má použít soubory. Můžete mít soubory, které je potřeba zpracovat při každé změně souborů nástroj. Projekty aplikace Visual Studio můžete zaznamenat tyto informace 
 
- Definujte hranice součástí. Pokud máte více komponent ve vaší aplikaci, můžete umístit každý z nich testovacího projektu. Tyto nakonec jde nasadit na různé servery, vytvořené pomocí jiné sestavení nebo nastavení ladění nebo může dokonce zapsány pomocí jiného jazyka, které podporuje Visual Studio, například C++ nebo Node.js 
 
  Existuje několik šablon projektů, které vám pomůžou začít. Pokud již máte kódu v Pythonu, kteří by chtěli pracovat na, z existujícího kódu Průvodce vám pomůže vytvořit projekt, který obsahuje všechny soubory. Více webových projektů existují pro několik oblíbených architektur. Další šablony jsou k dispozici v balíčku ukázek PTVS. Existují možnosti, jak zajistit Zadaná webová šablony pracovat s další architektury. Šablonu aplikace Pythonu je vyčistit, prázdný projekt. Existuje jeden modul, které vám pomůžou začít. 
 
  Sada Visual Studio zobrazí vaše projekty otevřít v okně Průzkumník řešení, včetně všech souborů, cesty pro hledání a prostředí Pythonu. K přidání nových položek, vyberte složku vašeho projektu a zvolte Přidat a pak novou položku v kontextové nabídce (stiskněte tlačítko vpravo ukazatele). Vyberte libovolnou položku v dialogovém okně, přizpůsobit název položky a přidejte položku do projektu. 
 
  Vám může přetažením do Průzkumníka řešení. Pokud jste již zkopírovat soubory do adresářové struktuře projektu, můžete zobrazit všechny soubory v horní části Průzkumníku řešení. Pak můžete vybrat položky, které chcete přidat a v místní nabídce zvolte možnost zahrnout v projektu. 
 
  Můžete sledovat tyto pokyny ve velmi krátké [videa youtube](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2). 
 
## <a name="see-also"></a>Viz také 
 [Dokumentace ke službě Wiki](https://github.com/Microsoft/PTVS/wiki/Projects) [PTVS Začínáme a Deep Dive videa](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

