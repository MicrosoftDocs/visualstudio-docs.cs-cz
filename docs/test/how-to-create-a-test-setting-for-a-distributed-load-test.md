---
title: Vytvořit nastavení testu pro distribuovaný zátěžový Test
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, for distributed load tests
ms.assetid: b63d4b71-3b74-4872-b2d1-f0bd1a9a8544
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3129aa5139533db0783c168c3489e071fe9339b5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589136"
---
# <a name="how-to-create-a-test-settings-file-for-a-distributed-load-test"></a>Postupy: vytvoření souboru nastavení testu pro distribuovaný zátěžový test

Konfigurace *nastavení testu* pro zátěžové testy, abyste mohli distribuce těchto testů mezi více počítačů pomocí testovacích agentů a řadičů testu. Můžete také nakonfigurovat nastavení testu *adaptéry diagnostických dat*, který určuje typy dat, která chcete shromažďovat nebo způsob, jak ovlivnit testovací počítače při spuštění zátěžových testů ze sady Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Například můžete použít adaptér diagnostiky dat Profiler technologie ASP.NET ke shromažďování rozdělení práce kódu. Navíc adaptéry diagnostických dat slouží k simulaci potenciálních slabých míst v testovacím počítači nebo snížení dostupné systémové paměti.

Nastavení testu pro sadu Visual Studio jsou uloženy v souboru. Nastavení testu definuje následující informace o jednotlivých rolích:

- Sadu rolí, které jsou požadovány pro vaši testovanou aplikaci

- Role se použije ke spuštění testů

- Adaptéry diagnostických dat pro každou roli

Při spuštění testů vyberte nastavení testu jako aktivní test nastavení v závislosti na tom, co vyžadujete pro tento konkrétní spuštění testu. Soubor nastavení testu je uložen jako součást vašeho řešení. Název souboru má příponu *.testsettings*.

Když přidáte webový výkon a zátěžové testování projektu do řešení, *Default.testsettings* se vytvoří soubor. Soubor je automaticky přidán do řešení ve složce **položky řešení** složky. Tento soubor se spustí lokálně bez jakýchkoli adaptérů diagnostických dat. Můžete přidat další *.testsettings* souboru, nebo upravit *.testsettings* soubor k určení adaptérů diagnostických dat a řadičů testu.

Testovací kontrolér bude mít agenty, které můžete použít pro každou roli v nastavení testu. Další informace o testovacích kontrolérů a testovacích agentů najdete v tématu [Správa testovacích kontrolérů a testovacích agentů v sadě Visual Studio](../test/manage-test-controllers-and-test-agents.md).

Postupujte podle těchto kroků k vytvoření a odebrání nastavení testu v rámci vašeho řešení pro zátěžové testy, které máte v úmyslu spustit ze sady Visual Studio.

## <a name="create-a-test-settings-file"></a>Vytvořit soubor s nastavením testu

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **položky řešení**, přejděte na **přidat**a klikněte na tlačítko **nová položka**.

     **Přidat novou položku** zobrazí se dialogové okno.

2. V **nainstalované šablony** podokně zvolte **nastavení testu**.

3. (Volitelné) V **název** pole, změňte název souboru nastavení testu.

4. Zvolte **přidat**.

     Nový soubor nastavení testu se zobrazí v **Průzkumníka řešení**v části **položky řešení** složky.

5. **Nastavení testu** se zobrazí dialogové okno. **Obecné** je vybrána stránka.

     Teď můžete upravit a uložit hodnoty nastavení testu.

6. V části **název**, zadejte název pro nastavení testu.

7. (Volitelné) V části **popis**, zadejte popis nastavení testu, aby ostatní členové týmu věděli, co je určený pro.

8. (Volitelné) Chcete-li vybrat výchozí schéma pojmenování pro vaše testovací běhy, vyberte **výchozí schéma pojmenování**. Chcete-li definovat vlastní schéma pojmenování, vyberte **uživatelem definované schéma** a pak zadejte text, který má v **text předpony**. Chcete-li datum a časové razítko se připojit k názvu běhu testu, vyberte **připojit časové razítko**.

9. Zvolte **role**.

     **Role** zobrazí se stránka.

     ![Roli nastavení testu](../test/media/load_testtestrole.png)

10. Pro spouštění testů vzdáleně, nebo chcete-li vzdáleně spustit testy a vzdáleně shromažďovat data, použijte **metoda spuštění testu** rozevíracího seznamu a vyberte **vzdálené spuštění**.

11. Použití **řadič** rozevíracího seznamu vyberte řadič testu pro testovací agenty z **řadič** , který se použije ke spuštění testů nebo shromažďování dat.

    > [!NOTE]
    > Pokud je to poprvé, co přidáváte řadič, žádné řadiče, zobrazí se v rozevíracím seznamu. Seznam je vyplněn předchozími řadiči, které jste zadali v rámci jiných nastaveních testu. Do pole musíte zadat název kontroleru (například **TestControllerMachine1**).

12. K přidání rolí, které chcete použít ke spuštění testů a shromažďování dat, v části **role**, zvolte **přidat**.

13. Zadejte název pro roli v **název** sloupce. Role může být například "Webový Server".

14. Opakujte kroky 12 a 13, chcete-li přidat všechny role, které potřebujete.

     Každá role používá testovacího agenta, který je spravovaný řadičem testu.

15. Vyberte roli, kterou chcete spustit testy a klikněte na tlačítko **nastavit jako roli pro spouštění testů**.

    > [!IMPORTANT]
    > Ostatní role, které vytvoříte a definujete nebudou spouštět testy, ale budou použity pouze ke sběru dat podle dat a diagnostických adaptérů zadaných pro role v **Data a Diagnostika** stránky.

16. Budou limitovat agenty, které můžete použít pro roli, vyberte roli a klikněte na tlačítko **přidat** na panelu nástrojů v rámci **atributy agenta pro vybranou roli**.

     **Pravidlo výběru agenta** se zobrazí dialogové okno.

     Zadejte název do **název atributu** a hodnotou v **hodnota atributu**a klikněte na tlačítko **OK**. Přidejte tolik atributů, kolik potřebujete.

     Můžete například přidat atribut s názvem "RAM > 16GB", který má hodnotu "True" nebo "False", chcete-li filtrovat počítače testovacího agenta, které mají více než 16GB paměti. Chcete-li použít stejný atribut pro jeden nebo více testovacích agentů, je použít **spravovat řadič testu** dialogové okno. Další informace najdete v tématu [Správa testovacích kontrolérů a testovacích agentů v sadě Visual Studio](../test/manage-test-controllers-and-test-agents.md).

17. Zvolte **dat a diagnostiky**.

     **Dat a diagnostiky** zobrazí se stránka.

     ![Test nastavení data a Diagnostika](../test/media/load_testtest.png)

18. V **Data a Diagnostika** stránce definujete význam role výběrem *adaptéry diagnostických dat* , které role bude využívat ke shromažďování dat. Proto pokud jeden nebo více data a diagnostické adaptéry jsou povoleny pro roli, řadič testu vybere dostupného testovacího agenta pro počítač shromažďovat data pro zadaná data a diagnostické adaptéry založené na parametrech definovaných pro danou roli. Pokud chcete vybrat data a adaptérů diagnostických dat, které chcete shromáždit pro každou roli, vyberte roli. Pro každou roli vyberte adaptéry diagnostických dat podle potřeby testů. Chcete-li konfigurovat jednotlivé adaptéry diagnostických dat, který jste vybrali pro každou roli, zvolte **konfigurovat**.

     **Příklad rolí a adaptérů diagnostických dat:**

     Můžete například vytvořit roli klienta s názvem "Desktop Client", který má atribut "Uses SQL" nastavený na "hodnotu True" a roli serveru s názvem "SQL Server" s atributem nastaveným na "RAM > 16GB". Pokud určíte, že "Klient plochy" spustí testy výběrem **nastavit jako roli pro spouštění testů** v **role** stránky, řadič testu vybere stroje testovacími agenty, které obsahují atribut "Používá SQL" nastaveným na hodnotu "True" na základě které chcete spustit testy. Řadič testu také vybere stroje serveru SQL testovacími agenty, které obsahují atribut "RAM > 16GB" pouze ke sběru dat, která je definovaná pomocí dat a diagnostických adaptérů zahrnutých v roli. Testovací agenti "Stolní klient" mohou také shromažďovat data pro počítače, na kterých jsou spuštěni, pokud příliš vybrat adaptéry dat a diagnostiky pro danou roli.

     Další podrobnosti o všech adaptérech diagnostiky dat a jeho konfiguraci můžete zobrazit v souvisejících tématech v následující tabulce.

     Další informace o adaptérech diagnostických dat naleznete v tématu [shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

     **Adaptéry diagnostických dat pro zátěžové testy**

    |Adaptér diagnostiky dat|Použití v zátěžových testech|Související téma|
    |-|-------------------------|-|
    |**Klient Proxy ASP.NET pro IntelliTrace a dopad testu:** tento server proxy umožňuje shromažďovat informace o voláních http z klienta na webový server pro adaptéry diagnostických dat IntelliTrace a dopad testu.|![Informační ikona](../test/media/vc364f4.gif)<br /><br /> Pokud nemáte specifickou potřebu shromažďovat informace o systému pro počítače testovacího agenta, nezahrnujte tento adaptér. **Upozornění:** nedoporučujeme používat adaptér IntelliTrace v zátěžových testech kvůli problémům, k nimž dochází kvůli velkému množství dat, která je shromažďována. <br /><br /> Údaje o vlivu testu nejsou při použití zátěžových testů shromažďovány.||
    |**IntelliTrace:** můžete nakonfigurovat informace o specifickém diagnostickém trasování, která je uložena v souboru protokolu. Soubor protokolu má příponou *.tdlog*. Při spuštění testu a testovací krok nezdaří, můžete vytvořit chybu. Soubor protokolu, který obsahuje diagnostické trasování je automaticky připojen k této chybě. Data sbírána do souboru protokolu zvyšují efektivitu ladění zkrácením doby potřebné k reprodukci a diagnostice chyby v kódu. Z tohoto protokolu souboru místní relace můžete znovu vytvořit na jiném počítači. Tím se snižuje riziko, že není možné reprodukovat chyby.<br /><br /> Další informace najdete v tématu [data IntelliTrace shromažďování](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).|![Ikona důležité](../test/media/vc364f3.gif)<br /><br /> Nedoporučujeme používat adaptér IntelliTrace v zátěžových testech kvůli problémům, k nimž dochází kvůli velkému množství dat, která jsou shromažďována a zaznamenána. Měli byste se pokusit použít adaptér IntelliTrace pouze v zátěžových testech, které neběží dlouho a nepoužívají spoustu testovacích agentů.|[Postupy: shromažďování dat IntelliTrace pro ladění složitých problémů](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|
    |**Profiler technologie ASP.NET:** můžete vytvořit nastavení testu, které zahrnuje profilování technologie ASP.NET, které shromažďuje údaje o výkonu webových aplikací ASP.NET.|Adaptér diagnostiky dat profiler technologie ASP.NET profily procesu Internetové informační služby (IIS), nebude fungovat proti vývojovému webovému serveru. Chcete-li Profilovat webu v zátěžovém testu, budete muset nainstalovat testovacího agenta na počítači, na kterém běží služby IIS na. Testovací agent nebude generovat zatížení, ale bude pouze agenta do kolekce. Další informace najdete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).|[Postupy: Konfigurace služby ASP.NET profiler pro zátěžové testy pomocí nastavení testu](../test/how-to-configure-aspnet-profiler-for-load-tests-using-test-settings.md)|
    |**Protokol událostí:** můžete nakonfigurovat tak, aby shromažďoval události protokolu, nastavení testu, který bude zahrnut ve výsledcích testu.||[Postupy: Konfigurace shromažďování událostí protokolů pomocí nastavení testů](https://msdn.microsoft.com/48d67891-6018-4549-83e3-213d5d824a02)|
    |**Emulace sítě:** můžete určit, že chcete do vašeho testu umělé zatížení sítě tak, že pomocí nastavení testu. Emulace sítě ovlivňuje komunikaci do a z počítače emulací konkrétního síťového připojení s rychlostí, vytáčeného. **Poznámka:** emulaci sítě nelze použít ke zvýšení rychlosti připojení k síti.|Adaptér emulace sítě je testy zatížení ignorován. Místo toho zátěžové testy pomocí nastavení, které jsou určené v síťové skladbě scénáře testování zatížení.<br /><br /> Další informace najdete v tématu [určení typů virtuálních sítí](../test/specify-virtual-network-types-in-a-load-test-scenario.md).||
    |**Informace o systému:** nastavení testu lze upravit na obsahovalo systémové informace o počítačích, na kterých běží systémové informace diagnostiky a dat kolekce. Systémové informace jsou uvedeny ve výsledcích testu s použitím nastavení testu.|![Ikona informací](../test/media/vc364f4.gif)<br /><br /> Informace o systému může shromažďovat z agentů zatížení i testovaného systému.|Tyto informace můžete shromáždit není nutná žádná konfigurace.|
    |**Dopad testu:** můžete shromažďovat informace o metodách kódu aplikace byly použity při spuštění testovacího procesu. To je možné společně se změnami kódu aplikace, která vyrábí celá vývojářům určit, jaké zkoušky byly ovlivněny změnami vývoje.|Data dopadu testů není použití zátěžových testů shromažďovány.||
    |**Záznam videa:** můžete vytvořit záznam videa relace plochy při spuštění automatického testování. To může být užitečné, chcete-li zobrazit akce uživatele pro kódovaný test uživatelského rozhraní. Video může pomoci ostatním členům týmu izolovat problémy aplikací, které je obtížné reprodukovat. **Poznámka:** při vzdáleném spuštění testů nebude záznamník videa fungovat, pokud je agent spuštěn v režimu interaktivního procesu.|![Ikona důležité](../test/media/vc364f3.gif) **upozornění:** společnost Microsoft nedoporučuje použití adaptéru nahrávacího pro zátěžové testy.|[Postupy: patří nahrávání obrazovky a hlasu během testů pomocí nastavení testu](../test/how-to-include-recordings-of-the-screen-and-voice-during-tests.md)|

19. Zvolte **nasazení**.

     **Nasazení** zobrazí se stránka.

20. Chcete-li vytvořit samostatný adresář pro nasazení pokaždé, když spustíte testy, vyberte **povolit nasazení**.

    > [!NOTE]
    > Pokud to uděláte, můžete pokračovat k sestavení aplikace při spuštění testů.

21. Chcete-li přidat soubor do adresáře, který používáte ke spuštění testů, zvolte **přidat soubor**a potom vyberte soubor, který chcete přidat.

    > [!NOTE]
    > Při spuštění zátěžového testu se automaticky nasadí sestavení s moduly plug-in, datové soubory a odeslané soubory.

22. Chcete-li přidat adresář do adresáře, který používáte ke spuštění testů, zvolte **přidat adresář** a potom vyberte adresář, který chcete přidat.

23. Chcete-li spouštět skripty před a po testech, zvolte **instalační a čistící skripty**.

     **Instalační a čistící skripty** zobrazí se stránka.

    1. Zadejte umístění souboru skriptu v **instalační skript** nebo zvolte tři tečky ( **...** ) a vyhledejte skript nastavení.

    2. Zadejte umístění souboru skriptu v **skript pro vyčištění** nebo zvolte tři tečky ( **...** ) a vyhledejte skript vyčištění.

24. Chcete-li spustit testy pomocí jiného hostitele, zvolte **hostitele**.

    1. V **typ hostitele**, ověřte, že **výchozí** zaškrtnuto.

        > [!NOTE]
        > **ASP.NET** v **hostovat typ** není podporována v zátěžových testech.

    2. Použití **spuštění testu v 32bitové nebo 64bitové** procesu rozevíracího seznamu vyberte, jestli chcete, aby webové testy výkonu a jednotky v zátěžovém testu ke spuštění jako 32bitový nebo 64bitové proces.

        > [!NOTE]
        > Pro maximální flexibilitu byste kompilace webového výkonu a načtěte projekty testů s použitím **jakýkoli procesor** konfigurace. Poté můžete spouštět na 32bitových a 64bitových agentech. Kompilace webového výkonu a zátěžové testování projektů pomocí **64-bit** konfigurace nenabízí žádnou výhodu.

25. (Volitelné) Chcete-li omezit dobu pro jednotlivé testovací běhy a jednotlivé testy, zvolte **časový limit testu.**

    1. Chcete-li přerušit testovací běh při překročení časového limitu, vyberte **přerušit spuštění testu, pokud překročí celkový čas** a potom zadejte hodnotu pro toto omezení.

    2. Chcete-li jednotlivé testy selhat při překročení časového limitu, vyberte **označit individuální test jako neúspěšný, pokud jeho doba běhu překročí**a zadejte hodnotu pro toto omezení.

26. Přeskočit **Jednotkový Test**. Zátěžové testy toto nastavení nepoužívají.

27. Přeskočit **webového testu**. Zátěžové testy toto nastavení nepoužívají.

28. Chcete-li uložit nastavení testu, zvolte **uložit jako**. Zadejte název souboru, který chcete v **název objektu**.

## <a name="remove-a-test-settings-file-from-your-solution"></a>Odebrání souboru nastavení testu z řešení

V části **položky řešení** složky **Průzkumníka řešení**, klikněte pravým tlačítkem na nastavení testu, které chcete odebrat a klikněte na tlačítko **odebrat**.

Soubor nastavení testu je odebrán z řešení.

## <a name="see-also"></a>Viz také:

- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Shromažďování diagnostických údajů pomocí nastavení testů](../test/collect-diagnostic-information-using-test-settings.md)
