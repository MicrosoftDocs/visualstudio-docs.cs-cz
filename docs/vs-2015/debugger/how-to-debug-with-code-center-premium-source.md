---
title: 'Postupy: ladění se zdrojem webu Code Center Premium | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Code Center Premium
- debugging [Visual Studio], Code Center Premium
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 090326e2bc86aee9acc6e9cee92bc518f64ad63d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800182"
---
# <a name="how-to-debug-with-code-center-premium-source"></a>Postupy: Ladění se zdrojem webu Code Center Premium
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] ladicího programu, můžete ladit zabezpečené sdílené zdroje od společnosti Microsoft MSDN Code Center Premium.  
  
 Toto téma vysvětluje, jak nastavit a ladění Code Center Premium zdrojového kódu v sadě Visual Studio.  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>Příprava ladění s Code Center Premium  
  
1. Připojte čtečky čipových karet a vložte kartu, kterou jste získali z Shared Source Initiative.  
  
2. Spusťte sadu Visual Studio.  
  
3. Na **nástroje** nabídky, klikněte na tlačítko **možnosti**.  
  
4. V **možnosti** dialogovém okně Otevřít **ladění** uzel a klikněte na tlačítko **Obecné**.  
  
5. Zrušte **povolit volbu pouze vlastní kód (pouze spravované)** zaškrtávací políčko.  
  
6. Vyberte **povolit podporu zdrojového serveru**.  
  
7. Vymazat **vyžadovat, aby zdrojové soubory shodovaly původní verze**.  
  
8. V části **ladění** uzel, klikněte na tlačítko **symboly**.  
  
9. V **soubor symbolů (PDB) umístění** políčka, zrušte **serveru symbolů Microsoft** zaškrtněte políčko a přidáním následujících umístění:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   >  Nezapomeňte zahrnout do adresy koncové lomítko<strong>/</strong> na konci cesty.  
  
     Přesuňte tato místa k hornímu okraji seznam a ověřit, že tyto symboly jsou načten jako první.  
  
   > [!NOTE]
   >  Tato umístění Code Center Premium musí být uvedena nejprve tak, aby byly první umístění, které jsou načteny. V sadě Visual Studio 2010, nelze přesunout všechny výše uvedené servery **Microsoft Symbol Servers** položku, která je důvod, proč je nutné zrušit zaškrtnutí políčka.  
   > 
   >  Chcete-li načíst symboly z symbolů Microsoft během relace ladění, postupujte takto:  
   > 
   > 1. Na **ladění** nabídce zvolte **Windows** a klikněte na tlačítko **moduly**.  
   >    2.  Vyberte modul, který chcete symboly pro a pak otevřete místní nabídku. Zvolte **načíst symboly z** a klikněte na tlačítko **Microsoft Symbol Servers**.  
  
10. V **mezipaměti symbolů ze serverů symbolů v tomto adresáři** zadejte umístění, jako `C:\symbols` kde Code Center Premium můžete ukládat do mezipaměti symbolů. Ukládání do mezipaměti symbolů může výrazně zlepšit výkon během ladění.  
  
     Pokud máte potíže při ladění zdrojový kód pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] po dokončení tohoto postupu zkontrolujte vaše umístění mezipaměti symbolů dříve uložený v mezipaměti a zastaralých souborů. Odeberte zastaralé symbol soubory.  
  
11. Klikněte na tlačítko **OK**.  
  
12. Restartujte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zajistit, že jsou zachované v nastavení.  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>Chcete-li ladit váš zdrojový kód pomocí připojit k procesu  
  
1.  Připojte čtečky čipových karet a vložte kartu, kterou jste získali z Shared Source Initiative.  
  
2.  Spusťte sadu Visual Studio.  
  
3.  Otevřete projekt sady Visual Studio.  
  
4.  Na **nástroje** nabídky, klikněte na tlačítko **připojit k procesu**.  
  
5.  V **připojit k procesu** dialogové okno, klikněte na tlačítko **vyberte**.  
  
6.  V **vybrat typ kódu** dialogovém okně **rozpoznat tyto typy kódu**vyberte **nativní**, **spravované**, a **Managed () V4.0)**.  
  
7.  Klikněte na tlačítko **OK** zrušíte **vybrat typ kódu** dialogové okno.  
  
8.  V **procesy k dispozici** vyberte proces, který chcete ladit.  
  
9. Klikněte na tlačítko **připojit**.  
  
10. Po zobrazení výzvy k potvrzení vašeho certifikátu, klikněte na tlačítko **OK**. Zadejte svůj PIN kód. Přijměte podmínky použití pro Code Center Premium, pokud se zobrazí výzva.  
  
     Stahování symbolů může trvat poměrně dlouho, v závislosti na rychlosti sítě. Stavový řádek bude o tom, kdy byly úspěšně staženy všechny symboly.  
  
11. Opakujte kroky připojení pro všechny spravované projekty v řešení.  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>Chcete-li ladit zdrojový kód z existujícího řešení  
  
1. V **Průzkumníka řešení**, otevřete místní nabídku řešení a klikněte na tlačítko **vlastnosti**.  
  
2. V dialogovém okně stránky vlastností řešení vyberte **zdrojové soubory ladění** v **společné vlastnosti** uzlu.  
  
3. Přidat do následujícího umístění **adresáře, který obsahuje zdrojové soubory** seznamu:  
  
    `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   >  Nezapomeňte zahrnout do adresy koncové lomítko<strong>/</strong> na konci cesty.  
  
4. Pro každý spravovaný projekt ve vašem řešení proveďte následující  
  
   1.  V Průzkumníku řešení otevřete místní nabídku pro projekt a klikněte na tlačítko **vlastnosti**.  
  
   2.  Vyberte **ladění** a klikněte na tlačítko **povolit ladění kódu unmanged**.  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>Chcete-li ladit vaše řešení se zdrojem webu Code Center Premium  
  
1.  Ve vaší `Package` třídy, nastavte zarážku v konstruktoru balíčku.  
  
2.  V `Debug` nabídky, klikněte na tlačítko **spustit ladění**.  
  
3.  Až se dostanete k zarážce v konstruktoru balíčku, přejděte **zásobník volání** okno a klikněte pravým tlačítkem na rámec zásobníku sestavení, který chcete načíst symboly z, pak klikněte na tlačítko **načíst symboly**.  
  
     Klikněte dvakrát na rámec volání se načíst zdroj.  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>K procházení zdrojového kódu na Code Center Premium  
  
1.  Připojte čtečky čipových karet a vložte kartu, kterou jste získali z Shared Source Initiative.  
  
2.  Spuštění aplikace Internet Explorer zadejte následující adresu URL: `https://codepremium.msdn.microsoft.com`  
  
3.  Procházením vyhledejte požadovaný zdroj.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení ladicího programu a příprava](../debugger/debugger-settings-and-preparation.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Code Center Premium](http://www.microsoft.com/resources/sharedsource/ccp.mspx)



