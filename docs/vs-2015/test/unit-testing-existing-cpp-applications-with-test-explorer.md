---
title: Testování částí stávajících C++ aplikací pomocí Průzkumníka testů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7d08de69-c32e-4f0b-89aa-75347b15fb82
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 34d1918522711f3070cf6988a83ebdbd1e80b2f4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659586"
---
# <a name="unit-testing-existing-c-applications-with-test-explorer"></a>Testování částí stávajících aplikací C++ pomocí Průzkumníka testů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Doporučujeme, abyste před změnou existující aplikace měli jistotu, že má dobrý rozsah s testováním částí. To vám dává jistotu, že vaše změny nevedly k chybám. Pokud aplikace ještě testy jednotek neobsahuje, můžete je přidat pomocí techniků, které jsou znázorněné v tomto tématu. Toto téma popisuje, jak přidat testy jednotek pro existující vizuální C++ kód, počínaje rozhodnutím o testování kódu a následným vytvořením, zápisem a nakonec spuštěním testů.

## <a name="deciding-how-to-test-your-code"></a>Rozhodnutí o testování kódu
 Otevřete existující C++ projekt a zkontrolujte ho a rozhodněte se, jak chcete přidat testy jednotek. Můžete chtít použít některé nástroje pro modelování, které vám pomůžou zobrazit závislosti v kódu, a porozumět tomu, jak části pracují. Další informace naleznete v tématu [vizualizace kódu](../modeling/visualize-code.md).

 Doporučujeme oddělit změny do malých úloh. Před každou malou změnou zapište testy jednotek pro aspekty chování, které zůstane stejné. Tyto testy budou po provedení změny i nadále předávány. Například pokud plánujete změnit funkci řazení tak, aby seřadí seznam osob podle příjmení, nikoli podle křestního jména, můžete napsat test jednotky, který ověří, zda se všechny vstupní názvy zobrazí ve výstupu. Po provedení změny můžete chtít přidat nové testy jednotek pro nové chování.

 Pokud je to praktické, mnoho nebo všechny testy jednotek by měly používat pouze funkce, které jsou exportovány. Pokud ale měníte jenom malou část celé aplikace, možná budete chtít použít funkce, které se neexportují. Například můžete chtít, aby testy volaly vnitřní funkce nebo testy, které nastavily a získaly hodnoty interních proměnných.

 Existuje několik způsobů, jak otestovat kód produktu v závislosti na tom, zda zpřístupňuje rozhraní, která chcete testovat. Vyberte jeden z následujících způsobů:

 **Testy jednotek budou používat pouze funkce, které jsou exportovány z testovaného kódu:** Přidejte samostatný testovací projekt. V testovacím projektu přidejte do testovaného projektu odkaz na testovaný projekt.

 Přejít na postup [pro odkazování na exportované funkce z testovacího projektu](#projectRef).

 **Testovaný kód je sestaven jako soubor. exe:** Přidejte samostatný testovací projekt. Propojte ji s výstupním objektovým souborem.

 Pro [propojení testů s objektem nebo knihovnou souborů](#objectRef)použijte postup.

 **Jednotkové testy musí používat soukromé funkce a data a testovaný kód může být sestaven jako Statická knihovna:** Změňte testovaný projekt tak, aby byl zkompilován do souboru. lib. Přidejte samostatný testovací projekt, který odkazuje na testovaný projekt.

 Tento přístup má výhodu v tom, že umožňuje vašim testům používat soukromé členy, ale stále tyto testy uchovávat v samostatném projektu. Nemusí ale být vhodný pro některé aplikace, kde musíte mít dynamickou knihovnu (. dll).

 Přejděte na postup [pro změnu testovaného kódu na statickou knihovnu](#staticLink).

 **Jednotkové testy musí používat soukromé funkce a data a kód musí být sestaven jako dynamická knihovna (DLL):** Přidejte jednotkové testy do stejného projektu jako kód produktu.

 Pro [Přidání jednotkových testů do stejného projektu](#sameProject)použijte postup.

## <a name="creating-the-tests"></a>Vytváření testů

### <a name="staticLink"></a>Změna testovaného kódu na statickou knihovnu

- Pokud testy musí používat členy, které nejsou exportovány v rámci testu projektu, a projekt v rámci testu je sestaven jako dynamická knihovna, zvažte jeho převod na statickou knihovnu.

  1. V Průzkumník řešení v místní nabídce testovaného projektu vyberte možnost **vlastnosti**. Otevře se okno Vlastnosti projektu.

  2. Vyberte **Vlastnosti konfigurace**, **Obecné**.

  3. Nastavte **typ konfigurace** na **statickou knihovnu (. lib)** .

  Pokračujte postupem [propojení testů s objekty nebo soubory knihovny](#objectRef).

### <a name="projectRef"></a>Odkazování na exportované funkce z testovacího projektu

- Pokud projekt v rámci testu exportuje funkce, které chcete otestovat, můžete přidat odkaz na projekt kódu z testovacího projektu.

  1. Vytvořte C++ testovací projekt.

      1. V nabídce **soubor** klikněte na příkaz **Nový**, **projekt**, **Visual C++, test**,  **C++ test jednotek projektu**.

  2. V Průzkumník řešení v místní nabídce testovacího projektu vyberte možnost **odkazy**. Otevře se okno Vlastnosti projektu.

  3. Vyberte **společné vlastnosti**, **Architektura a odkazy**a pak klikněte na tlačítko **Přidat nový odkaz** .

  4. Vyberte **projekty**a potom projekt, který chcete otestovat.

       Klikněte na tlačítko **Přidat** .

  5. Ve vlastnostech testovacího projektu přidejte do adresáře include umístění testovaného projektu.

       Vyberte **Vlastnosti konfigurace**, **adresáře VC + +** , **adresáře include**.

       Zvolte **Upravit**a pak přidejte adresář záhlaví testovaného projektu.

  Přejít na [Zápis testování částí](#addTests).

### <a name="objectRef"></a>Propojení testů s objekty nebo soubory knihovny

- Pokud testovaný kód neexportuje funkce, které chcete otestovat, můžete přidat výstupní soubor **. obj** nebo **. lib** do závislostí testovacího projektu.

  1. Vytvořte C++ testovací projekt.

      1. V nabídce **soubor** klikněte na příkaz **Nový**, **projekt**, **Visual C++, test**,  **C++ test jednotek projektu**.

  2. V Průzkumník řešení v místní nabídce testovacího projektu vyberte možnost **vlastnosti**. Otevře se okno Vlastnosti projektu.

  3. Vyberte **Vlastnosti konfigurace**, **linker**, **vstup**, **Další závislosti**.

       Vyberte **Upravit**a přidejte názvy souborů **. obj** nebo **. lib** . Nepoužívejte názvy úplných cest.

  4. Vyberte možnost **Vlastnosti konfigurace**, **linker**, **Obecné**, **Další adresáře knihoven**.

       Vyberte **Upravit**a přidejte cestu k adresáři souborů **. obj** nebo **. lib** . Cesta je obvykle ve složce sestavení testovaného projektu.

  5. Vyberte **Vlastnosti konfigurace**, **adresáře VC + +** , **adresáře include**.

       Zvolte **Upravit**a pak přidejte adresář záhlaví testovaného projektu.

  Přejít na [Zápis testování částí](#addTests).

### <a name="sameProject"></a>Přidání jednotkových testů do stejného projektu

1. Upravte vlastnosti projektu kódu produktu tak, aby obsahovaly hlavičky a soubory knihoven, které jsou požadovány pro testování částí.

   1. V Průzkumník řešení v místní nabídce testovaného projektu vyberte možnost Vlastnosti. Otevře se okno Vlastnosti projektu.

   2. Vyberte možnost **Vlastnosti konfigurace**, **adresáře VC + +** .

   3. Upravte adresáře include a knihovny:

       |||
       |-|-|
       |**Zahrnout adresáře**|**$ (VCInstallDir) UnitTest\include; $ (IncludePath)**|
       |**Adresáře knihoven**|**$ (VCInstallDir) UnitTest\lib; $ (LibraryPath)**|

2. Přidat soubor C++ testu jednotek:

   - V Průzkumník řešení v místní nabídce projektu zvolte možnost **Přidat**, **Nová položka**a pak zvolte možnost  **C++ test jednotky**.

   Přejít na [Zápis testování částí](#addTests).

## <a name="addTests"></a>Zápis testů jednotek

1. V každém souboru kódu testu jednotek přidejte příkaz `#include` pro hlavičky testovaného projektu.

2. Přidejte testovací třídy a metody do souborů kódu testování částí. Příklad:

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

   Další informace naleznete v tématu [testování částí nativního kódu pomocí Průzkumníka testů](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c).

## <a name="run-the-tests"></a>Spustit testy

1. V nabídce **zobrazení** vyberte možnost **ostatní okna**, **Průzkumník testů**.

2. V Průzkumníku testů vyberte možnost **Spustit vše**.

   Další informace naleznete v tématu [rychlé zprovoznění: Vývoj řízený testováním pomocí Průzkumníka testů](../test/quick-start-test-driven-development-with-test-explorer.md).
