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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77275211"
---
# <a name="options-text-editor-cc-advanced"></a>Možnosti, textový editor, C/C++, upřesnit

Změnou těchto možností můžete změnit chování související s IntelliSense a databáze procházení při programování v jazyce C nebo C++.

Chcete-li získat přístup **Options** k této stránce, rozbalte v levém podokně v levém podokně **textový editor**, rozbalte **c/c++** a pak zvolte **Upřesnit**.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Viz [Přizpůsobení prostředí IDE sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="browsingnavigation"></a>Procházení/navigace

Nikdy byste neměli zvolit tyto možnosti s výjimkou ve výjimečných případech, kdy je řešení tak velké, že databázová aktivita spotřebovává nepřijatelné množství systémových prostředků.

**Zakázat databázi**

Všechna použití databáze procházení kódu (SDF), všech ostatních možností procházení/navigace a všech funkcí technologie IntelliSense s výjimkou #include automatického dokončování jsou zakázány.

**Zakázat aktualizace databáze**

Databáze bude otevřena jen pro čtení a při úpravách souborů nebudou prováděny žádné aktualizace. Většina funkcí bude stále fungovat. Při úpravách se však data stanou zastaralými a zobrazí se nesprávné výsledky.

**Zakázat automatické aktualizace databáze**

Databáze procházení kódu nebude automaticky aktualizována při změně zdrojových souborů. Pokud však otevřete **Průzkumníka řešení**, otevřete místní nabídku projektu a pak zvolte **Znovu prohledat řešení**, budou zkontrolovány všechny zastaralé soubory a databáze bude aktualizována.

**Zakázat implicitní soubory**

Databáze procházení kódu neshromažďuje data pro soubory, které nejsou zadány v projektu. Projekt obsahuje zdrojové soubory a soubory hlaviček, které jsou explicitně zadány. Implicitní soubory jsou zahrnuty explicitní soubory (například afxwin.h, windows.h a atlbase.h). Za normálních okolností systém tyto soubory vyhledá a také je indexuje pro různé funkce procházení (včetně funkce Přejít na). Pokud zvolíte tuto možnost, tyto soubory nebudou indexovány a některé funkce pro ně nejsou k dispozici. Pokud zvolíte tuto možnost, "Zakázat implicitní vyčištění" a "Zakázat externí závislosti" jsou také implicitně vybrány.

**Zakázat implicitní vyčištění**

Databáze procházení kódu nečistí implicitní soubory, na které se již neodkazuje. Tato možnost zabrání odebrání implicitních souborů z databáze, když se již nepoužívají. Pokud například přidáte `#include` direktivu, která odkazuje na mapi.h do jednoho ze zdrojových souborů, bude soubor mapi.h nalezen a indexován. Pokud potom odeberete #include a soubor není odkazován jinde, informace o něm budou nakonec odebrány, pokud nezvolíte tuto možnost. (Viz možnost **Interval řešení opětovného prohledávat.)** Tato možnost je ignorována při explicitním opětovném prohledání řešení.

**Zakázání složek externích závislostí**

Složka Externí závislosti pro každý projekt není vytvořena ani aktualizována. V **Průzkumníku řešení**obsahuje každý projekt složku Externí závislosti, která obsahuje všechny implicitní soubory pro tento projekt. Pokud zvolíte tuto možnost, tato složka se nezobrazí.

**Znovu vytvořit databázi**

Při příštím načtení řešení znovu vytvořte databázi procházení kódu z ničeho. Pokud zvolíte tuto možnost, soubor databáze SDF se odstraní při příštím načtení řešení, což způsobí, že databáze bude znovu vytvořena a všechny soubory indexovány.

**Interval znovu prohledávat řešení**

Úloha Znovu prohledat řešení je naplánována na zadaný interval. Je nutné zadat mezi 0 a 5000 minut. Výchozí hodnota je 60 minut. Při opětovném prohledáně ní jsou kontrolována časová razítka souboru, aby se zjistilo, zda byl soubor změněn mimo ide. (Změny provedené v ide jsou automaticky sledovány a soubory jsou aktualizovány.) Implicitně zahrnuté soubory jsou kontrolovány k určení, zda jsou všechny stále odkazuje.

## <a name="diagnostic-logging"></a>Diagnostické protokolování

Tyto možnosti jsou k dispozici v případě, že vás společnost Microsoft požádá o shromažďování pokročilých informací pro diagnostiku problému. Informace o protokolování nejsou pro uživatele užitečné a doporučujeme ponechat je zakázané.

**Povolit protokolování**

Povolí diagnostické protokolování do výstupního okna.

**Úroveň protokolování**

Nastavte podrobnost protokolu od 0 do 5.

**Filtr protokolování**

Filtry zobrazují typy událostí pomocí bitové masky.

Nastavení pomocí součtu některé z následujících možností:

- 0 - Žádné

- 1 - Obecné

- 2 - Nečinný

- 4 - Pracovní položka

- 8 - Technologie IntelliSense

- 16 - ACPerf

- 32 - Zobrazení třídy

## <a name="fallback-location"></a>Záložní umístění

Záložní umístění je místo, kde sdf a IntelliSense podpůrné soubory (například iPCH) jsou umístěny při primární umístění (stejný adresář jako řešení) není použit. Tato situace může nastat uživatel nemá oprávnění k zápisu do adresáře řešení nebo adresář řešení je na pomalé zařízení. Výchozí záložní umístění je v dočasném adresáři uživatele.

**Vždy používat záložní umístění**

Označuje, že databáze procházení kódu a soubory IntelliSense by měly být vždy uloženy ve složce, kterou zadáte jako záložní umístění, nikoli vedle souboru .sln. Rozhraní IDE se nikdy nepokusí umístit soubory SDF nebo iPCH vedle adresáře řešení a bude vždy používat záložní umístění.

**Neupozorováno, pokud je použito záložní umístění**

Pokud se používá záložní umístění, nebudete informováni ani se na vás nezobrazí výzva. Za normálních okolností ide vám řekne, pokud bylo nutné použít záložní umístění. Tato možnost toto upozornění vypne.

**Záložní umístění**

Tato hodnota se používá jako sekundární umístění pro uložení databáze procházení kódu nebo souborů IntelliSense. Ve výchozím nastavení je dočasný adresář záložním umístěním. Rozhraní IDE vytvoří podadresář pod zadanou cestou (nebo dočasný medailon), který obsahuje název řešení spolu s hodnotou hash úplné cesty k řešení, což zabraňuje problémům s názvy řešení, které jsou identické.

## <a name="intellisense"></a>IntelliSense

**Rychlé automatické informace**

Povolí popisky QuickInfo, když přesunete ukazatel na text.

**Zakázat službu IntelliSense**

Zakáže všechny funkce Technologie IntelliSense. IDE nevytváří procesy VCPkgSrv.exe pro servis požadavků Technologie IntelliSense a nebudou fungovat žádné funkce Technologie IntelliSense (QuickInfo, Seznam členů, Automatické dokončení, Param nápověda). Sémantické zbarvení a zvýraznění odkazů jsou také zakázány. Tato možnost nezakáže funkce procházení, které jsou závislé výhradně na databázi (včetně navigačního panelu, zobrazení třídy a okna vlastností).

**Zakázat automatické aktualizace**

Aktualizace technologie IntelliSense se zpožďuje, dokud není podána skutečná žádost o službu IntelliSense. Toto zpoždění může mít za následek delší dobu provádění první operace IntelliSense v souboru, ale může být užitečné nastavit tuto možnost na velmi pomalé nebo prostředky omezené počítače. Pokud zvolíte tuto možnost, můžete také implicitně zvolit možnosti "Zakázat zasílání zpráv o chybách" a "Zakázat vlnovky".

**Zakázat zasílání zpráv o chybách**

Zakáže vytváření sestav chyb technologie IntelliSense pomocí vlnovek a okna Seznam chyb. Také zakáže analýzu na pozadí, která je spojena s zasíláním zpráv o chybách. Pokud zvolíte tuto možnost, můžete také implicitně zvolit možnost "Zakázat vlnovky".

**Zakázat vlnovky**

Zakáže vlnovky chyb technologie IntelliSense. Červené "klikyháky" se nezobrazují v okně editoru, ale chyba se stále zobrazí v okně Seznam chyb.

**Automatické ladění max cache překladu jednotky**

Maximální počet jednotek překladu, které budou v jednom okamžiku aktivní pro požadavky technologie IntelliSense. Je nutné zadat hodnotu mezi 2 a 15. Toto číslo přímo souvisí s maximálním počtem procesů VCPkgSrv.exe, které budou spuštěny (pro danou instanci sady Visual Studio). Výchozí hodnota je 2, ale pokud máte k dispozici paměť, můžete tuto hodnotu zvýšit a případně dosáhnout mírně lepšího výkonu v systému IntelliSense.

Další informace o překladatelských jednotkách naleznete [v tématu Fáze překladu](/cpp/preprocessor/phases-of-translation).

**Zakázat automatické dokončování #include**

Zakáže automatické `#include` dokončování příkazů.

**Použití lomítka přemítek v #include automatického dokončování**

Aktivuje automatické dokončování `#include` příkazů při použití "/". Výchozím oddělovačem je\'zpětné lomítko . Kompilátor může přijmout buď, takže pomocí této možnosti určit, co používá základní kód.

**Zakázat agresivní seznam členů**

Seznam členů se nezobrazí při psaní názvu typu nebo proměnné. Seznam se zobrazí až po zadání jednoho ze znaků potvrzení, jak je definováno v možnosti **Znaky potvrzení seznamu členů.**

**Zakázat klíčová slova seznamu členů**

Jazyková klíčová `void`slova, `switch` například , `class`se v návrzích seznamu členů nezobrazují.

**Zakázat fragmenty kódu seznamu členů**

Fragmenty kódu se nezobrazují v návrzích seznamu členů.

**Režim filtru seznamu členů**

Nastaví typ odpovídajícíalgoritmus. **Fuzzy** najde nejvíce možných shod, protože používá algoritmus, který je podobný kontrole pravopisu k nalezení shody, které jsou podobné, ale nejsou identické. **Inteligentní filtrování** odpovídá podřetězcům, i když nejsou na začátku slova. **Předpona** odpovídá pouze na identických podřetězců, které začínají na začátku slova.

**Zakázat sémantické zbarvení**

Vypne veškeré vybarvení kódu s výjimkou jazykových klíčových slov, řetězců a komentářů.

**Znaky potvrzení seznamu členů**

Určuje znaky, které způsobují, že aktuálně zvýrazněný návrh Seznamu členů bude potvrzen. Znaky můžete přidat nebo odebrat z tohoto seznamu.

**Potvrzení seznamu inteligentních členů**

Přidá řádek, když zvolíte klávesu Enter na konci plně zadávaného slova.

**Povolit seznam členů Tečka-To-Arrow**

Nahradí "." s '->', pokud je to možné pro seznam členů.

## <a name="references"></a>Odkazy

**Zakázat řešení**

Z důvodů výkonu zobrazuje služba Najít všechny odkazy ve výchozím nastavení nezpracované textové výsledky hledání namísto použití technologie IntelliSense k ověření každého kandidáta. Toto políčko můžete zrušte zaškrtnutí políčka, abyste měli přesnější výsledky všech operací hledání. Chcete-li filtrovat podle vyhledávání, otevřete místní nabídku seznamu výsledků a zvolte "Vyřešit výsledky".

**Skrýt nepotvrzené**

Skrýt nepotvrzené položky ve výsledcích hledání všech referencí. Pokud odstavíte možnost Zakázat řešení, můžete pomocí této možnosti skrýt nepotvrzené položky ve výsledcích.

**Zakázat zvýraznění odkazů**

Ve výchozím nastavení jsou při výběru některého textu v aktuálním dokumentu automaticky zvýrazněny všechny instance stejného textu. Tuto funkci můžete zakázat nastavením **zakázat zvýraznění odkazů** na **hodnotu True**.

## <a name="text-editor"></a>Textový editor

**Povolit prostorové složených závorek**

Pokud je tato možnost povolena, můžete vybraný text obklopit složenými závorkami zadáním "{" do textového editoru.

**Povolit prostorové s tvory**

Pokud je tato možnost povolena, můžete vybraný text obklopit závorky zadáním '(' do textového editoru.

## <a name="see-also"></a>Viz také

- [Nastavení možností editoru pro konkrétní jazyk](../../ide/reference/setting-language-specific-editor-options.md)
