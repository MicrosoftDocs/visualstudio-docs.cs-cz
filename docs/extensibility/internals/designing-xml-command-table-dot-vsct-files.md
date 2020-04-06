---
title: Návrh tabulky příkazů XML (. Vsct) Soubory | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcd29aee98139bb151c87590b256df6b8370abff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708743"
---
# <a name="design-xml-command-table-vsct-files"></a>Návrh souborů příkazové tabulky XML (.vsct)
Soubor příkazové tabulky XML (*.vsct*) popisuje rozložení a vzhled položek příkazů pro položky příkazu VSPackage. Mezi položky příkazů patří tlačítka, pole se seznamem, nabídky, panely nástrojů a skupiny položek příkazů. Tento článek popisuje soubory tabulek příkazů XML, jejich vliv na položky příkazů a nabídky a způsob jejich vytvoření.

## <a name="commands-menus-groups-and-the-vsct-file"></a>Příkazy, nabídky, skupiny a soubor .vsct
 Soubory *.vsct* jsou uspořádány kolem příkazů, nabídek a skupin příkazů. Tagy XML v souboru *.vsct* představují každou z těchto položek spolu s dalšími přidruženými položkami, jako jsou příkazová tlačítka, umístění příkazů a bitmapy.

 Když vytvoříte nový Balíček VSPackage spuštěním šablony [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] balíčku, šablona vygeneruje soubor *.vsct* s potřebnými prvky pro příkaz nabídky, okno nástroje nebo vlastní editor v závislosti na vašich výběrech. Tento soubor *.vsct* pak lze upravit tak, aby splňovaly požadavky konkrétní VSPackage. Příklady úprav souboru *.vsct* naleznete v tématu [Rozšíření nabídek a příkazů](../../extensibility/extending-menus-and-commands.md).

 Chcete-li vytvořit nový prázdný soubor *.vsct,* [přečtěte si postup: Vytvoření souboru *.vsct* ](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Po vytvoření přidáte do souboru elementy XML, atributy a hodnoty, které popisují rozložení příkazové položky. Podrobné schéma XML naleznete v [odkazu na schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md).

## <a name="differences-between-ctc-and-vsct-files"></a>Rozdíly mezi soubory CTC a .vsct
 Zatímco význam tagů XML v souboru *.vsct* je stejný jako u tagů ve nyní zastaralém formátu *CTC,* jejich implementace je trochu jiná:

- Nová značka ** \<extern>** je místo, kde odkazujete na jiné soubory [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] *H,* které mají být kompilovány, například tyto soubory pro panel nástrojů.

- Zatímco soubory *.vsct* podporují příkaz **/include,** jako to dělají soubory *CTC,* jsou také vybaveny novým ** \<prvkem importu>.** Rozdíl je, **/zahrnout** přináší *všechny* informace, zatímco ** \<import>** přináší pouze názvy.

- Zatímco soubory *CTC* vyžadují soubor záhlaví, ve kterém definujete direktivy preprocesoru, jeden není vyžadován pro soubory *.vsct.* Místo toho umístěte direktivy do tabulky symbolů, která se nachází v ** \<elementech Symbol>,** který se nachází v dolní části souboru *.vsct.*

- *Soubory .vsct* obsahují značku ** \<>poznámky,** která umožňuje vložit všechny informace, které se vám líbí, například poznámky nebo dokonce obrázky.

- Hodnoty jsou uloženy jako atributy na položku.

- Příkaz příznaky mohou být uloženy jednotlivě nebo skládaný.  Technologie IntelliSense však nefunguje na skládaných příkazových vlajkách. Další informace o vlajkách příkazů naleznete v [elementu CommandFlag](../../extensibility/command-flag-element.md).

- Můžete zadat více typů, jako jsou rozdělené rozevírací seznamy, komba atd.

- Identifikátory GUID se neověřují.

- Každý prvek rozhraní má řetězec, který představuje text, který je zobrazen s ním.

- Nadřazený objekt je volitelný. Pokud je vynechán, je použita hodnota *Skupina Neznámý.*

- Argument *Icon* je volitelný.

- Bitmapový oddíl: Tato část je stejná jako v souboru *CTC,* s tím rozdílem, že nyní můžete zadat název souboru prostřednictvím href, který bude vyžádán kompilátorem *vsct.exe* v době kompilace.

- ResID: Staré ID bitmapového prostředku lze použít a stále funguje stejně jako v souborech *CTC.*

- HRef: Nová metoda, která umožňuje zadat název souboru pro bitmapový prostředek. Předpokládá, že všechny jsou používány, takže můžete vynechat použité části. Kompilátor nejprve vyhledá místní prostředky pro soubor, potom na všech čistých sdílených složek a všechny prostředky definované přepínač **/I.**

- Klíčová vazba: Již není nutné zadat emulátor. Pokud zadáte jeden, kompilátor bude předpokládat, že editor a emulátor jsou stejné.

- Keychord: Keychord byl vynechán. Nový formát je *Key1, Mod1, Key2, Mod2*.  Můžete určit znak, šestnáctkové nebo VK konstanty.

Nový kompilátor *vsct.exe*zkompiluje soubory *CTC* i *.vsct.* Starý kompilátor *ctc.exe* však nerozpozná ani nezkompiluje soubory *.vsct.*

Kompilátor *vsct.exe* můžete použít k převodu existujícího souboru *CTO* na soubor *.vsct.* Další informace naleznete v [tématu Postup: Vytvoření souboru .vsct z existujícího souboru CTO](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

## <a name="the-vsct-file-elements"></a>Prvky souboru .vsct
 Tabulka příkazů má následující hierarchii a prvky:

- [Element CommandTable](../../extensibility/commandtable-element.md): Představuje všechny příkazy, skupiny nabídek a nabídky přidružené k balíčku VSPackage.

- [Extern element](../../extensibility/extern-element.md): Odkazuje na všechny externí soubory H, které chcete sloučit se souborem *.vsct.*

- [Zahrnout element](../../extensibility/include-element.md): Odkazuje na všechny další soubory záhlaví (.h), které chcete zkompilovat spolu se souborem *.vsct.* Soubor *.vsct* může obsahovat soubory *H* obsahující konstanty, které definují příkazy, skupiny nabídek a nabídky, které poskytuje ide nebo jiný VSPackage.

- [Element příkazy](../../extensibility/commands-element.md): Představuje všechny jednotlivé příkazy, které lze provést. Každý příkaz má následující čtyři podřízené prvky:

- [Prvek nabídky](../../extensibility/menus-element.md): Představuje všechny nabídky a panely nástrojů v Balíčku VSPackage. Nabídky jsou kontejnery pro skupiny příkazů.

- [Groups element](../../extensibility/groups-element.md): Představuje všechny skupiny v VSPackage. Skupiny jsou kolekce jednotlivých příkazů.

- [Element tlačítka](../../extensibility/buttons-element.md): Představuje všechna příkazová tlačítka a položky nabídky v balíčku VSPackage. Tlačítka jsou vizuální ovládací prvky, které mohou být přidruženy k příkazům.

- [Bitmaps element](../../extensibility/bitmaps-element.md): Představuje všechny bitmapy pro všechny tlačítka v VSPackage. Bitmapy jsou obrázky, které se zobrazují vedle nebo na příkazových tlačítkách, v závislosti na kontextu.

- [CommandPlacements element](../../extensibility/commandplacements-element.md): Označuje další umístění, kde by měly být umístěny jednotlivé příkazy v nabídkách vašeho VSPackage.

- [VisibilityConstraints element](../../extensibility/visibilityconstraints-element.md): Určuje, zda příkaz zobrazí po celou dobu, nebo pouze v určitých kontextech, například při zobrazení určitédialogové okno nebo okno. Nabídky a příkazy, které mají hodnotu pro tento prvek, se zobrazí pouze v případě, že je aktivní zadaný kontext. Výchozí chování je zobrazení příkazu za všech okolností.

- [KeyBindings Element](../../extensibility/keybindings-element.md): Určuje všechny vazby klíče pro příkazy. To znamená jednu nebo více kombinací kláves, které je třeba stisknout ke spuštění příkazu, například **Ctrl**+**S**.

- [UsedCommands element](../../extensibility/usedcommands-element.md): [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Informuje prostředí, že i když zadaný příkaz je implementován jiným kódem, když je aktuální VSPackage aktivní, poskytuje implementaci příkazu.

- [Symboly element](../../extensibility/symbols-element.md): Obsahuje názvy symbolů a IDENTIFIKÁTORY GUID pro všechny příkazy v balíčku.

## <a name="vsct-file-design-guidelines"></a>Pokyny pro návrh souboru .vsct
 Chcete-li úspěšně navrhnout soubor *.vsct,* postupujte podle těchto pokynů.

- Příkazy lze umísťovat pouze do skupin, skupiny lze umísťovat pouze do nabídek a nabídky lze umísťovat pouze do skupin. Pouze nabídky jsou skutečně zobrazeny v ide, skupiny a příkazy nejsou.

- Podnabídky nelze přímo přiřadit k nabídce, ale musí být přiřazeny ke skupině, která je zase přiřazena k nabídce.

- Příkazy, podnabídky a skupiny lze přiřadit k jedné nadřazené skupině nebo nabídce pomocí nadřazeného pole jejich definující direktivy.

- Uspořádání příkazové tabulky výhradně prostřednictvím nadřazených polí v direktivách má významné omezení. Direktivy, které definují objekty může trvat pouze jeden nadřazený argument.

- Opětovné použití příkazů, skupin nebo podnabídek vyžaduje použití nové směrnice k vytvoření nové instance `GUID:ID` objektu s vlastním párem.

- Každá `GUID:ID` dvojice musí být jedinečná. Opětovné použití příkazu, který byl například umístěn v nabídce, panelu nástrojů nebo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> v místní nabídce, je zpracováno rozhraním.

- Příkazy a podnabídky lze také přiřadit k více skupinám a skupiny lze přiřadit k více nabídkám pomocí [elementu Příkazy](../../extensibility/commands-element.md).

## <a name="vsct-file-notes"></a>Poznámky souboru .vsct
 Pokud provedete nějaké změny souboru *.vsct* poté, co jej zkompilujete a umístíte do nativní satelitní knihovny DLL, měli byste spustit **devenv.exe /setup /nosetupvstemplates**. Tím vynutím znovu přečtené prostředky VSPackage zadané v experimentálním [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registru a vnitřní databázi, která popisuje opětovné vytvoření.

 Během vývoje je možné pro více projektů VSPackage, které mají být vytvořeny a registrovány v podregistru experimentální, které mohou vést k matoucí nepořádek v ide. Chcete-li tento problém vyřešit, můžete obnovit experimentální podregistr na výchozí nastavení odebrat všechny registrované VSPackages a všechny změny, které mohou mít provedeny v ide. Chcete-li obnovit experimentální podregistr, použijte nástroj CreateExpInstance.exe, který je dodáván s sadou Visual Studio SDK. Najdete ji na adrese:

 *%PROGRAMFILES(x86)%\Visual\\\<Studio verze> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe*

 Spusťte nástroj pomocí příkazu **CreateExpInstance /Reset**. Nezapomeňte, že tento nástroj odebere z experimentálního podregistru všechny [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]registrované balíčky VSPackages, které nejsou normálně nainstalovány s .

## <a name="see-also"></a>Viz také
- [Rozšíření nabídek a příkazů](../../extensibility/extending-menus-and-commands.md)
