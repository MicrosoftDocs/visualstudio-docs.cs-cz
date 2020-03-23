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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595615"
---
# <a name="fonts-and-colors-environment-options-dialog-box"></a>Písma a barvy, prostředí, dialogové okno Možnosti

Stránka **Písma a barvy** v dialogovém okně **Možnosti** umožňuje vytvořit vlastní písmo a barevné schéma pro různé prvky uživatelského rozhraní v integrovaném vývojovém prostředí (IDE). K tomuto dialogovému oknu se dostanete klepnutím na**položku Možnosti** **nástroje** > a výběrem**možnosti Písma a barvy** **prostředí** > .

Změny barevného schématu se neprojeví během relace, ve které je provedete. Změny barev můžete vyhodnotit otevřením jiné instance sady Visual Studio a vytvořením podmínek, za kterých očekáváte, že změny použít.

**Zobrazit nastavení pro**

Zobrazí seznam všech prvků uživatelského rozhraní, pro které můžete změnit písma a barevná schémata. Po výběru položky z tohoto seznamu můžete přizpůsobit nastavení barev pro položku vybranou v **části Zobrazit položky**.

- **Textový editor**

     Změny nastavení stylu, velikosti a zobrazení barev pro textový editor ovlivňují vzhled textu ve výchozím textovém editoru. Dokumenty otevřené v textovém editoru mimo rozhraní IDE nebudou těmito nastaveními ovlivněny.

- **Tiskárna**

     Změny nastavení stylu, velikosti a zobrazení barev pro tiskárnu ovlivňují vzhled textu v tištěných dokumentech.

    > [!NOTE]
    > Podle potřeby můžete vybrat jiné výchozí písmo pro tisk, než které se používá pro zobrazení v textovém editoru. To může být užitečné při tisku kódu, který obsahuje jednobajtové i dvoubajtové znaky.

- **Doplňování výrazů**

     Změní styl a velikost písma pro text, který se zobrazí v rozbalovacím okně dokončování příkazů v editoru.

- **Popisek editoru**

     Změní styl a velikost písma pro text, který se zobrazí v popiscích zobrazených v editoru.

- **Písmo prostředí**

     Změní styl a velikost písma pro všechny prvky uživatelského rozhraní IDE, které ještě nemají samostatnou možnost v **nastavení zobrazit pro**.

     ::: moniker range="vs-2017"

     Tato možnost se například vztahuje na **úvodní stránku,** ale nemá vliv na okno **Výstup.**

     ::: moniker-end

- **[Všechny textové nástroje Windows]**

     Změny nastavení stylu, velikosti a zobrazení barev pro tuto položku ovlivňují vzhled textu v oknech nástrojů, která mají výstupní podokna v prostředí IDE. Například okno Výstup, Okno příkazu, Okamžité okno atd.

    > [!NOTE]
    > Změny textu položek **[Všechny textové nástroje systému Windows]** se neprojeví během relace, ve které je provedete. Tyto změny můžete vyhodnotit otevřením jiné instance sady Visual Studio.

**Použít výchozí hodnoty**

Obnoví hodnoty písma a barev položky seznamu vybrané v **části Zobrazit nastavení pro aplikace**. Tlačítko **Použít** se zobrazí, když jsou k dispozici pro výběr jiná schémata zobrazení. Můžete si například vybrat ze dvou schémat pro tiskárnu.

**Písmo (tučné písmo označuje písma s pevnou šířkou)**

Zobrazí seznam všech písem nainstalovaných v systému. Když se poprvé zobrazí rozevírací nabídka, zvýrazní se aktuální písmo prvku vybraného v poli **Zobrazit nastavení pro** pole. Pevná písma, která se v editoru snadněji zarovnávají, se zobrazují tučně.

**Velikost**

Zobrazí dostupné velikosti bodů zvýrazněného písma. Změna velikosti písma ovlivní všechny **položky zobrazení** **pro nastavení zobrazení pro** výběr.

**Zobrazit položky**

Zobrazí seznam položek, u kterých můžete upravit barvu popředí a pozadí.

> [!NOTE]
> **Prostý text** je výchozí položka zobrazení. Vlastnosti přiřazené **ke formátu PlainText** budou takto přepsány vlastnostmi přiřazenými jiným položkám zobrazení. Pokud například přiřadíte modrou barvu **plaintextu** a zelenou barvu **identifikátoru**, všechny identifikátory se zobrazí zeleně. V tomto příkladu vlastnosti **identifikátoru** přepíší vlastnosti **prostého textu.**

Některé položky zobrazení zahrnují:

|Zobrazit položku|Popis|
|------------------|-----------------|
|**Prostý text**|Text v editoru.|
|**Vybraný text**|Text, který je zahrnut v aktuálním výběru, když má editor fokus.|
|**Neaktivní vybraný text**|Text, který je zahrnut do aktuálního výběru, když editor ztratil fokus.|
|**Ukazatel marže**|Okraj vlevo od Editoru kódu, kde jsou zobrazeny zarážky a ikony záložek.|
|**Čísla řádků**|Volitelná čísla, která se zobrazují vedle každého řádku kódu|
|**Viditelné prázdné místo**|Mezery, tabulátory a indikátory zalamování slov|
|**Záložka**|Řádky, které mají záložky. **Záložka** je viditelná pouze v případě, že je indikátorová marže zakázána.|
|**Porovnávání složených závorek (zvýraznění)**|Zvýraznění, které je obvykle tučné formátování pro odpovídající závorky.|
|**Porovnávání složených závorek (obdélník)**|Zvýraznění, které je obvykle šedý obdélník na pozadí.|
|**Zarážka (zakázáno)**|Nepoužívá se.|
|**Zarážka (povolena)**|Určuje barvu zvýraznění pro příkazy nebo čáry obsahující jednoduché zarážky. Tato možnost je použitelná pouze v případě, že jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, Ladění, Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka (chyba)**|Určuje barvu zvýraznění pro příkazy nebo čáry obsahující zarážky, které jsou v chybovém stavu. Použitelné pouze v případě, že jsou aktivní zarážky na úrovni příkazu nebo je v [dialogovém okně Obecné, Ladění, Možnosti vybrána](../../debugger/general-debugging-options-dialog-box.md)možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální výpis** .|
|**Zarážka (upozornění)**|Určuje barvu zvýraznění pro příkazy nebo čáry obsahující zarážky, které jsou ve stavu upozornění. Použitelné pouze v případě, že jsou aktivní zarážky na úrovni příkazu nebo je v [dialogovém okně Obecné, Ladění, Možnosti vybrána](../../debugger/general-debugging-options-dialog-box.md)možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální výpis** .|
|**Zarážka – upřesnit (zakázáno)**|Určuje barvu zvýraznění pro příkazy nebo čáry obsahující zakázané podmíněné nebo spočítané zarážky. Použitelné pouze v případě, že jsou aktivní zarážky na úrovni příkazu nebo je v [dialogovém okně Obecné, Ladění, Možnosti vybrána](../../debugger/general-debugging-options-dialog-box.md)možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální výpis** .|
|**Zarážka – upřesnit (povoleno)**|Určuje barvu zvýraznění pro příkazy nebo čáry obsahující podmíněné zarážky nebo zarážky spočítané zásahem. Použitelné pouze v případě, že jsou aktivní zarážky na úrovni příkazu nebo je v [dialogovém okně Obecné, Ladění, Možnosti vybrána](../../debugger/general-debugging-options-dialog-box.md)možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální výpis** .|
|**Zarážka – upřesnit (chyba)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující podmíněné nebo spočítané zarážky, které jsou v chybovém stavu. Použitelné pouze v případě, že jsou aktivní zarážky na úrovni příkazu nebo je v [dialogovém okně Obecné, Ladění, Možnosti vybrána](../../debugger/general-debugging-options-dialog-box.md)možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální výpis** .|
|**Zarážka – upřesnit (upozornění)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující podmíněné nebo spočítané zarážky, které jsou ve stavu upozornění. Použitelné pouze v případě, že jsou aktivní zarážky na úrovni příkazu nebo je v [dialogovém okně Obecné, Ladění, Možnosti vybrána](../../debugger/general-debugging-options-dialog-box.md)možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální výpis** .|
|**Zarážka – mapováno (zakázáno)**|Určuje barvu zvýraznění pro příkazy nebo čáry obsahující zakázané mapované zarážky. Použitelné pro ladění Technologie ASP nebo ASP.NET, pokud jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, Ladění a Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka – mapováno (povoleno)**|Určuje barvu zvýraznění pro příkazy nebo čáry obsahující mapované zarážky. Použitelné pro ladění Technologie ASP nebo ASP.NET, pokud jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, Ladění a Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka – mapováno (chyba)**|Určuje barvu zvýraznění pro příkazy nebo čáry obsahující mapované zarážky v chybovém stavu. Použitelné pro ladění Technologie ASP nebo ASP.NET, pokud jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, Ladění a Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Zarážka – mapováno (upozornění)**|Určuje barvu zvýraznění pro příkazy nebo čáry obsahující mapované zarážky ve stavu upozornění. Použitelné pro ladění Technologie ASP nebo ASP.NET, pokud jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, Ladění a Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Uživatelská klíčová slova jazyka C/C++**|Konstanta v rámci souboru kódu `#define` definované pomocí směrnice.|
|**Návrat volání**|Určuje barvu zvýraznění pro zdrojové příkazy nebo řádky, které označují body zpětného volání při přepnutí kontextu do rámce nenejvyššího zásobníku při ladění.|
|**Pole závislé na fragmentu kódu**|Pole, které bude aktualizováno při změně aktuálního upravitelného pole.|
|**Pole fragmentu kódu**|Upravitelné pole, když je aktivní fragment kódu.|
|**Sbalitelný text**|Blok textu nebo kódu, který lze přepnout dovnitř a ven z pohledu v editoru kódu.|
|**Komentář**|Komentáře kódu.|
|**Chyba kompilátoru**|Modré vlnovky v editoru označující chybu kompilátoru.|
|**Oblast pokrytí se nedotkla**|Kód, který nebyl zahrnut do testování částí.|
|**Pokrytí částečně dotkl oblasti**|Kód, který byl částečně zahrnuta do testování částí.|
|**Pokrytí Dotkl oblast**|Kód, který byl zcela pokryt a testování částí.|
|**CsS Komentář**|Komentář v kaskádových šablonách stylů. Například:<br /><br /> /* komentář\*/|
|**Klíčové slovo CSS**|Klíčová slova v šabloně stylů Kaskádového stylu.|
|**Název vlastnosti CSS**|Název vlastnosti, například Background.|
|**Hodnota vlastnosti CSS**|Hodnota přiřazená vlastnosti, jako je například modrá.|
|**Výběr CSS**|Řetězec, který identifikuje, jaké prvky se vztahuje odpovídající pravidlo. Voličem může být buď jednoduchý volič, například "H1", nebo kontextový volič, například "H1 B", který se skládá z několika jednoduchých selektorů.|
|**Hodnota řetězce CSS**|Řetězec v kaskádových šablonách stylů.|
|**Aktuální umístění seznamu**|Aktuální řádek navigoval v okně nástroje seznamu, například v okně Výstup nebo v oknech Najít výsledky.|
|**Aktuální výpis**|Určuje barvu zvýraznění pro zdrojový příkaz nebo řádek, který označuje aktuální pozici kroku při ladění.|
|**Data ladicího programu byla změněna**|Barva textu použitá k zobrazení změněných dat v **oknech Registry a** **Memory.**|
|**Pozadí okna definice**|Barva pozadí okna **Definice kódu.**|
|**Aktuální shoda okna definice**|Aktuální definice v okně **Definice kódu.**|
|**Rozebrání názvu souboru**|Barva textu použitá k zobrazení názvu souboru se v okně **Demontáže** přeruší.|
|**Zdroj demontáže**|Barva textu použitá k zobrazení zdrojových řádků uvnitř okna **Demontáže.**|
|**Symbol demontáže**|Barva textu použitá k zobrazení názvů symbolů uvnitř okna **Demontáže.**|
|**Rozebrání textu**|Barva textu použitá k zobrazení operačního kódu a dat uvnitř okna **Demontáže.**|
|**Vyloučený kód**|Kód, který není třeba zkompilovat, na `#if`podmíněné preprocesorové směrnice, jako je například .|
|**Identifikátor**|Identifikátory v kódu, jako jsou názvy tříd, názvy metod a názvy proměnných.|
|**Klíčové slovo**|Klíčová slova pro daný jazyk, které jsou vyhrazeny. Příklad: třída a obor názvů.|
|**Adresa paměti**|Barva textu použitá k zobrazení sloupce adresy v okně **Paměť.**|
|**Paměť se změnila**|Barva textu použitá k zobrazení změněných dat v okně **Paměť.**|
|**Paměťová data**|Barva textu použitá k zobrazení dat v okně **Paměť.**|
|**Paměť nečitelná**|Barva textu použitá k zobrazení nečitelných oblastí paměti v okně **Paměť.**|
|**Číslo**|Číslo v kódu, které představuje skutečnou číselnou hodnotu.|
|**Operátor**|Operátory jako +, -a !=.|
|**Jiná chyba**|Jiné typy chyb, které nejsou zahrnuty do jiných chyb vlnovky. V současné době to zahrnuje hrubé úpravy v upravit a pokračovat.|
|**Klíčové slovo preprocesoru**|Klíčová slova používaná preprocesorem, například #include.|
|**Oblast jen pro čtení**|Kód, který nelze upravit. Například kód zobrazený v okně Zobrazení definice kódu nebo kód, který nelze změnit během úprav a pokračovat.|
|**Refaktoring pozadí**|Barva pozadí dialogového okna **Změny náhledu**|
|**Refaktoring aktuálního pole**|Barva pozadí aktuálního prvku, který má být refaktorován v dialogovém okně **Změny náhledu.**|
|**Refaktoring závislého pole**|Barva odkazů na prvek, který má být refaktorován v dialogovém okně **Změny náhledu.**|
|**Zaregistrovat data**|Barva textu použitá k zobrazení dat v okně **Registrys.**|
|**Zaregistrovat NAT**|Barva textu použitá k zobrazení nerozpoznaných dat a objektů v okně **Registrys.**|
|**Inteligentní značka**|Používá se k označení osnovy při vyvolání inteligentních značek.|
|**Značka SQL DML**|Platí pro editor Transact-SQL. Příkazy DML v tomto editoru jsou ve výchozím nastavení označeny ohraničujícím modrým rámečkem.|
|**Zastaralý kód**|Nahrazený kód čekající na aktualizaci. V některých případech upravit a pokračovat nelze použít změny kódu okamžitě, ale bude použít později, jak budete pokračovat v ladění. K tomu dochází, pokud upravíte funkci, která musí volat aktuálně spuštěnou funkci, nebo pokud přidáte více než 64 bajtů nových proměnných do funkce čekající v zásobníku volání. V takovém případě ladicí program zobrazí dialogové okno "Zastaralé upozornění kódu" a nahrazený kód pokračuje v provádění, dokud dotyčná funkce nedokončí a nebude znovu volána. Upravit a pokračovat použije změny kódu v té době.|
|**Řetězec**|Řetězcové literály.|
|**Řetězec (C# @ Verbatim)**|Řetězcové literály v c#, které jsou interpretovány doslovně. Například:<br /><br /> @"x"|
|**Chyba syntaxe**|Analyzovat chyby.|
|**Zástupce seznamu úkolů**|Pokud je zástupce **seznamu úkolů** přidán k řádku a okraj ukazatele je zakázán, řádek se zvýrazní.|
|**Trasovací bod (zakázáno)**|Nepoužívá se.|
|**Trasovací bod (povoleno)**|Určuje barvu zvýraznění pro příkazy nebo čáry obsahující jednoduché stopovací body. Tato možnost je použitelná pouze v případě, že jsou aktivní trasovací body na úrovni příkazu nebo je vybrána možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, Ladění, Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Tracepoint (chyba)**|Určuje barvu zvýraznění pro příkazy nebo čáry obsahující trasovací body, které jsou v chybovém stavu. Tato možnost je použitelná pouze v případě, že jsou aktivní trasovací body na úrovni příkazu nebo je vybrána možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, Ladění, Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Trasovací bod (upozornění)**|Určuje barvu zvýraznění pro příkazy nebo čáry obsahující trasovací body, které jsou ve stavu upozornění. Tato možnost je použitelná pouze v případě, že jsou aktivní trasovací body na úrovni příkazu nebo je vybrána možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, Ladění, Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Tracepoint - Upřesnit (zakázáno)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující zakázané podmíněné stopovací body nebo stopované body spočítané přístupem. Tato možnost je použitelná pouze v případě, že jsou aktivní trasovací body na úrovni příkazu nebo je vybrána možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, Ladění, Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Tracepoint - upřesnit (povoleno)**|Určuje barvu zvýraznění pro příkazy nebo čáry obsahující podmíněné stopovací body nebo stopované body spočítané přístupem. Tato možnost je použitelná pouze v případě, že jsou aktivní trasovací body na úrovni příkazu nebo je vybrána možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, Ladění, Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Tracepoint - Upřesnit (chyba)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující podmíněné stopovací body nebo stopovací body spočítané přístupem, které jsou v chybovém stavu. Tato možnost je použitelná pouze v případě, že jsou aktivní trasovací body na úrovni příkazu nebo je vybrána možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, Ladění, Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Tracepoint - Upřesnit (upozornění)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující podmíněné stopovací body nebo stopovací body spočítané přístupem, které jsou ve stavu upozornění. Tato možnost je použitelná pouze v případě, že jsou aktivní trasovací body na úrovni příkazu nebo je vybrána možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, Ladění, Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Tracepoint - mapováno (zakázáno)**|Určuje barvu zvýraznění pro příkazy nebo čáry obsahující zakázané mapované trasovací body. Použitelné pro ladění Technologie ASP nebo ASP.NET, pokud jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, Ladění a Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Tracepoint - mapováno (povoleno)**|Určuje barvu zvýraznění pro příkazy nebo čáry obsahující mapované stopovací body. Použitelné pro ladění Technologie ASP nebo ASP.NET, pokud jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, Ladění a Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Tracepoint - mapováno (chyba)**|Určuje barvu zvýraznění pro příkazy nebo čáry obsahující mapované trasovací body v chybovém stavu. Použitelné pro ladění Technologie ASP nebo ASP.NET, pokud jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, Ladění a Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Tracepoint - mapováno (upozornění)**|Určuje barvu zvýraznění pro příkazy nebo čáry obsahující mapované trasovací body ve stavu upozornění. Použitelné pro ladění Technologie ASP nebo ASP.NET, pokud jsou aktivní zarážky na úrovni příkazu nebo je vybrána možnost **Zvýraznit celý zdrojový řádek pro zarážky nebo aktuální příkaz** v [dialogovém okně Obecné, Ladění a Možnosti](../../debugger/general-debugging-options-dialog-box.md).|
|**Sledování změn po uložení**|Řádky kódu, které byly od otevření souboru změněny, ale jsou uloženy na disk.|
|**Sledování změn před uložením**|Řádky kódu, které byly změněny od otevření souboru, ale nejsou uloženy na disk.|
|**Typy uživatelů**|Typy definované uživateli.|
|**Typy uživatelů (delegáti)**|Zadejte barvu pro delegáty.|
|**Typy uživatelů (výčty)**|Zadejte barvu použitou pro výčty.|
|**Typy uživatelů (rozhraní)**|Zadejte barvu pro rozhraní.|
|**Typy uživatelů (typy hodnot)**|Zadejte barvu pro typy hodnot, jako jsou struktury v c#.|
|**Značka jen pro čtení v jazyce Visual Basic**|Značka specifická pro jazyk Visual Basic používaná pro označení enc, jako jsou oblasti výjimek, definice metody a rámce volání mimo list.|
|**Upozornění**|Upozornění kompilátoru.|
|**Cesta k výstražným čarám**|Používá se pro řádky upozornění statické analýzy.|
|**Atribut XML**|Názvy atributů.|
|**Uvozovky atributů XML**|Znaky uvozovek pro atributy XML.|
|**Hodnota atributu XML**|Obsah atributů XML.|
|**Oddíl Cdata XML**|Obsah \<! [CDATA[...]] >.|
|**Komentář XML**|Obsah \<!-- -->.|
|**Oddělovač XML**|Oddělovače syntaxe XML, včetně <, \<<?, <!, !--, -->? \>, \<! [, ]] > a [, ].|
|**Atribut dokumentu XML**|Hodnota atributu dokumentace xml, \<například param name="I"> kde je "I" obarven.|
|**Komentář dokumentu XML**|Komentáře přiložené v dokumentaci xml komentáře.|
|**Značka doc XML**|Tagy v komentářích dokumentu XML, například<br /><br /> /// \<souhrnné ho>.|
|**Klíčové slovo XML**|Klíčová slova DTD, například CDATA, IDREF a NDATA.|
|**Název XML**|Názvy prvků a název cíle pokyny pro zpracování.|
|**Instrukce zpracování XML**|Obsah pokynů pro zpracování, bez cílového názvu.|
|**XML Text**|Obsah prvku prostého textu.|
|**Klíčové slovo XSLT**|Názvy prvků XSLT.|

**Popředí položky**

Zobrazí seznam dostupných barev, které můžete zvolit pro popředí položky vybrané v **části Zobrazit položky**. Vzhledem k tomu, že některé položky souvisejí a proto by měly udržovat konzistentní schéma zobrazení, změna barvy textu v popředí také změní výchozí hodnoty pro prvky, jako je chyba kompilátoru, klíčové slovo nebo operátor.

**Automaticky**

Položky mohou dědit barvu popředí z jiných položek zobrazení, jako je **prostý text**. Při použití této možnosti se při změně barvy zděděné položky zobrazení automaticky změní také barva souvisejících položek zobrazení. Pokud jste například vybrali **automatickou** hodnotu pro **chybu kompilátoru** a později jste změnili barvu prostého textu na **červenou,** **chyba kompilátoru** také automaticky zdědí červenou barvu.

**Výchozí**

Barva, která se zobrazí pro položku při prvním otevření sady Visual Studio. Kliknutím na tlačítko **Použít výchozí nastavení** se tato barva obnoví.

**Vlastní**

Zobrazí dialogové okno Barva, které vám umožní nastavit vlastní barvu pro položku vybranou v seznamu Zobrazit položky.

> [!NOTE]
> Možnost definovat vlastní barvy může být omezena nastavením barev pro zobrazení počítače. Pokud je například počítač nastaven na zobrazení 256 barev a v dialogovém okně **Barva** vyberete vlastní barvu, rozhraní IDE bude ve výchozím nastavení nastaveno na nejbližší **dostupnou základní barvu** a zobrazí barvu černě v poli Náhled **barvy.**

**Pozadí položky**

Poskytuje paletu barev, ze které můžete zvolit barvu pozadí pro položku vybranou v **části Zobrazit položky**. Vzhledem k tomu, že některé položky souvisejí a proto by měly udržovat konzistentní schéma zobrazení, změna barvy pozadí textu také změní výchozí hodnoty pro prvky, jako je chyba kompilátoru, klíčové slovo nebo operátor.

**Automaticky**

Položky mohou dědit barvu pozadí z jiných položek zobrazení, například **prostého textu**. Při použití této možnosti se při změně barvy zděděné položky zobrazení automaticky změní také barva souvisejících položek zobrazení. Pokud jste například vybrali **automatickou** hodnotu pro **chybu kompilátoru** a později jste změnili barvu prostého textu na **červenou,** **chyba kompilátoru** také automaticky zdědí červenou barvu.

**Výchozí**

Barva, která se zobrazí pro položku při prvním otevření sady Visual Studio. Kliknutím na tlačítko **Použít výchozí nastavení** se tato barva obnoví.

**Vlastní**

Zobrazí dialogové okno Barva, které vám umožní nastavit vlastní barvu pro položku vybranou v seznamu Zobrazit položky.

**Tučný**

Tuto možnost vyberte, chcete-li zobrazit text vybraných **položek zobrazení** tučným písmem. Tučný text je snadněji identifikovatelný v editoru.

**Ukázka**

Zobrazí ukázku stylu, velikosti a barevného schématu pro vybrané **nastavení zobrazení** a **zobrazení položek.** Toto pole můžete použít k zobrazení náhledu výsledků při experimentování s různými možnostmi formátování.

## <a name="see-also"></a>Viz také

- [Dialogové okno Možnosti](../../ide/reference/options-dialog-box-visual-studio.md)
- [Postupy: Změna písma a barev](../../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
