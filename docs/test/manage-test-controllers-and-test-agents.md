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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75584410"
---
# <a name="manage-test-controllers-and-test-agents"></a>Správa kontrolerů testů a testovacích agentů

Pokud chcete použít Visual Studio pro vzdálené spuštění testů, distribuci testů mezi více počítačů nebo spuštění zátěžových testů, je nutné nakonfigurovat testovací kontrolér, testovací agenty a soubor nastavení testu. Toto téma popisuje, jak spravovat testovací kontroléry a testovací agenty po instalaci a konfiguraci poprvé.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Pokud používáte Microsoft Test Manager ke spuštění testů v testovacím prostředí, můžete spravovat testovací kontroléry a jejich agenty pomocí **správce řadičů testů** v **centra testovacích prostředí** pro nástroj Microsoft Test Manager. Toto téma platí pouze v případě, že používáte sadu Visual Studio ke spuštění testů.

Informace o tom, jak instalace a konfigurace testovacích agentů a řadičů testu pro testy v sadě Visual Studio najdete v tématu [konfigurace testovacích agentů a kontrolérů](../test/configure-test-agents-and-controllers-for-load-tests.md).

Ke konfiguraci a sledování testovacího řadiče a všech registrovaných agentů, musí mít soubor nastavení testu do testovacího projektu, který obsahuje testy, které chcete spustit. Otevřete soubor nastavení testu, zvolte **Role** a zvolte **spravovat řadič testu** z rozevíracího seznamu pro **řadič** pole.

Pro projekt zátěžového testu můžete také zvolit **spravovat řadič testu** z **zátěžový Test** nabídky.

## <a name="add-a-test-agent-to-a-test-controller"></a>Přidat testovacího agenta do testovacího kontroléru

Můžete chtít přidat testovacího agenta na jiný kontroler testů nebo bude pravděpodobně nutné přidat testovacího agenta do testovacího kontroléru, který jste právě nainstalovali.

### <a name="to-add-a-test-agent-to-a-test-controller"></a>Chcete-li přidat testovacího agenta do testovacího kontroléru

1. Zvolte **Start** > **konfigurační nástroj agenta testu**.

     **Konfigurace testovacího agenta** se zobrazí dialogové okno.

    > [!NOTE]
    > Musíte mít testovacího agenta už nainstalovaná ho přidat do testovacího kontroléru. Další informace o tom, jak nainstalovat testovacího agenta, najdete v části [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

2. Máte na výběr dvě možnosti, jak spustit testovacího agenta:

   - **Služba**: Pokud nemáte spuštěny automatické testy, které spolupracují s plochou, jako jsou kódované testy uživatelského rozhraní nebo pořizování záznamu, když test běží, v části videa **spustit testovacího agenta jako**vyberte **služby**. Testovací agent bude spuštěn jako služba. Zvolte **Další**.

      Nyní můžete zadat podrobnosti o uživateli, když se testovací agent spustí jako služba.

      1. Zadejte název do **uživatelské jméno**.

      2. Zadejte heslo **heslo**.

        |**Informace o důležitých uživatelském účtu**|
        |-|
        |-Null hesla nejsou pro uživatelské účty podporována.|
        |– Pokud chcete použít IntelliTrace collector nebo emulaci sítě, musí být uživatelský účet členem skupiny Administrators.|
        |– Pokud je uživatelské jméno agenta není ve službě agenta, pokusí se ho přidat, což vyžaduje oprávnění testovacího kontroléru.|
        |-Uživatel, který se pokouší použít testovací kontrolér musí být účet uživatelé testovacího kontroléru nebo se nebude moci spouštět v kontroléru testy.|

   - **Interaktivní proces**: Pokud chcete spustit automatizované testy, které musí spolupracovat s plochou, jako jsou kódované testy uživatelského rozhraní nebo vytvoření záznamu videa, když test běží, vyberte **interaktivní proces**. Testovací agent bude spuštěn jako interaktivní proces místo jako služba.

      Na další stránce zadejte podrobnosti o uživateli, když testovací agent spustí jako proces a další možnosti.

      1. Zadejte název do **uživatelské jméno**.

      2. Zadejte heslo **heslo**.

        > [!NOTE]
        > Při konfiguraci testovacího agenta ke spuštění jako interaktivní proces u jiného uživatele, který není aktuálně aktivních uživatelů, musíte restartovat počítač a přihlaste se jako tento jiný uživatel, abyste mohli spustit agenta. Kromě toho hesla s hodnotou null nejsou pro uživatelské účty podporována. Pokud chcete použít IntelliTrace collector nebo emulaci sítě, musí být uživatelský účet členem skupiny Administrators.

      3. Pokud chcete mít jistotu, že počítač, který s testovacím agentem můžete spouštět testy po restartování, můžete nastavit počítač pro automatické přihlášení jako testovací agent použití. Vyberte **automatické přihlášení**. Toto uloží uživatelské jméno a heslo v zašifrované podobě v registru.

      4. Chcete-li mít jistotu, že spořič obrazovky je zakázán, protože to může narušit jakékoli automatizované testy, které musí spolupracovat s plochou, vyberte **Ujistěte se, že spořič obrazovky je zakázán**.

        > [!WARNING]
        > Pokud automatické přihlášení nebo zakázání spořiče obrazovky, vznikají bezpečnostní rizika. Povolením automatického protokolování na můžete povolit ostatním uživatelům spustit tento počítač a použít účet, který se přihlásí automaticky. Pokud zakážete spořič obrazovky, počítač nemusí vyzvat uživatele k přihlášení k odemknutí počítače. Umožňuje všem uživatelům přístup k počítači, pokud mají fyzický přístup k počítači. Pokud povolíte tyto funkce v počítači, by měl Ujistěte se, že tyto počítače byly fyzicky zabezpečeny. Například tyto počítače jsou umístěny ve fyzicky zabezpečeném prostředí. (Pokud zrušíte výběr **Ujistěte se, že spořič obrazovky je zakázán**, nepovolíte spořič obrazovky.)

3. Chcete-li zaregistrovat tohoto agenta s jiný kontroler testů, vyberte **zaregistrovat u řadiče testů.** Zadejte název řadiče testu následovaný **:** a číslo portu, který používáte v **registraci testovacího agenta s tímto řadičem testu**. Zadejte například **agent1: 6901**.

    > [!NOTE]
    > Výchozí číslo portu je 6901.

4. Chcete-li uložit změny, zvolte **použít nastavení**. Zavřete **souhrnné informace o konfiguraci** dialogové okno a potom zavřete **Test Agent Configuration Tool**.

> [!WARNING]
> Pokud agent je nakonfigurován pro spuštění v jiném testovacím kontroléru, je třeba odebrat testovacího agenta z tohoto kontroléru.

## <a name="remove-a-test-agent-from-a-test-controller"></a>Odebrat testovacího agenta z řadiče testů

Testovací agent musí být nastavena do stavu offline, než je možné odebrat.

> [!NOTE]
> Nelze tímto postupem můžete odebrat agenty, které jsou registrovány k řadiči jako součást testovacího prostředí. Chcete-li tyto agenty odebrat z kontroleru, je třeba odebrat prostředí pomocí nástroje Microsoft Test Manager.

### <a name="to-remove-a-test-agent-from-a-test-controller"></a>Chcete-li odebrat testovacího agenta z řadiče testů

1. Pokud testovací kontrolér není zaregistrován s projektem, postupujte podle těchto kroků.

    1. Ze sady Visual Studio otevřete soubor nastavení testu pro testovací projekt, zvolte **Role** a zvolte **spravovat řadič testu** z rozevíracího seznamu pro **řadič** pole.

         **Spravovat testovací Kontrolér** se zobrazí dialogové okno.

    2. V **řadič** rozevíracího seznamu, zadejte název počítače, na kterém jste vytvořili testovací kontrolér. Pokud jste spravovali konkrétní testovací kontrolér dříve, můžete vybrat jméno ze seznamu.

    3. V **agentů** podokně, vyberte název testovacího agenta. Pokud je agent stále online, vyberte **Offline.** Chcete-li ho odebrat, zvolte **odebrat**.

        > [!NOTE]
        > Odstranění testovacího agenta pouze zruší přidružení z testovacího kontroléru. Chcete-li testovacího agenta zcela odinstalovat, použijte **programy a funkce** ovládacích panelech v počítači testovacího agenta.

2. Pokud testovací kontrolér je zaregistrován s projektem, odeberte agenta pomocí nástroje Microsoft Test Manager.

## <a name="change-the-settings-for-a-test-agent"></a>Změnit nastavení pro testovacího agenta

Stav testovacího agenta může být jedna z následujících hodnot:

|Stav|Popis|
|-|-----------------|
|Spouštění testů|Spouštění testů|
|Připraven|K dispozici pro spuštění testů nebo sběr dat a diagnostiky|
|Offline|Není k dispozici pro spuštění testů nebo sběr dat a diagnostiky|
|Odpojení|Testovací agent není spuštěn.|

Stav a další nastavení pro testovacího agenta pomocí následujících postupů můžete změnit.

### <a name="to-change-the-settings-of-a-test-agent"></a>Chcete-li změnit nastavení testovacího agenta

> [!NOTE]
> Pokud testovací agent registrován do testovacího kontroléru, který je zaregistrován s projektem, změňte nastavení v nástroji Microsoft Test Manager.

1. Ke konfiguraci a sledování testovacího řadiče a všech registrovaných agentů pro zátěžový test, zvolte **zátěžový Test** nabídky v sadě Visual Studio a klikněte na tlačítko **spravovat řadič testu**. Pro všechny jiné testy, otevřete soubor nastavení testu pro testovací projekt v sadě Visual Studio, zvolte **Role** a zvolte **spravovat řadič testu** z rozevíracího seznamu pro **řadič**pole.

   **Spravovat testovací Kontrolér** zobrazí se dialogové okno.

1. Vyberte název řadiče testu, jehož agenty testu chcete změnit v seznamu řadiče testu. Pokud testovací kontrolér nezobrazí v seznamu, zkontrolujte, že je testovací kontrolér správně zaregistrován. Další informace najdete v tématu postup týkající se konfigurace testovacího kontroléru.

1. (Volitelné) V **testovací agenti** podokně, vyberte počítači testovacího agenta, pro kterou chcete změnit vlastnosti.

1. Zvolte **vlastnosti**.

1. Změňte následující vlastnosti testovacího agenta podle potřeby:

|Vlastnost testovacího agenta|Popis|
|-|-----------------|
|**Vážení**|Slouží k distribuci zatížení při použití testovacích agentů s různými úrovněmi výkonnosti. Například testovací agent s vážením 100 obdrží dvakrát zatížení než testovací Agent s vážením 50.|
|**Přepínání IP**|Slouží ke konfiguraci přepínání IP. Přepínání protokolu IP umožňuje agentovi testu odesílání požadavků na server pomocí rozsahu IP adres. To simuluje volání, které pocházejí z různých klientských počítačů.<br /><br /> Přepínání IP je důležité, pokud vaše zkušební zatížení přistupuje k webové farmy. Většina Vyrovnávání zatížení vytvoří spřažení mezi klientem a konkrétní webový server s použitím IP adresy klienta. Pokud všechny požadavky zdá, že pocházejí z jednoho klienta, nebude nástroj pro vyrovnávání zatížení vyrovnávat zatížení. K dosažení dobré rovnováhy zatížení ve webové farmě, ujistěte se, že požadavky pocházejí z rozsahu IP adres. **Poznámka:** můžete určit síťový adaptér, nebo použijte **(všechny nepřiřazené)** automaticky vybrat jeden, který není aktuálně používán. <br /><br /> Pokud chcete použít funkci přepínání IP, musí být spuštěna služba Visual Studio Test Agent jako uživatel ve skupině Administrators pro daný počítač agenta. Tento uživatel je vybrán během instalace agenta, ale můžete změnit úpravou vlastností služby a restartováním.<br /><br /> Pokud chcete ověřit, že přepínání IP pracuje správně, povolit protokolování na webovém serveru služby IIS, ověřte, že požadavky pocházejí z IP adres, které jste nakonfigurovali pomocí funkce protokolování služby IIS.|
|**Atributy**|Sada párů název/hodnota, které lze použít ve výběru agenta testu. Test může například vyžadovat konkrétní operační systém. Můžete přidat atributy na **role** kartu vašeho testovacího souboru s nastavením a slouží k výběru testovacího agenta, který má shodné atributy. Pokud chcete spustit test ve více počítačích, vytvořte atribut v roli nastavení testu, který je nakonfigurován ke spuštění testů a potom nakonfigurujte odpovídající atribut na každého testovacího agenta, který chcete použít v této roli... **Poznámka:** toto nastavení dostupná jenom pro testovací agenty, které jsou registrované pomocí testovacího kontroléru, který není registrovaný k projektu, protože tyto atributy se používají v nastavení testu pro sadu Visual Studio.|

Testovací agent hmotnosti a atributů testovacího agenta změny vejdou v platnost okamžitě, ale nemají vliv na zkoušky, které jsou spuštěny. Rozsah adres IP se projeví po restartování řadiče testu.

(Volitelné) Chcete-li změnit stav testovacího agenta, vyberte agenta v seznamu a pak vyberte akci z dostupných voleb na základě aktuálního stavu agenta.

> [!NOTE]
> Pokud testovací agent je spuštěn jako proces, můžete spravovat stav testovacího agenta z ikony na oznamovací oblasti, na kterém běží na počítači, kde je nainstalován testovací agent. To zobrazuje stav testovacího agenta. Můžete spustit, zastavit nebo restartovat agenta, pokud je spuštěn jako proces, který používá tento nástroj.

## <a name="configure-a-test-controller"></a>Konfigurovat kontroler testů

Ke konfiguraci testovacího kontroléru, je nutné použít **Team Test Controller Configuration Tool**. Při konfiguraci testovacího kontroléru, můžete registrovat testovací kontrolér s různých projektech kolekce nebo zrušit registraci testovacího kontroléru z kolekce projektu.

Pokud chcete registrovat testovací kontrolér s vaší kolekcí projektu Team Foundation Server, účet, který používáte pro službu kontroleru testů musí být členem skupiny účtů služeb testu kolekce projektů pro kolekci projektu nebo účet můžete použít ke spuštění nástroje konfigurace testovacího kontroléru, musí být správcem kolekce projektu.

> [!NOTE]
> Pokud můžete zrušit registraci testovacího kontroléru z kolekce projektu, který má stávající prostředí v kolekci projektu, prostředí jsou stále zachována, pokud jste přesunuli tuto kolekci projektu a znovu registrovat testovací kontrolér na tuto kolekci přesunutý projektu.

### <a name="to-configure-a-test-controller"></a>Chcete-li konfigurovat řadič testu

1. Chcete-li spustit nástroj, který kdykoli změnit konfiguraci řadiče testu, zvolte **Start** > **Test Controller Configuration Tool**.

     **Nakonfigurovat testovací Kontrolér** se zobrazí dialogové okno.

2. Vyberte uživatele, který chcete použít jako přihlašovací účet pro službu řadiče testu.

    > [!NOTE]
    > Hesla s hodnotou Null nejsou pro uživatelské účty podporována.

4. (Volitelné) Pokud nechcete použít řadič testu s testovacím prostředím, ale pouze ke spouštění testů ze sady Visual Studio, zrušte **zaregistrovat řadič testu u kolekce týmových projektů**.

5. (Volitelné) Chcete-li nakonfigurovat řadič testů pro zátěžové testování, vyberte **konfigurovat řadič testu pro testování zatížení**. Zadejte instanci systému SQL Server v části **databázi vytvořit výsledky zátěžového testu následující instanci serveru SQL Server**.

> [!NOTE]
> Další informace o řešení potíží řadiče testů, naleznete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

## <a name="manage-your-agents-when-you-run-your-tests-with-a-test-controller"></a>Správa agentů při spuštění testů pomocí testovacího kontroléru

Při přidání role pro vaši aplikaci do nastavení testu pro sadu Visual Studio můžete přidat vlastnosti agenta pro všechny své role. Určuje, kteří testovací agenti jsou k dispozici pro tuto roli. Při spuštění testů pomocí těchto nastavení testu, testovací kontrolér, který je vybrán pro nastavení testu, zjišťuje dostupnost požadovaných agentů. Jedná se o následující situace, které může dojít, když je určena dostupnost agenta:

- Pro roli, která se musí spustit testy k dispozici není žádný agent. Testy nelze spustit. Můžete provést jednu z následujících akcí a opětovně spusťte vaše testy:

  - Můžete počkat, až agent k dispozici pro tuto roli pro spuštění testů.

  - Pokud existují agenti, kteří jsou v režimu offline, který můžete použít pro tuto roli, můžete restartovat agenta tak, aby byly k dispozici.

  - Přidat jiného agenta se správnými vlastnostmi pro tuto roli do testovacího kontroléru.

  - Můžete změnit vlastnosti agenta pro tuto roli v nastavení testu pro povolení jiných agentů, které chcete použít.

- Pro jednu nebo víc rolí, na kterých běží adaptéry diagnostických dat k dispozici není žádný agent. Testy můžete spustit, ale adaptér diagnostických dat nelze spustit. Můžete spustit testy bez adaptéru diagnostických dat, nebo můžete provést jednu z následujících akcí a znovu spustit testy:

  - Můžete počkat, až agent k dispozici pro tyto role.

  - Pokud existují agenti, kteří jsou v režimu offline, který můžete použít pro tuto roli, musíte změnit stav agenta na online z **spravovat testovací Kontrolér** na **Test** nabídky. Kromě toho budete muset restartovat agenta, pokud byl odpojen z kontroleru.

  - Ověřte, že všechny agenty, které můžete potřebovat pro tento testovací běh není zaneprázdněn spouštěním testů. Můžete zkontrolovat stav jakýchkoli agentů v **spravovat testovací Kontrolér** na **Test** nabídky.

  - Přidat jiného agenta se správnými vlastnostmi pro tuto roli do testovacího kontroléru.

  - Můžete změnit vlastnosti agenta pro roli v nastavení testu pro povolení jiných agentů, které chcete použít.

## <a name="load-tests-from-delay-signed-assemblies"></a>Načíst testy ze sestavení se zpožděným podpisem

Testovací kontrolér a testovací agenti mohou načítat pouze zkušební sestavení, které jsou silně podepsaná nebo nepodepsaná sestavení. Některé zkušební sestavení jsou podepsané se zpožděním protože potřebují mít přístup k produkčním sestavám aplikace. Tyto sestavení však nejsou podepsány silně protože jsou pouze zkušebními sestaveními a nejsou distribuovány. Tato sestavení nelze načíst, protože jsou podepsané se zpožděním, takže je potřeba zakázat ověřování silných názvů pro tato sestavení ve všech počítačích, kde bude sestavení načteno včetně počítače testovacího kontroléru. Chcete-li zakázat ověření podpisu se zpožděním, použijte *sn.exe*. Token veřejného klíče sestavení se zpožděným podpisem, pro které je požadováno přeskočení ověřování silných názvů také potřebovat mají být zahrnuty.

Použití *Sn.exe* (nástroj Strong Name) k zakázání ověření podpisu se zpožděním.

To zakáže ověřování silných názvů pro zadané sestavení, na počítači, na kterém jste příkaz spustili. To lze provést pouze v případě, že máte dostatečná oprávnění.

Po dokončení běhu testu, znovu povolte ověření zpožděného podepisování pomocí *SN.exe* příkazu.

Doporučený postup zakázání a opětovného povolení ověření podpisu je použití *SN.exe* příkazy ve skriptech. Můžete vypnout ověřování v instalačním skriptu a znovu povolit ověření ve skriptu vyčištění.

## <a name="see-also"></a>Viz také:

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
