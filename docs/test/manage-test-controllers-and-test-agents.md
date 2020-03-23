---
title: Správa kontrolerů testů a testovacích agentů
ms.date: 09/18/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efcc284291281b6e370cf51ddbe175faf8f1204c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584410"
---
# <a name="manage-test-controllers-and-test-agents"></a>Správa kontrolerů testů a testovacích agentů

Pokud chcete pomocí sady Visual Studio vzdáleně spouštět testy, distribuovat testy mezi více počítačů nebo spustit zátěžové testy, musíte nakonfigurovat soubor testovacího řadiče, testovacích agentů a nastavení testu. Toto téma popisuje, jak spravovat testovací řadiče a testovací agenty po jejich první instalaci a konfiguraci.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Pokud používáte Microsoft Test Manager ke spuštění testů v testovacích prostředích, můžete spravovat testovací řadiče a jejich agenty pomocí **Správce testovacího kontroléru** v **Centru testovacího prostředí** pro Správce testů společnosti Microsoft. Toto téma je použitelné pouze v případě, že ke spuštění testů používáte visual studio.

Informace o instalaci a konfiguraci testovacích agentů a testovacích řadičů pro spuštění testů v sadě Visual Studio naleznete v [tématu Konfigurace testovacích agentů a řadičů](../test/configure-test-agents-and-controllers-for-load-tests.md).

Chcete-li konfigurovat a sledovat testovací řadič a všechny registrované agenty, musíte mít soubor nastavení testu v testovacím projektu, který obsahuje testy, které chcete spustit. Otevřete soubor nastavení testu, zvolte **Role** a z rozbalovací nabídky pro pole **Řadič** zvolte **Spravovat testovací řadiče.**

Pro projekt zátěžového testu můžete také zvolit **Spravovat testovací řadiče** z nabídky **Zátěžový test.**

## <a name="add-a-test-agent-to-a-test-controller"></a>Přidání testovacího agenta do testovacího řadiče

Můžete chtít přidat testovacího agenta do jiného testovacího řadiče nebo budete muset přidat testovacího agenta do testovacího řadiče, který jste právě nainstalovali.

### <a name="to-add-a-test-agent-to-a-test-controller"></a>Přidání testovacího agenta do testovacího řadiče

1. Zvolte **Spustit** > **nástroj pro konfiguraci testovacího agenta**.

     Zobrazí se dialogové okno **Konfigurovat testovacího agenta.**

    > [!NOTE]
    > Chcete-li jej přidat do testovacího řadiče, musíte mít již nainstalovaného testovacího agenta. Další informace o instalaci testovacího agenta naleznete v [tématu Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

2. Zobrazí se dvě možnosti, jak lze spustit testovacího agenta:

   - **Služba**: Pokud není nutné spouštět automatizované testy, které interagují s plochou, například programové testy ui nebo vytvoření záznamu videa při spuštění testu, v části **Spustit testovacího agenta jako vyberte** **služba**. Testovací agent bude spuštěn jako služba. Zvolte **Další**.

      Nyní můžete zadat podrobnosti o uživateli při spuštění testovacího agenta jako služby.

      1. Zadejte jméno do **pole Uživatelské jméno**.

      2. Zadejte heslo do **pole Heslo**.

        |**Důležité informace o uživatelském účtu**|
        |-|
        |- Nulová hesla nejsou podporována pro uživatelské účty.|
        |- Pokud chcete použít kolekci IntelliTrace nebo emulaci sítě, musí být uživatelský účet členem skupiny Administrators.|
        |- Pokud uživatelské jméno agenta není ve službě agenta, pokusí se jej přidat, což vyžaduje oprávnění na testovacím řadiči.|
        |- Uživatel, který se pokouší použít testovací řadič, musí být v uživatelském účtu testovacího řadiče nebo nebude moci spustit testy proti kontroleru.|

   - **Interaktivní proces**: Pokud chcete spustit automatické testy, které musí pracovat s plochou, například kódované testy ui nebo vytvoření záznamu videa při spuštění testu, vyberte **interaktivní proces**. Testovací agent bude spuštěn jako interaktivní proces namísto služby.

      Na další stránce zadejte podrobnosti o uživateli při spuštění testovacího agenta jako proces a další možnosti.

      1. Zadejte jméno do **pole Uživatelské jméno**.

      2. Zadejte heslo do **pole Heslo**.

        > [!NOTE]
        > Pokud nakonfigurujete testovacího agenta tak, aby byl spuštěn jako interaktivní proces s jiným uživatelem, který není aktuálně aktivním uživatelem, je nutné restartovat počítač a přihlásit se jako tento jiný uživatel, aby bylo možné spustit agenta. Kromě toho nejsou pro uživatelské účty podporována nulová hesla. Pokud chcete použít kolekci IntelliTrace nebo emulaci sítě, musí být uživatelský účet členem skupiny Administrators.

      3. Chcete-li se ujistit, že počítač, který má testovacího agenta, může po restartování spustit testy, můžete nastavit, aby se počítač automaticky přihlašoval jako testovací agent. Vyberte **Možnost Přihlásit se automaticky**. Tím bude uživatelské jméno a heslo v registru ukládáno v zašifrované podobě.

      4. Chcete-li se ujistit, že je spořič obrazovky zakázán, protože by to mohlo narušit všechny automatizované testy, které musí pracovat s plochou, vyberte **možnost Zajistit zakázání spořiče obrazovky**.

        > [!WARNING]
        > Pokud se automaticky přihlásíte nebo zakážete spořič obrazovky, existují bezpečnostní rizika. Povolením automatického přihlášení povolíte ostatním uživatelům spuštění tohoto počítače a možnost používat účet, který se automaticky přihlásí. Pokud zakážete spořič obrazovky, počítač nemusí vyzvat uživatele k přihlášení k odemknutí počítače. To umožňuje komukoli přístup k počítači, pokud mají fyzický přístup k počítači. Pokud tyto funkce povolíte v počítači, měli byste se ujistit, že tyto počítače jsou fyzicky zabezpečené. Tyto počítače jsou například umístěny ve fyzicky zabezpečené laboratoři. (Pokud vymažete **funkci Ujistěte se, že je spořič obrazovky zakázán**, nepovolí te spořič obrazovky.)

3. Chcete-li zaregistrovat tohoto agenta u jiného testovacího řadiče, vyberte **registrovat s testovacím řadičem.** Zadejte název testovacího řadiče následovaný **:** a číslo portu, které používáte, v **části Zaregistrujte testovacího agenta pomocí následujícího testovacího řadiče**. Zadejte například **agent1:6901**.

    > [!NOTE]
    > Výchozí číslo portu je 6901.

4. Chcete-li změny uložit, zvolte **Použít nastavení**. Zavřete dialogové okno **Souhrn konfigurace** a potom zavřete nástroj **Konfigurace testovacího agenta**.

> [!WARNING]
> Pokud je agent aktuálně nakonfigurován pro spuštění na jiném testovacím řadiči, je nutné odebrat testovacího agenta z tohoto řadiče.

## <a name="remove-a-test-agent-from-a-test-controller"></a>Odebrání testovacího agenta z testovacího řadiče

Testovací agent musí být nastaven a offline stavu před jeho odebráním.

> [!NOTE]
> Tento postup nelze použít k odebrání agentů, kteří jsou registrováni na řadič jako součást testovacího prostředí. Chcete-li odebrat tyto agenty z řadiče, je nutné odebrat prostředí pomocí Správce testů společnosti Microsoft.

### <a name="to-remove-a-test-agent-from-a-test-controller"></a>Odebrání testovacího agenta z testovacího řadiče

1. Pokud testovací řadič není registrován v projektu, postupujte takto.

    1. V Sadě Visual Studio otevřete soubor nastavení testu pro testovací projekt, zvolte **Role** a zvolte **Spravovat testovací řadiče** z rozevíracího seznamu pro pole **Řadič.**

         Zobrazí se dialogové okno **Spravovat testovací řadič.**

    2. Do rozevíracího seznamu **Řadič** zadejte název počítače, ve kterém jste nastavili testovací řadič. Pokud jste dříve spravovali konkrétní testovací řadič, můžete vybrat název ze seznamu.

    3. V podokně **Agenti** vyberte název testovacího agenta. Pokud je agent stále online, zvolte **Offline.** Chcete-li ji odebrat, zvolte **Odebrat**.

        > [!NOTE]
        > Odebrání testovacího agenta pouze disassociates z testovacího řadiče. Chcete-li testovacího agenta zcela odinstalovat, použijte ovládací panel **Programy a funkce** v počítači testovacího agenta.

2. Pokud je testovací řadič registrován v projektu, odeberte agenta pomocí Správce testů společnosti Microsoft.

## <a name="change-the-settings-for-a-test-agent"></a>Změna nastavení testovacího agenta

Stav testovacího agenta může být některá z následujících hodnot:

|Status|Popis|
|-|-----------------|
|Běžecký test|Spuštění testů|
|Připraveno|K dispozici pro spuštění testů nebo shromažďování dat a diagnostiky|
|Offline|Není k dispozici pro spuštění testů nebo shromažďování dat a diagnostiky|
|Odpojen|Testovací agent není spuštěn.|

Můžete změnit stav a další nastavení testovacího agenta pomocí následujících postupů.

### <a name="to-change-the-settings-of-a-test-agent"></a>Změna nastavení testovacího agenta

> [!NOTE]
> Pokud je testovací agent registrován na testovací řadič, který je registrován v projektu, změňte nastavení ve Správci testů společnosti Microsoft.

1. Chcete-li nakonfigurovat a sledovat testovací řadič a všechny registrované agenty pro zátěžový test, zvolte nabídku **Zátěžový test** v sadě Visual Studio a pak zvolte **Spravovat řadiče testu**. Pro všechny ostatní testy otevřete soubor nastavení testu pro testovací projekt v sadě Visual Studio, zvolte **Role** a zvolte **Spravovat testovací řadiče** z rozbalovací nabídky pro pole **Řadič.**

   Otevře se dialogové okno **Spravovat testovací řadič.**

1. Vyberte název testovacího řadiče, jehož testovací agenty chcete změnit v seznamu testovacího řadiče. Pokud se testovací řadič v seznamu nezobrazí, zkontrolujte, zda je testovací řadič správně zaregistrován. Další informace naleznete v následujícím postupu o konfiguraci testovacího řadiče.

1. (Nepovinné) V podokně **Testovací agenti** vyberte počítač testovacího agenta, pro který chcete změnit vlastnosti.

1. Zvolte **Properties** (Vlastnosti).

1. Podle potřeby změňte následující vlastnosti testovacího agenta:

|Vlastnost testovacího agenta|Popis|
|-|-----------------|
|**Vážení**|Používá se k distribuci zatížení při použití testovacích agentů s různými úrovněmi výkonu. Například testovací agent s váhou 100 obdrží dvakrát větší zatížení jako testovací agent s váhou 50.|
|**Přepínání IP adres**|Slouží ke konfiguraci přepínání IP adres. Přepínání IP umožňuje testovacímu agentovi odesílat požadavky na server pomocí rozsahu adres IP. To simuluje volání, které pocházejí z různých klientských počítačů.<br /><br /> Přepínání IP je důležité, pokud váš zátěžový test přistupuje k webové farmě. Většina vykladačů zatížení vytvořit spřažení mezi klientem a konkrétní webový server pomocí IP adresy klienta. Pokud všechny požadavky vypadají, jako by pocházely z jednoho klienta, nevyvažovač zatížení nevyvažuje zatížení. Chcete-li získat správné vyrovnávání zatížení ve webové farmě, ujistěte se, že požadavky pocházejí z řady IP adres. **Poznámka:**  Můžete zadat síťový adaptér nebo použít **(Všechny nepřiřazené)** automaticky vybrat ten, který se právě nepoužívá. <br /><br /> Chcete-li použít funkci přepínání IP, musí být služba Test Agent sady Visual Studio spuštěna jako uživatel ve skupině Administrators pro tento počítač agenta. Tento uživatel je vybrán během instalace agenta, ale lze jej změnit úpravou vlastností služby a restartováním.<br /><br /> Chcete-li ověřit, zda přepínání IP funguje správně, povolte protokolování služby IIS na webovém serveru, ověřte pomocí funkce protokolování služby IIS, zda požadavky pocházejí z nakonfigurovaných adres IP.|
|**Atributy**|Sada párů název/hodnota, které lze použít při výběru testovacího agenta. Test může například vyžadovat konkrétní operační hod. Atributy můžete přidat na kartě **Role** v souboru nastavení testu a lze je použít k výběru testovacího agenta, který má odpovídající atributy. Pokud chcete spustit test na více počítačích, vytvořte atribut v roli nastavení testu, který je nakonfigurován pro spuštění testů, a pak nakonfigurujte odpovídající atribut u každého testovacího agenta, který chcete v této roli použít. **Poznámka:**  Toto nastavení je k dispozici pouze pro testovací agenty, kteří jsou registrováni s testovacím řadičem, který není registrován v projektu, protože tyto atributy se používají pouze v nastavení testu pro sady Visual Studio.|

Změny atributů testu agenta a atributu testovacího agenta vstoupí v platnost okamžitě, ale nemají vliv na testy, které jsou spuštěny. Rozsah IP adres se projeví po restartování testovacího řadiče.

(Nepovinné) Chcete-li změnit stav testovacího agenta, vyberte agenta v seznamu a pak vyberte akci z dostupných voleb na základě aktuálního stavu agenta.

> [!NOTE]
> Pokud testovací agent běží jako proces, můžete spravovat stav testovacího agenta z ikony oznamovací oblasti, která běží v počítači, ve kterém je nainstalován testovací agent. To ukazuje stav testovacího agenta. Agenta můžete spustit, zastavit nebo restartovat, pokud je spuštěn jako proces pomocí tohoto nástroje.

## <a name="configure-a-test-controller"></a>Konfigurace testovacího řadiče

Chcete-li nakonfigurovat testovací řadič, musíte použít **nástroj pro konfiguraci řadiče týmového testu**. Při konfiguraci testovacího řadiče můžete zaregistrovat testovací řadič s jinou kolekcí projektu nebo zrušit registraci testovacího řadiče z kolekce projektu.

Pokud chcete zaregistrovat testovací řadič s kolekcí projektů Team Foundation Server, musí být účet, který používáte pro službu testovacího řadiče, členem skupiny Účty testovací služby kolekce projektů pro kolekci projektů nebo účet který používáte ke spuštění nástroje konfigurace testovacího řadiče, musí být správce množin.

> [!NOTE]
> Pokud zrušíte registraci testovacího řadiče z kolekce projektu, který má existující prostředí v kolekci projektu, prostředí jsou stále udržovány, pokud jste přesunuli tuto kolekci projektu a znovu zaregistrujete testovací řadič do této přesunuté kolekce projektu.

### <a name="to-configure-a-test-controller"></a>Konfigurace testovacího řadiče

1. Chcete-li nástroj kdykoli překonfigurovat, zvolte **spustit** > **nástroj pro konfiguraci řadiče testovacího provozu**.

     Zobrazí se dialogové okno **Konfigurovat testovací řadič.**

2. Vyberte uživatele, který chcete použít jako přihlašovací účet pro službu testovacího řadiče.

    > [!NOTE]
    > Nulová hesla nejsou pro uživatelské účty podporována.

4. (Nepovinné) Pokud nechcete používat testovací řadič s testovacím prostředím, ale pouze ke spuštění testů z aplikace Visual Studio, **zrušte zaškrtnutí zrušte seznam registrut testovacího řadiče s kolekcí týmových projektů**.

5. (Nepovinné) Chcete-li nakonfigurovat testovací řadič pro zátěžové testování, vyberte **konfigurovat testovací řadič pro zátěžové testování**. Zadejte instanci serveru SQL Server v části **Vytvořit databázi výsledků zátěžového testu v následující instanci serveru SQL Server**.

> [!NOTE]
> Další informace o snímání testovacích řadičů naleznete v [tématu Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

## <a name="manage-your-agents-when-you-run-your-tests-with-a-test-controller"></a>Správa agentů při spuštění testů pomocí testovacího řadiče

Když přidáte role pro vaši aplikaci do nastavení testu pro Visual Studio, můžete přidat vlastnosti agenta pro každou z vašich rolí. To určuje, které testovací agenti jsou k dispozici pro tuto roli. Při spuštění testů pomocí těchto nastavení testu, řadič testu, který je vybrán pro nastavení testu určuje dostupnost požadovaných agentů. Jedná se o následující situace, které mohou nastat při určení dostupnosti agenta:

- Pro roli, která musí spustit testy, není k dispozici žádný agent. Testy nelze spustit. Můžete provést jednu z následujících akcí a potom testy znovu spustit:

  - Můžete počkat agenta k dispozici pro tuto roli ke spuštění testů.

  - Pokud existují agenti, které jsou v offline, které lze použít pro tuto roli, můžete restartovat agenta tak, aby byl k dispozici.

  - Do testovacího řadiče můžete přidat jiného agenta se správnými vlastnostmi agenta pro tuto roli.

  - Vlastnosti agenta pro tuto roli můžete změnit v nastavení testu a povolit další agenty, které chcete použít.

- Pro jednu nebo více rolí, které spouštějí adaptéry diagnostických dat, není k dispozici žádný agent. Testy lze spustit, ale adaptér diagnostických dat nelze spustit. Testy můžete spustit bez adaptéru diagnostických dat nebo můžete provést jednu z následujících akcí a znovu spustit testy:

  - Můžete počkat na agenta, aby byly k dispozici pro tyto role.

  - Pokud existují agenti, které jsou v režimu offline, které lze použít pro tuto roli, je nutné změnit stav agenta na online z **Spravovat testovací kontroler** v nabídce **Test.** Kromě toho bude pravděpodobně nutné restartovat agenta, pokud byl odpojen od řadiče.

  - Ověřte, zda nejsou všichni agenti, které budete potřebovat pro tento test, nejsou zaneprázdněni spuštěním testů. Můžete zkontrolovat stav všech agentů z **Spravovat řadič testu** v nabídce **Test.**

  - Do testovacího řadiče můžete přidat jiného agenta se správnými vlastnostmi agenta pro roli.

  - Můžete změnit vlastnosti agenta pro roli v nastavení testu povolit další agenty, které chcete použít.

## <a name="load-tests-from-delay-signed-assemblies"></a>Zátěžové testy ze sestav podepsaných zpožděním

Testovací řadič a testovací agenti mohou zatížit pouze testovací sestavení, která jsou silně podepsaná sestavení nebo nepodepsaná sestavení. Některá testovací sestavení jsou podepsána zpožděním, protože potřebují mít přístup do výrobních sestavení pro aplikaci. Tato sestavení však nejsou silně podepsány, protože jsou pouze testovací sestavení a nejsou distribuovány. Tato sestavení nelze načíst, protože jsou podepsána zpožděním, proto je nutné zakázat ověření silného názvu pro tato sestavení na všech počítačích, kde bude sestava načtena včetně testovacího řídicího zařízení. Chcete-li zakázat ověření podepsané zpožděním, použijte *program sn.exe*. Token veřejného klíče sestavení podepsaného zpožděním, pro které je požadováno ověření silného názvu, může být také nutné zahrnout.

Pomocí *nástroje Sn.exe* (nástroj silný název) zakažte ověření podepsané zpožděním.

Tím se zakáže ověření silného názvu pouze pro zadané sestavení v počítači, ve kterém spustíte příkaz. To lze provést pouze v případě, že máte dostatečná oprávnění.

Po dokončení testu znovu povolte ověření zpožděného podepisování pomocí příkazu *SN.exe.*

Doporučeným způsobem, jak zakázat a znovu povolit ověřování podepisování, je použití příkazů *SN.exe* ve skriptech. Ověření můžete zakázat v instalačním skriptu a znovu povolit ověření ve skriptu pro vyčištění.

## <a name="see-also"></a>Viz také

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
