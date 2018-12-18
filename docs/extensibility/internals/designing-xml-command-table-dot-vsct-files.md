---
title: Návrh tabulky příkazů XML (. Soubory Vsct) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4e94d93d407f7499afbd43c8af2b7532ca1b4d8e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934558"
---
# <a name="design-xml-command-table-vsct-files"></a>Návrh souborů tabulky (.vsct) příkaz XML
Tabulky příkazů XML (*.vsct*) soubor popisuje rozložení a vzhled příkaz položek pro balíček VSPackage. Příkaz položky zahrnují tlačítka, pole se seznamem, nabídky, panely nástrojů a skupiny položek příkazu. Tento článek popisuje XML souborů tabulky příkazů, jak ovlivňují příkaz položky a v nabídkách a postupy jejich vytvoření.

## <a name="commands-menus-groups-and-the-vsct-file"></a>Příkazy, nabídky, skupin a souboru .vsct
 *.Vsct* soubory jsou uspořádány podle příkazy, nabídky a skupiny příkazů. XML – značky v *.vsct* souboru představují každý z těchto položek, společně s další související položky jako příkazová tlačítka, příkaz umístění a rastrové obrázky.

 Při vytváření nového balíčku VSPackage spuštěním [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] balíček šablony, tato šablona vygeneruje *.vsct* soubor s prvky nezbytné pro příkaz nabídky, okna nástroje nebo vlastní editor, v závislosti na zvolené položky. To *.vsct* soubor pak lze upravit podle požadavků konkrétního balíčku VSPackage. Příklady toho, jak upravit *.vsct* souborů naleznete v tématu [rozšířit nabídek a příkazů](../../extensibility/extending-menus-and-commands.md).

 Vytvořit nový, prázdný *.vsct* souborů naleznete v tématu [postupy: vytvoření *.vsct* souboru](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Po vytvoření přidat prvky, atributy a hodnoty XML do souboru k popisu rozložení položky příkazu. Podrobné schématu XML, najdete v článku [– referenční dokumentace schématu VSCT XML](../../extensibility/vsct-xml-schema-reference.md).

## <a name="differences-between-ctc-and-vsct-files"></a>Rozdíly mezi soubory .ctc a .vsct
 Zatímco význam za XML – značky v *.vsct* souboru jsou stejné jako značky v nyní zastaralé *.ctc* formát souboru, jejich implementace se trochu liší:

- Nové  **\<extern >** značka je, kde můžete odkazovat na jiné *.h* soubory ke kompilaci, jako je například pro tyto soubory [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nástrojů.

- Zatímco *.vsct* soubory podpory **/ include** příkazu, jako *.ctc* do souborů, je také nabízí novou  **\<import >** element. Rozdíl je, **/ include** přináší *všechny* informací, zatímco  **\<import >** přináší pouze názvy.

- Zatímco *.ctc* soubory vyžadují soubor hlaviček, ve kterém definujete preprocesor – direktivy, jeden není vyžadováno pro *.vsct* soubory. Místo toho umístit vaše direktivy do tabulky symbolů umístěny v  **\<Symbol >** prvky, které jsou umístěné v dolní části *.vsct* souboru.

- *.vsct* funkce soubory  **\<Poznámka >** značky, které umožňuje vložit jakékoli informace o rádi používáte, jako jsou poznámky nebo dokonce i obrázky.

- Hodnoty jsou uloženy jako atributy v položce.

- Příkaz příznaky lze uložit jednotlivě nebo nad sebou.  Technologie IntelliSense, však nelze použít u skládaných příkaz příznaky. Další informace o příznaků příkazů najdete v článku [CommandFlag element](../../extensibility/command-flag-element.md).

- Můžete zadat více typů, jako je například rozdělení rozevírací seznamy, combos – atd.

- Ověření není GUID.

- Každý prvek uživatelského rozhraní obsahuje řetězec, který představuje text, který se zobrazí s ním.

- Nadřazené je volitelný. Pokud tento parametr vynechán, hodnota *skupiny neznámý* se používá.

- *Ikonu* argument je nepovinný.

- Bitmap – část: v této části jsou stejné jako v *.ctc* souboru, s tím rozdílem, že teď můžete zadat název souboru prostřednictvím Href, který bude i v *vsct.exe* kompilátor v době kompilace.

- ResID: ID může být použité a stále funguje stejně jako v prostředku rastrového obrázku starého *.ctc* soubory.

- HRef: Novou metodu, která vám umožní zadat název souboru prostředku rastrového obrázku. Předpokládá, že se používají všechny, tak můžete vynechat využité části. Kompilátor nejprve vyhledat místní prostředky pro soubor a pak na žádné čisté sdílených složek a všechny prostředky definované **/I** přepnout.

- Klávesové zkratky: Už máte k určení emulátoru. Pokud zadáte jednu, kompilátor bude předpokládat, že v editoru a emulátor jsou stejné.

- Keychord: Keychord byla vyřazena. Nový formát je *klíč1, Mod1, klic2, Mod2*.  Můžete zadat znak, šestnáctkové číslo nebo konstantu VK.
       
Nový kompilátor *vsct.exe*, zkompiluje obě *.ctc* a *.vsct* soubory. Starý *ctc.exe* kompilátoru, ale nebude rozpoznat nebo kompilací *.vsct* soubory.

Můžete použít *vsct.exe* kompilátor pro převod z existujícího *.cto* do souboru *.vsct* souboru. Další informace najdete v tématu [postupy: vytvoření souboru .vsct z existujícího souboru .cto](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

## <a name="the-vsct-file-elements"></a>Prvky souborů .vsct
 Příkaz Tabulka obsahuje následující hierarchie a prvky:

 [Commandtable – element](../../extensibility/commandtable-element.md): představuje všechny příkazy, nabídky skupin a nabídky přidružené sady VSPackage.

 [Extern – element](../../extensibility/extern-element.md): odkazuje na všechny externí .h soubory, které chcete sloučit s *.vsct* souboru.

 [Prvek direktivy include](../../extensibility/include-element.md): odkazuje na další záhlaví (.h) soubory chcete kompilovat spolu s vaší *.vsct* souboru. A *.vsct* soubor může obsahovat *.h* soubory, které obsahují konstanty, které určují příkazy skupiny nabídek a nabídek, které poskytuje integrované vývojové prostředí nebo jiné VSPackage.

 [Commands – element](../../extensibility/commands-element.md): představuje všechny jednotlivé příkazy, které mohou být provedeny. Každý příkaz má následující čtyři podřízených elementů:

 [Menus – element](../../extensibility/menus-element.md): představuje všechny nabídky a panely nástrojů v sady VSPackage. Nabídky jsou kontejnery pro skupiny příkazů.

 [Groups – element](../../extensibility/groups-element.md): představuje všechny skupiny v sady VSPackage. Skupiny jsou kolekce jednotlivé příkazy.

 [Buttons – element](../../extensibility/buttons-element.md): představuje všechny příkazy a položek nabídky v sady VSPackage. Tlačítka jsou vizuální ovládací prvky, které můžou být spojené s příkazy.

 [Bitmaps – element](../../extensibility/bitmaps-element.md): představuje všechny rastrové obrázky pro všechna tlačítka ve sady VSPackage. Rastrové obrázky mají obrázky, které zobrazují vedle nebo na příkazových tlačítkách, v závislosti na kontextu.

 [Commandplacements – element](../../extensibility/commandplacements-element.md): Určuje další umístění, kde jednotlivé příkazy by měl být umístěn v nabídkách vašeho balíčku VSPackage.

 [Visibilityconstraints – element](../../extensibility/visibilityconstraints-element.md): Určuje, zda příkaz zobrazí vůbec časy, nebo pouze v určitých kontextech, například když se objeví dialogové okno zvláštní nebo okno. Nabídek a příkazů, které mají hodnotu u tohoto elementu se zobrazí pouze v případě, že zadaný kontext je aktivní. Výchozím chováním je zobrazení příkazu za všech okolností.

 [Keybindings – element](../../extensibility/keybindings-element.md): Určuje všechny klávesové zkratky pro příkazy. To znamená, že nejmíň jeden kombinace kláves, které musí být stisknutí k provedení příkazu, jako například **Ctrl**+**S**.

 [Usedcommands – element](../../extensibility/usedcommands-element.md): informuje o tom, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prostředí, i když zadaný příkaz je implementována jiným kódem, pokud aktuální VSPackage je aktivní, poskytuje implementace příkazu.

 [Symbols – element](../../extensibility/symbols-element.md): obsahuje názvy symbolů a identifikátory GUID všech příkazů v balíčku.

## <a name="vsct-file-design-guidelines"></a>Pokyny k návrhu souboru .vsct
 Úspěšně návrhu *.vsct* souborů, postupujte podle následujících pokynů.

-   Příkazy lze umístit pouze do skupin, skupin je možné použít pouze v nabídkách a nabídky je možné použít pouze ve skupinách. Pouze nabídek zobrazených ve skutečnosti v rozhraní IDE, skupiny a příkazy nejsou.

-   Podnabídek se nedají přímo přiřadit k nabídce, ale musí být přiřazen do skupiny, které je následně přiřazeno do nabídky.

-   Příkazy, podnabídek a skupiny lze přiřadit k jedné skupině vztahy k nadřazeným položkám nebo nabídky pomocí nadřazeného pole jejich definování směrnice.

-   Uspořádání příkaz tabulky výhradně prostřednictvím nadřazené pole ve směrnicích má významné omezení. Direktivy, které definují objekty může trvat argumentu pouze jeden nadřazený prvek.

-   Opětovné použití příkazů, skupin nebo podnabídek vyžaduje použití nové direktivy pro vytvoření nové instance objektu vlastní `GUID:ID` pár.

-   Každý `GUID:ID` dvojice musejí být jedinečné. Opětovné použití příkaz, který, například se nachází v nabídce, panel nástrojů, nebo v místní nabídce se zpracovává souborem <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní.

-   Příkazy a podnabídek můžete také přiřadit k několika skupinám a skupin je možné přiřadit k více pomocí nabídky [Commands – element](../../extensibility/commands-element.md).

## <a name="vsct-file-notes"></a>Poznámky k souboru .vsct
 Pokud provedete změny *.vsct* soubor po jak zkompilovat jej a umístěte ho do nativní satelitní knihovny DLL, měli byste spustit **devenv.exe/Setup /nosetupvstemplates**. To tedy vynutí VSPackage prostředky zadané v experimentální registru, aby se znovu načíst a vnitřní databázi, která popisuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ji znovu sestavit.

 Během vývoje je možné pro více projektů VSPackage vytvořené a registrované v experimentální podregistru, který může mít za následek matoucí nepořádku v integrovaném vývojovém prostředí. To pokud chcete napravit, můžete resetovat experimentální hive do výchozího nastavení pro odebrání všech registrovaných rozšíření VSPackages a všechny změny, které mohou mít provedené integrovaného vývojového prostředí. Resetovat experimentální hive, použijte nástroj CreateExpInstance.exe, který je součástí sady Visual Studio SDK. Najdete ho na:

 *% PROGRAMFILES (x 86) %\Visual Studio\\\<verze > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe*

 Spusťte nástroj pomocí příkazu **/reset CreateExpInstance**. Mějte na paměti, že tento nástroj odebere z podregistru experimentální všechny registrované nejsou obvykle nainstalovány s rozšířením VSPackages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Viz také:
 [Rozšíření nabídek a příkazů](../../extensibility/extending-menus-and-commands.md)