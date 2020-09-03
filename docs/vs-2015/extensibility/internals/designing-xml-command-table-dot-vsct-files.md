---
title: Návrh tabulky příkazů jazyka XML (. Soubory vsct) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 987536af051de4a66b3eccadb105fd98455ddf06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196853"
---
# <a name="designing-xml-command-table-vsct-files"></a>Návrh souborů tabulky příkazů XML (.Vsct)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Soubor tabulky příkazů XML (. vsct) popisuje rozložení a vzhled položek příkazů pro VSPackage. Položky příkazů obsahují tlačítka, pole se seznamem, nabídky, panely nástrojů a skupiny položek příkazů. V tomto tématu jsou popsány soubory tabulek příkazů jazyka XML, jak ovlivňují položky příkazů a nabídky a jak je vytvořit.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>Příkazy, nabídky, skupiny a soubor. vsct  
 soubory. vsct jsou uspořádány kolem příkazů, nabídek a skupin příkazů. Značky XML v souboru. vsct reprezentují každou z těchto položek spolu s dalšími přidruženými položkami, jako jsou například příkazová tlačítka, umístění příkazů a rastry.  
  
 Při vytváření nového rozhraní VSPackage spuštěním [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] šablony balíčku vygeneruje šablona soubor. vsct s nezbytnými prvky pro příkaz nabídky, panel nástrojů nebo vlastní editor v závislosti na vašich volbách. Tento soubor. vsct je pak možné upravit tak, aby splňoval požadavky specifického VSPackage. Příklady úprav souboru. vsct najdete v příkladech [rozšíření nabídek a příkazů](../../extensibility/extending-menus-and-commands.md).  
  
 Chcete-li vytvořit nový prázdný soubor. vsct, přečtěte si téma [How to: Create a. Soubor vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md) Po vytvoření přidáte elementy XML, atributy a hodnoty do souboru pro popis rozložení položky příkazu. Podrobné schéma XML naleznete v [referenčních informacích o schématu XML vsct](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>Rozdíly mezi soubory. CTC a. vsct  
 I když je význam značek XML v souboru. vsct stejný jako ve formátu aktuálně zastaralého souboru. CTC, jejich implementace je trochu odlišná.  
  
- Nová **\<extern>** značka je místo, kde odkazujete na jiné soubory. h, které mají být zkompilovány, například pro [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] panel nástrojů.  
  
- I když soubory. vsct podporují příkaz **/include** , jako soubory. CTC, je také součástí nového \<**import> elementu * *. Rozdílem je, že **/include** přinese **všechny** informace, ale \<**import> * * převede jenom názvy.  
  
- Soubory. ctc vyžadují soubor hlaviček, ve kterém definujete direktivy preprocesoru, jeden není pro soubory. vsct vyžadován. Místo toho umístěte direktivy do tabulky symbolů nacházející se v **\<Symbol>** prvcích nacházejících se v dolní části souboru. vsct.  
  
- soubory. vsct obsahují **\<Annotation>** značku, která umožňuje vkládat libovolné informace, jako jsou poznámky nebo dokonce obrázky.  
  
- Hodnoty jsou uloženy jako atributy položky.  
  
- Příznaky příkazu mohou být uloženy jednotlivě nebo skládaný.  Technologie IntelliSense ale nefunguje na skládaných příkazových příznacích. Další informace o příznacích příkazu naleznete v tématu [příznak příkazu](../../extensibility/command-flag-element.md).  
  
- Můžete zadat více typů, například rozdělená rozevírací seznamy, Combos atd.  
  
- Identifikátory GUID se neověřují.  
  
- Každý prvek uživatelského rozhraní obsahuje řetězec, který představuje text, který se zobrazí.  
  
- Nadřazený objekt je nepovinný. Je-li tento parametr vynechán, je použita hodnota "skupina neznámá".  
  
- Argument ikony je nepovinný.  
  
- Část rastrového obrázku – totéž jako soubor. CTC, s tím rozdílem, že nyní můžete zadat název souboru prostřednictvím href, který bude v době kompilace načten kompilátorem vsct.exe.  
  
- ResID – lze použít staré ID prostředku rastrového obrázku a stále funguje stejně jako v souborech. ctc.  
  
- HRef – nová metoda, která umožňuje zadat název souboru rastrového obrázku. Předpokládá se, že se používají všechny, takže můžete vypustit použitou část. Kompilátor nejprve vyhledá místní prostředky pro daný soubor, pak na všech sdílených položkách NET a všech prostředcích definovaných přepínačem/I.  
  
- Vazba klíčů – už nemusíte zadávat emulátor. Pokud zadáte jednu, kompilátor bude předpokládat, že editor a emulátor budou stejné.  
  
- Keychord – bylo vyřazeno. Nový formát je Klíč1, MOD1, key2, MOD2.  Můžete zadat znak, šestnáctkovou nebo VK konstantu.  
  
  Nový kompilátor, vsct.exe, zkompiluje soubory. CTC a. vsct. Starý ctc.exe kompilátor však nebude rozpoznat ani kompilovat soubory. vsct.  
  
  Pomocí kompilátoru vsct.exe můžete převést existující soubor. technický ředitel na soubor. vsct. Další informace o tomto postupu naleznete v tématu [How to: Create a. Soubor vsct ze stávajícího souboru. Soubor technický ředitel](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)  
  
## <a name="the-vsct-file-elements"></a>Prvky souboru. vsct  
 Tabulka příkazů má následující hierarchii a prvky:  
  
 [Element s parametry](../../extensibility/commandtable-element.md) – představuje všechny příkazy, skupiny nabídek a nabídky přidružené k VSPackage.  
  
 [Extern – element](../../extensibility/extern-element.md) – odkazuje na jakékoli externí soubory. h, které chcete sloučit se souborem. vsct.  
  
 [Include – element](../../extensibility/include-element.md) – odkazuje na jakékoli další soubory hlaviček (. h), které chcete zkompilovat spolu se souborem. vsct. Soubor. vsct může obsahovat soubory. h obsahující konstanty definující příkazy, skupiny nabídek a nabídky, které poskytuje rozhraní IDE nebo jiné VSPackage.  
  
 [Element Commands](../../extensibility/commands-element.md) – představuje všechny jednotlivé příkazy, které lze provést. Každý příkaz má následující čtyři podřízené prvky:  
  
 [Element menu](../../extensibility/menus-element.md) – představuje všechny nabídky a panely nástrojů v VSPackage. Nabídky jsou kontejnery pro skupiny příkazů.  
  
 [Element Groups](../../extensibility/groups-element.md) – představuje všechny skupiny v VSPackage. Skupiny jsou kolekce jednotlivých příkazů.  
  
 [Buttons](../../extensibility/buttons-element.md) – představuje všechny příkazy příkazů a položky nabídky v VSPackage. Tlačítka jsou vizuální ovládací prvky, které mohou být přidruženy k příkazům.  
  
 [Rastry – element](../../extensibility/bitmaps-element.md) – představuje všechny rastrové obrázky pro všechna tlačítka v VSPackage. Rastrové obrázky jsou obrázky, které se zobrazují vedle příkazů nebo na příkazových tlačítkách v závislosti na kontextu.  
  
 [CommandPlacements Element](../../extensibility/commandplacements-element.md) – označuje další umístění, kde by měly být jednotlivé příkazy v nabídkách VSPackage.  
  
 [VisibilityConstraints element](../../extensibility/visibilityconstraints-element.md) – určuje, zda se příkaz zobrazí v každém okamžiku, nebo pouze v některých kontextech, například při zobrazení konkrétního dialogového okna nebo okna. Nabídky a příkazy, které mají hodnotu pro tento element, budou zobrazeny pouze v případě, že je zadaný kontext aktivní. Výchozím chováním je zobrazit příkaz po celou dobu.  
  
 [Element Bindings](../../extensibility/keybindings-element.md) – určuje všechny klíčové vazby pro příkazy. To znamená, že jedna nebo více kombinací kláves, které je třeba stisknout ke spuštění příkazu, například **CTRL + S**.  
  
 [UsedCommands element](../../extensibility/usedcommands-element.md) – informuje o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prostředí, že i když je zadaný příkaz implementován jiným kódem, pokud je aktuální prvek VSPackage aktivní, poskytuje implementaci příkazu.  
  
 `Symbols Element` – Obsahuje názvy symbolů a identifikátory identifikátorů GUID pro všechny příkazy v balíčku.  
  
## <a name="vsct-file-design-guidelines"></a>. Pokyny pro návrh souborů vsct  
 Chcete-li úspěšně navrhnout soubor. vsct, postupujte podle těchto pokynů.  
  
- Příkazy lze umístit pouze do skupin, skupiny lze umístit pouze do nabídek a nabídky lze umístit pouze do skupin. V integrovaném vývojovém prostředí (IDE) jsou aktuálně zobrazeny pouze nabídky, nikoli skupiny a příkazy.  
  
- Podnabídky nelze přímo přiřadit do nabídky, ale je třeba ji přiřadit ke skupině, která je zase přiřazena k nabídce.  
  
- Příkazy, podnabídky a skupiny se dají přiřadit k jedné nadřazené skupině nebo nabídce pomocí nadřazeného pole direktivy definující jejich definování.  
  
- Uspořádání tabulek příkazů výhradně prostřednictvím nadřazených polí v direktivách má významné omezení. Direktivy definující objekty mohou mít pouze jeden nadřazený argument.  
  
- Opětovné použití příkazů, skupin nebo podnabídek vyžaduje použití nové směrnice k vytvoření nové instance objektu s vlastní `GUID:ID` dvojicí.  
  
- Každý `GUID:ID` pár musí být jedinečný. Použití příkazu, který byl například umístěn v nabídce, na panelu nástrojů nebo v místní nabídce, je zpracováno <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraním.  
  
- Příkazy a podnabídky lze také přiřadit více skupinám a skupiny lze přiřadit více nabídkám pomocí [elementu Commands](../../extensibility/commands-element.md).  
  
## <a name="vsct-file-notes"></a>. Poznámky k souboru vsct  
 Pokud provedete jakékoli změny souboru. vsct po jeho kompilaci a jeho umístění do nativní satelitní knihovny DLL, měli byste spustit **devenv.exe/Setup/nosetupvstemplates**. Tím se vynutí přečtení prostředků VSPackage zadaných v experimentálním registru a interní databáze, která popisuje, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aby se znovu vytvořila.  
  
 Během vývoje je možné vytvořit a zaregistrovat více projektů VSPackage v experimentálním podregistru, což může vést k matoucímu zaplnění v integrovaném vývojovém prostředí (IDE). Chcete-li tento problém vyřešit, můžete obnovit výchozí nastavení, aby se odebraly všechny zaregistrované sady VSPackage a všechny změny, které mohly být provedeny v integrovaném vývojovém prostředí (IDE). Chcete-li obnovit experimentální podregistr, použijte nástroj CreateExpInstance.exe, který je součástí sady Visual Studio SDK. Můžete ji najít na adrese  
  
 **% PROGRAMFILES (x86)% \ Visual Studio \<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Spusťte nástroj pomocí příkazového řádku **CreateExpInstance/reset po vyčištění**. Mějte na paměti, že tento nástroj odebere z experimentálního podregistru všechny registrované sady VSPackage, které nejsou běžně nainstalovaná s nástrojem [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřování nabídek a příkazů](../../extensibility/extending-menus-and-commands.md)
