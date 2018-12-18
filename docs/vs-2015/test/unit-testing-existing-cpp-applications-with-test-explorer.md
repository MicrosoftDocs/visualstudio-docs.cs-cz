---
title: Testování částí stávajících aplikací C++ pomocí Průzkumníka testů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7d08de69-c32e-4f0b-89aa-75347b15fb82
caps.latest.revision: 13
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8dab39c5718b8872df5e81281ba9dda886ebf313
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941201"
---
# <a name="unit-testing-existing-c-applications-with-test-explorer"></a>Testování částí stávajících aplikací C++ pomocí Průzkumníka testů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Doporučujeme, před změnou existující aplikace, zkontrolujte, že na něm dobrým pokrytá jednotkovými testy. To vám dává jistotu, že vaše změny nebyly zavedeny chyby. Pokud aplikace neobsahuje jednotkové testy, můžete je přidat pomocí technik naznačených v tomto tématu. Toto téma popisuje, jak přidat jednotkové testy pro existující kód jazyka Visual C++, počínaje rozhodnutí o způsobu testování kódu a vytváření a psaní a nakonec, spouštění testů.  
  
## <a name="deciding-how-to-test-your-code"></a>Rozhodnutí o způsobu testování kódu  
 Otevřete existující projekt C++ a rozhodněte, jak chcete jednotkové testy přidat. Můžete chtít použít některé modelovací nástroje, které nápovědu najdete v kapitole závislosti v kódu a pomáhají pochopit interakci jednotlivých částí. Další informace najdete v tématu [vizualizovat kód](../modeling/visualize-code.md).  
  
 Doporučujeme rozdělit změny na malé úlohy. Před každou malou změnou, vytvořte jednotkové testy pro aspekty chování, které zůstanou stejné. Tyto testy budou proběhnout úspěšně i po provedení změny. Například pokud budete chtít změnit funkci třídění tak, aby setřídila seznam osob podle příjmení namísto podle křestního jména, můžete napsat Jednotkový test ověřující, že všechna vstupní jména zobrazí ve výstupu. Po provedení změny, můžete chtít přidat nové jednotkové testy pro nové chování.  
  
 Pokud je to praktické, většinu nebo všechny testy jednotky používejte pouze funkce, které jsou exportovány. Ale pokud měníte pouze malou část celé aplikace, pak může být vhodné použít Neexportované. Můžete například testy, které volávají vnitřní funkce nebo testy, které nastavují a získávají hodnoty vnitřních proměnných.  
  
 Existuje několik způsobů jak otestovat produkční kód podle toho, zda poskytuje rozhraní, které chcete testovat. Vyberte jednu z následujících způsobů:  
  
 **Jednotkové testy budou používat pouze funkce, které byly exportovány z testovaného kódu:**  
 Přidejte samostatný testovací projekt. V testovacím projektu přidejte odkaz na testovaný projekt.  
  
 Pokračujte podle postupu [odkazovat exportované funkce z testovacího projektu](#projectRef).  
  
 **Testovaný kód je vytvořen jako soubor s příponou .exe:**  
 Přidejte samostatný testovací projekt. Propojte jej k výstupnímu objektovému souboru.  
  
 Pokračujte podle postupu [připojení testů k souborům objektů nebo knihoven](#objectRef).  
  
 **Jednotkové testy musí používat soukromé funkce a data a testovaný kód může být sestaven jako statická knihovna:**  
 Změňte Testovaný projekt tak, aby byl kompilován do souboru LIB. Přidejte samostatný testovací projekt, který odkazuje na projekt v rámci testu.  
  
 Tento přístup má výhodu umožňuje používat soukromé členy, ale zachováním samostatnosti testovacího projektu testů. Však nemusí být vhodný pro některé aplikace, které musí obsahovat dynamickou knihovnu (DLL).  
  
 Pokračujte podle postupu [změna testovaného kódu na statickou knihovnu](#staticLink).  
  
 **Jednotkové testy musí používat soukromé funkce a data a kód musí být sestaven jako dynamická knihovna (DLL):**  
 Přidáte testy jednotek ve stejném projektu s testovaným kódem.  
  
 Pokračujte podle postupu [přidání jednotkových testů do stejného projektu](#sameProject).  
  
## <a name="creating-the-tests"></a>Vytváření testů  
  
###  <a name="staticLink"></a> Změna testovaného kódu na statickou knihovnu  
  
- Pokud musí testy používat členy Neexportované testovaného projektu a testovaný projekt je sestaven jako dynamická knihovna, zvažte jeho převod na statickou knihovnu.  
  
  1.  V Průzkumníku řešení zvolte v místní nabídce testovaného projektu **vlastnosti**. Otevře se okno s vlastnostmi projektu.  
  
  2.  Zvolte **vlastnosti konfigurace**, **Obecné**.  
  
  3.  Nastavte **typ konfigurace** k **statická knihovna (.lib)**.  
  
  Pokračujte postupem [připojení testů k souborům objektů nebo knihoven](#objectRef).  
  
###  <a name="projectRef"></a> Odkazování na exportované funkce z testovacího projektu  
  
- Pokud Testovaný projekt exportuje funkce, které chcete testovat, můžete přidat odkaz na projekt kódu z testovacího projektu.  
  
  1.  Vytvoření testovacího projektu C++.  
  
      1.  Na **souboru** nabídce zvolte **nový**, **projektu**, **Visual C++, testovací**, **projekt testu jednotek C++**.  
  
  2.  V Průzkumníku řešení zvolte v místní nabídce testovaného projektu **odkazy**. Otevře se okno s vlastnostmi projektu.  
  
  3.  Vyberte **společné vlastnosti**, **rámec a odkazy**a klikněte na tlačítko **přidat nový odkaz** tlačítko.  
  
  4.  Vyberte **projekty**a pak Testovaný projekt.  
  
       Zvolte **přidat** tlačítko.  
  
  5.  Ve vlastnostech testovacího projektu přidejte umístění testovaného projektu do adresáře Include.  
  
       Zvolte **vlastnosti konfigurace**, **adresáře VC ++**, **adresáře souborů k zahrnutí**.  
  
       Zvolte **upravit**a poté přidejte hlavní adresář testovaného projektu.  
  
  Přejděte na [psaní jednotkových testů](#addTests).  
  
###  <a name="objectRef"></a> Připojení testů k souborům objektů nebo knihoven  
  
- Pokud testovaný kód neexportuje funkce, které chcete testovat, můžete přidat výstup **.obj** nebo **lib** souboru do závislostí testovacího projektu.  
  
  1.  Vytvoření testovacího projektu C++.  
  
      1.  Na **souboru** nabídce zvolte **nový**, **projektu**, **Visual C++, testovací**, **projekt testu jednotek C++**.  
  
  2.  V Průzkumníku řešení zvolte v místní nabídce testovaného projektu **vlastnosti**. Otevře se okno s vlastnostmi projektu.  
  
  3.  Zvolte **vlastnosti konfigurace**, **Linkeru**, **vstup**, **Další závislosti**.  
  
       Zvolte **upravit**a přidejte názvy **.obj** nebo **lib** soubory. Nepoužívejte úplné cesty k souborům.  
  
  4.  Zvolte **vlastnosti konfigurace**, **Linkeru**, **Obecné**, **další adresáře knihoven**.  
  
       Zvolte **upravit**a přidejte cestu k adresáři **.obj** nebo **lib** soubory. Cesta je obvykle ve složce sestavení testovaného projektu.  
  
  5.  Zvolte **vlastnosti konfigurace**, **adresáře VC ++**, **adresáře souborů k zahrnutí**.  
  
       Zvolte **upravit**a poté přidejte hlavní adresář testovaného projektu.  
  
  Přejděte na [psaní jednotkových testů](#addTests).  
  
###  <a name="sameProject"></a> Přidání jednotkových testů do stejného projektu  
  
1. Úprava vlastností projektu kódu produktu k zahrnovaly hlavičkové soubory a soubory knihoven, které jsou požadovány pro testování částí.  
  
   1.  V Průzkumníku řešení v místní nabídce testovaného projektu zvolte Vlastnosti. Otevře se okno s vlastnostmi projektu.  
  
   2.  Zvolte **vlastnosti konfigurace**, **adresáře VC ++**.  
  
   3.  Upravte adresáře Include a Library:  
  
       |||  
       |-|-|  
       |**Adresáře souborů k zahrnutí**|**$(VCInstallDir)UnitTest\include;$(IncludePath)**|  
       |**Adresáře knihoven**|**$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|  
  
2. Přidáte soubor testu jednotek C++:  
  
   -   V Průzkumníku řešení v místní nabídce projektu zvolte **přidat**, **nová položka**a klikněte na tlačítko **Jednotkový Test C++**.  
  
   Přejděte na [psaní jednotkových testů](#addTests).  
  
##  <a name="addTests"></a> Zápis testů jednotek  
  
1. Do každého souboru kódu jednotkového testu přidejte `#include` příkaz pro záhlaví testovaného projektu.  
  
2. Přidejte testovací třídy a metody do souborů s kódy testu jednotek. Příklad:  
  
   ```cpp  
   #include "stdafx.h"  
   #include "CppUnitTest.h"  
   #include "MyProjectUnderTest.h"  
   using namespace Microsoft::VisualStudio::CppUnitTestFramework;  
   namespace MyTest  
   {  
     TEST_CLASS(MyTests)  
     {  
     public:  
         TEST_METHOD(MyTestMethod)  
         {  
             Assert::AreEqual(MyProject::Multiply(2,3), 6);  
         }  
     };  
   }  
   ```  
  
   Další informace najdete v tématu [testování částí nativního kódu pomocí Průzkumníka testů](http://msdn.microsoft.com/en-us/8a09d6d8-3613-49d8-9ffe-11375ac4736c).  
  
## <a name="run-the-tests"></a>Spustit testy  
  
1. Na **zobrazení** nabídce zvolte **ostatní Windows**, **Průzkumník testů**.  
  
2. V Průzkumníku testů, zvolte **spustit všechny**.  
  
   Další informace najdete v tématu [rychlý Start: vývoj řízených testů pomocí Průzkumníka testů](../test/quick-start-test-driven-development-with-test-explorer.md).



