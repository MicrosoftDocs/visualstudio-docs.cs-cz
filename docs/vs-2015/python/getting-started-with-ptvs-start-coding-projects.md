---
title: 'Začínáme s PTVS: začátek kódování (projekty) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 14b85e70-b9a8-415c-a307-8c8c316a0495
caps.latest.revision: 7
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 28622f290d82f86bf3d18cc4f40cfcfc8e953dad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537140"
---
# <a name="getting-started-with-ptvs-start-coding-projects"></a>Začínáme s PTVS: Začínáme kódovat (projekty)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Python Tools for Visual Studio (PTVS) vám pomůže se správou kódu. 
 
 Tyto pokyny můžete sledovat ve velmi krátkém [videu YouTube](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2). 
 
 Pokud jste předtím používali Python, víte, že je projekt definován pomocí způsobu rozložení souborů na disk. To funguje skvěle pro jednoduché projekty v Pythonu, ale pokud máte více souborů (webové stránky s JavaScriptem, jednotkové testy a skripty sestavení), můžou systémy souborů začínat omezením bitu. Visual Studio používá projekty k dosažení tří věcí. 
 
- Identifikujte důležité soubory. Důležité soubory jsou ty, které zaškrtnete v systému správy verzí (zdrojové soubory, prostředky atd.), ale ne soubory, které jsou generovány jako výstup sestavení. Důležité soubory jsou také ty, které byste zkopírovali do jiného počítače, aby mohli v aplikaci pracovat někdo jiný. 
 
- Určete, jak se mají soubory používat. Je možné, že máte soubory, které nástroj potřebuje ke zpracování při každé změně souborů. Projekty sady Visual Studio mohou zachytit tyto informace 
 
- Definujte hranice svých komponent. Pokud máte v aplikaci více komponent, můžete každý z nich umístit do samostatného projektu. Ty mohou být nakonec nasazeny na různé servery, sestavené s různými nastaveními sestavení nebo ladění, nebo mohou být dokonce vytvořeny pomocí jiného jazyka podporovaného sadou Visual Studio, jako je například C++ nebo Node.js 
 
  K dispozici je několik šablon projektů, které vám pomůžou začít. Pokud již máte kód Pythonu, na kterém byste chtěli pracovat, průvodce z existujícího kódu vám pomůže vytvořit projekt, který obsahuje všechny vaše soubory. Pro některá oblíbená rozhraní existuje více webových projektů. Další šablony jsou k dispozici v sadě PTVS Samples Pack. K dispozici jsou možnosti, jak zajistit, aby poskytované webové šablony fungovaly s ostatními rozhraními. Šablona aplikace Python je čistý prázdný projekt. Je k dispozici jeden modul, který vám umožní začít. 
 
  Visual Studio zobrazí otevřené projekty v okně Průzkumník řešení, včetně všech souborů, vyhledávacích cest a prostředí Pythonu. Chcete-li přidat nové položky, vyberte složku projektu a z kontextové nabídky (stiskněte pravé tlačítko ukazatele myši), zvolte možnost Přidat a poté nová položka. Můžete vybrat libovolnou položku v dialogovém okně, přizpůsobit název položky a přidat položku do projektu. 
 
  Můžete přetáhnout do Průzkumník řešení. Pokud jste již zkopírovali soubory do adresářové struktury projektu, můžete zvolit možnost Zobrazit všechny soubory v horní části Průzkumník řešení. Pak můžete vybrat položky, které chcete přidat, a z kontextové nabídky zvolit zahrnout do projektu. 
 
  Tyto pokyny můžete sledovat ve velmi krátkém [videu YouTube](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2). 
 
## <a name="see-also"></a>Viz také 
 [Dokumentace wiki](https://github.com/Microsoft/PTVS/wiki/Projects) [PTVS Začínáme a rozsáhlá podrobně videa](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
