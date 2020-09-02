---
title: Import projektu XCode | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 4faa2ecae7f53d29e6aad92723ca6d12e50e2812
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150892"
---
# <a name="import-an-xcode-project"></a>Import projektu XCode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft Visual C++ pro vývoj mobilních aplikací pro různé platformy zahrnuje podporu pro přesun projektů XCode do sady Visual Studio, kde můžete vytvářet knihovny pro různé platformy a sdílet kód s ostatními projekty. Průvodce importem z XCode zjednodušuje proces importu projektů a rozdělení kódu C++ ve vašich cílech XCode pro použití jako statické knihovny nebo projektu sdíleného kódu. Můžete spravovat kód specifický pro iOS v aplikaci Visual Studio a dál používat XCode ke scénářům a sestavením. Informace o tom, jak snadno přesunout kód mezi Visual Studio a XCode, najdete v tématu přesun změn mezi XCode a Visual Studio.  
  
## <a name="using-the-import-from-xcode-wizard"></a>Pomocí Průvodce importem z XCode  
 V tomto tématu se dozvíte, jak přesunout projekt XCode do sady Visual Studio, abyste mohli využít výhod sdílení kódu a řešení pro různé platformy. Za předpokladu je potřeba spárovat svůj počítač Mac s Visual Studiem, aby bylo možné naimportovat, exportovat a sestavovat váš projekt. Pokyny, jak nastavit párování, najdete v tématu [instalace a konfigurace nástrojů pro sestavení pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Svůj projekt XCode musíte také sdílet přes síť nebo ho přesunout do počítače s Visual Studio, abyste mohli použít Průvodce importem z XCode.  
  
#### <a name="import-from-xcode"></a>Import z XCode  
  
1. V nabídce **soubor** klikněte na příkaz **Nový**, **importovat**a **importovat z Xcode**. Tím se spustí dialog průvodce **importem z Xcode** .  
  
    ![Zvolit cílový projekt XCode, který se má importovat](../cross-platform/media/cppmdd-u2-importxcode-choose.PNG "CPPMDD_U2_ImportXCode_Choose")  
  
2. V podokně **Zvolte projekt** klikněte na tlačítko Procházet a vyberte soubor Xcode. pbxproj. V dialogovém okně **Vybrat soubor projektu Xcode** přejděte do souboru projektu a pak zvolte **otevřít**.  
  
    ![Vyberte soubor projektu v dialogovém okně Vybrat soubor projektu Xcode.](../cross-platform/media/cppmdd-u2-importxcode-browse.PNG "CPPMDD_U2_ImportXCode_Browse")  
  
    V průvodci Import z XCode klikněte na tlačítko **Další**.  
  
3. V podokně **cílové cíle** vyberte cíle z projektu Xcode pro import do projektů sady Visual Studio. Cíle XCode jsou podobné projektům sady Visual Studio; Většina je kolekce kódu a prostředků, které vytváří binární soubor. Průvodce importem z XCode umožňuje pouze import cílů, které tvoří binární, ale ne statickou knihovnu, jako cílové cíle. Cíle statických knihoven XCode jsou předmětem dalšího kroku.  
  
    ![Podokno cílové cíle Průvodce importem z XCode](../cross-platform/media/cppmdd-u2-importxcode-destination.jpg "CPPMDD_U2_ImportXCode_Destination")  
  
    Pro každý cíl vybraný v **cíli, který se má importovat**, průvodce automaticky detekuje soubory kódu C++, které mohou být rozděleny do samostatného projektu statických knihoven, a umístí je do oddílu **položky projektu C++** . Další kód a prostředky jsou ponechány v části **položky projektu Xcode** . Tyto projekty se stanou samostatnými statickými knihovnami a aplikacemi v aplikaci Visual Studio, jakmile průvodce dokončí proces importu. Ve výchozím nastavení se pro testování částí a cíle architektury nedělí do samostatných projektů průvodce.  
  
    Chcete-li změnit, které soubory jsou v každém projektu, použijte tlačítka nahoru a dolů. Až budete s soubory v každém projektu spokojeni, klikněte na tlačítko **Další** a pokračujte.  
  
4. V podokně **cíle knihovny** vyberte statické knihovny, které jsou cíle z projektu Xcode, které chcete importovat do projektů sady Visual Studio. V tomto podokně můžete zvolit, které soubory jsou umístěny do projektu sdíleného kódu a které jsou umístěny v projektu statických knihoven. V každém z cílů v seznamu **cíle na Import** můžete určit, které soubory jsou umístěny v **položkách projektu sdíleného kódu** a **položky projektu statické knihovny** pomocí tlačítek nahoru a dolů.  
  
    ![Podokno cílení na Import z knihovny XCode](../cross-platform/media/cppmdd-u2-importxcode-library.jpg "CPPMDD_U2_ImportXCode_Library")  
  
    Projekt sdíleného kódu je způsob, jak sdílet sadu souborů zdrojového kódu mezi projekty v sadě Visual Studio. Kód je sestaven jako součást projektu, který jej obsahuje, nikoli jako vlastní projekt. Vzhledem k tomu, že projekty, které obsahují sdílený kód, mohou mít různé architektury a konfigurace, jedná se o nejlepší způsob, jak poskytnout jeden projekt obsahující kód, který může být sestaven pro mnoho druhů platforem.  
  
    Až budete s soubory v každém projektu spokojeni, klikněte na tlačítko **Další** a pokračujte.  
  
5. Podokno **globální vlastnosti** lze použít k nastavení cesty hledání rozhraní a cesty pro hledání záhlaví include pro všechny projekty iOS v sadě Visual Studio. Visual Studio používá tyto cesty pro procházení zdrojového kódu a pro IntelliSense. Tyto globální cesty jsou užitečné, když vytváříte projekty iOS, které používají společnou sadu hlaviček a architektur.  
  
    ![Import z podokna globálních vlastností XCode](../cross-platform/media/cppmdd-u2-importxcode-global.jpg "CPPMDD_U2_ImportXCode_Global")  
  
    Tyto globální cesty lze také nastavit v sadě Visual Studio v dialogovém okně **Možnosti** . Pokud je chcete vyhledat, v nabídce **nástroje** vyberte **Možnosti**. V dialogovém okně **Možnosti** rozbalte položku **různé platformy**, **C++**, **iOS**, **globální vlastnosti**.  
  
    Pokračujte výběrem položky **Další**.  
  
6. Podokno **architektury** se používá ke konfiguraci cest používaných v aplikaci Visual Studio pro procházení a IntelliSense pro váš projekt. Cesty musí být dostupné pro Visual Studio pro každé rozhraní, na které odkazuje váš projekt XCode. Průvodce kontroluje odkazy na rozhraní v projektech XCode a zobrazuje, zda aplikace Visual Studio dokáže najít rozhraní. Všechny cesty, které jste již nastavili v globálních vlastnostech, by měly být zjišťovány sadou Visual Studio. Výjimky jsou uvedeny v seznamu rozhraní. Pro každé rozhraní uvedené s X zadejte cestu dostupnou pro počítač pro Visual Studio, kde najdete rozhraní. Pomocí tlačítka Procházet [...] můžete najít cestu pomocí dialogového okna pro **Výběr složky** . Cesta k rozhraní může být buď místní kopie, nebo sdílená složka přístupná přes síť na Macu.  
  
    ![Import z podokna XCode Frameworks](../cross-platform/media/cppmdd-u2-importxcode-frameworks.jpg "CPPMDD_U2_ImportXCode_Frameworks")  
  
    Pokračujte výběrem položky **Další**.  
  
7. Podokno **nastavení projektu** umožňuje změnit rozhraní a zahrnout nastavení cesty pro hledání hlaviček pro každý projekt, který průvodce vytvoří. Toto podokno použijte k nastavení cest specifických pro projekt, které se liší od globálních nastavení.  
  
    Chcete-li nastavit cestu pro určitý projekt, vyberte v rozevíracím seznamu **cílový projekt** soubor projektu, pak nastavte hodnoty v **cestě hledání rozhraní** a přidejte ovládací prvky pro **cestu pro hledání v hlavičce** . Pomocí tlačítka Procházet [...] vedle každého ovládacího prvku můžete cestu najít pomocí dialogového okna pro **Výběr složky** .  
  
    ![Import z podokna projekty XCode](../cross-platform/media/cppmdd-u2-importxcode-projects.jpg "CPPMDD_U2_ImportXCode_Projects")  
  
    Pokud se na tomto počítači v aplikaci Visual Studio nespáruje žádná Vzdálená adresa MAC, zobrazí se odkaz konfigurace vzdáleného počítače. Pokyny, jak nastavit párování, najdete v tématu [instalace a konfigurace nástrojů pro sestavení pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
    Chcete-li importovat projekt XCode pomocí nastavení průvodce, klikněte na tlačítko **importovat**.  
  
   Průvodce Import z XCode vytvoří projekty v aplikaci Visual Studio, které odpovídají vybraným cílům projektu XCode. Kód, který lze sdílet s jinými projekty jazyka C++, je rozdělen do samostatného sdíleného kódu a projektů statické knihovny. Zbývající kód je umístěn v knihovně iOS a projektech aplikace, které mohou být vytvořeny vzdáleně pomocí aplikace Visual Studio. Další informace o přesouvání kódu mezi Visual Studio a XCode najdete v tématu [synchronizace změn mezi Xcode a Visual Studio](../cross-platform/sync-changes-between-xcode-and-visual-studio.md).
