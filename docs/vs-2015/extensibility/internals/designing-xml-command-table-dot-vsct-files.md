---
title: Návrh tabulky příkazů XML (. Soubory Vsct) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6c7a4e07c45c5d651af057e1eb33c23d37601cb3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762807"
---
# <a name="designing-xml-command-table-vsct-files"></a>Návrh tabulky příkazů XML (. Soubory Vsct)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Soubor XML příkaz tabulky (.vsct) popisuje rozložení a vzhled příkaz položek pro balíček VSPackage. Příkaz položky zahrnují tlačítka, pole se seznamem, nabídky, panely nástrojů a skupiny položek příkazu. Toto téma popisuje XML souborů tabulky příkazů, jak ovlivňují příkaz položky a v nabídkách a postupy jejich vytvoření.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>Příkazy, nabídky, skupin a souboru .vsct  
 soubory .vsct jsou uspořádány podle příkazy, nabídky a skupiny příkazů. Značky XML v souboru .vsct představují každou z těchto položek, společně s další související položky jako příkazová tlačítka, příkaz umístění a rastrové obrázky.  
  
 Při vytváření nového balíčku VSPackage spuštěním [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] balíček šablony, tato šablona vygeneruje souboru .vsct nezbytné prvky pro příkaz nabídky, okna nástroje nebo vlastní editor, v závislosti na zvolené položky. Tohoto souboru .vsct je pak upravit pro splnění požadavků na konkrétní VSPackage. Pro příklady k úpravě souboru .vsct, podívejte se na příklady v [rozšiřování nabídek a příkazů](../../extensibility/extending-menus-and-commands.md).  
  
 Vytvoření souboru .vsct nový, prázdný, najdete v tématu [postupy: vytvoření. Soubor Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Po vytvoření přidat prvky, atributy a hodnoty XML do souboru k popisu rozložení položky příkazu. Podrobné schématu XML, najdete v článku [VSCT – referenční dokumentace schématu XML](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>Rozdíly mezi soubory .ctc a .vsct  
 Význam za značky XML v souboru .vsct jsou stejné jako ty v aktuální zastaralý formát souboru .ctc, jejich implementace je trochu jiná.  
  
- Nové  **\<extern >** značka je, kde můžete odkazovat na jiné soubory .h ke kompilaci, třeba kroky týkající se [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nástrojů.  
  
- Zatímco .vsct soubory podpory **/ include** prohlášení, stejně jako soubory .ctc, také nabízí nový \< **import >** elementu. Rozdíl je, **/ include** přináší **všechny** informací, ale \< **import >** přináší pouze názvy.  
  
- Zatímco .ctc soubory vyžadují soubor hlaviček, ve kterém definujete preprocesor – direktivy, jeden není vyžadováno pro soubory .vsct. Místo toho umístit vaše direktivy do tabulky symbolů umístěny v  **\<Symbol >** prvky, které jsou umístěné v dolní části souboru .vsct.  
  
- Funkce souborů .vsct  **\<Poznámka >** značky, které umožňuje vložit jakékoli informace o rádi používáte, jako jsou poznámky nebo dokonce i obrázky.  
  
- Hodnoty jsou uloženy jako atributy v položce.  
  
- Příkaz příznaky lze uložit jednotlivě nebo nad sebou.  Technologie IntelliSense, však nelze použít u skládaných příkaz příznaky. Další informace o příznaků příkazů najdete v článku [Command Flag – Element](../../extensibility/command-flag-element.md).  
  
- Můžete zadat více typů, jako je například rozdělení rozevírací seznamy, combos – atd.  
  
- Ověření není GUID.  
  
- Každý prvek uživatelského rozhraní obsahuje řetězec, který představuje text, který se zobrazí s ním.  
  
- Nadřazené je volitelný. Pokud tento parametr vynechán, se používá hodnotu "Skupina neznámý".  
  
- Ikona argument je nepovinný.  
  
- Soubor rastrového obrázku části – stejně jako .ctc, s tím rozdílem, že teď můžete zadat název souboru prostřednictvím href, který bude i vsct.exe kompilátor v době kompilace.  
  
- ResID – původní ID prostředku rastrového obrázku je možné a stále funguje stejně jako v .ctc soubory.  
  
- HRef – novou metodu, která vám umožní zadat název souboru prostředku rastrového obrázku. Předpokládá, že se používají všechny, tak můžete vynechat využité části. Kompilátor vyhledá první místních prostředků pro soubor, pak na žádné čisté sdílené složky a všechny prostředky definované /I přepínačem.  
  
- Klávesové zkratky – Nepotřebujete k určení emulátoru. Pokud zadáte jednu, kompilátor bude předpokládat, že v editoru a emulátor jsou stejné.  
  
- Keychord – byla vyřazena. Nový formát je klíč1, Mod1, klic2, Mod2.  Můžete zadat znak, šestnáctkové číslo nebo konstantu VK.  
  
  Nový kompilátor, vsct.exe, zkompiluje .ctc a .vsct soubory. Staré ctc.exe kompilátoru, ale bude rozpoznat ani kompilaci souborů .vsct.  
  
  Můžete převést existující soubor .cto do souboru .vsct vsct.exe kompilátoru. Další informace o tom, naleznete v tématu [postupy: vytvoření. Vsct soubor z existující. Technologický ředitel souboru](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
## <a name="the-vsct-file-elements"></a>Prvky souborů .vsct  
 Příkaz Tabulka obsahuje následující hierarchie a prvky:  
  
 [Commandtable – Element](../../extensibility/commandtable-element.md) – reprezentuje všechny příkazy, nabídky skupin a nabídky přidružené sady VSPackage.  
  
 [Extern – Element](../../extensibility/extern-element.md) – odkazuje na všechny externí .h soubory, které chcete sloučit s souboru .vsct.  
  
 [Prvek direktivy include](../../extensibility/include-element.md) – odkazuje na další záhlaví (.h) soubory chcete kompilovat se souborem your.vsct. Souboru .vsct může obsahovat .h soubory, které obsahují konstanty, které určují příkazy skupiny nabídek a nabídek, které poskytuje integrované vývojové prostředí nebo jiné VSPackage.  
  
 [Příkazy Element](../../extensibility/commands-element.md) – reprezentuje všechny jednotlivé příkazy, které mohou být provedeny. Každý příkaz má následující čtyři podřízených elementů:  
  
 [Menus – Element](../../extensibility/menus-element.md) – reprezentuje všechny nabídek a panelů nástrojů v sady VSPackage. Nabídky jsou kontejnery pro skupiny příkazů.  
  
 [Groups – Element](../../extensibility/groups-element.md) – reprezentuje všechny skupiny v sady VSPackage. Skupiny jsou kolekce jednotlivé příkazy.  
  
 [Tlačítka Element](../../extensibility/buttons-element.md) – reprezentuje všechny příkazová tlačítka a položek nabídky v sady VSPackage. Tlačítka jsou vizuální ovládací prvky, které můžou být spojené s příkazy.  
  
 [Bitmaps – Element](../../extensibility/bitmaps-element.md) – reprezentuje všechny rastrové obrázky pro všechna tlačítka ve sady VSPackage. Rastrové obrázky mají obrázky, které zobrazují vedle nebo na příkazových tlačítkách, v závislosti na kontextu.  
  
 [Commandplacements – Element](../../extensibility/commandplacements-element.md) – označuje další umístění, kde jednotlivé příkazy by měl být umístěn v nabídkách vašeho balíčku VSPackage.  
  
 [Visibilityconstraints – Element](../../extensibility/visibilityconstraints-element.md) – Určuje, zda je nebo není příkaz zobrazí vůbec časy nebo pouze v určitých kontextech, například když se objeví dialogové okno zvláštní nebo okno. Nabídek a příkazů, které mají hodnotu u tohoto elementu se zobrazí pouze v případě, že zadaný kontext je aktivní. Výchozím chováním je zobrazení příkazu za všech okolností.  
  
 [Keybindings – Element](../../extensibility/keybindings-element.md) – Určuje všechny klávesové zkratky pro příkazy. To znamená, že nejmíň jeden kombinace kláves, které musí být stisknutí k provedení příkazu, jako například **CTRL + S**.  
  
 [Usedcommands – Element](../../extensibility/usedcommands-element.md) – Informs [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prostředí, i když zadaný příkaz je implementována jiným kódem, pokud aktuální VSPackage je aktivní, poskytuje implementace příkazu.  
  
 `Symbols Element` – Obsahuje názvy symbolů a identifikátory GUID všech příkazů v balíčku.  
  
## <a name="vsct-file-design-guidelines"></a>. Pokyny k návrhu souboru Vsct  
 Úspěšně navrhnout souboru .vsct, postupujte podle následujících pokynů.  
  
-   Příkazy lze umístit pouze do skupin, skupin je možné použít pouze v nabídkách a nabídky je možné použít pouze ve skupinách. Pouze nabídek zobrazených ve skutečnosti v rozhraní IDE, skupiny a příkazy nejsou.  
  
-   Podnabídek se nedají přímo přiřadit k nabídce, ale musí být přiřazen do skupiny, které je následně přiřazeno do nabídky.  
  
-   Příkazy, podnabídek a skupiny lze přiřadit k jedné skupině vztahy k nadřazeným položkám nebo nabídky pomocí nadřazeného pole jejich definování směrnice.  
  
-   Uspořádání příkaz tabulky výhradně prostřednictvím nadřazené pole ve směrnicích má významné omezení. Direktivy, které definují objekty může trvat argumentu pouze jeden nadřazený prvek.  
  
-   Opětovné použití příkazů, skupin nebo podnabídek vyžaduje použití nové direktivy pro vytvoření nové instance objektu vlastní `GUID:ID` pár.  
  
-   Každý `GUID:ID` dvojice musejí být jedinečné. Opětovné použití příkaz, který, například se nachází v nabídce, panel nástrojů, nebo v místní nabídce se zpracovává souborem <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní.  
  
-   Příkazy a podnabídek můžete také přiřadit k několika skupinám a skupin je možné přiřadit k více pomocí nabídky [Commands – Element](../../extensibility/commands-element.md).  
  
## <a name="vsct-file-notes"></a>. Poznámky k souboru Vsct  
 Pokud provedete změny souboru .vsct po vás i zkompilovat jej a umístěte ho do nativní satelitní knihovny DLL, měli byste spustit **devenv.exe/Setup /nosetupvstemplates**. To vynutí VSPackage prostředky zadané v experimentální registru, aby se znovu načíst a vnitřní databázi, která popisuje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ji znovu sestavit.  
  
 Během vývoje je možné pro více projektů VSPackage vytvořené a registrované v experimentální podregistru, který může mít za následek matoucí nepořádku v integrovaném vývojovém prostředí. To pokud chcete napravit, můžete resetovat experimentální hive do výchozího nastavení pro odebrání všech registrovaných rozšíření VSPackages a všechny změny, které mohou mít provedené integrovaného vývojového prostředí. Resetovat experimentální hive, použijte nástroj CreateExpInstance.exe, který je součástí sady Visual Studio SDK. Najdete ho na  
  
 **%PROGRAMFILES(x86)%\Visual Studio \<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Spusťte nástroj příkazového řádku **/reset CreateExpInstance**. Mějte na paměti, že tento nástroj odebere z podregistru experimentální všechny registrované nejsou obvykle nainstalovány s rozšířením VSPackages [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřování nabídek a příkazů](../../extensibility/extending-menus-and-commands.md)

