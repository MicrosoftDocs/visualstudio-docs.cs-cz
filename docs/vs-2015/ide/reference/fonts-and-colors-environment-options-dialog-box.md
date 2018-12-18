---
title: Písma a barvy, prostředí, dialogové okno Možnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPag.Environment.Fonts_And_Colors
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
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dbaaab64a50a918844a8f9060ce80ee8c8e7ae00
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220232"
---
# <a name="fonts-and-colors-environment-options-dialog-box"></a>Písma a barvy, prostředí, dialogové okno Možnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
**Písma a barvy** stránku **možnosti** dialogové okno umožňuje vytvořit vlastní písma a barvy režim pro různé prvky uživatelského rozhraní v integrovaném vývojovém prostředí (IDE). Toto dialogové okno se zpřístupní po kliknutí **Nástroje / možnosti**a pak vyberete **prostředí / písma a barvy**. Pokud se tato stránka se nezobrazí v seznamu, vyberte **zobrazit všechna nastavení** v **možnosti** dialogové okno.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Barevné schéma změny se projeví během relace, ve kterém je provedete. Změny barev můžete vyhodnotit otevřením jiná instance sady Visual Studio a vytváření podmínky, za kterých očekáváte, že vaše změny se můžou použít.  
  
 **Zobrazit nastavení pro**  
 Obsahuje seznam všech prvků uživatelského rozhraní, pro které můžete změnit písma a barevná schémata. Po výběru položky z tohoto seznamu můžete upravit nastavení barev pro vybranou položku v **zobrazení položek**.  
  
- **Textový Editor**  
  
   Změny styl písma, velikosti a zobrazení nastavení barev pro textový Editor vliv na vzhled textu v textovém editoru výchozí. Tato nastavení se nevztahuje dokumenty otevřené v textovém editoru mimo rozhraní IDE.  
  
- **Tiskárny**  
  
   Změny styl písma, velikosti a zobrazení nastavení barev pro tiskárnu vliv na vzhled textu v dokumentu.  
  
  > [!NOTE]
  >  Podle potřeby, můžete vybrat různé výchozí písmo pro tisk než, který používá pro zobrazení v textovém editoru. To může být užitečné při tisku kódu, který obsahuje jednobajtových a dvoubajtových znaků.  
  
- **Dokončování příkazů**  
  
   Změní styl písma a velikost textu, který se zobrazí v doplňování výrazů rozbalovací v editoru.  
  
- **Nápověda editoru**  
  
   Změní styl písma a velikost textu, který se zobrazí v popisu zobrazí v editoru.  
  
- **Písmo prostředí**  
  
   Mění styl písma a velikost pro všechny prvky uživatelského rozhraní IDE, které ještě nemají samostatnou možností v **zobrazit nastavení pro.** Například tato možnost se vztahuje na **úvodní stránka** ale nebude mít vliv **výstup** okna.  
  
- **[Všechny textový nástroj Windows]**  
  
   Změny písmo, velikost a barvu zobrazit nastavení pro tuto položku vliv na vzhled textu v oknech nástrojů, které mají výstupní podokna v integrovaném vývojovém prostředí. Například okno výstup, okno příkazového řádku, hodnot proměnných atd.  
  
  > [!NOTE]
  >  Změní text **[všechny textový nástroj Windows]** položky projeví během relace, ve kterém je provedete. Můžete si vyzkoušet tyto změny tak, že otevřete jinou instanci aplikace Visual Studio.  
  
  **Použít výchozí nastavení**  
  Obnoví písma a barvy hodnoty seznamu položky vybrané v **zobrazit nastavení pro**. **Použití** tlačítko se zobrazí, když jsou k dispozici pro výběr jiné režimy zobrazení. Můžete například zvolit ze dvou režimů tiskárny.  
  
  **Písmo (tučné písmo označuje neproporcionální písma)**  
  Zobrazí seznam všech písem nainstalovaný ve vašem systému. Když poprvé objeví v rozevírací nabídce, aktuální písmo vybrané v elementu **zobrazit nastavení pro** pole je zvýrazněn. Oprava písma – což je snazší zarovnání v editoru – zobrazí tučným písmem.  
  
  **Velikost**  
  Seznamy, které jsou k dispozici bod velikosti zvýrazněné písma. Změna velikosti písma ovlivní všechny **zobrazení položek** pro **zobrazit nastavení pro** výběru.  
  
  **Zobrazení položek**  
  Zobrazí seznam položek, pro které můžete změnit barvu popředí a pozadí.  
  
> [!NOTE]
>  **Prostý Text** je výchozí zobrazení položky. V důsledku toho vlastnosti přiřazená **ve formátu prostého textu** podle vlastností, které jsou přiřazeny k ostatním položkám zobrazení, budou ignorovány. Například, pokud přiřadíte k modrou barvu **ve formátu prostého textu** a na zelenou barvu **identifikátor**, všechny identifikátory se zobrazí zeleně. V tomto příkladu **identifikátor** přepsání vlastnosti **ve formátu prostého textu** vlastnosti.  
  
 Zobrazit položky patří:  
  
|Zobrazení položky|Popis|  
|------------------|-----------------|  
|**Prostý Text**|Text v editoru.|  
|**Vybraný Text**|Text, který je součástí aktuální výběr, když je editoru fokus.|  
|**Neaktivní vybraný Text**|Text, který je součástí aktuální výběr, pokud editor ztratil fokus.|  
|**Okraj indikátoru**|Okraj na levé straně editoru kódu ve kterém se zobrazují zarážky a záložky ikony.|  
|**Čísla řádků**|Volitelné čísla, která se zobrazí vedle každého řádku kódu|  
|**Viditelné prázdné znaky**|Mezery, tabulátory a indikátory zalamování řádků|  
|**záložky**|Řádky, které mají záložky. **Záložka** je viditelné pouze pokud je zakázán okraj indikátoru.|  
|**Související závorky (zvýraznit)**|Zvýraznění, které je obvykle tučné písmo pro párování složených závorek.|  
|**Související závorky (obdélník)**|Zvýraznění, které je obvykle šedou obdélník na pozadí.|  
|**Bod přerušení (vypnut)**|Nepoužívá se.|  
|**Bod přerušení (zapnut)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující jednoduché zarážky. Tato možnost se vztahuje pouze v případě, že příkaz úrovni zarážky jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|  
|**Bod přerušení (chyba)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující zarážek, které jsou v chybovém stavu. Použít pouze v případě, že příkaz úrovni zarážky jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|  
|**Bod přerušení (upozornění)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující zarážek, které jsou ve varovném stavu. Použít pouze v případě, že příkaz úrovni zarážky jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|  
|**Zarážka - rozšířená (zakázána)**|Určuje barvu zvýraznění pro příkazy nebo řádky, které obsahují zakázané podmíněný nebo daným počtem průchodů zarážky. Použít pouze v případě, že příkaz úrovni zarážky jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|  
|**Zarážka - rozšířená (povolena)**|Určuje barvu zvýraznění pro příkazy nebo řádky, které obsahují podmíněné nebo daným počtem průchodů zarážky. Použít pouze v případě, že příkaz úrovni zarážky jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|  
|**Zarážka - rozšířená (chyba)**|Určuje barvu zvýraznění pro příkazy nebo řádky, které obsahují podmíněné nebo daným počtem průchodů zarážky, které jsou v chybovém stavu. Použít pouze v případě, že příkaz úrovni zarážky jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|  
|**Zarážka - rozšířená (varování)**|Určuje barvu zvýraznění pro příkazy nebo řádky, které obsahují podmíněné nebo stiskněte referenčně započítaný zarážek, které jsou ve varovném stavu. Použít pouze v případě, že příkaz úrovni zarážky jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|  
|**Zarážka - mapovaná (zakázána)**|Určuje barvu zvýraznění pro příkazy nebo řádky, které obsahují zakázané mapované zarážky. Platí pro ASP nebo ASP.NET ladění, pokud příkaz úrovni zarážky jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti Pole](../../debugger/general-debugging-options-dialog-box.md).|  
|**Zarážka - mapovaná (povolena)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující namapované zarážky. Platí pro ASP nebo ASP.NET ladění, pokud příkaz úrovni zarážky jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti Pole](../../debugger/general-debugging-options-dialog-box.md).|  
|**Zarážka - mapovaná (chyba)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující namapované zarážky v chybovém stavu. Platí pro ASP nebo ASP.NET ladění, pokud příkaz úrovni zarážky jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti Pole](../../debugger/general-debugging-options-dialog-box.md).|  
|**Zarážka - mapovaná (varování)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující namapované zarážky ve varovném stavu. Platí pro ASP nebo ASP.NET ladění, pokud příkaz úrovni zarážky jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti Pole](../../debugger/general-debugging-options-dialog-box.md).|  
|**Uživatelská klíčová slova C/C++**|Konstanty v souboru kódu definované prostřednictvím `#define` směrnice.|  
|**Zavolat návrat**|Určuje barvu zvýraznění pro příkazy zdrojového nebo řádky, které indikují volání návratový body při přepnutí kontextu na-horní části zásobníku při ladění.|  
|**Závislé na fragmentu kódu**|Pole, které budou aktualizovány, když se změní aktuální upravitelné pole.|  
|**Pole fragmentů kódu**|Upravitelné pole při aktivním fragmentu kódu.|  
|**Sbalitelné Text**|Blok textu nebo kód, který lze přepínat do zobrazení v editoru kódu.|  
|**Komentář**|Komentáře ke kódu.|  
|**Chyba kompilátoru**|V editoru udávající chybu kompilátoru modrou vlnovkou.|  
|**Pokrytím nedotčená oblast**|Kód, která není předmětem testování částí.|  
|**Pokrytím částečně dotčená oblast**|Kód, který má částečně pokryty ve testování částí.|  
|**Pokrytím dotčená oblast**|Kód, který je zcela popsaná pomocí testování částí.|  
|**Komentář CSS**|Komentář do šablony stylů CSS. Příklad:<br /><br /> / * Komentář \*/|  
|**Klíčové slovo CSS**|Klíčová slova v stylů CSS.|  
|**Název vlastnosti CSS**|Název vlastnosti, jako je například na pozadí.|  
|**Hodnota vlastnosti CSS**|Hodnota přiřazená k vlastnosti, například modrá.|  
|**Selektor šablon stylů CSS**|Řetězec, který identifikuje prvky odpovídající pravidlo vztahuje. Selektor může být buď jednoduchého selektoru, takové "H1" nebo kontextové selektor, jako je například "H1 B", který se skládá z několika jednoduchých selektorů.|  
|**Hodnota řetězce šablon stylů CSS**|Řetězec v kaskádová šablona stylů.|  
|**Aktuální seznam umístění**|Aktuální řádek přejde v panelu nástrojů seznamu, jako je například okno výstupu nebo windows výsledky hledání.|  
|**Aktuální příkaz**|Určuje barvu zvýraznění u příkazu source ani určující aktuální pozici krok při ladění.|  
|**Změny dat ladicího programu**|Barva textu slouží k zobrazení změněná data uvnitř **zaregistruje** a **paměti** systému windows.|  
|**Definice pozadí okna**|Barva pozadí **definice kódu** okna.|  
|**Definice okna aktuální shody**|V aktuální definici **definice kódu** okna.|  
|**Název souboru zpětného překladu**|Barva textu slouží k zobrazení konce názvu souboru uvnitř **zpětný překlad** okna.|  
|**Zdroj zpětného překladu**|Barva textu slouží k zobrazení zdrojové řádky uvnitř **zpětný překlad** okna.|  
|**Symbol zpětného překladu**|Barva textu slouží k zobrazení názvy symbolů uvnitř **zpětný překlad** okna.|  
|**Text zpětného překladu**|Barva textu slouží k zobrazení operační kód a data uvnitř **zpětný překlad** okna.|  
|**Vyřazený kód**|Kód, který není ke kompilaci, za podmíněné direktivy preprocesoru, jako je `#if`.|  
|**identifikátor**|Identifikátory v kódu, jako jsou názvy tříd, metod názvy a názvy proměnných.|  
|**Klíčové slovo**|Klíčová slova pro daný jazyk, které jsou vyhrazené. Příklad: třídy a oboru názvů.|  
|**Adresa paměti**|Barva textu slouží k zobrazení sloupce Adresa uvnitř **paměti** okna.|  
|**Paměť změněna**|Barva textu slouží k zobrazení změněná data uvnitř **paměti** okna.|  
|**Data paměti**|Barva textu slouží k zobrazení dat uvnitř **paměti** okna.|  
|**Paměť není čitelná**|Barva textu slouží k zobrazení nečitelná paměť oblastí v rámci **paměti** okna.|  
|**Číslo**|Číslo v kódu, který představuje skutečný číselnou hodnotu.|  
|**– Operátor**|Operátory, jako například +, -, a! =.|  
|**Jiná chyba**|Jiné typy chyb, není pokrytá jiných podtržení vlnovkou u chyb. V současné době to zahrnuje článku neslušní úpravy v dialogu Upravit a pokračovat.|  
|**Klíčové slovo preprocesoru**|Klíčová slova používaná preprocesorem jako #include.|  
|**Oblast jen pro čtení**|Kód, který nelze upravit. Například kód zobrazený v okně zobrazení definice kódu nebo kód, který nelze změnit během příkazu upravit a pokračovat.|  
|**Pozadí refaktorování**|Barva pozadí **náhled změn** dialogové okno.|  
|**Refaktorování aktuálního pole**|Barva aktuálního elementu má být refaktorovány v pozadí **náhled změn** dialogové okno.|  
|**Refaktorování závislého pole**|Barva odkazů elementu, který chcete být refaktorovány v **náhled změn** dialogové okno.|  
|**Data v registru**|Barva textu slouží k zobrazení dat uvnitř **zaregistruje** okna.|  
|**Registrovat NAT**|Barva textu slouží k zobrazení nerozpoznatelná data a objekty uvnitř **zaregistruje** okna.|  
|**Inteligentní značky**|Používá k označení obrys, když jsou vyvolány inteligentních značek.|  
|**SQL DML značka**|Platí pro editor jazyka Transact-SQL. Příkazy DML v tomto editoru jsou označené ohraničujícího rámečku modrá ve výchozím nastavení.|  
|**Zastaralý kód**|Nahrazené kód čeká na aktualizace. V některých případech funkce upravit a pokračovat nemůže použít změny kódu okamžitě, ale je použít později v průběhu ladění. K tomu dochází při úpravě funkce, která se musí volat funkci právě probíhá, nebo pokud chcete přidat více než 64 bajtů nové proměnné čekání v zásobníku volání funkce. Pokud k tomu dojde, ladicí program zobrazí dialogové okno "Upozornění na starý kód", a kód nahrazené pokračuje v provádění, dokud dotyčný funkce dokončí a je volána znovu. Upravit a pokračovat platí v daném čase změny kódu.|  
|**řetězec**|Řetězcových literálů.|  
|**Řetězce (C# @ Verbatim)**|Textové literály v jazyce C#, které dokáže interpretovat znění. Příklad:<br /><br /> @"x"|  
|**Chyba syntaxe**|Chyby analýzy.|  
|**Zástupce seznamu úkolů**|Pokud **seznamu úkolů** řádku, je přidán zástupce a okraj indikátoru je zakázané, budou zvýrazněny řádku.|  
|**Zarážka s trasováním (zakázána)**|Nepoužívá se.|  
|**Zarážka s trasováním (povolena)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující jednoduché zarážky s trasováním. Tato možnost se vztahuje pouze v případě, že příkaz úroveň trasování jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|  
|**Zarážka s trasováním (chyba)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující zarážek s trasováním, které jsou v chybovém stavu. Tato možnost se vztahuje pouze v případě, že příkaz úroveň trasování jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|  
|**Zarážka s trasováním (varování)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující zarážky s trasováním, jsou ve varovném stavu. Tato možnost se vztahuje pouze v případě, že příkaz úroveň trasování jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|  
|**Zarážka s trasováním - rozšířená (zakázána)**|Určuje barvu zvýraznění pro příkazy nebo řádky, které obsahují zakázané podmíněný nebo daným počtem průchodů zarážky s trasováním. Tato možnost se vztahuje pouze v případě, že příkaz úroveň trasování jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|  
|**Zarážka s trasováním - rozšířená (povolena)**|Určuje barvu zvýraznění pro příkazy nebo řádky, které obsahují podmíněné nebo daným počtem průchodů zarážky s trasováním. Tato možnost se vztahuje pouze v případě, že příkaz úroveň trasování jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|  
|**Zarážka s trasováním - rozšířená (chyba)**|Určuje barvu zvýraznění pro příkazy nebo řádky, které obsahují podmíněné nebo stiskněte referenčně započítaný zarážek s trasováním, které jsou v chybovém stavu. Tato možnost se vztahuje pouze v případě, že příkaz úroveň trasování jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|  
|**Zarážka s trasováním - rozšířená (varování)**|Určuje barvu zvýraznění pro příkazy nebo řádky, které obsahují podmíněné nebo stiskněte referenčně započítaný zarážek s trasováním, které jsou ve varovném stavu. Tato možnost se vztahuje pouze v případě, že příkaz úroveň trasování jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti](../../debugger/general-debugging-options-dialog-box.md).|  
|**Zarážka s trasováním - mapovaná (zakázána)**|Určuje barvu zvýraznění pro příkazy nebo řádky, které obsahují zakázané mapované zarážky s trasováním. Platí pro ASP nebo ASP.NET ladění, pokud příkaz úrovni zarážky jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti Pole](../../debugger/general-debugging-options-dialog-box.md).|  
|**Zarážka s trasováním - mapovaná (povolena)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující namapované zarážky s trasováním. Platí pro ASP nebo ASP.NET ladění, pokud příkaz úrovni zarážky jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti Pole](../../debugger/general-debugging-options-dialog-box.md).|  
|**Zarážka s trasováním - mapovaná (chyba)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující namapované zarážky s trasováním v chybovém stavu. Platí pro ASP nebo ASP.NET ladění, pokud příkaz úrovni zarážky jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti Pole](../../debugger/general-debugging-options-dialog-box.md).|  
|**Zarážka s trasováním - mapovaná (varování)**|Určuje barvu zvýraznění pro příkazy nebo řádky obsahující namapované zarážky s trasováním ve varovném stavu. Platí pro ASP nebo ASP.NET ladění, pokud příkaz úrovni zarážky jsou aktivní nebo **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz** výběru na [Obecné, ladění, dialogové okno Možnosti Pole](../../debugger/general-debugging-options-dialog-box.md).|  
|**Sledovat změny po uložení**|Řádků kódu, které byly změněny, protože soubor byl otevřen, ale jsou uloženy na disk.|  
|**Sledovat změny před uložením**|Řádky kódu, které byly změněny, protože soubor byl otevřen, ale není uloženo na disk.|  
|**Uživatelské typy**|Typy definované uživatelem.|  
|**Uživatelské typy (delegátů)**|Zadejte barvu pro delegáty.|  
|**Uživatelské typy (výčtů)**|Zadejte barvu používanou pro výčty.|  
|**Uživatelské typy (rozhraní)**|Zadejte barvu pro rozhraní.|  
|**Uživatelské typy (hodnotové typy)**|Zadejte barvu pro typy hodnot, jako je například struktury v jazyce C#.|  
|**Pouze značky jazyka Visual Basic pro čtení**|Značky specifické pro Visual Basic používá pro určení EnC, například výjimka oblastí, definici metody a snímků volání mimo úroveň listu.|  
|**Upozornění**|Upozornění kompilátoru.|  
|**Cesta řádku upozornění**|Používá se pro řádky upozornění statické analýzy.|  
|**Atribut XML**|Názvy atributů.|  
|**Uvozovky atributu XML**|Znaky uvozovek pro atributy ve formátu XML.|  
|**Hodnota atributu XML**|Obsah atributy ve formátu XML.|  
|**Sekce XML Cdata**|Obsah \<! [ CDATA [...]] >.|  
|**Komentář XML**|Obsah \<!---->.|  
|**Oddělovač XML**|Syntaxe jazyka XML oddělovače, včetně <, <?, <!, \<!-,-->,?\>, \<! [,]] > a [,].|  
|**Atribut XML Doc**|Hodnota dokumentaci xml atribut, například \<param name = "I" > "I", kde je obarveny.|  
|**Komentář XML**|Komentáře v dokumentační komentáře xml.|  
|**– Značka XML Doc**|Značky v dokumentu XML jako komentáře<br /><br /> /// \<Souhrn >.|  
|**XML – klíčové slovo**|DTD klíčová slova jako CDATA, IDREF a NDATA.|  
|**Název XML**|Názvy prvků a název cílové zpracování pokyny.|  
|**Instrukce pro zpracování XML**|Obsah zpracování instrukcí nezahrnuje název cíle.|  
|**XML Text**|Textový obsah elementu.|  
|**Klíčové slovo XSLT**|Názvy elementů XSLT.|  
  
 **Popředí položky**  
 Zobrazí seznam dostupných barev, které můžete použít pro popředí položky vybrané v **zobrazení položek**. Protože některé položky se týkají a proto vhodné ponechat schéma konzistentní zobrazení, změna textového barvu popředí také změní výchozí hodnoty pro prvky, jako jsou Chyba kompilátoru, – klíčové slovo nebo operátora.  
  
 **Automatické** položek může barvu popředí dědit z jiné zobrazit položky, jako **prostý Text**. S touto volbou, když se změní barvu položky zděděné zobrazení, barvu zobrazit související položky také automaticky změnit. Například, pokud jste vybrali **automatické** hodnota **Chyba kompilátoru** a později změnit barvu **prostý Text** na červený, **Chyba kompilátoru**také automaticky zdědí červenou barvu.  
  
 **Výchozí** barva zobrazující se pro položku první čas spuštění sady Visual Studio. Kliknutím **použít výchozí hodnoty** tlačítko obnoví pro tuto barvu.  
  
 **Vlastní**  
 Zobrazí dialogové okno barev můžete nastavit vlastní barvu pro vybranou položku v zobrazení seznamu položek.  
  
> [!NOTE]
>  Nastavení barev pro zobrazení vašeho počítače může být omezena vaši schopnost definovat vlastní barvy. Například, pokud je váš počítač nastavený na zobrazení 256 barev a vybrat vlastní barvu z **barva** dialogové okno, integrovaném vývojovém prostředí výchozí hodnoty na nejbližší dostupné **základní barvy** a zobrazí v černé barvy **Barva** pole ve verzi preview.  
  
 **Pozadí položky**  
 Obsahuje paletu barev, ze kterého můžete nastavit barvu pozadí položky vybrané v **zobrazení položek**. Protože některé položky se týkají a proto vhodné ponechat schéma konzistentní zobrazení, změna barvy pozadí textu změní také výchozí hodnoty pro prvky, jako jsou Chyba kompilátoru, – klíčové slovo nebo operátora.  
  
 **Automatické** položek může barvu pozadí dědit z jiné zobrazit položky, jako **prostý Text**. S touto volbou, když se změní barvu položky zděděné zobrazení, barvu zobrazit související položky také automaticky změnit. Například, pokud jste vybrali **automatické** hodnota **Chyba kompilátoru** a později změnit barvu **prostý Text** na červený, **Chyba kompilátoru**také automaticky zdědí červenou barvu.  
  
 **Výchozí** barva zobrazující se pro položku první čas spuštění sady Visual Studio. Kliknutím **použít výchozí hodnoty** tlačítko obnoví pro tuto barvu.  
  
 **Vlastní**  
 Zobrazí dialogové okno barev můžete nastavit vlastní barvu pro vybranou položku v zobrazení seznamu položek.  
  
 **Tučné**  
 Tuto možnost použijte k zobrazení textu vybraného **zobrazení položek** tučným písmem. Tučný text je snadnější identifikovat v editoru.  
  
 **Ukázka**  
 Zobrazuje řez písma, velikosti a barevného schématu pro ukázku **zobrazit nastavení pro** a **zobrazení položek** vybrané. Toto pole můžete zobrazit náhled výsledků, jak experimentovat s různými možnostmi formátování.  
  
## <a name="see-also"></a>Viz také  
 [Dialogové okno Možnosti prostředí](../../ide/reference/environment-options-dialog-box.md)   
 [Dialogové okno Možnosti](../../ide/reference/options-dialog-box-visual-studio.md)   
 [Postupy: Změna písma a barev](../../ide/how-to-change-fonts-and-colors-in-visual-studio.md)



