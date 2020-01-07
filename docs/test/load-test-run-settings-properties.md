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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75584462"
---
# <a name="load-test-run-settings-properties"></a>Vlastnosti nastavení běhu zátěžového testu

Parametry běhu zátěžového testu určují různá nastavení, včetně doby trvání testu, úrovně podrobností kolekce výsledků a sady čítačů, které jsou shromažďovány při spuštění testu. Pro každý zátěžový test lze vytvořit a uložit několik parametrů spuštění a následně při spouštění testu zvolit jedno konkrétní nastavení. Počáteční nastavení spuštění je přidáno do zátěžového testu při vytvoření zátěžového testu pomocí **nového Průvodce zátěžovým testem**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

V následujících tabulkách jsou popsány různé vlastnosti pro parametry běhu zátěžového testu. Tyto vlastnosti lze upravit tak, aby splňovaly konkrétní požadavky zátěžového testu.

Další informace najdete v tématu [Konfigurace nastavení běhu zátěžového testu](../test/configure-load-test-run-settings.md).

## <a name="general-properties"></a>Obecné vlastnosti

|Vlastnost|Definice|
|-|----------------|
|**Popis**|Popis nastavení spuštění.|
|**Maximální chyba na typ**|Maximální počet chyb na typ, který se má uložit pro zátěžový test.<br /><br /> Toto číslo můžete zvýšit, pokud je to nutné, ale v takovém případě dojde také ke zvýšení velikosti a doby zpracování výsledku zátěžového testu.|
|**Maximální počet vykázaných adres URL žádosti**|Maximální počet jedinečných adres URL žádostí testu webového výkonu, na kterých se má vykázat výsledky v tomto zátěžovém testu.<br /><br /> Toto číslo můžete zvýšit, pokud je to nutné, ale v takovém případě dojde také ke zvýšení velikosti a doby zpracování výsledku zátěžového testu.|
|**Maximální počet překročení mezních hodnot**|Maximální počet překročení mezních hodnot, které mají být uloženy pro tento zátěžový test.<br /><br /> Toto číslo můžete zvýšit, pokud je to nutné, ale v takovém případě dojde také ke zvýšení velikosti a doby zpracování výsledku zátěžového testu.|
|**Spustit testy jednotek v aplikační doméně**|Logická hodnota, která určuje, zda každé testovací sestavení jednotky bude spuštěno v samostatné aplikační doméně, pokud zátěžový test obsahuje testy jednotek. Výchozí nastavení je true (pravda).<br /><br /> Pokud testy jednotek nevyžadují, aby správně fungovala samostatná aplikační doména nebo soubor App. config, můžete testy jednotek běžet rychleji nastavením hodnoty této vlastnosti na `False`.|
|**Jméno**|Název nastavení spuštění, jak se zobrazí v uzlu **nastavení spuštění** **Editor zátěžového testu**.|
|**Úroveň ověření**|Tato definice definuje nejvyšší úroveň ověřovacího pravidla, které se spustí v rámci zátěžového testu. Ověřovací pravidla jsou přidružena k žádostem o test výkonnosti webu. Každé ověřovací pravidlo má přidruženou úroveň ověření: **Vysoká**, **střední**nebo **Nízká**. Toto nastavení běhu zátěžového testu určí, která ověřovací pravidla budou spuštěna, když je test výkonnosti webu spuštěn v rámci zátěžového testu. Pokud je například toto nastavení běhu nastaveno na **hodnotu Střední**, spustí se všechna ověřovací pravidla označená jako **střední**nebo **Nízká** .|

## <a name="logging-properties"></a>Vlastnosti protokolování

|Vlastnost|Definice|
|-|----------------|
|**Maximální počet protokolů testu**|Určuje maximální počet protokolů testu, které se mají uložit pro zátěžový test. Když je dosaženo hodnoty zadané pro maximální počet protokolů testu, zátěžový test přestane shromažďovat protokoly. Protokoly budou proto shromažďovány na začátku testu, nikoli na konci. Zátěžový test bude nadále běžet až do dokončení.|
|**Uložit četnost protokolu pro dokončené testy**|Určuje četnost zápisu protokolu testu. Číslo označuje, že se do protokolu testu uloží jeden z každého zadaného počtu testů. Například zadáním hodnoty deset určíte, že desáté, dvacáté, thirtieth a tak dále budou zapsány do protokolu testu. Nastavením hodnoty na 0 určíte, že se neuloží žádné protokoly testů.|
|**Při selhání testu uložit protokol**|Logická hodnota, která určuje, zda jsou v případě neúspěšného testu v rámci zátěžového testu uloženy protokoly testů. Výchozí hodnota je `True`.<br /><br /> Další informace naleznete v tématu [How to: Určete, zda jsou testovací selhání uložena do protokolů testu.](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|

Další informace najdete v tématu [Úprava nastavení protokolování zátěžového testu](../test/modify-load-test-logging-settings.md).

## <a name="results-properties"></a>Vlastnosti výsledků

|Vlastnost|Definice|
|-|----------------|
|**Typ úložiště**|Způsob ukládání čítačů výkonu, které jsou získány v rámci zátěžového testu. Možnosti jsou tyto:<br /><br /> -   **Database** – vyžaduje databázi SQL, která má **výsledky testů úložiště Load**.<br />-   **žádné**.|
|**Úložiště podrobností časování**|Slouží k určení, které podrobnosti budou uloženy v **úložišti výsledky testů zatížení**. K dispozici jsou tři hodnoty:<br /><br /> -   **AllIndividualDetails** – shromažďování a ukládání hodnot jednotlivých časování pro každý test, transakci a stránku, které byly spuštěny nebo vydány během zátěžového testu v **úložišti zatížení výsledky testů**. Je vyžadováno, pokud chcete v **analyzátoru zátěžového testu**použít **graf aktivity virtuálního uživatele** .<br />     Další informace najdete v tématu [analýza aktivity virtuálních uživatelů v podrobném zobrazení](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).<br />-   **none** – neshromažďuje žádné hodnoty jednotlivých časování. Toto je výchozí hodnota pro Visual Studio 2013 Update 4 a novější verze.<br />-   **StatisticsOnly** – shromažďují a ukládají pouze statistické údaje místo uložení jednotlivých hodnot časování pro každý test, transakci a stránku, které byly provedeny nebo vydány během zátěžového testu v **úložišti zatížení výsledky testů**.<br /><br /> Další informace najdete v tématu [postupy: určení vlastnosti úložiště podrobností časování](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).|

## <a name="sql-tracing-properties"></a>Vlastnosti trasování SQL

|Vlastnost|Definice|
|-|----------------|
|**Minimální doba vysledovacích operací SQL**|Minimální doba trvání operace SQL zaznamenaná trasováním SQL v milisekundách. Například vám umožní ignorovat operace, které se dokončí rychle, pokud se pokoušíte najít operace SQL, které jsou při zatížení pomalé.|
|**Řetězec připojení trasování SQL**|Připojovací řetězec, který se používá pro přístup k databázi, ke které se má trasovat.|
|**Adresář trasování SQL**|Umístění, kde je trasovací soubor SQL umístěn po ukončení trasování. Tento adresář musí mít oprávnění k zápisu pro SQL Server a oprávnění ke čtení pro kontroler.|
|**Trasování SQL povoleno**|To umožňuje trasování operací SQL. Výchozí hodnota je `False`.|

## <a name="test-iterations-properties"></a>Vlastnosti iterací testu

|Vlastnost|Definice|
|-|----------------|
|**Iterace testu**|Určuje celkový počet jednotlivých testů, které mají být spuštěny před dokončením zátěžového testu. Tato vlastnost se vztahuje pouze v případě, že je `True`vlastnost použít iterace testu.|
|**Použít iterace testu**|Pokud je `True`použít iterace testu, pak se zátěžový test spustí, dokud počet jednotlivých testů dokončených v rámci zátěžového testu nedosáhne čísla zadaného vlastností "test iterací". V tomto případě se budou ignorovat časová nastavení, která jsou zahřívání, doba běhu a doba trvání chlazení. Pokud je `False`použít iterace testu, platí všechna nastavení časování a "iterace testu" se ignorují.|

Další informace naleznete v tématu [How to: zadejte počet testovacích iterací v nastavení spuštění](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="timing-properties"></a>Vlastnosti časování

|Vlastnost|Definice|
|-|----------------|
|**Doba trvání chlazení**|Doba, po kterou se testovací doba nepracuje, vyjádřená ve formátu hh: mm: ss. Jednotlivé testy v rámci zátěžového testu mohou i nadále běžet po dokončení zátěžového testu. Během doby chladnutí mohou tyto testy pokračovat, dokud nebudou dokončeny, nebo dokud nedosáhnete konce doby chlazení. Ve výchozím nastavení neexistuje žádná doba chladnutí a jednotlivé testy jsou ukončeny po dokončení zátěžového testu na základě nastavení trvání běhu.|
|**Doba trvání běhu**|Délka testu ve formátu hh: mm: ss.|
|**Vzorkovací frekvence**|Interval, ve kterém mají být zachyceny hodnoty čítače výkonu ve formátu hh: mm: ss.<br /><br /> Další informace najdete v tématu [postupy: určení vzorkovací frekvence](../test/how-to-specify-the-sample-rate-for-a-load-test.md).|
|**Doba zahřívání**|Období mezi začátkem testu a zahájením zaznamenávání ukázkových dat ve formátu hh: mm: ss. To se často používá pro krok načtení virtuálních uživatelů, aby se dosáhlo určité úrovně zatížení předtím, než se zaznamenávají ukázkové hodnoty. Vzorové hodnoty, které jsou zachyceny před uplynutím doby zahřívání, jsou zobrazeny v **analyzátoru zátěžového testu**.|

## <a name="webtest-connections-properties"></a>Vlastnosti připojení webového testu

|Vlastnost|Definice|
|-|----------------|
|**Model připojení WebTest**|To řídí použití připojení od agenta zátěžového testu na webový server pro testy výkonnosti webu, které běží v rámci zátěžového testu. K dispozici jsou tři možnosti modelu připojení test výkonnosti webu:<br /><br /> – **Připojení pro model uživatele** simuluje chování uživatele, který používá reálný prohlížeč. Když je aplikace Internet Explorer 6 nebo Internet Explorer 7 simulovaná, každý virtuální uživatel, který spouští test výkonnosti webu, používá jedno nebo dvě vyhrazená připojení k webovému serveru. První připojení je navázáno při vydání první žádosti v testu výkonnosti webu. Druhé připojení může být použito, pokud stránka obsahuje více než jeden závislý požadavek. Tyto požadavky jsou vydávány paralelně pomocí dvou připojení. Tato připojení se znovu použijí pro následné požadavky v testu výkonnosti webu. Připojení jsou po dokončení testu výkonnosti webu zavřena. Nevýhodou tohoto modelu je, že počet připojení, která jsou otevřená v počítači agenta, může být vysoký (až dvakrát se uživatel načítá). V důsledku toho mohou prostředky, které jsou požadovány pro podporu tohoto vysokého počtu připojení, omezit uživatelské zatížení, které může být ovládáno jedním agentem zátěžového testu. Když je aplikace Internet Explorer 8 simulovaná, podporuje se šest souběžných připojení.<br />– Model **fondu připojení** udržuje prostředky v agentovi zátěžového testu tím, že sdílí připojení k webovému serveru mezi několika uživateli testu výkonnosti virtuálního webu. Pokud je zatížení uživatele větší než velikost fondu připojení, testy webového výkonu, které jsou spuštěny různými virtuálními uživateli, budou sdílet připojení. To může znamenat, že jeden test výkonnosti webu může počkat, než vydá požadavek, pokud je použito pro jiný test výkonnosti webu. Průměrná doba, kterou test výkonnosti webu čeká před odesláním požadavku, je sledován průměrnou dobou čekání připojení zátěžového testu. Toto číslo by mělo být nižší než průměrná doba odezvy stránky. Pokud tomu tak není, je velikost fondu připojení pravděpodobně příliš malá.<br />-Připojení pro model **iterace testu** Určuje použití vyhrazených připojení pro každou iteraci testu.|
|**Velikost fondu připojení WebTest**|Toto nastavení určuje maximální počet připojení mezi agentem zátěžového testu a webovým serverem. To platí jenom pro model **fondu připojení** .|

## <a name="change-run-setting-properties"></a>Změnit vlastnosti nastavení spuštění

K zátěžovému testu lze přidat více parametrů spuštění s různými nastaveními vlastností a spouštět tak zátěžový test za jiných podmínek. Lze například přidat nové nastavení testu a použít jinou vzorkovací frekvenci či zadat delší dobu běhu. V jednom okamžiku můžete použít jenom jedno nastavení spuštění a musíte určit, které nastavení spuštění má použít, a to tak, že ho označíte jako aktivní. Příklad naleznete v tématu [Postupy: výběr aktivního nastavení spuštění pro zátěžový test](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

Postup změny nastavení spuštění:

1. Otevřete zátěžový test.

2. Rozbalte **parametrů běhu** složky.

3. Vyberte uzel **nastavení spuštění** .

4. Na **zobrazení** nabídce zvolte **okno vlastností**.

     Zobrazí se **okno Vlastnosti** a zobrazí se vlastnosti vybraného nastavení spuštění.

5. Použijte **okno Vlastnosti** ke změně parametrů běhu. Například změnit dobu spuštění **00:05:00** na test běžel pět minut.

    > [!NOTE]
    > Úplný seznam vlastností parametrů spuštění a jejich popis naleznete v tématu [Vlastnosti nastavení běhu zátěžového testu](../test/load-test-run-settings-properties.md).

6. Až dokončíte změnu vlastností, uložte zátěžový test. V nabídce **soubor** klikněte na příkaz **Uložit**.

> [!NOTE]
> Mapování sad čítačů jsou také součástí parametrů běhu. Další informace najdete v tématu [určení sad čítačů a mezních pravidel pro počítače v rámci zátěžového testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="see-also"></a>Viz také:

- [Konfigurace parametrů spuštění zátěžového testu](../test/configure-load-test-run-settings.md)
