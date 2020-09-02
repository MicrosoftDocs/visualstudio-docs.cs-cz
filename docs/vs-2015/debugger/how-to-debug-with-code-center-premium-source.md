---
title: 'Postupy: ladění ve zdroji služby Code Center Premium | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: db9a3e08e14e7fadca6df9e32361c0b042f565e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64783466"
---
# <a name="how-to-debug-with-code-center-premium-source"></a>Postupy: Ladění se zdrojem webu Code Center Premium
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] ladicího programu můžete ladit zabezpečený sdílený zdroj z webu Microsoft MSDN Code Center Premium.  
  
 Toto téma vysvětluje, jak nastavit a ladit zdrojový kód centra Code úrovně Premium v sadě Visual Studio.  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>Příprava na ladění pomocí centra Code úrovně Premium  
  
1. Připojte čtečku čipových karet a vložte kartu, kterou jste získali z iniciativy Shared Source.  
  
2. Spusťte Visual Studio.  
  
3. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).  
  
4. V dialogovém okně **Možnosti** otevřete uzel **ladění** a klikněte na **Obecné**.  
  
5. Zrušte zaškrtnutí políčka **povolit pouze můj kód (pouze spravované)** .  
  
6. Vyberte možnost **Povolit podporu zdrojového serveru**.  
  
7. Clear **vyžaduje, aby se zdrojové soubory přesně shodovaly s původní verzí**.  
  
8. V uzlu **ladění** klikněte na **symboly**.  
  
9. V poli **umístění souborů symbolů (. pdb)** zrušte zaškrtnutí políčka **symboly serveru společnosti Microsoft** a přidejte následující umístění:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   > Nezapomeňte na konec cesty zahrnout koncové lomítko <strong>/</strong> .  
  
     Přesuňte tato umístění do horní části seznamu, aby se zajistilo, že se tyto symboly načtou jako první.  
  
   > [!NOTE]
   > Tato umístění centra Code úrovně Premium musí být uvedená jako první, aby se načetla první umístění. V aplikaci Visual Studio 2010 nelze přesunout žádné servery nad položku **Microsoft Symbol Servers** , což je důvod, proč je nutné zrušit zaškrtnutí políčka.  
   > 
   >  Chcete-li načíst symboly z symbolů společnosti Microsoft během relace ladění, postupujte takto:  
   > 
   > 1. V nabídce **ladit** zvolte **okna** a pak zvolte **moduly**.  
   >    2.  Vyberte modul, pro který chcete symboly pro, a pak otevřete místní nabídku. Zvolte **načíst symboly z** a pak zvolte **Microsoft Symbol Servers**.  
  
10. V poli **symboly mezipaměti ze serverů symbolů v tomto adresáři** zadejte umístění, jako například `C:\symbols` , kde může kód Premium centra Code ukládat symboly do mezipaměti. Ukládání symbolů do mezipaměti může významně zlepšit výkon během ladění.  
  
     Pokud máte potíže s laděním zdrojového kódu pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] po dokončení tohoto postupu, Prohlédněte si umístění mezipaměti dříve uložených v mezipaměti a zastaralých souborů symbolů. Odeberte zastaralé soubory symbolů.  
  
11. Klikněte na **OK**.  
  
12. Restartujte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , abyste zajistili, že nastavení budou trvalá.  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>Ladění zdrojového kódu pomocí příkazu připojit k procesu  
  
1. Připojte čtečku čipových karet a vložte kartu, kterou jste získali z iniciativy Shared Source.  
  
2. Spusťte Visual Studio.  
  
3. Otevřete projekt sady Visual Studio.  
  
4. V nabídce **nástroje** klikněte na tlačítko **připojit k procesu**.  
  
5. V dialogovém okně **připojit k procesu** klikněte na **Vybrat**.  
  
6. V dialogovém okně **Vybrat typ kódu** v části **detekovat tyto typy kódu**vyberte **nativní**, **spravované**a **spravované (v 4.0)**.  
  
7. Kliknutím na tlačítko **OK** zavřete dialogové okno **Vybrat typ kódu** .  
  
8. V poli **Dostupné procesy** vyberte proces, který chcete ladit.  
  
9. Klikněte na **připojit**.  
  
10. Po zobrazení výzvy k potvrzení certifikátu klikněte na tlačítko **OK**. Pak zadejte svůj PIN kód. Pokud se zobrazí výzva, přijměte podmínky použití pro středisko Code úrovně Premium.  
  
     Stahování symbolů může trvat spoustu času v závislosti na rychlosti sítě. Stavový řádek bude označovat, že všechny symboly byly úspěšně staženy.  
  
11. Opakujte kroky připojení pro všechny spravované projekty ve vašem řešení.  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>Ladění zdrojového kódu z existujícího řešení  
  
1. V **Průzkumník řešení**otevřete místní nabídku řešení a pak zvolte možnost **vlastnosti**.  
  
2. V dialogovém okně stránky vlastností řešení vyberte možnost **Ladit zdrojové soubory** v uzlu **společné vlastnosti** .  
  
3. Přidejte následující umístění do seznamu **adresáře obsahující zdrojové soubory** :  
  
    `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   > Nezapomeňte na konec cesty zahrnout koncové lomítko <strong>/</strong> .  
  
4. Pro každý spravovaný projekt ve vašem řešení udělejte toto:  
  
   1. V Průzkumník řešení otevřete místní nabídku pro projekt a poté zvolte možnost **vlastnosti**.  
  
   2. Vyberte **ladit** a pak zvolte **Povolit ladění kódu unmanged**.  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>Ladění řešení pomocí zdroje kódu na úrovni Premium  
  
1. V `Package` třídě nastavte zarážku na konstruktoru balíčku.  
  
2. V `Debug` nabídce klikněte na **Spustit ladění**.  
  
3. Když zaškrtnete zarážku v konstruktoru balíčku, přejděte do okna **zásobník volání** a klikněte pravým tlačítkem myši na rámec zásobníku sestavení, ze kterého chcete načíst symboly, a poté klikněte na možnost **načíst symboly**.  
  
     Dvojím kliknutím na rámec volání načtěte zdroj.  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>Procházení zdrojového kódu na centra kódu Premium  
  
1. Připojte čtečku čipových karet a vložte kartu, kterou jste získali z iniciativy Shared Source.  
  
2. Spusťte Internet Explorer a zadejte následující adresu URL: `https://codepremium.msdn.microsoft.com`  
  
3. Vyhledejte zdroj, který chcete najít.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Centrum Code úrovně Premium](https://www.microsoft.com/en-us/sharedsource/code-center-premium.aspx)
