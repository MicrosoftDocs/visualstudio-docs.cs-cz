---
title: Písma a barvy, prostředí, dialogové okno Možnosti
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.FontsAndColors
- VS.ToolsOptionsPages.Environment.Fonts_And_Colors
- VS.Environment.Fonts And Colors
helpviewer_keywords:
- colors, customizing IDE
- Query and View Designer, customizing
- fonts, editors
- menus, customizing
- Table Designer, customizing
- Database Designer, customizing environment
- default colors
- accessibility, options
- editors, customizing
- designers, customizing environment
- defaults, colors
- printers, customizing
ms.assetid: c767d302-51ed-47a8-a527-c07bce2aa485
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d5c9edd47e3db43735d3c6e8f6a4ec1a881214e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595615"
---
# <a name="fonts-and-colors-environment-options-dialog-box"></a>Písma a barvy, prostředí, dialogové okno Možnosti

Stránka **písma a barvy** v dialogovém okně **Možnosti** umožňuje vytvořit vlastní písmo a barevné schéma pro různé prvky uživatelského rozhraní v integrovaném vývojovém prostředí (IDE). Chcete-li získat přístup k tomuto dialogovému oknu, klikněte na možnost **nástroje**  >  a pak vyberte**možnost** **Environment**  >  **písma a barvy**prostředí.

Změny barevného schématu se neprojeví během relace, ve které jste je provedli. Změny barev můžete vyhodnotit tak, že otevřete jinou instanci aplikace Visual Studio a vydáte podmínky, za kterých očekáváte, že se vaše změny použijí.

**Zobrazit nastavení pro**

Obsahuje seznam všech prvků uživatelského rozhraní, u kterých můžete měnit schémata písma a barev. Po výběru položky z tohoto seznamu můžete přizpůsobit nastavení barev pro položku vybranou v **zobrazení položky**.

- **Textový editor**

     Změny stylu písma, velikosti a nastavení barev v textovém editoru ovlivňují vzhled textu ve výchozím textovém editoru. Pomocí těchto nastavení nebudou ovlivněny dokumenty otevřené v textovém editoru mimo rozhraní IDE.

- **Tiskárna**

     Změny stylu písma, velikosti a nastavení barev pro tiskárnu ovlivní vzhled textu ve vytištěných dokumentech.

    > [!NOTE]
    > Podle potřeby můžete pro tisk vybrat jiné výchozí písmo, než které se používá pro zobrazení v textovém editoru. To může být užitečné při tisku kódu, který obsahuje jednobajtové i dvoubajtové znaky.

- **Doplňování výrazů**

     Změní styl písma a velikost textu, který se zobrazí v místním okně dokončování příkazů v editoru.

- **Popis editoru**

     Změní styl písma a velikost textu, který se zobrazí v popiscích tlačítek zobrazených v editoru.

- **Písmo prostředí**

     Změní styl písma a velikost pro všechny prvky uživatelského rozhraní IDE, které ještě nemají samostatnou možnost v části **Zobrazit nastavení pro**.

     ::: moniker range="vs-2017"

     Například tato možnost se vztahuje na **úvodní stránku** , ale nemá vliv na okno **výstup** .

     ::: moniker-end

- **[Všechna okna textových nástrojů]**

     Změny stylu písma, velikosti a nastavení barev pro tuto položku ovlivňují vzhled textu v oknech nástrojů, které mají výstupní podokna v integrovaném vývojovém prostředí (IDE). Například okno výstup, okno Příkaz, okamžité okno atd.

    > [!NOTE]
    > Změny textu **[všechna okna textových nástrojů]** se neprojeví během relace, ve které jste je provedli. Tyto změny můžete vyhodnotit otevřením jiné instance aplikace Visual Studio.

**Použít výchozí**

Obnoví hodnoty písma a barev položky seznamu vybrané v **možnosti Zobrazit nastavení pro**. Tlačítko **použít** se zobrazí, pokud jsou pro výběr k dispozici další schémata zobrazení. Můžete si například vybrat ze dvou schémat pro tiskárnu.

**Font (tučný typ indikuje písma s pevnou šířkou)**

Zobrazí seznam všech písem nainstalovaných ve vašem systému. Při prvním zobrazení rozevírací nabídky se zvýrazní aktuální písmo pro prvek vybraný v poli **Zobrazit nastavení pro** . Pevná písma, která jsou v editoru jednodušší, se zobrazují tučně.

**Velikost**

Vypíše dostupné velikosti bodů pro zvýrazněné písmo. Změna velikosti písma má vliv na všechny **položky zobrazení** pro volbu **Zobrazit nastavení pro** výběr.

**Zobrazit položky**

Obsahuje seznam položek, pro které lze změnit barvu popředí a pozadí.

> [!NOTE]
> Výchozí položkou zobrazení je **prostý text** . V takovém případě vlastnosti přiřazené k **prostému textu** budou přepsány vlastnostmi přiřazenými jiným položkám zobrazení. Například pokud přiřadíte barvu modrou jako **prostý text** a zelenou barvu na **identifikátor**, všechny identifikátory budou zobrazeny zeleně. V tomto příkladu vlastnosti **identifikátoru** přepisují vlastnosti **nešifrovaného textu** .

Mezi některé položky zobrazení patří:

|Zobrazit položku|Popis|
|------------------|-----------------|
|**Prostý text**|Text v editoru|
|**Vybraný text**|Text, který je obsažen v aktuálním výběru, když má Editor fokus.|
|**Neaktivní vybraný text**|Text, který je zahrnut v aktuálním výběru, když Editor ztratil fokus.|
|**Okraj indikátoru**|Okraj na levé straně editoru kódu, kde se zobrazují zarážky a ikony záložek.|
|**Čísla řádků**|Volitelná čísla, která se zobrazí vedle každého řádku kódu|
|**Viditelné prázdné znaky**|Mezery, tabulátory a indikátory zalamování slov|
|**Záložku**|Řádky, které mají záložky. **Záložka** je viditelná pouze v případě, že je okraj indikátoru zakázán.|
|**Spárování složených závorek (zvýraznění)**|Zvýraznění, které obvykle formátuje tučně pro odpovídající závorky.|
|**Spárování složených závorek (obdélník)**|Zvýraznění, které je obvykle šedý obdélník na pozadí.|
|**Zarážka (zakázaná)**|Nepoužívá se.|
|**Zarážka (povolena)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující jednoduché zarážky. Tato možnost je k dispozici pouze v případě, že jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** pro [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka (chyba)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující zarážky, které jsou v chybovém stavu. Platí pouze v případě, že jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, ladění, možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka (upozornění)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující zarážky, které jsou ve stavu upozornění. Platí pouze v případě, že jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, ladění, možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka-Rozšířená (zakázána)**|Určuje barvu zvýraznění pro příkazy nebo řádky, které obsahují zakázané zarážky podmíněného nebo vypočítaného počtu volání. Platí pouze v případě, že jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, ladění, možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka-Rozšířená (povolena)**|Určuje barvu zvýraznění pro příkazy nebo řádky, které obsahují podmíněné a zahozené zarážky. Platí pouze v případě, že jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, ladění, možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka-Rozšířená (chyba)**|Určuje barvu zvýraznění pro příkazy nebo řádky, které obsahují podmíněné a zahozené zarážky, které jsou v chybovém stavu. Platí pouze v případě, že jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, ladění, možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka-Rozšířená (upozornění)**|Určuje barvu zvýraznění pro příkazy nebo řádky, které obsahují podmíněné a zahozené zarážky, které jsou ve stavu upozornění. Platí pouze v případě, že jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, ladění, možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka-mapovaná (zakázaná)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující zakázané mapované zarážky. Platí pro ladění skriptů ASP nebo ASP.NET, pokud jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** , a to v [dialogovém okně Obecné, ladění, možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka-mapovaná (povolená)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující namapované zarážky. Platí pro ladění skriptů ASP nebo ASP.NET, pokud jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** , a to v [dialogovém okně Obecné, ladění, možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka-mapovaná (chyba)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující namapované zarážky v chybovém stavu. Platí pro ladění skriptů ASP nebo ASP.NET, pokud jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** , a to v [dialogovém okně Obecné, ladění, možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka-mapovaná (upozornění)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující namapované zarážky ve stavu upozornění. Platí pro ladění skriptů ASP nebo ASP.NET, pokud jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** , a to v [dialogovém okně Obecné, ladění, možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Uživatelská klíčová slova C/C++**|Konstanta v rámci určitého souboru kódu definovaného prostřednictvím `#define` direktivy.|
|**Volání metody Return**|Určuje barvu zvýraznění pro zdrojové příkazy nebo řádky, které označují vracené body volání, když je kontext přepnut na rámec nehorního zásobníku při ladění.|
|**Pole závislé na fragmentu kódu**|Pole, které bude aktualizováno při úpravě aktuálního upravitelného pole.|
|**Pole fragmentu kódu**|Upravitelné pole, když je fragment kódu aktivní|
|**Sbalitelný text**|Blok textu nebo kódu, který lze přepnout a z pohledu zobrazení v editoru kódu.|
|**Komentář**|Komentáře ke kódu.|
|**Chyba kompilátoru**|Modré vlnovky v editoru indikující chybu kompilátoru.|
|**Pokrytí – nedotčená oblast**|Kód, který nebyl pokryt jednotkovým testem.|
|**Pokrytí částečně prokryté oblasti**|Kód, který byl částečně pokryt jednotkovým testem.|
|**Disponibilní oblast pokrytí**|Kód, který byl zcela pokryt jednotkovým testem.|
|**Komentář CSS**|Komentář v šablony stylů CSS. Příklad:<br /><br /> /* komentář \*/|
|**Klíčové slovo CSS**|Klíčová slova v šabloně stylů CSS.|
|**Název vlastnosti CSS**|Název vlastnosti, například pozadí.|
|**Hodnota vlastnosti CSS**|Hodnota přiřazená vlastnosti, například modrá.|
|**Selektor šablon stylů CSS**|Řetězec určující, na které prvky se odpovídající pravidlo vztahují. Selektor může být jednoduchý selektor, například "H1" nebo kontextový selektor, například "H1 B", který se skládá z několika jednoduchých selektorů.|
|**Hodnota řetězce CSS**|Řetězec v šablony stylů CSS.|
|**Aktuální umístění seznamu**|Aktuální řádek přešel do okna nástroje seznamu, jako je například okno výstup nebo okna výsledků hledání.|
|**Aktuální příkaz**|Určuje barvu zvýraznění zdrojového příkazu nebo řádku, který označuje pozici aktuálního kroku při ladění.|
|**Data ladicího programu se změnila**|Barva textu používaná k zobrazení změněných dat v oknech **Registry** a **paměť**|
|**Pozadí okna definice**|Barva pozadí okna **definice kódu** .|
|**Aktuální shoda okna definice**|Aktuální definice v okně **definice kódu** .|
|**Název souboru zpětného překladu**|Barva textu používaná pro zobrazení konců názvů souborů v okně zpětného **překladu**|
|**Zdroj zpětného překladu**|Barva textu používaná k zobrazení řádků zdroje uvnitř okna zpětného **překladu**|
|**Symbol zpětného překladu**|Barva textu používaná pro zobrazení názvů symbolů v okně zpětného **překladu**|
|**Text zpětného překladu**|Barva textu používaná pro zobrazení op-Code a data uvnitř okna zpětného **překladu** .|
|**Vyloučený kód**|Kód, který nemá být zkompilován, pro podmíněnou direktivu preprocesoru, například `#if` .|
|**Identifikátor**|Identifikátory v kódu, jako jsou názvy tříd, názvy metod a názvy proměnných.|
|**Klíčové slovo**|Klíčová slova pro daný jazyk, která jsou vyhrazena. Například: Class a Namespace.|
|**Adresa paměti**|Barva textu použitá pro zobrazení sloupce adresa v okně **paměti**|
|**Paměť změněna**|Barva textu používaná k zobrazení změněných dat v okně **paměti**|
|**Data paměti**|Barva textu používaná k zobrazení dat v okně **paměti**|
|**Paměť je nečitelná.**|Barva textu používaná k zobrazení nečitelných paměťových oblastí v okně **paměti**|
|**Číselná**|Číslo v kódu, které představuje skutečnou číselnou hodnotu.|
|**Podnikatel**|Operátory, jako jsou +,-a! =.|
|**Jiná chyba**|Jiné typy chyb, na které se nevztahují jiné chybové vlnovky. V současné době zahrnuje úpravy hrubé v úpravách a pokračování.|
|**Klíčové slovo preprocesoru**|Klíčová slova používaná preprocesorem, jako je například #include.|
|**Oblast jen pro čtení**|Kód, který nelze upravovat. Například kód zobrazený v okně zobrazení definice kódu nebo kód, který nelze změnit během úprav a pokračování.|
|**Refaktoring pozadí**|Barva pozadí dialogového okna **Náhled změn**|
|**Refaktoring aktuálního pole**|Barva pozadí aktuálního prvku, který má být refaktorovaná v dialogovém okně **Náhled změn** .|
|**Refaktorování závislého pole**|Barva odkazů elementu, který má být refaktorované v dialogovém okně **Náhled změn** .|
|**Registrovat data**|Barva textu používaná pro zobrazení dat v okně **Registry**|
|**Registrovat NAT**|Barva textu používaná k zobrazení nerozpoznaných dat a objektů uvnitř okna **Registry**|
|**Inteligentní značka**|Slouží k označení obrysu při vyvolání inteligentních značek.|
|**Značka DML SQL**|Platí pro Editor jazyka Transact-SQL. Příkazy DML v tomto editoru jsou ve výchozím nastavení označeny ohraničujícím modrým polem.|
|**Zastaralý kód**|Nahrazený kód čeká na aktualizaci. V některých případech nemůže příkaz Upravit a pokračovat okamžitě použít změny kódu, ale použije se později při pokračování ladění. K tomu dochází, pokud upravíte funkci, která musí volat aktuálně prováděnou funkci, nebo pokud přidáte více než 64 bajtů nových proměnných do funkce čekající na zásobník volání. Pokud k tomu dojde, ladicí program zobrazí dialogové okno upozornění na zastaralé kódy a nahrazený kód bude pokračovat, dokud nebude dokončena funkce a bude volána znovu. Upravit a pokračovat aplikuje změny kódu v daném čase.|
|**Řetězec**|Řetězcové literály.|
|**Řetězec (v jazyce C# @ doslovné)**|Řetězcové literály v jazyce C#, které jsou interpretovány jako doslovné. Příklad:<br /><br /> @"x"|
|**Chyba syntaxe**|Analyzovat chyby.|
|**Zástupce Seznam úkolů**|Pokud je do řádku přidána klávesová zkratka **seznam úkolů** a okraj indikátoru je zakázán, bude zvýrazněna čára.|
|**Zarážka s trasováním (zakázáno)**|Nepoužívá se.|
|**Zarážka s trasováním (povolený)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující jednoduché trasováním. Tato možnost je k dispozici pouze v případě, že je trasováním na úrovni příkazu aktivní nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** pro [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka s trasováním (chyba)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující trasováním, které jsou v chybovém stavu. Tato možnost je k dispozici pouze v případě, že je trasováním na úrovni příkazu aktivní nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** pro [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka s trasováním (upozornění)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující trasováním, které jsou ve stavu upozornění. Tato možnost je k dispozici pouze v případě, že je trasováním na úrovni příkazu aktivní nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** pro [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka s trasováním – rozšířený (zakázaný)**|Určuje barvu zvýraznění pro příkazy nebo řádky, které obsahují zakázané podmíněné nebo trasováním se započítávající volání. Tato možnost je k dispozici pouze v případě, že je trasováním na úrovni příkazu aktivní nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** pro [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka s trasováním – rozšířený (povolený)**|Určuje barvu zvýraznění pro příkazy nebo řádky, které obsahují podmíněné trasováním nebo počet vypočítaných přístupů. Tato možnost je k dispozici pouze v případě, že je trasováním na úrovni příkazu aktivní nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** pro [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka s trasováním – rozšířený (chyba)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující podmíněné nebo trasováním započítané hodnoty, které jsou v chybovém stavu. Tato možnost je k dispozici pouze v případě, že je trasováním na úrovni příkazu aktivní nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** pro [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka s trasováním – rozšířený (upozornění)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující podmíněné nebo trasováním započítané hodnoty, které jsou ve stavu upozornění. Tato možnost je k dispozici pouze v případě, že je trasováním na úrovni příkazu aktivní nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** pro [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka s trasováním – mapovaný (zakázaný)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující zakázané mapované trasováním. Platí pro ladění skriptů ASP nebo ASP.NET, pokud jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** , a to v [dialogovém okně Obecné, ladění, možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka s trasováním – mapovaný (povolený)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující namapované trasováním. Platí pro ladění skriptů ASP nebo ASP.NET, pokud jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** , a to v [dialogovém okně Obecné, ladění, možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka s trasováním-mapovaná (chyba)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující namapované trasováním v chybovém stavu. Platí pro ladění skriptů ASP nebo ASP.NET, pokud jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** , a to v [dialogovém okně Obecné, ladění, možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka s trasováním-mapovaná (upozornění)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující namapované trasováním ve stavu upozornění. Platí pro ladění skriptů ASP nebo ASP.NET, pokud jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **zvýraznit celý řádek zdroje pro zarážky nebo aktuální příkaz** , a to v [dialogovém okně Obecné, ladění, možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Sledovat změny po uložení**|Řádky kódu, které byly od otevření souboru změněny, ale uloženy na disk.|
|**Sledovat změny před uložením**|Řádky kódu, které byly od otevření souboru změněny, ale nebyly uloženy na disk.|
|**Uživatelské typy**|Typy definované uživateli|
|**Uživatelské typy (delegáti)**|Barva typu pro delegáty|
|**Uživatelské typy (výčty)**|Barva typu použitá pro výčty|
|**Uživatelské typy (rozhraní)**|Barva typu pro rozhraní|
|**Uživatelské typy (typy hodnot)**|Barva typu pro typy hodnot, jako jsou struktury v jazyce C#.|
|**Visual Basic značka jen pro čtení**|Značka specifická pro Visual Basic slouží k určení typu EnC, jako jsou například oblasti výjimek, definice metody a rámce volání mimo list.|
|**Upozornění**|Upozornění kompilátoru.|
|**Cesta k řádkům upozornění**|Používá se pro výstražné řádky statické analýzy.|
|**Atribut XML**|Názvy atributů.|
|**Uvozovky atributů XML**|Znaky uvozovek pro atributy XML|
|**Hodnota atributu XML**|Obsah atributů XML|
|**Oddíl XML CDATA**|Obsah \<![CDATA[...]]> .|
|**Komentář XML**|Obsah \<!-- --> .|
|**Oddělovač XML**|Oddělovače syntaxe XML, včetně <, <?, <!, \<!--, --> ,? \> , a \<![, ]]> [,].|
|**Atribut doc XML**|Hodnota atributu dokumentace XML, například \<param name="I"> kde je "I" zabarvení.|
|**Komentář k dokumentu XML**|Komentáře uzavřené v dokumentačních komentářích XML|
|**Značka XML doc**|Značky v komentářích k dokumentu XML, jako např.<br /><br /> /// \<summary>.|
|**XML – klíčové slovo**|Klíčová slova DTD jako CDATA, IDREF a NTYP datové.|
|**Název XML**|Názvy elementů a název cíle instrukcí pro zpracování.|
|**Instrukce pro zpracování XML**|Obsah instrukcí pro zpracování, včetně názvu cíle|
|**Text XML**|Obsah elementu prostého textu.|
|**XSLT – klíčové slovo**|Názvy elementů XSLT.|

**Popředí položky**

Zobrazuje dostupné barvy, které můžete zvolit pro popředí položky vybrané v části **Zobrazit položky**. Vzhledem k tomu, že některé položky souvisejí a měly by proto udržovat konzistentní schéma zobrazení, změna barvy popředí textu také změní výchozí hodnoty pro prvky, jako je chyba kompilátoru, klíčové slovo nebo operátor.

**Automaticky**

Položky mohou dědit barvu popředí z jiných položek zobrazení, jako je například **prostý text**. Použijete-li tuto možnost, bude při změně barvy zděděné položky zobrazení také automaticky změněna barva souvisejících položek zobrazení. Například pokud jste vybrali možnost **Automatická** hodnota pro **chybu kompilátoru** a později jste změnili barvu **prostého textu** na červenou, **Chyba kompilátoru** by také automaticky dědila červenou barvu.

**Výchozí**

Barva, která se zobrazí pro položku při prvním otevření sady Visual Studio. Kliknutím na tlačítko **použít výchozí** obnovíte tuto barvu.

**Vlastní**

Zobrazí dialogové okno barvy, které umožňuje nastavit vlastní barvu pro položku vybranou v seznamu zobrazit položky.

> [!NOTE]
> Možnost definovat vlastní barvy může být omezena nastavením barev pro zobrazení vašeho počítače. Například pokud je váš počítač nastavený na zobrazení 256 barev a v dialogovém okně **Barva** vyberete vlastní barvu, rozhraní IDE se nastaví jako výchozí k nejbližší dostupné **základní barvě** a v poli Náhled **barvy** se zobrazí černá barva.

**Pozadí položky**

Poskytuje paletu barev, ze které můžete zvolit barvu pozadí pro položku vybranou v **zobrazení položky**. Vzhledem k tomu, že některé položky jsou v relaci, a měla by proto zachovat konzistentní schéma zobrazení, změna barvy pozadí textu také změní výchozí hodnoty pro prvky, jako je chyba kompilátoru, klíčové slovo nebo operátor.

**Automaticky**

Položky mohou dědit barvu pozadí z jiných položek zobrazení, jako je například **prostý text**. Použijete-li tuto možnost, bude při změně barvy zděděné položky zobrazení také automaticky změněna barva souvisejících položek zobrazení. Například pokud jste vybrali možnost **Automatická** hodnota pro **chybu kompilátoru** a později jste změnili barvu **prostého textu** na červenou, **Chyba kompilátoru** by také automaticky dědila červenou barvu.

**Výchozí**

Barva, která se zobrazí pro položku při prvním otevření sady Visual Studio. Kliknutím na tlačítko **použít výchozí** obnovíte tuto barvu.

**Vlastní**

Zobrazí dialogové okno barvy, které umožňuje nastavit vlastní barvu pro položku vybranou v seznamu zobrazit položky.

**Bold**

Tuto možnost vyberte, chcete-li zobrazit text vybraných **položek zobrazení** v tučném textu. V editoru je snadnější identifikovat tučný text.

**Ukázka**

Zobrazí ukázku stylu písma, velikosti a barevného schématu pro vybrané položky **Zobrazit nastavení pro** a **zobrazené položky** . Pomocí tohoto pole můžete zobrazit náhled výsledků při experimentování s různými možnostmi formátování.

## <a name="see-also"></a>Viz také

- [Dialogové okno Možnosti](../../ide/reference/options-dialog-box-visual-studio.md)
- [Postupy: Změna písma a barev](../../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
