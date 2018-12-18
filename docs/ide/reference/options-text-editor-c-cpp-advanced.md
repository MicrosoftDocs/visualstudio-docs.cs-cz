---
title: Možnosti, textový editor, C/C++, upřesnit
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C\C++.Advanced
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Advanced
- VS.ToolsOptionsPages.Text_Editor.C/C++.Advanced
helpviewer_keywords:
- Text Editor Options dialog box, advanced
ms.assetid: 67c82ae5-fddd-49df-baec-8e7498b156f3
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: fd6522f80a367be33830f02a30c056531593d9ac
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220427"
---
# <a name="options-text-editor-cc-advanced"></a>Možnosti, textový editor, C/C++, upřesnit
Změnou tyto možnosti můžete změnit chování související se technologie IntelliSense a procházení databází, když programujete v jazyce C nebo C++.

 Pro přístup k této stránce v **možnosti** dialogové okno, v levém podokně rozbalte **textový Editor**, rozbalte **C/C++** a klikněte na tlačítko **Upřesnit**.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Zobrazit [přizpůsobit prostředí IDE sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).


## <a name="browsingnavigation"></a>Procházení a navigace
 Tyto možnosti s výjimkou případů, měli byste zvolit nikdy ve výjimečných případech, kde je tak velká, že aktivita databáze používá nepřijatelné množství systémových prostředků řešení.

 **Zakázat databázi**

 Veškeré možnosti použití databáze (SDF), všechny ostatní možnosti procházení/navigace a všechny funkce technologie IntelliSense, s výjimkou procházení kódu # automatické dokončování include jsou zakázané.

 **Zakázat aktualizace databáze**

 Databáze se otevřou jen pro čtení a žádné aktualizace se provede, jako jsou soubory upravovat. Většina funkcí budou i nadále fungovat. Ale jak jsou provedeny změny, data budou zastaralá a získáte nesprávné výsledky.

 **Zakázat automatické aktualizace databáze**

 Databáze procházení kódu nebude automaticky aktualizovat při změně zdrojových souborů. Ale pokud otevřete **Průzkumníka řešení**, otevřete místní nabídku pro projekt a klikněte na tlačítko **znovu prohledat řešení**, zkontroluje všechny zastaralé soubory a databáze bude aktualizována.

 **Zakázat implicitní soubory**

 Databáze procházení kódu nebude shromažďovat data pro soubory, které nejsou uvedeny v projektu. Projekt obsahuje zdrojové soubory a soubory hlaviček, které jsou explicitně zadány. Implicitní soubory jsou zahrnuty explicitní soubory (například afxwin.h windows.h a atlbase.h). Za normálních okolností systém vyhledá tyto soubory a také je indexuje pro různé funkce procházení (včetně přejít na). Pokud zvolíte tuto možnost, tyto soubory nejsou indexovány a některé funkce nejsou k dispozici pro ně. Pokud zvolíte tuto možnost, jsou také implicitně zvolili "Zakázat implicitní vyčištění" a "Zakázat externích závislostí".

 **Zakázat implicitní vyčištění**

 Databáze procházení kódu nebude vyčištění implicitní soubory, které se už neodkazuje. Tato možnost zabraňuje implicitní soubory odebírá z databáze, pokud jste už nebude používat. Například, pokud chcete přidat `#include` direktiv, která odkazuje na mapi.h do jednoho z vašich zdrojových souborů, mapi.h bude nalezen a indexovat. Pokud později odeberete #include a soubor není odkazovat kdekoli, informace o tom se nakonec odeberou, pokud zvolíte tuto možnost. (Viz **znovu prohledat řešení Interval** možnost.) Tato možnost se ignoruje, pokud explicitně znovu prohledat řešení.

 **Zakázat složky vnějších závislostí**

 Složka externí závislosti pro každý projekt se vytvoří nebo aktualizuje. V **Průzkumníka řešení**, každý projekt obsahuje externí závislosti složky, která obsahuje všechny implicitní soubory pro daný projekt. Pokud zvolíte tuto možnost, nezobrazí se této složky.

 **Znovu vytvořit databázi**

 Znovu vytvořte databázi procházení kódu od nic při příštím načtení řešení. Pokud zvolíte tuto možnost, odstraní se tento soubor databáze SDF při příštím načtení řešení, což způsobuje databáze, kterou chcete znovu vytvořit všechny soubory a indexovat a.

 **Znovu prohledat řešení Interval**

 Úloha "Znovu prohledat řešení nyní" je naplánováno interval, který zadáte. Je nutné zadat mezi 0 a 5000 minut. Výchozí hodnota je 60 minut. Zatímco probíhá prohledávání řešení, časová razítka souborů jsou zkontrolována k určení, zda soubor byl změněn mimo rozhraní IDE. (Jsou automaticky sleduje změny provedené v integrovaném vývojovém prostředí, a soubory se aktualizují.) Implicitně zahrnuté soubory jsou zkontrolována k určení, jestli se máte vše stále odkazuje.

## <a name="diagnostic-logging"></a>Protokolování diagnostiky
 Tyto možnosti jsou k dispozici v případě, že Microsoft vás vyzve k shromažďování upřesňující informace pro diagnostiku problému. Informace o protokolování není vhodný pro uživatele, a doporučujeme ponechat jej zakázán.

 **Povolení protokolování**

 Povolí protokolování diagnostiky v okně výstupu.

 **Úroveň protokolování**

 Nastavte úroveň podrobností protokolu, od 0 do 5.

 **Protokolování filtru**

 Filtry se zobrazí typy událostí s využitím bitová maska.

 Nastavení s použitím součet některý z následujících možností:

-   0 – žádný

-   1 - Obecné

-   2 – nečinné

-   4 – pracovní položky

-   8 – technologie IntelliSense

-   16 - ACPerf

-   32 - ClassView

## <a name="fallback-location"></a>Záložní umístění
 Záložní umístění je, kde jsou umístěny podpůrné soubory SDF a technologii IntelliSense (například iPCH), když primární umístění (stejného adresáře jako řešení) se nepoužívá. Tato situace může nastat, uživatel nemá oprávnění k zápisu do adresáře řešení nebo řešení adresář je na pomalé zařízení. Výchozí umístění pro použití náhradní lokality je v adresáři temp uživatele.

 **Vždy použít záložní umístění**

 Označuje, že kód databázi procházení a soubory IntelliSense by měl vždy být uloženy ve složce, který zadáte jako "Záložní umístění", ne u souboru .sln. Rozhraní IDE se nikdy pokusí pro soubory SDF nebo iPCH vedle adresáři řešení a bude vždy používat záložní umístění.

 **Nezobrazí upozornění, pokud je použito záložní umístění**

 Nejsou informován nebo dotaz, zda se používá záložní umístění. Za normálních okolností rozhraní IDE vám oznámí, pokud bylo nutné použít záložní umístění. Tato volba vypne tohoto upozornění.

 **Záložní umístění**

 Tato hodnota se používá jako sekundární umístění pro uložení kódu, procházení databáze nebo soubory IntelliSense. Ve výchozím nastavení je dočasný adresář záložní umístění. Rozhraní IDE vytvoří podadresář pod zadanou cestu (nebo na dočasný adresář), který obsahuje název řešení spolu s hodnotu hash úplnou cestu k řešení, které předchází problémům s názvy řešení je stejná.

## <a name="intellisense"></a>IntelliSense
 **Automatické rychlé informace**

 Umožňuje zobrazovat popisy tlačítek QuickInfo, při přesunutí ukazatele myši text.

 **Zakázat technologii IntelliSense**

 Zakáže všechny funkce technologie IntelliSense. Rozhraní IDE nevytváří VCPkgSrv.exe procesy pro žádosti o služby technologie IntelliSense a bude fungovat bez funkce IntelliSense (rychlé informace, seznam členů, automatické dokončování, Param nápovědy). Sémantické zbarvení a zvýraznění odkazů jsou zakázané taky. Tato možnost není zakázat procházení funkcí, které spoléhají výhradně na databázi (včetně navigační panel, ClassView a vlastnost okno).

 **Zakázat automatické aktualizace**

 Aktualizace IntelliSense zpožděn až do aktuálního požadavku pro technologii IntelliSense. Toto zpoždění může vést k delší dobu provádění první operace IntelliSense na souboru, ale může být užitečné nastavit tuto možnost na počítačích velmi pomalý nebo s omezenými zdroji. Pokud zvolíte tuto možnost, zvolíte také implicitně možnosti "Zakázat Error Reporting" a "Zakázat podtržení vlnovkou".

 **Vypnout hlášení chyb**

 Zakáže hlášení chyb IntelliSense formě podtržení vlnovkou a v okně Seznam chyb. Zakáže také analýzu na pozadí, který je spojen s hlášením chyb. Pokud zvolíte tuto možnost, zvolíte také implicitně možnost "Zakázat podtržení vlnovkou".

 **Zakázat podtržení vlnovkou**

 Zakáže podtržení vlnovkou u chyb IntelliSense. Nezobrazovat red "podtržení vlnovkou" v okně editoru, ale tato chybová zpráva stále zobrazí v okně Seznam chyb.

 **Automaticky ladit maximální počet jednotek překladu uložené v mezipaměti.**

 Maximální počet jednotek překladu, které se budou uchovávat v daný okamžik aktivní pro požadavky IntelliSense. Musíte zadat hodnotu v rozmezí 2 až 15. Toto číslo přímo souvisí s maximální počet procesů VCPkgSrv.exe, které bude možné spustit (pro danou instanci sady Visual Studio). Výchozí hodnota je 2, ale pokud máte dostupnou paměť, můžete tuto hodnotu zvýšit a případně dosáhnout mírně vyšší výkon na IntelliSense.

 Další informace o jednotkách překladu naleznete v tématu [fáze překladu](/cpp/preprocessor/phases-of-translation).

 **Zakázat #include automatické dokončování**

 Zakáže Automatické doplňování `#include` příkazy.

 **Použít lomítko vpřed v #include automatické dokončování**

 Aktivuje automatické doplňování `#include` příkazy při "/" se používá. Výchozím oddělovačem je zpětné lomítko "\'. Kompilátor může přijímat buď, proto tuto možnost použijte, chcete-li určit, co vašeho základu kódu používá.

 **Zakázat agresivní člena seznamu**

 Seznam členů se nezobrazí, když zadáte název typu nebo proměnné. V seznamu se zobrazí pouze po zadání jedním ze znaků potvrzení, jak jsou definovány v **potvrzující znaky seznamu členů** možnost.

 **Zakázat klíčová slova v seznamu členů**

 Klíčová slova jazyka, jako `void`, `class`, `switch` nezobrazí v seznamu návrhů člen.

 **Zakázat fragmenty kódu člena seznamu**

 Fragmenty kódu se nezobrazují v seznamu návrhů člen.

 **Režim filtrování seznamu členů**

 Nastaví typ porovnávací algoritmus. **Přibližné** najde, co nejvíce odpovídá, protože ho používá algoritmus, který je podobný kontrolu pravopisu pro hledání shody, které jsou podobné, ale nejsou identické. **Inteligentní filtrování** odpovídá podřetězců, i když nejsou na začátku slova. **Předpona** odpovídá pouze na stejné dílčích řetězců, které začínají na začátku slova.

 **Zakázat sémantické zbarvení**

 Vypne všechny barevné zvýraznění kódu s výjimkou klíčová slova jazyka, řetězce a komentáře.

 **Potvrzující znaky seznamu členů**

 Určuje znaky, které způsobují aktuálně zvýrazněný seznam členů návrh pro potvrzení. Můžete přidat nebo odebrat znaky z tohoto seznamu.

 **Potvrzení seznamu členů inteligentní**

 Pokud zvolíte klávesu Enter na konci úplně napsaného slova, přidá nový řádek.

 **Povolit člena seznamu tečky na šipku**

 Nahradí "." znaky->' Pokud se dá použít pro seznam členů.

## <a name="references"></a>Odkazy
 **Zakázat řešení**

 Z důvodů výkonu "Najít všechny odkazy" zobrazí nezpracované textové výsledky hledání ve výchozím nastavení namísto použití IntelliSense k ověření každého kandidáta. Pro přesnější výsledky pro všechny operace hledání můžete zrušte zaškrtnutí tohoto políčka. Filtrovat na základě za vyhledávání, otevřete místní nabídku pro seznam výsledků a klikněte na tlačítko "Vyřešit výsledky."

 **Skrýt nepotvrzené**

 Skryjte nepotvrzené položky ve výsledcích najít všechny odkazy. Pokud jste možnost zrušit nastavení "Zakázat řešení", můžete použít tuto možnost skryjete nepotvrzené položky ve výsledcích.

 **Zakázat zvýraznění odkazů**

Ve výchozím nastavení když vyberete nějaký text, všechny výskyty stejného textu jsou automaticky zvýrazněné v aktuálním dokumentu. Tuto funkci můžete zakázat nastavením **zakázat zvýraznění odkazu** k **True**.

 ## <a name="text-editor"></a>Textový editor
 **Povolit kulatých závorek**

 Pokud je povoleno, je možné ohraničit vybraný text pomocí složených závorek zadáním "{" v textovém editoru.

 **Povolit kulatých závorek**

 Pokud je povoleno, je možné ohraničit vybraný text v závorkách zadáním "(" v textovém editoru.

## <a name="see-also"></a>Viz také

- [Nastavení možností editoru pro konkrétní jazyk](../../ide/reference/setting-language-specific-editor-options.md)
