---
title: Možnosti, textový editor, C/C++, upřesnit
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C\C++.Advanced
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Advanced
- VS.ToolsOptionsPages.Text_Editor.C/C++.Advanced
helpviewer_keywords:
- Text Editor Options dialog box, advanced
ms.assetid: 67c82ae5-fddd-49df-baec-8e7498b156f3
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 2e7e031836c9762d9666a5624e78ecc7c8cc7dd9
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77275211"
---
# <a name="options-text-editor-cc-advanced"></a>Možnosti, textový editor, C/C++, upřesnit

Změnou těchto možností můžete změnit chování související s technologií IntelliSense a databází procházení při programování v jazyce C nebo C++.

Chcete-li získat přístup k této stránce, v dialogovém okně **Možnosti** rozbalte v levém podokně položku **textový editor**, rozbalte položku **C++C/** a pak zvolte možnost **Upřesnit**.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Viz [Přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="browsingnavigation"></a>Procházení/navigace

Tyto možnosti byste nikdy neměli volit s výjimkou případů, kdy je řešení tak velké, že aktivita databáze spotřebovává nepřijatelný objem systémových prostředků.

**Zakázat databázi**

Veškeré použití databáze procházení kódu (SDF), všech dalších možností procházení/navigace a všech funkcí IntelliSense s výjimkou #include automatické dokončování jsou zakázané.

**Zakázat aktualizace databáze**

Databáze bude otevřena jen pro čtení a nebudou provedeny žádné aktualizace, protože soubory budou upravovány. Většina funkcí bude pořád fungovat. Při úpravách se ale data stanou zastaralá a získáte nesprávné výsledky.

**Zakázat automatické aktualizace databáze**

Databáze procházení kódu nebude automaticky aktualizována při změně zdrojových souborů. Pokud však otevřete **Průzkumník řešení**, otevřete místní nabídku pro projekt a pak zvolte možnost **Prohledat řešení**, všechny soubory se zastaralou verzí a bude aktualizována databáze.

**Zakázat implicitní soubory**

Databáze procházení kódu neshromažďuje data pro soubory, které nejsou zadány v projektu. Projekt obsahuje zdrojové soubory a hlavičkové soubory, které jsou explicitně určeny. Implicitní soubory jsou zahrnuty v explicitních souborech (například afxwin. h, Windows. h a atlbase. h). Systém obvykle tyto soubory najde a také je indexuje pro různé funkce procházení (včetně přechodu na). Pokud zvolíte tuto možnost, tyto soubory nebudou indexovány a některé funkce nejsou pro ně k dispozici. Pokud zvolíte tuto možnost, implicitně se volí taky možnost zakázat implicitní vyčištění a zakázat externí závislosti.

**Zakázat implicitní vyčištění**

Databáze procházení kódu nečistí implicitní soubory, které již nejsou odkazovány. Tato možnost zabrání odebrání implicitních souborů z databáze, pokud už se nepoužívají. Pokud například přidáte direktivu `#include`, která odkazuje na rozhraní MAPI. h na jeden ze zdrojových souborů, bude nalezeno a indexováno rozhraní MAPI. h. Pokud odeberete #include a soubor se neodkazuje jinam, informace o něm se nakonec odeberou, pokud tuto možnost nevyberete. (Viz možnost **znovu prohledat interval řešení** .) Tato možnost se ignoruje, když řešení explicitně prohledáváte.

**Zakázat složky externích závislostí**

Složka externích závislostí pro každý projekt není vytvořena nebo aktualizována. V **Průzkumník řešení**každý projekt obsahuje složku externích závislostí, která obsahuje všechny implicitní soubory pro daný projekt. Pokud zvolíte tuto možnost, tato složka se nezobrazí.

**Znovu vytvořit databázi**

Znovu vytvořit databázi procházení kódu od okamžiku, kdy řešení příště nebylo načteno. Pokud zvolíte tuto možnost, soubor databáze SDF se odstraní při příštím načtení řešení, což způsobí, že se databáze znovu vytvoří a naindexují se všechny soubory.

**Interval řešení opětovného prohledání**

Úloha opětovného prohledání řešení je naplánovaná pro interval, který zadáte. Je nutné zadat mezi 0 a 5000 minutami. Výchozí hodnota je 60 minut. I když je řešení znovu naskenováno, jsou zkontrolována časová razítka souborů, aby bylo možné určit, zda byl soubor změněn mimo rozhraní IDE. (Změny provedené v integrovaném vývojovém prostředí (IDE) se automaticky sledují a aktualizují se soubory.) Implicitně zahrnuté soubory jsou zkontrolovány, aby bylo možné zjistit, zda jsou všechny stále odkazovány.

## <a name="diagnostic-logging"></a>Protokolování diagnostiky

Tyto možnosti jsou k dispozici v případě, že vás Microsoft požaduje, abyste shromáždili rozšířené informace pro diagnostiku problému. Informace o protokolování nejsou vhodné pro uživatele a doporučujeme, abyste ji nechali zakázanou.

**Povolit protokolování**

Povolí diagnostické protokolování do okna výstup.

**Úroveň protokolování**

Nastavte podrobnosti protokolu z 0 na 5.

**Filtr protokolování**

Filtruje zobrazené typy událostí pomocí bitové masky.

Nastavte pomocí součtu některé z následujících možností:

- 0 – žádné

- 1 – Obecné

- 2 – nečinný

- 4\. pracovní položka

- 8 – IntelliSense

- 16 – ACPerf

- 32 – ClassView

## <a name="fallback-location"></a>Záložní umístění

Záložní umístění je místo, kde se soubory podpory SDF a IntelliSense (například iPCH) vloží, když se nepoužije primární umístění (stejný adresář jako řešení). K této situaci může dojít, když uživatel nemá oprávnění k zápisu do adresáře řešení nebo když je adresář řešení na pomalé zařízení. Výchozí záložní umístění je v dočasném adresáři uživatele.

**Vždy použít záložní umístění**

Označuje, že databáze procházení kódu a soubory IntelliSense by měly být vždy uloženy ve složce, kterou zadáte jako záložní umístění, nikoli u souboru. sln. Rozhraní IDE se nikdy nepokusí umístit soubory SDF nebo iPCH vedle adresáře řešení a bude vždy používat záložní umístění.

**Neupozorňovat na použití záložního umístění**

Nebudete informováni ani se zobrazí výzva, pokud je použito záložní umístění. V normálním případě bude IDE vědět, jestli by musel používat záložní umístění. Tato možnost vypne toto upozornění.

**Záložní umístění**

Tato hodnota se používá jako sekundární umístění pro uložení databáze procházení kódu nebo souborů IntelliSense. Ve výchozím nastavení je vaším dočasným adresářem vaše záložní umístění. Rozhraní IDE vytvoří podadresáře v zadané cestě (nebo v dočasném adresáři), který obsahuje název řešení společně s hodnotou hash úplné cesty k řešení, což zabrání problémům se stejnými názvy řešení.

## <a name="intellisense"></a>IntelliSense

**Automatické rychlé informace**

Povoluje QuickInfo popisy tlačítek při přesunutí ukazatele myši na text.

**Zakázat IntelliSense**

Zakáže všechny funkce technologie IntelliSense. Rozhraní IDE nevytváří procesy VCPkgSrv. exe pro obsluhu požadavků technologie IntelliSense a žádné funkce technologie IntelliSense nebudou fungovat (QuickInfo, seznam členů, automatické dokončování, pomocníka param). Zároveň jsou zakázané sémantické zabarvení a zvýrazňování odkazů. Tato možnost nezakáže funkce procházení, které se spoléhají výhradně na databázi (včetně navigačního panelu, ClassView a okna vlastností).

**Zakázat automatické aktualizace**

Aktualizace technologie IntelliSense je zpožděna, dokud nebude vytvořena skutečná žádost o IntelliSense. Tato prodleva může mít za následek delší dobu provádění první operace IntelliSense v souboru, ale může být užitečné nastavit tuto možnost na velmi pomalé nebo na počítačích s omezenými prostředky. Pokud zvolíte tuto možnost, implicitně zvolíte možnosti "zakázat zasílání zpráv o chybách" a "zakázat vlnovky".

**Zakázat zasílání zpráv o chybách**

Zakáže zasílání zpráv o chybách IntelliSense prostřednictvím vlnovek a okna Seznam chyb. Také zakáže analýzu na pozadí, která je přidružena k zasílání zpráv o chybách. Pokud zvolíte tuto možnost, implicitně zvolíte možnost zakázat vlnovky.

**Zakázat vlnovky**

Zakáže chybové vlnovky technologie IntelliSense. Červené "vlnovky" se v okně editoru nezobrazují, ale v okně Seznam chyb se stále zobrazuje chyba.

**Automaticky vyladit maximální počet jednotek překladu v mezipaměti**

Maximální počet jednotek překladu, které budou v jednom okamžiku aktivní pro požadavky IntelliSense. Je nutné zadat hodnotu mezi 2 a 15. Toto číslo přímo souvisí s maximálním počtem procesů VCPkgSrv. exe, které se spustí (pro danou instanci sady Visual Studio). Výchozí hodnota je 2, ale pokud máte dostupnou paměť, můžete tuto hodnotu zvýšit a pravděpodobně dosáhnout mírného lepšího výkonu technologie IntelliSense.

Další informace o jednotkách překladu naleznete v tématu [fáze překladu](/cpp/preprocessor/phases-of-translation).

**Zakázat automatické dokončování #include**

Zakáže automatické dokončování `#include` příkazů.

**Použití lomítka v #include automatické dokončování**

Spustí automatické dokončování `#include` příkazy při použití "/". Výchozím oddělovačem je zpětné lomítko\'. Kompilátor může přijmout buď, a tuto možnost použijte k určení toho, co váš základ kódu používá.

**Zakázat agresivní seznam členů**

Seznam členů se nezobrazí, když zadáte název typu nebo proměnné. Seznam se zobrazí až po zadání jednoho ze znaků potvrzení, jak je definováno v možnosti pro **zápis znaků v seznamu členů** .

**Zakázat klíčová slova v seznamu členů**

Klíčová slova jazyka, například `void`, `class`, `switch` se nezobrazí v návrzích na seznam členů.

**Zakázat fragmenty kódu v seznamu členů**

Fragmenty kódu se nezobrazují v návrzích na seznam členů.

**Režim filtrování seznamu členů**

Nastaví typ odpovídajícího algoritmu. **Fuzzy** najde nejvíc možné shody, protože používá algoritmus, který je podobný kontrole pravopisu k nalezení shod, které jsou podobné, ale nejsou totožné. **Inteligentní filtrování** odpovídá podřetězcům i v případě, že nejsou na začátku slova. **Prefix** se shoduje jenom se stejnými podřetězci, které začínají na začátku slova.

**Zakázat sémantickou zabarvení**

Vypne všechny barvy kódu s výjimkou klíčových slov jazyka, řetězců a komentářů.

**Znaky potvrzení seznamu členů**

Určuje znaky, které způsobují, že návrh aktuálně zvýrazněného seznamu členů bude potvrzen. V tomto seznamu můžete přidat nebo odebrat znaky.

**Potvrzení seznamu inteligentních členů**

Přidá řádek, když na konci plně zadaného slova vyberete klávesu ENTER.

**Povolit u seznamu členů změnu tečky na šipku**

Nahradí '. ' s '-> ', pokud je použit pro seznam členů.

## <a name="references"></a>Odkazy

**Zakázat řešení**

Z důvodů výkonu se ve výchozím nastavení zobrazí nezpracované textové výsledky hledání bez použití IntelliSense k ověření každého kandidáta. Zaškrtnutím tohoto políčka můžete přesnější výsledky u všech operací hledání zrušit. Chcete-li filtrovat podle konkrétního výběru, otevřete místní nabídku seznamu výsledků a zvolte možnost vyřešit výsledky.

**Skrýt nepotvrzené**

Ve výsledcích hledání všech odkazů skryjte nepotvrzené položky. Pokud zrušíte možnost zakázat řešení, můžete tuto možnost použít ke skrytí nepotvrzených položek ve výsledcích.

**Zakázat zvýrazňování odkazů**

Ve výchozím nastavení, když vyberete nějaký text, všechny výskyty stejného textu se v aktuálním dokumentu automaticky zvýrazní. Tuto funkci můžete zakázat nastavením **Zakázat zvýraznění odkazů** na **hodnotu true**.

## <a name="text-editor"></a>Textový editor

**Povolit Surround pomocí složených závorek**

Pokud je povoleno, můžete vybraný text uzavřít do složených závorek zadáním "{" do textového editoru.

**Povolit Surround pomocí závorek**

Pokud je povoleno, můžete vybraný text uzavřít závorkami zadáním ' (' do textového editoru.

## <a name="see-also"></a>Viz také

- [Nastavení možností editoru pro konkrétní jazyk](../../ide/reference/setting-language-specific-editor-options.md)
