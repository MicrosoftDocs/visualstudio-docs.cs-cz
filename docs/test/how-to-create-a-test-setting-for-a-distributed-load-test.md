---
title: Vytvoření testovacího nastavení pro distribuovaný zátěžový test
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, for distributed load tests
ms.assetid: b63d4b71-3b74-4872-b2d1-f0bd1a9a8544
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3129aa5139533db0783c168c3489e071fe9339b5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589136"
---
# <a name="how-to-create-a-test-settings-file-for-a-distributed-load-test"></a>Postup: Vytvoření souboru nastavení testu pro distribuovaný zátěžový test

Nakonfigurujte *nastavení testů* pro zátěžové testy, abyste tyto testy mohli distribuovat mezi více počítačů pomocí testovacích agentů a testovacích řadičů. Můžete také nakonfigurovat nastavení testu pro použití *adaptérů diagnostických dat*, které určují druhy dat, které chcete shromažďovat, nebo jak ovlivnit testovací počítače při spuštění zátěžových testů z aplikace Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Můžete například použít adaptér diagnostických dat ASP.NET Profiler ke shromažďování rozdělení výkonu kódu. Adaptéry diagnostických dat lze navíc použít k simulaci potenciálních kritických míst v testovacím počítači nebo ke snížení dostupné systémové paměti.

Nastavení testu pro Visual Studio jsou uloženy v souboru. Nastavení testu definuje následující informace o každé roli:

- Sada rolí, které jsou požadovány pro testovku aplikace

- Role, která se má použít ke spuštění testů

- Adaptéry diagnostických dat, které se mají použít pro každou roli

Při spuštění testů vyberete nastavení testu, které se použije jako aktivní nastavení testu v závislosti na tom, co potřebujete pro tento konkrétní test. Soubor nastavení testu je uložen jako součást vašeho řešení. Název souboru má příponu *.testsettings*.

Když přidáte webový výkon a načíst testovací projekt do řešení, vytvoří se soubor *Default.testsettings.* Soubor je automaticky přidán do řešení ve složce **Položky řešení.** Tento soubor spustí testy místně bez adaptérů diagnostických dat. Můžete přidat další soubor *.testsettings* nebo upravit soubor *.testsettings* a určit adaptéry diagnostických dat a testovací řadiče.

Testovací řadič bude mít agenty, které lze použít pro každou roli v nastavení testu. Další informace o testovacích řadičích a testovacích agentech naleznete v [tématu Správa testovacích řadičů a testovacích agentů pomocí sady Visual Studio](../test/manage-test-controllers-and-test-agents.md).

Následujícím postupem vytvořte a odeberte nastavení testů v řešení pro zátěžové testy, které chcete spustit z sady Visual Studio.

## <a name="create-a-test-settings-file"></a>Vytvoření souboru nastavení testu

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **položku Položky řešení**, přejděte na **Přidat**a pak zvolte **Nová položka**.

     Zobrazí se dialogové okno **Přidat novou položku**.

2. V podokně **Nainstalované šablony** zvolte **Testovat nastavení**.

3. (Nepovinné) V poli **Název** změňte název souboru nastavení testu.

4. Zvolte **Přidat**.

     Nový soubor nastavení testu se zobrazí v **Průzkumníku řešení**ve složce **Položky řešení.**

5. Zobrazí se dialogové okno **Nastavení testu.** Je vybrána stránka **Obecné.**

     Nyní můžete upravovat a ukládat hodnoty nastavení testu.

6. V **části Název**zadejte název nastavení testu.

7. (Nepovinné) V **části Popis**zadejte popis nastavení testu, aby ostatní členové týmu věděli, k čemu je určen.

8. (Nepovinné) Chcete-li vybrat výchozí schéma pojmenování pro testovací běhy, vyberte **možnost Výchozí schéma pojmenování**. Chcete-li definovat vlastní schéma pojmenování, vyberte **schéma definované uživatelem** a zadejte požadovaný text do **textové opravy**. Chcete-li připojit datum a časové razítko k názvu testovacího běhu, vyberte **připojit časové razítko**.

9. Zvolte **Role**.

     Zobrazí se stránka **Role.**

     ![Role nastavení testu](../test/media/load_testtestrole.png)

10. Chcete-li spustit testy vzdáleně nebo spustit testy vzdáleně a vzdáleně shromažďovat data, použijte rozbalovací soubor **metody spuštění testu** a vyberte vzdálené **spuštění**.

11. Pomocí rozevíracího **souboru Řadič** vyberte testovací řadič pro testovací agenty z **řadiče,** který bude použit ke spuštění testů nebo ke shromažďování dat.

    > [!NOTE]
    > Pokud je to poprvé, co přidáváte řadič, žádné řadiče budou uvedeny v rozevíracím seznamu. Seznam je naplněn předchozími řadiči, které jste zadali v jiných nastaveních testu. Do pole musíte zadat název řadiče (například **TestControllerMachine1**).

12. Chcete-li přidat role, které chcete použít ke spuštění testů a shromažďování dat, zvolte V části **Role**zvolte **Přidat**.

13. Do sloupce **Název** zadejte název role. Role může být například "Webový server".

14. Opakováním kroků 12 a 13 přidejte všechny role, které požadujete.

     Každá role používá testovacího agenta, který je spravován testovacím řadičem.

15. Vyberte roli, kterou chcete spustit testy a pak zvolte **Nastavit jako roli pro spuštění testů**.

    > [!IMPORTANT]
    > Ostatní role, které vytvoříte a definujete, nebudou spouštět testy, ale budou použity pouze ke shromažďování dat podle dat a diagnostických adaptérů, které zadáte pro role na stránce **Data a Diagnostika.**

16. Chcete-li omezit agenty, které lze použít pro roli, vyberte roli a pak zvolte **Přidat** na panelu nástrojů v části **Atributy agenta pro vybranou roli**.

     Zobrazí se dialogové okno **Pravidlo výběru agenta.**

     Zadejte název do **pole Název atributu** a hodnotu v **pole Hodnota atributu**a pak zvolte **OK**. Přidejte tolik atributů, kolik potřebujete.

     Můžete například přidat atribut s názvem "RAM > 16 GB", který má hodnotu "True" nebo "False" pro filtrování na počítačích testovacího agenta, které mají více než 16 GB paměti. Chcete-li použít stejný atribut u jednoho nebo více testovacích agentů, použijte dialogové okno **Spravovat testovací řadič.** Další informace naleznete v [tématu Správa testovacích řadičů a testovacích agentů pomocí sady Visual Studio](../test/manage-test-controllers-and-test-agents.md).

17. Zvolte **Data a diagnostika**.

     Zobrazí se stránka **Data a diagnostika.**

     ![Testování nastavení dat a diagnostiky](../test/media/load_testtest.png)

18. Na stránce **Data a diagnostika** definujete, co role dělá výběrem *adaptérů diagnostických dat,* které bude role používat ke shromažďování dat. Proto pokud jeden nebo více dat a diagnostické adaptéry jsou povoleny pro roli, testovací řadič vybere počítač s dostupným testovacím agentem pro sběr dat pro zadaná data a diagnostické adaptéry na základě atributů, které jste definovali pro roli. Chcete-li vybrat adaptéry dat a diagnostických dat, které chcete shromáždit pro každou roli, vyberte roli. Pro každou roli vyberte adaptéry diagnostických dat podle potřeb testů. Chcete-li nakonfigurovat každý adaptér diagnostických dat, který jste vybrali pro každou roli, zvolte **Konfigurovat**.

     **Příklad rolí a adaptérů diagnostických dat:**

     Můžete například vytvořit roli klienta s názvem "Desktop Client", která má atribut "Používá SQL" nastavený na hodnotu "True" a roli serveru s názvem "SQL Server", která má atribut nastavený na "RAM > 16GB". Pokud zadáte, že "Desktop Client" spustí testy výběrem **Nastavit jako role pro spuštění testů na** stránce **Role,** testovací řadič vybere počítače, které mají testovací agenty, které obsahují atribut "Používá SQL" nastavený na "True", na kterém chcete spustit testy. Testovací řadič také vybere počítače serveru SQL, které mají testovací agenty, které obsahují atribut "RAM > 16GB" pouze pro sběr dat, která jsou definována daty a diagnostickými adaptéry, které jsou zahrnuty v roli. Agent testů "Desktop Client" může také shromažďovat data pro počítače, na kterých je spuštěn, pokud vyberete data a diagnostické adaptéry pro tuto roli.

     Podrobnosti o každém adaptéru diagnostických dat a jeho konfiguraci naleznete v následující tabulce.

     Další informace o adaptérech diagnostických dat naleznete v [tématu Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

     **Adaptéry diagnostických dat pro zátěžové testy**

    |Adaptér diagnostiky dat|Použití v zátěžových testech|Přidružené téma|
    |-|-------------------------|-|
    |**ASP.NET proxy klienta pro IntelliTrace a dopad testu:** Tento proxy server umožňuje shromažďovat informace o volání http z klienta na webový server pro adaptéry diagnostických dat IntelliTrace a Test Impact.|![Ikona Informace](../test/media/vc364f4.gif)<br /><br /> Pokud nemáte konkrétní potřebu shromažďovat systémové informace pro počítače testovacího agenta, nezahrnujte tento adaptér. **Pozor:**  Nedoporučujeme použití adaptéru IntelliTrace v zátěžových testech z důvodu problémů, ke kterým dochází z důvodu velkého množství dat, která jsou shromažďována. <br /><br /> Data dopadu testu nejsou shromažďována pomocí zátěžových testů.||
    |**IntelliTrace:** Můžete nakonfigurovat konkrétní diagnostické trasování informace, které jsou uloženy v souboru protokolu. Soubor protokolu obsahuje příponu *TDLog*. Při spuštění testu a krok testu se nezdaří, můžete vytvořit chybu. K této chybě je automaticky připojen soubor protokolu, který obsahuje diagnostické trasování. Data shromážděná v souboru protokolu zvyšuje produktivitu ladění zkrácením doby potřebné k reprodukci a diagnostice chyby v kódu. Z tohoto souboru protokolu lze místní relaci znovu vytvořit v jiném počítači. To snižuje riziko, že chybu nelze reprodukovat.<br /><br /> Další informace naleznete [v tématu Shromažďování dat IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).|![Ikona Důležité](../test/media/vc364f3.gif)<br /><br /> Nedoporučujeme použití adaptéru IntelliTrace v zátěžových testech z důvodu problémů, ke kterým dochází z důvodu velkého množství dat, která jsou shromažďována a protokolována. Měli byste se pokusit použít adaptér IntelliTrace pouze v zátěžových testech, které neběží dlouho a nepoužívají mnoho testovacích agentů.|[Postup: Shromažďování dat IntelliTrace, které vám pomohou při ladění obtížných problémů](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|
    |**ASP.NET profiler:** Můžete vytvořit testovací nastavení, které zahrnuje ASP.NET profilování, které shromažďuje údaje o výkonu ASP.NET webových aplikací.|Adaptér diagnostických dat ASP.NET profileru profiluje proces Internetové informační služby (IIS), takže nebude fungovat proti vývojovému webovému serveru. Chcete-li profilovat web v zátěžovém testu, je nutné nainstalovat testovacího agenta do počítače, na který je služba IIS spuštěna. Testovací agent nebude generovat zatížení, ale bude pouze agent kolekce. Další informace naleznete v [tématu Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).|[Postup: Konfigurace ASP.NET profileru pro zátěžové testy pomocí nastavení testu](../test/how-to-configure-aspnet-profiler-for-load-tests-using-test-settings.md)|
    |**Protokol událostí:** Můžete nakonfigurovat nastavení testu tak, aby zahrnovalo shromažďování protokolu událostí, které budou zahrnuty do výsledků testu.||[Postup: Konfigurace kolekce protokolů událostí pomocí nastavení testu](https://msdn.microsoft.com/48d67891-6018-4549-83e3-213d5d824a02)|
    |**Emulace sítě:** Můžete určit, že chcete umístit umělé zatížení sítě na test pomocí nastavení testu. Emulace sítě ovlivňuje komunikaci do a ze zařízení emulací určité rychlosti připojení k síti, například telefonického připojení. **Poznámka:**  Emulaci sítě nelze použít ke zvýšení rychlosti připojení k síti.|Adaptér emulace sítě je zátěžovými testy ignorován. Místo toho zátěžové testy použít nastavení, které jsou zadány v kombinaci sítě scénáře zátěžového testu.<br /><br /> Další informace naleznete v [tématu Specify virtual network types](../test/specify-virtual-network-types-in-a-load-test-scenario.md).||
    |**Systémové informace:** Nastavení testu lze nastavit tak, aby zahrnovalo systémové informace o počítačích, na kterých je spuštěna diagnostika systémových informací a sběrač dat. Systémové informace jsou určeny ve výsledcích testu pomocí nastavení testu.|![Ikona Informace](../test/media/vc364f4.gif)<br /><br /> Můžete shromažďovat informace o systému z agentů zatížení i z testovného systému.|Ke shromažďování těchto informací není nutná žádná konfigurace.|
    |**Dopad testu:** Můžete shromažďovat informace o tom, které metody kódu aplikace byly použity při spuštění testovacího případu. To lze použít společně se změnami kódu aplikace, které jsou provedeny vývojáři k určení, které testy byly ovlivněny těmito změnami vývoje.|Data dopadu testu nejsou shromažďována pomocí zátěžových testů.||
    |**Videorekordér:** Při spuštění automatického testu můžete vytvořit videozáznam relace na ploše. To může být užitečné pro zobrazení akcí uživatele pro kódovaný test uživatelského rozhraní. Video může pomoci ostatním členům týmu izolovat problémy s aplikacemi, které je obtížné reprodukovat. **Poznámka:**  Při vzdáleném spuštění testů nebude videorekordér fungovat, pokud není agent spuštěn v interaktivním režimu procesu.|![Upozornění](../test/media/vc364f3.gif) na důležitou **ikonu:** Pro zátěžové testy nedoporučujeme používat adaptér videorekordéru.|[Postup: Zahrnout nahrávky obrazovky a hlasu během testů pomocí nastavení testu](../test/how-to-include-recordings-of-the-screen-and-voice-during-tests.md)|

19. Zvolte **Nasazení**.

     Zobrazí se stránka **Nasazení.**

20. Chcete-li vytvořit samostatný adresář pro nasazení při každém spuštění testů, vyberte **možnost Povolit nasazení**.

    > [!NOTE]
    > Pokud tak učiníte, můžete pokračovat v sestavení aplikace při spuštění testů.

21. Chcete-li přidat soubor do adresáře, který používáte ke spuštění testů, zvolte **Přidat soubor**a vyberte soubor, který chcete přidat.

    > [!NOTE]
    > Při spuštění zátěžových testů se automaticky nasadí sestavení modulů plug-in, datové soubory a nahrané soubory.

22. Chcete-li přidat adresář do adresáře, který používáte ke spuštění testů, zvolte **Přidat adresář** a vyberte adresář, který chcete přidat.

23. Chcete-li spustit skripty před a po testech, zvolte **Instalační a vyčištění skriptů**.

     Zobrazí se stránka **Skripty nastavení a vyčištění.**

    1. Zadejte umístění souboru skriptu **do instalačního skriptu** nebo zvolte tři tečky (**...**) pro vyhledání instalačního skriptu.

    2. Zadejte umístění souboru skriptu do **skriptu Vyčištění** nebo zvolte tři tečky (**...**) pro nalezení skriptu vyčištění.

24. Chcete-li testy spustit pomocí jiného hostitele, zvolte **Možnost Hostitelé**.

    1. V **části Typ hostitele**ověřte, zda je vybrána možnost **Výchozí.**

        > [!NOTE]
        > **ASP.NET** v **typu Host** není v zátěžových testech podporována.

    2. Pomocí **spustit test v 32bitové nebo 64bitové** proces rozevírací rozbalovací rozbalit vybrat, zda chcete, aby výkon webu a testování částí v zátěžovém testu spustit jako 32bitové nebo 64bitové procesy.

        > [!NOTE]
        > Pro maximální flexibilitu byste měli zkompilovat váš výkon webu a načíst testovací projekty pomocí konfigurace **libovolného procesoru.** Pak můžete spustit na 32bitové i 64bitové agenty. Kompilace webovývýkon a zatížení testovací projekty pomocí **64bitové** konfigurace nenabízí žádnou výhodu.

25. (Nepovinné) Chcete-li omezit čas pro každý test spustit a jednotlivé testy, zvolte **Test časové limity.**

    1. Chcete-li přerušit spuštění testu při překročení časového limitu, vyberte **přerušit test, pokud celkový čas překročí,** a zadejte hodnotu pro tento limit.

    2. Chcete-li neuspět jednotlivé test při překročení časového limitu, vyberte **Označit jednotlivé test jako neúspěšný, pokud jeho doba provádění překročí**a zadejte hodnotu pro tento limit.

26. Přeskočit **jednotkový test**. Zátěžové testy tato nastavení nepoužívají.

27. Přeskočit **webový test**. Zátěžové testy tato nastavení nepoužívají.

28. Chcete-li uložit nastavení testu, zvolte **Uložit jako**. Do **názvu objektu**zadejte požadovaný název souboru .

## <a name="remove-a-test-settings-file-from-your-solution"></a>Odebrání souboru nastavení testu z řešení

Ve složce **Položky řešení** v **Průzkumníku řešení**klepněte pravým tlačítkem myši na nastavení testu, které chcete odebrat, a pak zvolte **Odebrat**.

Soubor nastavení testu je odebrán z vašeho řešení.

## <a name="see-also"></a>Viz také

- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md)
