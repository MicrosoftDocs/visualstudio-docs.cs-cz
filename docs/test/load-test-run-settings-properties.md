---
title: Parametry spuštění zátěžového testu
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, run settings
ms.assetid: de10dabb-02ed-403b-9e6f-0b735524988c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8898a474888ce9efbf4c91a5251bf8fe7036fe5f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584462"
---
# <a name="load-test-run-settings-properties"></a>Vlastnosti nastavení spuštění zátěžového testu

Nastavení spuštění zátěžového testu určují řadu dalších nastavení, včetně doby trvání testu, úrovně podrobností kolekce výsledků a sad čítačů, které jsou shromažďovány při spuštění testu. Pro každý zátěžový test lze vytvořit a uložit několik parametrů spuštění a následně při spouštění testu zvolit jedno konkrétní nastavení. Počáteční nastavení spuštění je přidáno do zátěžového testu při vytváření zátěžového testu pomocí **Průvodce novým zátěžového testu**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Následující tabulky popisují různé vlastnosti nastavení spuštění zátěžového testu. Tyto vlastnosti lze upravit tak, aby splňovaly konkrétní požadavky zátěžového testu.

Další informace naleznete v [tématu Konfigurace nastavení spuštění zátěžového testu](../test/configure-load-test-run-settings.md).

## <a name="general-properties"></a>Obecné vlastnosti

|Vlastnost|Definice|
|-|----------------|
|**Popis**|Popis nastavení spuštění.|
|**Maximální chyba na typ**|Maximální počet chyb na typ uložit pro zátěžový test.<br /><br /> Toto číslo můžete zvýšit, pokud je to třeba, ale tím se také zvýší velikost a doba zpracování výsledku zátěžového testu.|
|**Nahlášené adresy URL s maximálním požadavkem**|Maximální počet jedinečných webových požadavků na test výkonu, na kterých mají být vykazovány výsledky tohoto zátěžového testu.<br /><br /> Toto číslo můžete zvýšit, pokud je to třeba, ale tím se také zvýší velikost a doba zpracování výsledku zátěžového testu.|
|**Porušení maximální prahové hodnoty**|Maximální počet porušení prahové hodnoty uložit pro tento zátěžový test.<br /><br /> Toto číslo můžete zvýšit, pokud je to třeba, ale tím se také zvýší velikost a doba zpracování výsledku zátěžového testu.|
|**Spuštění testů částí v doméně aplikace**|Logická hodnota, která určuje, zda bude každé sestavení testování částí spuštěno v samostatné doméně aplikace, pokud zátěžový test obsahuje testy částí. Výchozí nastavení je True.<br /><br /> Pokud testy částí nevyžadují samostatnou doménu aplikace nebo soubor app.config, aby fungovaly správně, `False`mohou testy částí běžet rychleji nastavením hodnoty této vlastnosti na .|
|**Název**|Název nastavení spustit tak, jak je uvedeno v uzlu **Spustit nastavení** **editoru zátěžového testu**.|
|**Úroveň ověření**|To definuje nejvyšší úroveň ověřovacího pravidla, která bude spuštěna v zátěžovém testu. Ověřovací pravidla jsou přidružena k požadavkům na test výkonu webu. Každé ověřovací pravidlo má přidruženou úroveň ověření: **Vysoká**, **Střední**nebo **Nízká**. Toto nastavení spuštění zátěžového testu určí, která ověřovací pravidla budou spuštěna při spuštění testu výkonu webu v zátěžovém testu. Pokud je například toto nastavení spuštění nastaveno na **střední**, budou spuštěna všechna ověřovací pravidla označená jako **Střední**nebo **Nízká.**|

## <a name="logging-properties"></a>Vlastnosti protokolování

|Vlastnost|Definice|
|-|----------------|
|**Maximální počet testovacích protokolů**|Určuje maximální počet testovacích protokolů, které mají být uloženy pro zátěžový test. Po dosažení hodnoty zadané pro maximální počet protokolů test, zátěžový test zastaví shromažďování protokolů. Proto protokoly budou shromažďovány na začátku testu, nikoli na konci. Zátěžový test bude pokračovat v jeho spuštění, dokud nebude dokončen.|
|**Uložit frekvenci protokolu pro dokončené testy**|Určuje frekvenci, s jakou bude protokol testu zapsán. Číslo označuje, že jeden z každého zadaného počtu testů budou uloženy do protokolu testu. Například zadání hodnoty deset určuje, že desátý, dvacátý, třicátý a tak dále budou zapsány do testovacího protokolu. Nastavení hodnoty na hodnotu 0 určuje, že nebudou uloženy žádné testovací protokoly.|
|**Uložení selhání testu přihlášení**|Logická hodnota, která určuje, zda pokud jsou protokoly testu uloženy, pokud test selže v zátěžovém testu. Výchozí formát je `True`.<br /><br /> Další informace naleznete v [tématu Postup: Určení, zda jsou pro protokoly testování uloženy chyby testu.](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|

Další informace naleznete [v tématu Modify load test logging settings](../test/modify-load-test-logging-settings.md).

## <a name="results-properties"></a>Vlastnosti výsledků

|Vlastnost|Definice|
|-|----------------|
|**Typ úložiště**|Způsob uložení čítačů výkonu, které jsou získány v zátěžovém testu. Možnosti jsou tyto:<br /><br /> -   **Databáze** - Vyžaduje databázi SQL, která má **úložiště výsledků zátěžového testu**.<br />-   **Žádné**.|
|**Úložiště podrobností časování**|Používá se k určení, které podrobnosti budou uloženy v **úložišti výsledků zátěžových testů**. K dispozici jsou tři hodnoty:<br /><br /> -   **AllIndividualDetails** - Shromažďovat a ukládat jednotlivé hodnoty časování pro každý test, transakce a stránky, která byla spuštěna nebo vydána během zátěžového testu v **úložišti výsledků zátěžového testu**. Je vyžadováno, pokud máte v úmyslu použít **virtuální graf aktivity uživatele** v **analyzátoru zátěžového testu**.<br />     Další informace naleznete [v tématu Analýza aktivity virtuálního uživatele v zobrazení Podrobnosti](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).<br />-   **Žádné** – Neshromážděte žádné jednotlivé hodnoty časování. Toto je výchozí hodnota pro Visual Studio 2013 Update 4 a novější verze.<br />-   **StatisticsOnly** - Shromažďovat a ukládat pouze statistiky namísto ukládání jednotlivých časování hodnoty pro každý test, transakce a stránky, která byla provedena nebo vydána během zátěžového testu v **úložišti výsledků zátěžového testu**.<br /><br /> Další informace naleznete v [tématu Postup: Zadejte vlastnost úložiště podrobností časování](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).|

## <a name="sql-tracing-properties"></a>Vlastnosti trasování SQL

|Vlastnost|Definice|
|-|----------------|
|**Minimální doba trvání trasovaných operací SQL**|Minimální doba trvání operace SQL, která má být zachycena trasování SQL v milisekundách. Například to umožňuje ignorovat operace, které se dokončí rychle, pokud se pokoušíte najít operace SQL, které jsou pomalé při zatížení.|
|**Řetězec připojení trasování SQL**|Připojovací řetězec, který se používá pro přístup k databázi, která má být sledována.|
|**Adresář trasování SQL**|Umístění, kde je soubor trasování SQL umístěn po ukončení trasování. Tento adresář musí mít oprávnění k zápisu pro SQL Server a oprávnění ke čtení pro řadič.|
|**Trasování SQL povoleno**|To umožňuje trasování operací SQL. Výchozí hodnota je `False`.|

## <a name="test-iterations-properties"></a>Testovat vlastnosti iterací

|Vlastnost|Definice|
|-|----------------|
|**Testovat iterace**|Určuje celkový počet jednotlivých testů, které mají být spuštěny před dokončením zátěžového testu. Tato vlastnost platí pouze v případě, že `True`je vlastnost "Použít test iterací" .|
|**Použít testovací iterace**|Pokud je `True`použít test iterací , pak zátěžový test běží, dokud počet jednotlivých testů dokončených v rámci zátěžového testu dosáhne čísla, které je určeno vlastností "Test Itrace". V tomto případě jsou ignorovány nastavení založené na čase, které jsou Doba zahřívání, Doba trvání spuštění a Doba ochlazování. Pokud "Použít test iterací" je `False`, všechna nastavení časování použít a "Test iterací" je ignorována.|

Další informace naleznete v [tématu Postup: Určení počtu iterací testu v nastavení spuštění](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="timing-properties"></a>Vlastnosti časování

|Vlastnost|Definice|
|-|----------------|
|**Doba ochlazuje**|Doba trvání testu cool-down období, vyjádřené ve formátu hh:mm:ss. Jednotlivé testy v rámci zátěžového testu může být stále spuštěna po dokončení zátěžového testu. Během doby ochlazování mohou tyto testy pokračovat, dokud nedosáhnou úplného nebo konce doby ochlazování. Ve výchozím nastavení neexistuje žádné období cool-down a jednotlivé testy jsou ukončeny po dokončení zátěžového testu na základě nastavení Doba trvání spuštění.|
|**Doba trvání spuštění**|Délka testu ve formátu hh:mm:ss.|
|**Vzorkovací frekvence**|Interval, ve kterém mají být zachyceny hodnoty čítače výkonu ve formátu hh:mm:ss.<br /><br /> Další informace naleznete v [tématu How to: Specify the sample rate](../test/how-to-specify-the-sample-rate-for-a-load-test.md).|
|**Doba zahřívání**|Období mezi začátkem testu a kdy se vzorky dat začnou zaznamenávat ve formátu hh:mm:ss. To se často používá ke kroku načíst virtuální uživatele k dosažení určité úrovně zatížení před zaznamenáním ukázkových hodnot. Ukázkové hodnoty, které jsou zachyceny před ukončením zahřívací doby, jsou zobrazeny v **analyzátoru zátěžového testu**.|

## <a name="webtest-connections-properties"></a>Vlastnosti připojení WebTest

|Vlastnost|Definice|
|-|----------------|
|**Model připojení webového testu**|To řídí využití připojení z agenta zátěžového testu na webový server pro testy výkonu webu, které běží uvnitř zátěžového testu. K dispozici jsou tři možnosti modelu připojení test výkonu webu:<br /><br /> - **Připojení na uživatele** modelu simuluje chování uživatele, který používá skutečný prohlížeč. Při simulaci aplikace Internet Explorer 6 nebo Internet Explorer 7 používá každý virtuální uživatel, který používá test výkonu webu, jedno nebo dvě vyhrazená připojení k webovému serveru. První připojení je navázáno při vydání prvního požadavku v testu výkonu webu. Druhé připojení lze použít, pokud stránka obsahuje více než jeden závislý požadavek. Tyto požadavky jsou vydávány paralelně pomocí dvou připojení. Tato připojení jsou znovu použity pro následné požadavky v testu výkonu webu. Připojení jsou uzavřeny po dokončení testu výkonu webu. Nevýhodou tohoto modelu je, že počet připojení, která je držena otevřené v počítači agenta může být vysoká (až dvakrát zatížení uživatele). V důsledku toho prostředky, které jsou požadovány pro podporu tohoto vysokého počtu připojení může omezit zatížení uživatele, které lze řídit z jednoho agenta zátěžového testu. Při simulaci aplikace Internet Explorer 8 je podporováno šest souběžných připojení.<br />- Model **fondu připojení** šetří prostředky na agenta zátěžového testu sdílením připojení k webovému serveru mezi více uživateli testu výkonu virtuálního webu. Pokud je zatížení uživatele větší než velikost fondu připojení, budou testy výkonu webu spuštěné různými virtuálními uživateli sdílet připojení. To může znamenat, že jeden test výkonu webu může čekat, než vydá požadavek, když jiný test výkonu webu používá připojení. Průměrná doba, po kterou test výkonu webu čeká před odesláním požadavku, je sledován čítač výkonu zátěžového testu Průměrná čekací doba připojení. Toto číslo by mělo být menší než průměrná doba odezvy na stránce. Pokud tomu tak není, velikost fondu připojení je pravděpodobně příliš malá.<br />- Model **Iterace připojení na test** určuje použití vyhrazených připojení pro každou iteraci testu.|
|**Velikost fondu připojení webtest**|Určuje maximální počet připojení mezi agentem zátěžového testu a webovým serverem. To platí pouze pro model **fondu připojení.**|

## <a name="change-run-setting-properties"></a>Změna vlastností nastavení spuštění

K zátěžovému testu lze přidat více parametrů spuštění s různými nastaveními vlastností a spouštět tak zátěžový test za jiných podmínek. Lze například přidat nové nastavení testu a použít jinou vzorkovací frekvenci či zadat delší dobu běhu. Současně můžete používat pouze jedno nastavení spuštění a je nutné určit, které nastavení spuštění se má použít, a to tak, že ho označíte jako aktivní. Příklad najdete v [tématu Postup: Vyberte nastavení aktivního spuštění zátěžového testu](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

Změna nastavení spuštění:

1. Otevřete zátěžový test.

2. Rozbalte složku **Spustit nastavení.**

3. Zvolte uzel **Nastavení spuštění.**

4. V nabídce **View** zvolte **Properties Window**.

     Zobrazí se **okno Vlastnosti** a zobrazí se vlastnosti vybraného nastavení spuštění.

5. Pomocí **okna Vlastnosti** změňte nastavení spuštění. Můžete například změnit dobu trvání spuštění na **00:05:00** a spusťte test po dobu pěti minut.

    > [!NOTE]
    > Úplný seznam vlastností nastavení spuštění a jejich popisy naleznete v tématu [Načtení vlastností nastavení spuštění testu](../test/load-test-run-settings-properties.md).

6. Po dokončení změny vlastností uložte zátěžový test. V nabídce **Soubor** zvolte **Uložit**.

> [!NOTE]
> Mapování sad čítačů je také součástí nastavení spuštění. Další informace naleznete [v tématu Určení sad čítačů a prahových hodnot pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="see-also"></a>Viz také

- [Konfigurace nastavení spuštění zátěžového testu](../test/configure-load-test-run-settings.md)
