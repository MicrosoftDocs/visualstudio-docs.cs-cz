---
title: 'Diagramy závislostí: Pokyny'
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: b7e282ed6aa93189ab15e608a5b3abe0c56411b9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863331"
---
# <a name="dependency-diagrams-guidelines"></a>Diagramy závislostí: pokyny

Popisu architektury aplikace na vysoké úrovni tak, že vytvoříte *diagramů závislostí* v sadě Visual Studio. Ujistěte se, že váš kód zůstane konzistentní s tímto návrhem pomocí ověřování kódu pomocí diagram závislostí. Můžete také zahrnout ověřování vrstvy v procesu sestavení. Zobrazit [Video pro kanál 9: návrh a ověření architektury pomocí diagramů závislostí](http://go.microsoft.com/fwlink/?LinkID=252073).

Chcete-li zjistit, jaké edice sady Visual Studio podporují tuto funkci, přečtěte si téma [podpora edice nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Diagramy závislostí nejsou podporovány pro projekty .NET Core v sadě Visual Studio 2017.

## <a name="what-is-a-dependency-diagram"></a>Co je diagram závislostí?

Jako diagramu tradiční architektura identifikuje diagram závislostí hlavní součásti nebo funkční jednotky a jejich vzájemných závislostí. Volá se, každý uzel v diagramu *vrstvy*, představuje logické skupiny obory názvů, projekty nebo jiné artefakty. Nakreslení závislosti, které by měly existovat v návrhu. Na rozdíl od tradiční architektura diagramu můžete ověřit, že skutečné závislosti ve zdrojovém kódu odpovídají zamýšlených závislostí, které jste zadali. Tím, že část ověření regulárního sestavení na [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)], můžete zajistit, že kód programu pořád dodržovat architektury systému prostřednictvím budoucí změny. Zobrazit [diagramy závislostí: referenční](../modeling/layer-diagrams-reference.md).

## <a name="how-to-design-or-update-your-app-with-dependency-diagrams"></a>Jak návrh nebo aktualizaci vaší aplikace pomocí diagramů závislostí

Následující kroky poskytují přehled o tom, jak pomocí diagramů závislostí v rámci vývojového procesu. Pozdější části tohoto tématu popisují další podrobnosti o každém kroku. Pokud vyvíjíte novou návrhu, vynechejte kroky, které odkazují na existující kód.

> [!NOTE]
> Tyto kroky jsou v přibližné pořadí. Bude pravděpodobně chcete překrývat s úkoly, přeuspořádat je tak, aby vyhovovala vaší vlastní situaci a opakování na začátku každé iterace ve vašem projektu.

1.  [Vytvořit diagram závislostí](#Create) pro celou aplikaci nebo pro vrstvu v něm.

2.  [Definovat vrstvy představující primární funkční oblasti nebo součásti](#CreateLayers) vaší aplikace. Pojmenujte tyto vrstvy podle jejich funkce, například "Prezentaci" či "Službami". Pokud máte řešení sady Visual Studio můžete přidružit každou vrstvu s kolekcí *artefakty*, jako jsou projekty, obory názvů, soubory a tak dále.

3.  [Zjistit existujícího závislosti](#Generate) mezi vrstvami.

4.  [Úprava vrstev a závislostí](#EditArchitecture) zobrazíte aktualizovaný návrh, který má kód tak, aby odrážela.

5.  [Návrh nové oblasti vaší aplikace](#NewAreas) vytvořením vrstvy představují hlavní architektonických bloků nebo komponenty a definování závislostí za účelem zobrazení, jak ostatní každou vrstvu používá.

6.  [Upravit rozložení a vzhled diagramu](#EditLayout) můžete diskutovat s kolegy.

7.  [Ověření kódu proti diagramu závislost](#Validate) zvýrazněte konfliktů mezi kódem a architekturu, budete potřebovat.

8.  [Aktualizace kódu tak, aby odpovídal vaší nové architektury](#UpdateCode). Iterativní vývoj a Refaktorovat kód, dokud nebude ověření ukazovat žádné konflikty.

9. [Zahrnout ověřování vrstvy v procesu sestavení](#BuildValidation) zajistit, že kód pořád dodržovat do svého návrhu.

## <a name="Create"></a> Vytvořit diagram závislostí

Diagram závislostí musí být vytvořeny v projektu modelování. Můžete přidat do existujícího projektu modelování nový diagram závislostí, vytvořte nový projekt modelování pro diagram závislostí nebo zkopírovat existující diagram závislostí ve stejném projektu modelování.

> [!IMPORTANT]
> Přidat, přetáhněte nebo zkopírujte existující diagram závislostí z jednoho projektu modelování do jiného projektu modelování nebo do jiného umístění v řešení. Diagram závislostí, který je tímto způsobem zkopírují budou mít stejné odkazy jako původní diagram i v případě, že změníte diagram. To zabrání ověřování vrstev podle vašich představ a může způsobit další problémy, jako jsou například chybějící prvky nebo jiné chyby při pokusu o otevření diagramu.

Zobrazit [vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="CreateLayers"></a> Definovat vrstvy představují funkčních oblastí nebo komponenty

Vrstvy představují logické skupiny *artefakty*, jako jsou projekty, soubory kódu, obory názvů, třídy a metody. Můžete vytvořit vrstvu z artefaktů z projektů Visual C# a Visual Basic nebo připojíte specifikace nebo plány do vrstvy propojením dokumentů, jako je Word nebo prezentace aplikace PowerPoint. Každá vrstva se zobrazí jako obdélníku v diagramu a zobrazuje počet artefaktů, které jsou propojeny k němu. Vrstva může obsahovat vnořené vrstvy, které popisují podrobnější úlohy.

V rámci obecných pokynů název vrstvy podle jejich funkce, například "Prezentaci" či "Službami". Pokud artefakty, které jsou úzce vzájemně závislé, je umístíte do stejné vrstvě. Pokud artefakty, které lze aktualizovat samostatně nebo použít v samostatné aplikace, je umístíte do různých vrstev. Informace o vzorech vrstev, navštivte web vzory a postupy v [ http://go.microsoft.com/fwlink/?LinkId=145794 ](http://go.microsoft.com/fwlink/?LinkId=145794).

> [!TIP]
> Existují určité typy artefaktů, které lze propojit s vrstvami, ale nepodporují ověření proti diagram závislostí. Chcete-li zobrazit, zda artefakt podporuje ověřování, otevřete **Průzkumník vrstev** prozkoumat **podporuje ověřování** vlastnosti propojení artefaktu. Zobrazit [zjistit existujících závislostech mezi vrstvami](#Generate).

Při aktualizaci aplikace seznámeni, může také vytváření map kódu. Tyto diagramy vám můžou pomoct odhalit vzory a závislostí při zkoumání kódu. Průzkumník řešení používá k prozkoumání oborů názvů a třídy, které často odpovídají existujících vrstev. Přiřazení těchto kód artefaktů do vrstev jejich přetažením z Průzkumníka řešení do diagramů závislostí. Potom můžete diagramů závislostí můžete aktualizovat kód a zachování jejich konzistence s návrhu.

Další informace:

-   [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)

-   [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)

-   [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)

## <a name="Generate"></a> Zjistit existujících závislostech mezi vrstvami

Závislost existuje všude, kde artefakt, který je spojen s jednou vrstvou, odkazuje na artefakt, který je přidružen k jiné vrstvě. Třída v jedné vrstvě například deklaruje proměnnou, která má třídu v jiné vrstvě. Existujícího závislosti můžete zjistit pomocí zpětnou je.

> [!NOTE]
> Pro určité druhy artefaktů nelze provádět zpětnou analýzu žádných závislostí. Zpětnou analýzou například nebudou získány žádné závislosti z vrstvy nebo do ní, když je propojena s textovým souborem. Pokud chcete zobrazit, které artefakty mají závislosti, které je možné provádět zpětnou analýzu, klikněte pravým tlačítkem na jednu nebo více vrstev a klikněte na **zobrazit odkazy**. V **Průzkumník vrstev**, zkontrolujte **podporuje ověřování** sloupce. Závislosti se nebudou provést zpětnou analýzu pro artefakty, u kterých tento sloupec zobrazuje **False**.

### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Provádět zpětnou analýzu existujících závislostí mezi vrstvami

Vyberte vrstvu jeden nebo více vrstev, klikněte pravým tlačítkem na vybrané vrstvy a klikněte na **generovat závislosti**.

Obvykle se zobrazí nějaké závislosti, které by neměly existovat. Tyto závislosti lze upravit, aby odpovídaly zamýšlenému návrhu.

## <a name="EditArchitecture"></a> Úprava vrstev a závislostí za účelem zobrazení zamýšleného návrhu

K popisu změn, které máte v plánu provést vašeho systému nebo v požadované architektuře, postupujte následovně Chcete-li upravit diagram závislostí. Můžete také zvážit provádíme některé změny refaktoringu pro zlepšení strukturu kódu před jeho rozšíření. Zobrazit [zlepšení strukturu kódu](#Improving).

|**k**|**Proveďte tyto kroky**|
|-|-|
|Odstranit závislost, která by neměla existovat|Klepněte na závislost a stiskněte klávesu **odstranit**.|
|Změna nebo omezení směru závislosti|Nastavte jeho **směr** vlastnost.|
|Vytvoření nových závislostí|Použití **závislost** a **obousměrná závislost** nástroje.<br /><br /> Chcete-li nakreslit více závislostí, klikněte na nástroj dvakrát. Až budete hotovi, klikněte na tlačítko **ukazatel** nástrojů nebo stisknete klávesu **ESC** klíč.|
|Zadání toho, aby artefakty spojené s vrstvou nemohly záviset na zadaných oborech názvů|Zadejte obory názvů do vrstvy **je zakázané závislosti Namespace** vlastnost. Použijte středník (**;**) k oddělení oborů názvů.|
|Zadání toho, aby artefakty spojené s vrstvou nesměly patřit zadanému oboru názvů|Zadejte obory názvů do vrstvy **zakázané obory názvů** vlastnost. Použijte středník (**;**) k oddělení oborů názvů.|
|Zadání toho, aby artefakty spojené s vrstvou musely patřit jednomu ze zadaných oborů názvů|Zadejte obor názvů vrstvy **požadované obory názvů** vlastnost. Použijte středník (**;**) k oddělení oborů názvů.|

### <a name="Improving"></a> Zlepšení struktury kódu

Refaktorování změnami jsou vylepšení, které nemají vliv na chování aplikace, ale pomohou lépe kód změnit a v budoucnu rozšířit. Strukturované kódu je návrh, který se snadno abstraktní diagram závislostí.

Například pokud vytvoříte vrstvy pro každý obor názvů v editoru kódu a pak provést zpětnou analýzu závislostí, by měla existovat minimální sadu jednosměrné závislosti mezi vrstvami. Pokud vytvoříte více podrobný diagram použití tříd a metod jako vrstvy, pak výsledek musí být také stejné vlastnosti.

Pokud to není tento případ, kód bude obtížnější, chcete-li změnit v celé jeho životnosti a bude méně vhodná pro ověření pomocí diagramů závislostí.

## <a name="NewAreas"></a> Nové oblasti návrhu vaší aplikace

Při spuštění vývoje nový projekt nebo nové oblasti v novém projektu můžete nakreslit vrstvy a závislostech, abyste mohli identifikovat hlavní komponenty, než začnete vyvíjet kód.

-   **Zobrazit údaje vzorech architektury** do diagramů závislostí, pokud je to možné. Diagram závislostí, který popisuje aplikace klasické pracovní plochy může obsahovat třeba vrstvy, jako je například Data Store, prezentaci a logiku domény. Diagram závislostí, která zahrnuje jednu funkci v rámci aplikace může mít vrstvy, jako je Model, zobrazení a kontroler. Další informace o těchto vzorech najdete v tématu [vzory a postupy: Architektura aplikace](http://go.microsoft.com/fwlink/?LinkId=145794).

-   **Vytvořit kód artefakt pro každou vrstvu** například obor názvů, třídy nebo komponenty. Díky tomu snadněji následují kód a propojit kód artefakty do vrstvy. Jakmile vytvoříte každý artefakt, připojit ho k příslušné vrstvě.

-   **Nemáte propojení Většina tříd a jiných artefaktů do vrstev** protože spadají větší součásti, jako jsou obory názvů, které jste již propojeny s vrstvami.

-   **Vytvoření nového diagramu na novou funkci**. Obvykle bude existovat jeden nebo více diagramů závislostí popisující celou aplikaci. Pokud navrhujete novou funkci v rámci aplikace, přidat nebo změnit stávající diagramů. Místo toho vytvořte vlastní diagram, který odráží nové části kódu. Vrstvy v novém diagramu může zahrnovat prezentace, logiku domény a vrstvy databáze pro nové funkce.

     Při sestavování aplikace, kód ověří, jak proti celý diagram a diagramu podrobnější funkce.

## <a name="EditLayout"></a> Upravit rozložení pro prezentaci a diskusi

Které vám pomůžou identifikovat vrstev a závislostí nebo projednávat s členy týmu, upravte vzhled a rozložení diagramu následujícími způsoby:

-   Změna velikosti, tvary a pozice vrstvy.

-   Změna barvy vrstvy a závislosti.

    -   Vyberte jeden nebo více vrstev nebo závislosti, klikněte pravým tlačítkem a pak klikněte na tlačítko **vlastnosti**. V **vlastnosti** okně Upravit **barva** vlastnost.

## <a name="Validate"></a> Ověření kódu proti diagramu

Pokud jste upravili diagramu, můžete ověřit ho s kódem kdykoli ručně nebo automaticky pokaždé, když vytváříte.

Další informace:

-   [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)

-   [Zahrnout ověřování vrstvy v procesu sestavení](#BuildValidation)

## <a name="UpdateCode"></a> Aktualizace kódu tak, aby odpovídal na nové architektuře

Obvykle chyby se objeví při prvním ověřování kódu proti diagramu aktualizované závislostí. K těmto chybám může mít několik příčin:

-   Artefakt je přiřazen nesprávné vrstvě. V tomto případě přesuňte artefakt.

-   Artefakt, jako je například třída, používá jiné třídy způsobem, který je v konfliktu s architekturou. V tomto případě refaktorujte kód a odeberte závislost.

Chcete-li tyto chyby odstranit, aktualizujte kód, dokud se během ověřování neobjeví žádné chyby. To je obvykle iterativní proces. Další informace o těchto chybách naleznete v tématu [ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
> Při vývoji a Refaktorovat kód, můžete mít nový artefakty odkaz na diagram závislostí. Nicméně to nemusí být nezbytné, například když máte vrstvy, které představují stávající obory názvů a nový kód pouze přidá další materiály obory názvů.

Během procesu vývoje můžete chtít potlačit některé vykázané konflikty během ověřování. Například můžete chtít potlačit chyby, které již řešíte nebo které nejsou relevantní k danému scénáři. Při potlačení chyby je praktikou zaznamenat pracovní položku v Team Foundation. K provedení této úlohy, naleznete v tématu [ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md).

## <a name="BuildValidation"></a> Zahrnout ověřování vrstvy v procesu sestavení

Pokud chcete mít jistotu, že budoucí změny v kódu v souladu do diagramů závislostí, zahrňte ověřování vrstvy do vašeho řešení standardní proces sestavení. Pokaždé, když se ostatní členové týmu mohli sestavit řešení, případné rozdíly mezi závislostmi v kódu a diagram závislostí se ohlásí jako chyby sestavení. Další informace týkající se ověřování vrstvy v procesu sestavení naleznete v tématu [ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>Viz také:

- [Diagramy závislostí: Referenční dokumentace](../modeling/layer-diagrams-reference.md)
- [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)