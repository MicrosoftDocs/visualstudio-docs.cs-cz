---
title: Parametry spuštění zátěžového testu
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, run settings
ms.assetid: de10dabb-02ed-403b-9e6f-0b735524988c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 9b0123ba4e6f9565cc31f63a23bb0be0b5bee344
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895493"
---
# <a name="load-test-run-settings-properties"></a>Vlastnosti nastavení běhu zátěžového testu

Parametry spuštění zátěžového testu určují celou řadu dalších nastavení, včetně doby trvání testu, úroveň podrobností shromažďování výsledků a sady čítačů, které se shromažďují za běhu testu. Pro každý zátěžový test lze vytvořit a uložit několik parametrů spuštění a následně při spouštění testu zvolit jedno konkrétní nastavení. Při vytváření vašeho testu zatížení pomocí doplňuje počáteční parametry spuštění zátěžového testu **nového Průvodce zátěžovým testem**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Následující tabulky popisují různé vlastnosti parametrů spuštění zátěžového testu. Tyto vlastnosti lze upravit tak, aby splňovaly konkrétní požadavky zátěžového testu.

Další informace najdete v tématu [konfigurovat zátěžovým testem nastavení](../test/configure-load-test-run-settings.md).

## <a name="general-properties"></a>Obecné vlastnosti

|Vlastnost|Definice|
|-|----------------|
|**Popis**|Popis nastavení spuštění.|
|**Maximální chyby podle typu**|Maximální počet chyb na typ lze pro zátěžový test uložit.<br /><br /> Toto číslo můžete zvýšit, pokud je nutné, ale to se také zvýší velikost a doba zpracování výsledku zátěžového testu.|
|**Zaznamenaných maximální požadavků URL**|Maximální počet testu výkonnosti webu jedinečný požadavek adresy URL, na kterém se má ohlásit výsledky v zátěžovém testu.<br /><br /> Toto číslo můžete zvýšit, pokud je nutné, ale to se také zvýší velikost a doba zpracování výsledku zátěžového testu.|
|**Maximální mezních hodnot**|Maximální počet překročení mezních hodnot lze pro zátěžový test uložit.<br /><br /> Toto číslo můžete zvýšit, pokud je nutné, ale to se také zvýší velikost a doba zpracování výsledku zátěžového testu.|
|**Testy jednotek v aplikační doméně**|Logická hodnota, která určuje, zda každá jednotka testovací sestavení poběží v samostatné doméně aplikace, pokud zátěžový test obsahuje testy jednotek. Ve výchozím nastavení má hodnotu True.<br /><br /> Pokud testování částí nevyžadují samostatnou aplikační domény nebo app.config souboru fungovat správně, testování částí může pracovat rychleji pomocí nastavení hodnoty této vlastnosti `False`.|
|**Jméno**|Název nastavení Spustit jako se zobrazuje v **parametrů běhu** uzlu **editoru zátěžových testů**.|
|**Úroveň validace**|Definuje ověřovací pravidlo, které poběží v rámci zátěžového testu na nejvyšší úrovni. Ověřovací pravidla jsou spojeny s požadavky testu výkonnosti webu. Každý ověřovací pravidlo má úroveň přidruženého ověřování: **vysokou**, **střední**, nebo **nízká**. Nastavení spuštění zátěžového testu určí, které ověření pravidla se spustí při spuštění testu výkonnosti webu v zátěžovém testu. Například pokud spustíte nastavení nastavená na **střední**, označení všech ověřovacích pravidel **střední**, nebo **nízká** se spustí.|

## <a name="logging-properties"></a>Vlastnosti protokolování

|Vlastnost|Definice|
|-|----------------|
|**Maximální počet protokolů testu**|Určuje maximální počet protokolů testu lze pro zátěžový test uložit. Při zadání hodnoty pro maximální počet protokolů testu je dosaženo, zátěžového testu se zastaví shromažďování protokolů. Proto se v protokolech neshromáždí na začátku testu není konec. Zátěžový test bude nadále spouštět, dokud se nedokončí.|
|**Pro dokončené testy uložit frekvenci protokolování**|Určuje frekvenci, s jakou se zapíše protokol testu. Číslo označuje, že jedno vzdálené každý zadaný počet testů, které se uloží do protokolu testu. Například zadáte hodnotu 10 Určuje, že desetinu, dvacáté, třicetiny a tak dále, se zapíšou do protokolu testu. Nastavením této hodnoty na 0 určuje, že se uloží protokolů testu.|
|**Selhání testu uložit protokol**|Logická hodnota, která určuje, zda-li ukládání protokolů testování selhání testu v rámci zátěžového testu. Výchozí hodnota je `True`.<br /><br /> Další informace najdete v tématu [postupy: určení, zda jsou selhání testu ukládána do protokolů testování](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|

 Další informace najdete v tématu [nastavení upravit zátěžového testu protokolování](../test/modify-load-test-logging-settings.md).

## <a name="results-properties"></a>Vlastnosti výsledků

|Vlastnost|Definice|
|-|----------------|
|**Typ úložiště**|Způsob, jak ukládat čítačů výkonu, které jsou získány v rámci zátěžového testu. Možnosti jsou následující:<br /><br /> -   **Databáze** -vyžaduje databázi SQL, který má **Store výsledků testu zatížení**.<br />-   **Žádný**.|
|**Úložiště podrobností časování**|To se dá určit podrobnosti, které se budou ukládat v **Store výsledků testu zatížení**. K dispozici jsou tři hodnoty:<br /><br /> -   **AllIndividualDetails** – shromažďování a ukládání jednotlivé hodnoty časování pro každý test, transakci a stránku, které se spouštějí nebo vydanou v průběhu zátěžového testu v **Store výsledků testu zatížení**. Je vyžadován, pokud máte v úmyslu použít **graf aktivity virtuálního uživatele** v **Analyzéru zátěžového testu**.<br />     Další informace najdete v tématu [analýza aktivity virtuálních uživatelů v podrobném zobrazení](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).<br />-   **Žádný** -neshromažďují žádné hodnoty jednotlivých časování. Toto je výchozí hodnota pro Visual Studio 2013 Update 4 a novější verze.<br />-   **StatisticsOnly** – shromažďování a ukládání pouze statistiky místo uložení jednotlivé hodnoty časování pro každý test, transakci a stránku, který byl spuštěn nebo vydanou v průběhu zátěžového testu v **Store výsledků testu zatížení**.<br /><br /> Další informace najdete v tématu [postupy: určení vlastnosti úložiště podrobností časování](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).|

## <a name="sql-tracing-properties"></a>Vlastnosti trasování SQL

|Vlastnost|Definice|
|-|----------------|
|**Minimální doba trvání trasovaných SQL operací**|Minimální doba trvání operace SQL se dají zachytit pomocí trasování SQL, v milisekundách. Například tímto způsobem můžete ignorovat operace, které rychle dokončit, pokud se pokoušíte najít SQL operací, které jsou pomalé pod zátěží.|
|**Řetězec připojení trasování SQL**|Připojovací řetězec, který se používá pro přístup k databázi k trasování.|
|**Adresář trasování SQL**|Umístění, kde přejde souboru trasování SQL trasování bude ukončeno. Tento adresář musí mít oprávnění k zápisu pro SQL Server a oprávnění ke čtení pro kontroler.|
|**Trasování SQL povoleno**|To umožňuje trasování SQL operací. Výchozí hodnota je `False`.|

## <a name="test-iterations-properties"></a>Vlastnosti iterací testu

|Vlastnost|Definice|
|-|----------------|
|**Test iterací**|Určuje celkový počet jednotlivých testů ke spuštění před dokončením zátěžového testu. Tato vlastnost se týká pouze pokud je vlastnost "použití testovacích iterací" `True`.|
|**Použít průchod cyklem**|Pokud je testovací iterace použijte `True`, pak běhu zátěžového testu, dokud nedosáhne čísla, která je zadána vlastnost "Testovací iterace" počet jednotlivých testů dokončeno v rámci zátěžového testu. V takovém případě nastavení podle času, které jsou zahřívání doby trvání, doba běhu a doba trvání mimo provoz, jsou ignorovány. Pokud je "Iterace testu použijte" `False`použít všechna nastavení časování a "Testovacích iterací" se ignoruje.|

 Další informace najdete v tématu [postupy: určení počtu testovacích iterací v nastavení spuštění](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="timing-properties"></a>Vlastnosti časování

|Vlastnost|Definice|
|-|----------------|
|**Doba trvání mimo provoz**|Doba trvání zkušebního období chladnutí, vyjádřené ve formátu hh: mm:. Po dokončení zátěžového testu, může být stále spuštěn jednotlivé testy v rámci zátěžového testu. Během období chladnutí tyto testy můžete pokračovat, dokud po dokončení nebo je dosaženo konce dobu chladnutí. Ve výchozím nastavení neexistuje žádný chladnutí a jednotlivé testy budou ukončeny, až se dokončí podle nastavení Doba běhu zátěžového testu.|
|**Doba trvání běhu**|Délku testu, ve formátu hh: mm:.|
|**Vzorkovací frekvence**|Interval, ve kterém chcete zaznamenat hodnoty čítače výkonu ve formátu hh: mm:.<br /><br /> Další informace najdete v tématu [postupy: určení vzorkovací frekvence](../test/how-to-specify-the-sample-rate-for-a-load-test.md).|
|**Doba zahřívání**|Období mezi počátečním testu a při spuštění ukázky data se zaznamenávají ve formátu hh: mm:. To se často používá ke kroku zatížení virtuálních uživatelů na určitou úroveň zatížení před provedením záznamu ukázkové hodnoty. Ukázkové hodnoty, které jsou zachyceny předtím, než jsou uvedeny skončení doby zahřívání v **Analyzéru zátěžového testu**.|

## <a name="webtest-connections-properties"></a>Vlastnosti připojení WebTest

|Vlastnost|Definice|
|-|----------------|
|**Model připojení WebTest**|Tato volba určuje použití připojení z zátěžový testovací agent na webový server pro testy výkonnosti webu, které jsou spouštěny v rámci zátěžového testu. K dispozici jsou tři webového výkonu testu připojení modelu možnosti:<br /><br /> – **Připojení na uživatele** modelu simuluje chování uživatele, který používá skutečný prohlížeč. Pokud je simulované aplikace Internet Explorer 6 nebo Internet Explorer 7, jednotlivé virtuální uživatele, který spouští test výkonnosti webu používá jeden nebo dva vyhrazené připojení k webovému serveru. První připojení při prvním požadavku v testu výkonnosti webu. Druhé připojení může použít, pokud stránka obsahuje více než jeden závislý požadavek. Tyto požadavky jsou vydávány paralelně s použitím dvě připojení. Tato připojení údaje znovu použijí pro následné požadavky v testu výkonnosti webu. Připojení zavřená, po dokončení testu výkonnosti webu. Navracení k tomuto modelu je, že počet připojení, která je otevřena v počítači agenta může být vysoká (až do dvojnásobku uživatelské zatížení). Prostředky, které jsou potřebné k podpoře tento počet vysokou připojení v důsledku toho může omezit uživatelské zatížení, které mohou být řízeny z agenta testu zatížení. Pokud je simulované aplikace Internet Explorer 8, jsou podporovány šest souběžných připojení.<br />– **Fondu připojení** modelu šetří prostředky na zátěžový testovací agent při sdílení připojení k webovému serveru mezi víc uživateli test výkonu virtuální web. Pokud uživatelské zatížení je větší než velikost fondu připojení, testů webového výkonu, které jsou spouštěny v různých virtuálních uživatelů budou sdílet připojení. To může znamenat, že tento test výkonnosti webu jeden muset počkat, než se vydá požadavek na, jestli používáte jiného testu výkonnosti webu je připojení. Průměrná doba testu výkonnosti webu čeká předtím, než odešle, že žádost je sledován pomocí funkce čítač výkonu zátěžového testu Průměrná doba čekání připojení. Tato hodnota musí být menší než průměrná doba odezvy stránky. Pokud není, je pravděpodobně příliš malá velikost fondu připojení.<br />– **Testem** model Určuje použití vyhrazené připojení pro každou iteraci testu.|
|**Velikosti fondu připojení WebTest**|Určuje maximální počet připojení, aby mezi zátěžový testovací agent a webový server. To se týká pouze **fondu připojení** modelu.|

##  <a name="change-run-setting-properties"></a>Změna vlastností parametrů spuštění
 K zátěžovému testu lze přidat více parametrů spuštění s různými nastaveními vlastností a spouštět tak zátěžový test za jiných podmínek. Lze například přidat nové nastavení testu a použít jinou vzorkovací frekvenci či zadat delší dobu běhu. Můžete použít pouze jeden parametr spuštění najednou a je nutné zadat, která spuštění pro označením jako aktivní. Příklad najdete v tématu [postupy: výběr aktivního parametru spuštění pro zátěžový test](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

### <a name="to-change-run-settings"></a>Chcete-li změnit nastavení běhu

1.  Otevřete zátěžový test.

2.  Rozbalte **parametrů běhu** složky.

3.  Zvolte **parametrů běhu** uzlu.

4.  Na **zobrazení** nabídce zvolte **okno vlastností**.

     **Okno vlastností** se zobrazí a zobrazí se vlastnosti pro vybraný parametr spuštění.

5.  Použití **okno vlastností** Změna parametrů běhu. Například změnit dobu spuštění **00:05:00** na test běžel pět minut.

    > [!NOTE]
    > Úplný seznam vlastností parametrů spuštění a jejich popis najdete v části [vlastností parametrů spuštění zátěžového testu](../test/load-test-run-settings-properties.md).

6.  Po dokončení změn vlastností uložte zátěžového testu. Na **souboru** nabídce zvolte **Uložit**.

> [!NOTE]
> Mapování sady čítačů jsou taky součástí parametrů běhu. Další informace najdete v tématu [určení sad čítačů a mezních pravidel pro počítače v rámci zátěžového testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="see-also"></a>Viz také:

- [Konfigurace parametrů spuštění zátěžového testu](../test/configure-load-test-run-settings.md)